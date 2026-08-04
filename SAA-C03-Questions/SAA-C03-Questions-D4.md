# Preguntas de Práctica - Dominio 4: Diseño de Arquitecturas con Optimización de Costos

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 4](../SAA-C03-Domains/SAA-C03-Domain-4.md) · [Siguiente: Índice de Servicios](../SAA-C03-Services/SAA_C03_Servicios.md)

---

## Tarea 4.1 - Diseñar soluciones de almacenamiento rentables

### Pregunta 1

Una empresa almacena 50 TB de registros de auditoría en Amazon S3 Standard. Los registros deben conservarse por 7 años por cumplimiento normativo, pero después del primer mes rara vez se consultan. Cuando se necesitan, la empresa puede tolerar un tiempo de recuperación de hasta 12 horas. El arquitecto debe reducir los costos de almacenamiento al mínimo posible sin comprometer el cumplimiento. ¿Cuál es la solución más rentable?

- A) Configurar una Lifecycle Policy que mueva los objetos a S3 Glacier Flexible Retrieval después de 30 días y a S3 Glacier Deep Archive después de 90 días.
- B) Migrar todos los registros inmediatamente a S3 Intelligent-Tiering y dejar que el servicio optimice automáticamente la clase de almacenamiento.
- C) Configurar una Lifecycle Policy que mueva los objetos a S3 Standard-IA después de 30 días y eliminar los objetos después de 365 días.
- D) Configurar S3 One Zone-IA para todos los registros y habilitar versionado para protección contra eliminación accidental.

---

### Pregunta 2

Una empresa ejecuta una aplicación de análisis de datos que requiere un volumen de almacenamiento con alto rendimiento secuencial para procesar archivos de logs de 500 GB diarios. Las operaciones son principalmente de lectura/escritura secuencial con throughput sostenido. La empresa quiere minimizar costos de almacenamiento sin afectar el rendimiento de la carga de trabajo. El volumen actual es un gp3 de 1 TB. ¿Cuál es la recomendación más rentable?

- A) Mantener el volumen gp3 pero aumentar el throughput provisionado a 1,000 MB/s.
- B) Cambiar a un volumen st1 (Throughput Optimized HDD) que ofrece alto throughput secuencial a menor costo por GB.
- C) Cambiar a un volumen io2 Block Express para maximizar el rendimiento de I/O.
- D) Cambiar a un volumen sc1 (Cold HDD) para minimizar el costo de almacenamiento.

---

### Pregunta 3

Una empresa tiene un centro de datos on-premises con 200 TB de datos de archivo que necesita migrar a AWS. Después de la migración, las aplicaciones on-premises deben seguir accediendo a un subconjunto de los datos con baja latencia mediante protocolo NFS, mientras que el almacenamiento principal debe estar en S3 para reducir costos de infraestructura local. ¿Cuál es la solución más rentable que cumple estos requisitos?

- A) Utilizar AWS DataSync para migrar todos los datos a S3 y acceder directamente desde las aplicaciones on-premises mediante S3 API.
- B) Desplegar AWS Storage Gateway en modo File Gateway on-premises, que almacena los datos en S3 y mantiene una caché local de los archivos más accedidos.
- C) Configurar AWS Direct Connect y montar un bucket S3 como sistema de archivos utilizando s3fs-fuse en los servidores on-premises.
- D) Migrar todos los datos a Amazon EFS con acceso cross-region y conectar las aplicaciones on-premises mediante VPN.

---

## Tarea 4.2 - Diseñar soluciones de computación rentables

### Pregunta 4

Una empresa ejecuta un pipeline de procesamiento de video que convierte archivos en múltiples formatos. El procesamiento de cada video tarda entre 10 y 45 minutos y puede reiniciarse sin pérdida de progreso si se interrumpe. La carga de trabajo es variable: entre semana procesa 100 videos diarios y los fines de semana solo 10. Actualmente usan instancias On-Demand m5.xlarge 24/7. El arquitecto debe reducir costos significativamente. ¿Cuál es la estrategia más rentable?

- A) Comprar Reserved Instances de 1 año con pago total anticipado para las instancias m5.xlarge.
- B) Utilizar Spot Instances con una cola SQS que distribuya los trabajos y Auto Scaling que lance instancias solo cuando hay videos en la cola.
- C) Migrar el procesamiento a funciones Lambda con un timeout de 15 minutos y dividir cada video en segmentos más pequeños.
- D) Implementar Savings Plans de computación con un compromiso basado en el uso promedio semanal.

---

### Pregunta 5

