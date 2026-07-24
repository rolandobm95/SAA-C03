# Preguntas de Práctica — Dominio 2: Diseño de Arquitecturas Resistentes

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 2](../dominios/SAA_C03_Dominio2.md) · [Siguiente: Dominio 3](../dominios/SAA_C03_Dominio3.md)

---

## Tarea 2.1 — Diseñar arquitecturas escalables y con acoplamiento débil

### Pregunta 1

Una empresa de comercio electrónico tiene una aplicación monolítica que procesa pedidos. Durante eventos de ventas especiales, el componente de procesamiento de pagos se satura y provoca la caída de toda la aplicación. El equipo necesita desacoplar el procesamiento de pedidos para que los picos de tráfico no afecten la experiencia del usuario al navegar el catálogo. Los pedidos pueden procesarse con un retraso máximo de 5 minutos. ¿Cuál es la solución más adecuada?

- A) Implementar Amazon SNS para enviar notificaciones de pedidos directamente al componente de pagos con reintentos automáticos.
- B) Colocar una cola Amazon SQS entre el frontend y el servicio de procesamiento de pagos, con un grupo de Auto Scaling que consuma mensajes según la profundidad de la cola.
- C) Migrar toda la aplicación a AWS Lambda con API Gateway para manejar los picos de forma automática.
- D) Agregar instancias EC2 adicionales al grupo de Auto Scaling del monolito con una política de escalado basada en CPU.

---

### Pregunta 2

Una empresa está migrando su arquitectura de notificaciones. Actualmente, cuando un usuario completa un registro, el servicio backend envía un email de bienvenida, actualiza un sistema CRM externo y registra un evento en la base de datos de analítica. El equipo necesita que agregar nuevos consumidores en el futuro no requiera modificar el servicio de registro. ¿Qué arquitectura cumple este requisito con mínimo acoplamiento?

- A) Configurar Amazon SQS con una cola para cada consumidor y que el servicio de registro envíe mensajes a cada cola individualmente.
- B) Publicar el evento de registro en un tema de Amazon SNS con suscripciones para cada consumidor (Lambda para email, HTTP endpoint para CRM, cola SQS para analítica).
- C) Usar Amazon EventBridge con un bus de eventos personalizado y reglas que enruten el evento de registro a cada destino según patrones de eventos.
- D) Implementar llamadas HTTP directas desde el servicio de registro a cada consumidor con un circuit breaker para manejar fallos.

---

### Pregunta 3

Una startup necesita desplegar su aplicación de microservicios en contenedores. El equipo tiene experiencia limitada con Kubernetes y no quiere gestionar la infraestructura subyacente. La aplicación tiene patrones de tráfico impredecibles con períodos de inactividad donde no se reciben solicitudes. La prioridad es minimizar costos operativos y de infraestructura. ¿Cuál es la mejor opción de despliegue?

- A) Amazon EKS con nodos administrados de EC2 usando instancias Spot para reducir costos.
- B) Amazon ECS con tipo de lanzamiento Fargate, configurando el escalado automático con métricas de utilización de CPU.
- C) Amazon ECS con instancias EC2 reservadas para garantizar capacidad y reducir costos a largo plazo.
- D) Amazon EKS en Fargate con Karpenter para gestión automática de nodos.

---

### Pregunta 4

Una empresa de procesamiento de imágenes necesita una arquitectura que procese las imágenes cargadas por los usuarios. El procesamiento tarda entre 10 segundos y 4 minutos por imagen. La carga es variable: entre 100 y 50,000 imágenes por hora dependiendo del momento del día. El procesamiento no requiere mantener estado entre invocaciones. La empresa quiere minimizar la gestión de infraestructura. ¿Cuál es la arquitectura más adecuada?

- A) Instancias EC2 en un grupo de Auto Scaling con una AMI personalizada que incluya el software de procesamiento, escalando según mensajes en SQS.
- B) Un evento de S3 que dispare una función AWS Lambda configurada con 10 GB de memoria y un timeout de 5 minutos para procesar cada imagen.
- C) Un clúster de Amazon ECS Fargate con tareas que se escalen según la profundidad de una cola SQS donde se encolan las solicitudes de procesamiento.
- D) AWS Batch con un entorno de cómputo de tipo Fargate que ejecute trabajos de procesamiento enviados desde eventos de S3 a través de EventBridge.

---

### Pregunta 5

Una aplicación web recibe tráfico global con usuarios en Norteamérica, Europa y Asia. La aplicación tiene un API REST desplegado en us-east-1 que sirve tanto contenido dinámico como imágenes estáticas. Los usuarios de Asia reportan latencias superiores a 3 segundos al cargar las páginas. El equipo necesita reducir la latencia para todos los usuarios sin desplegar la infraestructura en múltiples regiones. ¿Cuál es la solución más efectiva?