Una startup tiene una aplicación web con tráfico predecible durante horario laboral (8:00-20:00) que requiere un mínimo de 4 instancias, y un pico estacional durante dos meses al año donde necesita hasta 20 instancias. Fuera de horario laboral, 2 instancias son suficientes. La empresa quiere optimizar costos manteniendo la disponibilidad. ¿Cuál es la estrategia de compra más rentable?

- A) Comprar 20 Reserved Instances de 3 años para cubrir el pico estacional completo.
- B) Comprar Savings Plans para 4 instancias base, usar On-Demand para las instancias adicionales durante horario laboral y Spot para el escalado estacional.
- C) Usar exclusivamente On-Demand con Auto Scaling para ajustarse automáticamente a la demanda.
- D) Comprar 2 Reserved Instances, complementar con Savings Plans para las 2 instancias adicionales del horario laboral y usar Spot Instances para el escalado estacional con fallback a On-Demand.

---

### Pregunta 6

Una empresa tiene una API que procesa solicitudes de forma variable: recibe entre 0 y 10,000 solicitudes por hora, con cada solicitud requiriendo 200 ms de procesamiento y 256 MB de memoria. Actualmente ejecutan un contenedor en una instancia EC2 t3.medium que permanece encendida 24/7. La empresa quiere pagar solo por el tiempo de procesamiento real. ¿Cuál es la opción más rentable?

- A) Migrar a AWS Lambda detrás de API Gateway, pagando solo por las invocaciones y el tiempo de ejecución.
- B) Migrar a AWS Fargate con un servicio ECS que escale a cero cuando no haya solicitudes.
- C) Cambiar a una instancia t3.nano con Savings Plans de 1 año para reducir el costo de la instancia.
- D) Implementar un Auto Scaling Group con instancias Spot que reduzca a una instancia mínima durante periodos de bajo tráfico.

---

## Tarea 4.3 - Diseñar soluciones de bases de datos rentables

### Pregunta 7

Una aplicación SaaS multi-tenant tiene patrones de uso impredecibles: algunos tenants generan picos de miles de lecturas por segundo durante minutos y luego permanecen inactivos por horas. La empresa usa DynamoDB con capacidad provisionada de 5,000 RCU y 2,000 WCU, pero la utilización promedio es solo del 15%. El arquitecto necesita reducir costos sin afectar el rendimiento durante los picos. ¿Cuál es la solución más rentable?

- A) Reducir la capacidad provisionada a 1,000 RCU y 500 WCU para ajustarla a la utilización promedio.
- B) Cambiar la tabla a modo de capacidad On-Demand, que escala automáticamente y cobra solo por las lecturas/escrituras realizadas.
- C) Mantener la capacidad provisionada actual y agregar DynamoDB Accelerator (DAX) para reducir las lecturas directas a la tabla.
- D) Migrar a Amazon Aurora Serverless v2 que escala automáticamente según la demanda.

---

### Pregunta 8

Una empresa tiene una aplicación de reportes que ejecuta consultas intensivas contra una base de datos Aurora MySQL. Los reportes se generan diariamente a las 6:00 AM y el proceso dura 2 horas. El resto del día, la base de datos solo recibe escrituras transaccionales ligeras de la aplicación principal. Actualmente usan una instancia Aurora db.r6g.2xlarge (8 vCPU, 64 GB RAM) ejecutándose 24/7. ¿Cuál es la estrategia más rentable para reducir costos?

- A) Crear una Read Replica de Aurora que se encienda solo durante las 2 horas de reportes usando Aurora Serverless v2, y mantener la instancia principal con un tamaño menor (db.r6g.large) para las escrituras.
- B) Migrar toda la base de datos a Aurora Serverless v2 para que escale automáticamente según la carga.
- C) Implementar ElastiCache Redis para cachear los resultados de los reportes y reducir la carga en la base de datos.
- D) Comprar una Reserved Instance de 3 años para la instancia db.r6g.2xlarge actual.

---

## Tarea 4.4 - Diseñar arquitecturas de redes con optimización de costos

### Pregunta 9

Una empresa tiene una aplicación en una VPC que realiza miles de llamadas diarias a la API de Amazon S3 y Amazon DynamoDB. Todo el tráfico sale a internet a través de un NAT Gateway, generando costos significativos de procesamiento de datos. El arquitecto debe reducir los costos de red sin modificar la arquitectura de la aplicación. ¿Cuál es la solución más rentable?

- A) Reemplazar el NAT Gateway con una instancia NAT (NAT Instance) en una instancia t3.micro para reducir el costo por hora.
- B) Crear Gateway VPC Endpoints para S3 y DynamoDB, eliminando la necesidad de que ese tráfico pase por el NAT Gateway.
- C) Mover las instancias de la aplicación a subnets públicas con Elastic IPs para evitar el NAT Gateway.
- D) Implementar AWS PrivateLink para todos los servicios de AWS utilizados por la aplicación.