- A) Migrar la aplicación a una instancia EC2 más grande con mayor ancho de banda de red para responder más rápido a las solicitudes.
- B) Implementar Amazon CloudFront como CDN para distribuir contenido estático y configurar un comportamiento de caché para respuestas del API con TTL corto para contenido dinámico.
- C) Configurar un Network Load Balancer con direcciones IP estáticas y AWS Global Accelerator para enrutar el tráfico por la red de AWS.
- D) Desplegar réplicas de lectura de la base de datos en las regiones de Europa y Asia para reducir la latencia de las consultas.

---

### Pregunta 6

Una aplicación de análisis financiero realiza consultas frecuentes a una base de datos Amazon RDS PostgreSQL. El 80% de las consultas son de lectura sobre los mismos reportes que se regeneran cada hora. La base de datos está experimentando alta utilización de CPU debido al volumen de consultas repetitivas. El equipo necesita reducir la carga en la base de datos sin modificar significativamente el código de la aplicación. ¿Cuál es la mejor solución?

- A) Crear múltiples réplicas de lectura de RDS y distribuir las consultas de lectura entre ellas usando un endpoint de lectura.
- B) Implementar Amazon ElastiCache for Redis como capa de caché frente a la base de datos, almacenando los resultados de los reportes con un TTL de 1 hora.
- C) Migrar la base de datos a Amazon Aurora PostgreSQL que soporta mayor concurrencia de lecturas de forma nativa.
- D) Aumentar el tamaño de la instancia RDS a un tipo de instancia optimizado para memoria con mayor capacidad de CPU.

---

## Tarea 2.2 — Diseñar arquitecturas con alta disponibilidad y tolerancia a fallos

### Pregunta 7

Una empresa opera una aplicación web crítica para el negocio con una base de datos RDS MySQL. Actualmente la aplicación está desplegada en una sola zona de disponibilidad. El requisito del negocio es que la aplicación tolere la pérdida completa de una zona de disponibilidad con un tiempo de recuperación menor a 2 minutos para la base de datos y sin pérdida de datos. ¿Cuál es la arquitectura que cumple estos requisitos?

- A) Configurar RDS con Multi-AZ deployment, desplegar instancias de aplicación en múltiples AZs detrás de un ALB, y usar Route 53 con health checks.
- B) Crear una réplica de lectura de RDS en otra AZ y promoverla manualmente en caso de fallo, con instancias EC2 en múltiples AZs.
- C) Configurar backups automáticos de RDS con point-in-time recovery y restaurar en otra AZ si la primaria falla.
- D) Implementar Amazon Aurora con Global Database para replicación multi-región con failover automático.

---

### Pregunta 8

Una empresa necesita definir una estrategia de recuperación ante desastres para su aplicación principal. Los requisitos del negocio establecen un RPO (Recovery Point Objective) de 1 hora y un RTO (Recovery Time Objective) de 15 minutos. La aplicación utiliza EC2, RDS y S3. El presupuesto es limitado pero la empresa no puede tolerar más de 15 minutos de inactividad. ¿Cuál estrategia de DR cumple con los requisitos de forma más costo-efectiva?

- A) Backup & Restore: mantener backups regulares en una región secundaria y restaurar toda la infraestructura cuando ocurra un desastre.
- B) Pilot Light: mantener los componentes críticos (RDS con réplica cross-region) activos en la región secundaria y escalar los demás componentes durante un evento de DR.
- C) Warm Standby: mantener una versión reducida pero funcional de la aplicación ejecutándose en la región secundaria, lista para escalar a producción.
- D) Multi-site Active/Active: ejecutar la aplicación a plena capacidad en ambas regiones simultáneamente con Route 53 distribuyendo el tráfico.

---

### Pregunta 9

Un equipo de operaciones necesita implementar monitoreo proactivo para una arquitectura de microservicios desplegada en Amazon ECS. La aplicación experimenta degradaciones intermitentes de rendimiento que son difíciles de diagnosticar. Necesitan identificar cuellos de botella entre servicios, recibir alertas antes de que los problemas afecten a los usuarios, y visualizar el flujo de solicitudes entre componentes. ¿Qué combinación de servicios proporciona la solución más completa?