---

### Pregunta 10

Una empresa distribuye contenido estático (imágenes, videos y documentos) almacenado en un bucket S3 en us-east-1 a usuarios globales. Actualmente los usuarios acceden directamente al bucket S3, generando altos costos de transferencia de datos salientes y experimentando latencia elevada desde regiones lejanas como Asia-Pacífico y Europa. ¿Cuál es la solución más rentable para reducir costos de transferencia y mejorar el rendimiento?

- A) Replicar el bucket S3 a múltiples regiones usando S3 Cross-Region Replication y dirigir a los usuarios a la región más cercana con Route 53 latency-based routing.
- B) Colocar una distribución de Amazon CloudFront delante del bucket S3, aprovechando el caché en edge locations y las tarifas reducidas de transferencia de datos.
- C) Migrar el contenido a instancias EC2 con Elastic IPs en múltiples regiones usando Global Accelerator para enrutamiento.
- D) Habilitar S3 Transfer Acceleration para que los usuarios suban y descarguen contenido a través de los edge locations de CloudFront.

---

# Respuestas y Explicaciones

### Pregunta 1
**Respuesta correcta: A**
**Explicación:** Una Lifecycle Policy que transicione los objetos a S3 Glacier Flexible Retrieval (después del primer mes de acceso frecuente) y luego a S3 Glacier Deep Archive (la clase más económica de S3, ideal para archivos de largo plazo) ofrece el menor costo posible. Glacier Deep Archive cuesta aproximadamente $0.00099/GB/mes, es decir, hasta un 95% menos que S3 Standard. El tiempo de recuperación de 12 horas aceptable se alinea perfectamente con Deep Archive (12 horas estándar). La opción B (Intelligent-Tiering) no mueve datos automáticamente a las capas de Glacier sin configuración adicional de Archive Access. La opción C elimina los datos después de 365 días, violando la retención de 7 años. La opción D (One Zone-IA) no ofrece el menor costo y tiene menor durabilidad al usar una sola zona.

### Pregunta 2
**Respuesta correcta: B**
**Explicación:** Los volúmenes st1 (Throughput Optimized HDD) están diseñados específicamente para cargas de trabajo con acceso secuencial frecuente que requieren alto throughput a bajo costo. Ofrecen hasta 500 MB/s de throughput a un costo de $0.045/GB/mes, significativamente menor que gp3 ($0.08/GB/mes). Para procesamiento de logs con patrón de lectura/escritura secuencial, st1 es la opción óptima en relación costo-rendimiento. La opción A mantiene un volumen SSD más caro cuando no se necesita rendimiento de IOPS aleatorias. La opción C (io2) es la más costosa y está diseñada para cargas transaccionales de baja latencia, no para throughput secuencial. La opción D (sc1) tiene throughput insuficiente (máximo 250 MB/s) para una carga de trabajo intensiva.

### Pregunta 3
**Respuesta correcta: B**
**Explicación:** AWS Storage Gateway en modo File Gateway presenta un sistema de archivos NFS/SMB a las aplicaciones on-premises mientras almacena los datos en S3. La caché local asegura baja latencia para los archivos más accedidos, cumpliendo ambos requisitos: acceso NFS con baja latencia y almacenamiento principal en S3 para reducir costos. La opción A no proporciona acceso NFS con baja latencia desde on-premises. La opción C (s3fs-fuse) no es una solución soportada oficialmente por AWS y tiene problemas de rendimiento y consistencia. La opción D usa EFS que es significativamente más costoso que S3 para 200 TB de datos de archivo y no optimiza costos.

### Pregunta 4
**Respuesta correcta: B**
**Explicación:** Spot Instances ofrecen hasta un 90% de descuento respecto a On-Demand y son ideales para cargas de trabajo tolerantes a interrupciones. Combinadas con SQS (que actúa como buffer de trabajos) y Auto Scaling, la infraestructura solo existe cuando hay videos por procesar. Si una instancia Spot se interrumpe, el mensaje vuelve a la cola y otro worker lo procesa. La opción A no aborda la variabilidad de carga y paga por capacidad reservada incluso los fines de semana con baja utilización. La opción C no funciona porque Lambda tiene un timeout máximo de 15 minutos y los videos tardan hasta 45 minutos. La opción D compromete un pago fijo basado en un promedio que no refleja los periodos de inactividad.