- A) Amazon CloudWatch Logs con filtros de métricas + Amazon SNS para alertas manuales basadas en patrones de error en los logs.
- B) Amazon CloudWatch con métricas personalizadas y alarmas compuestas + AWS X-Ray para rastreo distribuido de solicitudes entre microservicios.
- C) AWS CloudTrail para auditar llamadas de API + Amazon CloudWatch Dashboards para visualización de métricas estándar de ECS.
- D) Amazon EventBridge para capturar eventos de ECS + AWS Lambda para análisis personalizado y notificaciones vía SNS.

---

### Pregunta 10

Una empresa migra su aplicación a AWS y necesita elegir servicios que maximicen la disponibilidad con el menor esfuerzo operativo. La aplicación tiene una capa web, una capa de lógica de negocio y una base de datos relacional compatible con MySQL. Los requisitos son: escalado automático en todas las capas, patching automático, tolerancia a fallos sin intervención manual y capacidad de manejar tráfico variable. ¿Cuál combinación de servicios administrados cumple estos requisitos?

- A) EC2 con Auto Scaling para la capa web + EC2 para lógica de negocio + RDS MySQL Multi-AZ.
- B) AWS Elastic Beanstalk para capas web y de negocio + Amazon RDS MySQL con réplicas de lectura.
- C) Amazon ECS Fargate con Application Load Balancer para las capas web y de negocio + Amazon Aurora MySQL con Auto Scaling de réplicas.
- D) Amazon Lightsail para la capa web + AWS Lambda para lógica de negocio + Amazon DynamoDB.

---

# Respuestas y Explicaciones

### Pregunta 1
**Respuesta correcta: B**
**Explicación:** Amazon SQS actúa como un buffer de desacoplamiento entre el frontend y el servicio de procesamiento de pagos. Los mensajes se almacenan en la cola y se procesan de forma asíncrona, absorbiendo los picos de tráfico sin afectar la experiencia del usuario. El grupo de Auto Scaling puede escalar los consumidores según la métrica ApproximateNumberOfMessagesVisible de la cola. La opción A (SNS) es un servicio push que no proporciona buffering ni manejo de backpressure. La opción C requiere una migración completa y no aborda el desacoplamiento específico del componente problemático. La opción D escala todo el monolito sin resolver el problema de acoplamiento entre componentes.

### Pregunta 2
**Respuesta correcta: C**
**Explicación:** Amazon EventBridge con un bus de eventos personalizado proporciona el máximo desacoplamiento. El servicio de registro solo publica un evento con un esquema definido, y las reglas de EventBridge enrutan el evento a los destinos correspondientes sin que el productor conozca a los consumidores. Para agregar un nuevo consumidor, solo se crea una nueva regla sin modificar el servicio de registro. EventBridge también ofrece filtrado avanzado por patrones de contenido, schema registry y archivo de eventos. La opción B (SNS) también desacopla pero requiere que el productor conozca el tema y ofrece menos capacidad de filtrado y transformación. La opción A no desacopla porque el servicio debe enviar a cada cola. La opción D crea acoplamiento directo.

### Pregunta 3
**Respuesta correcta: B**
**Explicación:** Amazon ECS con Fargate elimina la necesidad de gestionar servidores o clústeres, no requiere experiencia en Kubernetes, y cobra solo por los recursos utilizados durante la ejecución de las tareas. Con el escalado automático basado en CPU/memoria, las tareas se reducen a cero durante períodos de inactividad (si se configura con escalado a 0 mediante Application Auto Scaling), minimizando costos. La opción A requiere experiencia en Kubernetes. La opción C usa instancias reservadas que cobran 24/7 incluso sin tráfico. La opción D combina EKS (requiere experiencia en Kubernetes) con Karpenter que es un gestor de nodos EC2, agregando complejidad innecesaria.

### Pregunta 4
**Respuesta correcta: B**
**Explicación:** AWS Lambda es ideal para este escenario: procesa cada imagen de forma independiente (sin estado), escala automáticamente de 100 a 50,000 invocaciones concurrentes, no requiere gestión de infraestructura y cobra solo por tiempo de ejecución. Con 10 GB de memoria y un timeout de 15 minutos (máximo disponible), cubre los requerimientos de procesamiento de 10 segundos a 4 minutos por imagen. La opción A requiere gestionar instancias EC2 y AMIs. La opción C es viable pero agrega complejidad con la gestión de una cola SQS y configuración de tareas ECS. La opción D (AWS Batch) está diseñado para trabajos batch de larga duración y agrega latencia de programación innecesaria para un procesamiento de minutos.