### Pregunta 5
**Respuesta correcta: D**
**Explicación:** La estrategia óptima combina múltiples modelos de compra para cada capa de demanda: Reserved Instances (o Savings Plans) para la capacidad base mínima que siempre se necesita (2 instancias 24/7), Savings Plans adicionales para la capa predecible del horario laboral (2 instancias más), y Spot Instances para los picos estacionales que son tolerantes a interrupciones (con fallback a On-Demand si Spot no está disponible). La opción A desperdicia el 90% de la capacidad reservada durante la mayor parte del año. La opción B es cercana pero pagar 4 instancias de Savings Plans es más caro fuera de horario laboral cuando solo se necesitan 2. La opción C es la más costosa al usar solo On-Demand sin descuentos.

### Pregunta 6
**Respuesta correcta: A**
**Explicación:** AWS Lambda es ideal para este patrón: solicitudes de corta duración (200 ms), bajo consumo de memoria (256 MB) y tráfico variable que puede llegar a cero. Con Lambda se paga exactamente por el tiempo de computación consumido (por cada 1 ms de ejecución), sin pagar por tiempo inactivo. Para 10,000 solicitudes/hora × 200 ms × 256 MB, el costo de Lambda es significativamente menor que mantener una instancia 24/7. La opción B (Fargate) no escala a cero de forma instantánea y tiene un costo mínimo por tarea. La opción C reduce el costo de la instancia pero sigue pagando 24/7 incluso cuando no hay solicitudes. La opción D aún requiere mantener al menos una instancia ejecutándose y tiene costos fijos de la infraestructura de Auto Scaling.

### Pregunta 7
**Respuesta correcta: B**
**Explicación:** El modo On-Demand de DynamoDB es ideal para cargas impredecibles y con baja utilización promedio. Cobra exactamente por cada lectura/escritura realizada sin necesidad de provisionar capacidad. Con solo 15% de utilización de la capacidad provisionada, la empresa está pagando por el 85% de capacidad no utilizada. On-Demand maneja automáticamente los picos de miles de lecturas por segundo sin planificación. La opción A degradaría el rendimiento durante los picos. La opción C agrega costo de DAX pero no resuelve el problema fundamental de capacidad ociosa. La opción D implica una migración compleja y Aurora no escala de la misma forma para patrones de acceso de clave-valor.

### Pregunta 8
**Respuesta correcta: A**
**Explicación:** Crear una Read Replica con Aurora Serverless v2 para los reportes permite escalar la capacidad de lectura solo durante las 2 horas necesarias (pagando ACU solo cuando se usa) y reducir la instancia principal a un tamaño menor para las escrituras ligeras del resto del día. Esto optimiza costos al pagar alta capacidad solo 2 horas/día en lugar de 24. La opción B migra todo a Serverless v2, lo cual podría ser más costoso para las escrituras sostenidas de la aplicación principal si hay un mínimo de ACU alto. La opción C no reduce el costo de la instancia sobredimensionada y agrega costo de ElastiCache. La opción D bloquea el compromiso por 3 años con una instancia sobredimensionada para 22 horas del día.

### Pregunta 9
**Respuesta correcta: B**
**Explicación:** Los Gateway VPC Endpoints para S3 y DynamoDB son gratuitos (sin costo por hora ni por GB procesado) y permiten que el tráfico hacia estos servicios fluya directamente por la red privada de AWS sin pasar por el NAT Gateway. Dado que el NAT Gateway cobra $0.045/GB procesado, eliminar miles de llamadas diarias a S3 y DynamoDB del tráfico NAT genera un ahorro significativo. La opción A reduce el costo por hora pero sigue cobrando por procesamiento de datos y agrega responsabilidad operativa. La opción C expone las instancias a internet, comprometiendo la seguridad. La opción D (PrivateLink/Interface Endpoints) tiene un costo por hora y por GB, siendo más costosa que los Gateway Endpoints para S3 y DynamoDB.

### Pregunta 10
**Respuesta correcta: B**
**Explicación:** Amazon CloudFront reduce los costos de transferencia de datos porque las tarifas de transferencia desde CloudFront son menores que las tarifas de transferencia directa desde S3 (especialmente para volúmenes altos). Además, el caché en edge locations reduce la cantidad de solicitudes al origen S3, disminuyendo aún más los costos. CloudFront también mejora la latencia global sirviendo contenido desde la ubicación más cercana al usuario. La opción A duplica los costos de almacenamiento en múltiples regiones y las tarifas de replicación, sin reducir el costo de transferencia por solicitud. La opción C usa EC2 que es significativamente más costoso que S3 para servir contenido estático. La opción D (Transfer Acceleration) está diseñada para uploads, no para distribución de contenido, y tiene un costo adicional por GB transferido.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 4](../SAA-C03-Domains/SAA-C03-Domain-4.md) · [Siguiente: Índice de Servicios](../SAA-C03-Services/SAA_C03_Servicios.md)