### Pregunta 5
**Respuesta correcta: B**
**Explicación:** Amazon CloudFront distribuye contenido desde ubicaciones de borde (edge locations) cercanas a los usuarios globales, reduciendo drásticamente la latencia. Para contenido estático (imágenes), CloudFront lo sirve desde la caché del edge. Para contenido dinámico del API, CloudFront optimiza la conexión usando la red backbone de AWS y puede cachear respuestas con TTL corto para reducir llamadas al origen. La opción A no resuelve el problema de distancia geográfica. La opción C (Global Accelerator) mejora el enrutamiento pero no cachea contenido ni reduce la latencia de contenido estático como una CDN. La opción D requiere despliegue multi-región que el escenario explícitamente descarta.

### Pregunta 6
**Respuesta correcta: B**
**Explicación:** Amazon ElastiCache for Redis es ideal para este escenario donde el 80% de las consultas son lecturas repetitivas de datos que cambian cada hora. Al configurar un TTL de 1 hora, los resultados de los reportes se sirven desde la caché en memoria (latencia de microsegundos) sin consultar la base de datos, reduciendo drásticamente la carga en RDS. La implementación requiere mínimos cambios: verificar la caché antes de consultar la base de datos (cache-aside pattern). La opción A distribuye la carga pero no elimina las consultas repetitivas. La opción C mejora el rendimiento pero sigue procesando consultas repetitivas. La opción D es una solución temporal que no aborda la causa raíz del problema.

### Pregunta 7
**Respuesta correcta: A**
**Explicación:** RDS Multi-AZ mantiene una réplica síncrona en otra zona de disponibilidad con failover automático que típicamente completa en 60-120 segundos, cumpliendo el requisito de menos de 2 minutos de RTO. La replicación síncrona garantiza cero pérdida de datos (RPO = 0). Combinado con instancias de aplicación en múltiples AZs detrás de un ALB, la aplicación tolera la pérdida completa de una AZ. La opción B requiere promoción manual de la réplica (mayor RTO) y las réplicas de lectura usan replicación asíncrona (posible pérdida de datos). La opción C requiere restaurar desde backup, lo que puede tardar varios minutos u horas dependiendo del tamaño. La opción D es multi-región, excede los requisitos y el costo necesario para el escenario descrito.

### Pregunta 8
**Respuesta correcta: C**
**Explicación:** Warm Standby mantiene una versión reducida pero funcional de la aplicación en la región secundaria, permitiendo failover en minutos (cumple RTO de 15 minutos) simplemente escalando los recursos. Con réplicas cross-region de RDS y replicación de S3, el RPO de 1 hora se cumple fácilmente. La opción A (Backup & Restore) tiene un RTO de horas porque requiere provisionar toda la infraestructura desde cero. La opción B (Pilot Light) requiere provisionar y configurar componentes de cómputo durante el evento, lo que puede exceder los 15 minutos de RTO si la infraestructura es compleja. La opción D cumple los requisitos pero es significativamente más costosa y no es la opción más costo-efectiva.

### Pregunta 9
**Respuesta correcta: B**
**Explicación:** Amazon CloudWatch con métricas personalizadas permite monitorear indicadores específicos de la aplicación, y las alarmas compuestas permiten crear alertas sofisticadas que detectan degradaciones antes de que afecten a los usuarios (por ejemplo, combinando latencia alta + tasa de errores elevada). AWS X-Ray proporciona rastreo distribuido que muestra el flujo completo de solicitudes entre microservicios, identifica cuellos de botella, y genera mapas de servicio para visualizar las dependencias. La opción A es reactiva y no identifica cuellos de botella entre servicios. La opción C audita llamadas de API pero no rastrea solicitudes de usuario entre microservicios. La opción D captura eventos de infraestructura pero no proporciona rastreo de solicitudes ni métricas de rendimiento de aplicación.

### Pregunta 10
**Respuesta correcta: C**
**Explicación:** Amazon ECS Fargate elimina la gestión de servidores, escala automáticamente las tareas, y se integra con ALB para distribución de tráfico. Amazon Aurora MySQL ofrece compatibilidad total con MySQL, alta disponibilidad con replicación en 3 AZs, failover automático en menos de 30 segundos, Auto Scaling de réplicas de lectura, y patching automático. Esta combinación maximiza la disponibilidad con mínima intervención operativa. La opción A requiere gestionar instancias EC2 y patching manual. La opción B (Elastic Beanstalk) simplifica el despliegue pero tiene menos flexibilidad para microservicios y RDS MySQL estándar no iguala la disponibilidad de Aurora. La opción D mezcla servicios incompatibles: DynamoDB no es relacional ni compatible con MySQL, y Lightsail no está diseñado para cargas variables de producción.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 2](../dominios/SAA_C03_Dominio2.md) · [Siguiente: Dominio 3](../dominios/SAA_C03_Dominio3.md)
