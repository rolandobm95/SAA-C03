# Preguntas de Práctica — Dominio 3: Diseño de Arquitecturas de Alto Rendimiento

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 3](../dominios/SAA_C03_Dominio3.md) · [Siguiente: Dominio 4](../dominios/SAA_C03_Dominio4.md)

---

## Tarea 3.1 — Determinar soluciones de almacenamiento escalables o de alto rendimiento

### Pregunta 1

Una empresa de producción de video necesita almacenar archivos de edición de 50-200 GB que son accedidos simultáneamente por 30 estaciones de trabajo Linux en la misma zona de disponibilidad. Los editores requieren latencia inferior a 1 milisegundo y un throughput sostenido de al menos 2 GB/s para reproducir contenido 4K en tiempo real. Los archivos se eliminan después de 30 días de completado el proyecto. ¿Cuál es la solución de almacenamiento más adecuada?

- A) Amazon EFS con modo de rendimiento Max I/O y clase de almacenamiento One Zone para maximizar throughput compartido entre las estaciones de trabajo.
- B) Amazon FSx for Lustre vinculado a un bucket S3, proporcionando acceso compartido de alto throughput con latencia sub-milisegundo.
- C) Volúmenes Amazon EBS io2 Block Express individuales de 64,000 IOPS montados en cada estación de trabajo con snapshots periódicos a S3.
- D) Amazon S3 con S3 Transfer Acceleration y multipart upload para distribuir los archivos directamente a cada estación de trabajo.

---

### Pregunta 2

Una empresa de comercio electrónico necesita migrar 80 TB de datos de imágenes de producto desde un servidor NFS on-premises a Amazon S3. La conexión de red disponible es de 1 Gbps dedicada. Los datos deben estar disponibles en S3 en un máximo de 5 días y la transferencia debe ser incremental para sincronizar cambios posteriores. Además, la aplicación on-premises seguirá necesitando acceso de baja latencia a los archivos más recientes durante los próximos 3 meses de transición. ¿Cuál es la solución que cumple todos los requisitos?

- A) Configurar AWS DataSync para transferir los datos a S3 con programación diaria para sincronización incremental, y usar AWS Storage Gateway File Gateway on-premises para proporcionar acceso local con caché a los archivos en S3.
- B) Solicitar un AWS Snowball Edge para la transferencia inicial de 80 TB y configurar AWS DataSync para las sincronizaciones incrementales posteriores.
- C) Configurar una conexión AWS Direct Connect dedicada de 10 Gbps y usar la CLI de AWS con comandos S3 sync para transferir y sincronizar los datos.
- D) Usar AWS Transfer Family con protocolo SFTP para transferir los datos a S3 y montar el bucket como sistema de archivos usando s3fs-fuse en los servidores on-premises.

---

## Tarea 3.2 — Diseñar soluciones de computación elásticas y de alto rendimiento

### Pregunta 3

Una empresa de simulación científica ejecuta cargas de trabajo de cómputo intensivo que requieren comunicación de baja latencia entre nodos. Cada simulación usa entre 50 y 500 instancias con procesadores de alto rendimiento durante 4-8 horas. Las simulaciones se ejecutan 3-4 veces por semana y pueden tolerar interrupciones siempre que se pueda guardar un checkpoint y reiniciar. La prioridad es minimizar el costo de cómputo manteniendo el rendimiento de red entre nodos. ¿Cuál es la configuración más adecuada?

- A) Instancias EC2 C6i (Compute Optimized) On-Demand en un Placement Group tipo Cluster con Elastic Fabric Adapter (EFA) habilitado.
- B) Instancias EC2 Hpc6a (HPC Optimized) Spot en un Placement Group tipo Cluster con Elastic Fabric Adapter (EFA), usando checkpoints en S3 para recuperación ante interrupciones.
- C) AWS Batch con entorno de cómputo Fargate usando instancias con 16 vCPUs y 120 GB de memoria para ejecutar las simulaciones en contenedores.
- D) Amazon EMR con instancias Spot en un clúster transitorio que se aprovisiona bajo demanda para cada simulación.

---

### Pregunta 4

Una empresa SaaS tiene una API REST que procesa transformaciones de documentos PDF. El tiempo promedio de procesamiento es de 45 segundos por documento y el tráfico varía entre 20 solicitudes por minuto en horario bajo y 2,000 solicitudes por minuto durante picos. La aplicación es stateless y cada solicitud es independiente. El equipo necesita escalar de forma automática sin administrar servidores y minimizando costos durante los períodos de bajo tráfico. El tiempo máximo aceptable de cold start es de 3 segundos. ¿Cuál es la arquitectura más adecuada?

- A) AWS Lambda con memoria de 10 GB y Provisioned Concurrency para eliminar cold starts durante los picos, expuesto a través de API Gateway.
- B) Amazon ECS Fargate con Application Auto Scaling basado en la métrica de solicitudes por target del ALB, configurando tareas con 4 vCPUs y escalado a cero durante inactividad.
- C) Instancias EC2 Graviton3 en un grupo de Auto Scaling con política de escalado basada en solicitudes por instancia del ALB y una instancia mínima para evitar cold starts.
- D) AWS App Runner con configuración de auto scaling basada en concurrencia, que escala automáticamente desde cero y gestiona el despliegue sin intervención.

---

## Tarea 3.3 — Determinar soluciones de bases de datos de alto rendimiento

### Pregunta 5

Una aplicación de juegos móviles tiene 5 millones de usuarios activos diarios y necesita almacenar perfiles de jugador, puntuaciones y estado de partidas. Las lecturas representan el 95% de las operaciones y se requiere latencia de lectura inferior a 5 milisegundos en el percentil 99. Durante eventos especiales, las lecturas se multiplican por 10x alcanzando 500,000 lecturas por segundo. El esquema de datos es flexible y los patrones de acceso están bien definidos por partition key (user_id). ¿Cuál es la solución de base de datos más adecuada?

- A) Amazon Aurora MySQL con Auto Scaling de réplicas de lectura (hasta 15 réplicas) y conexión a través de RDS Proxy para pooling de conexiones.
- B) Amazon DynamoDB con modo de capacidad On-Demand y DynamoDB Accelerator (DAX) como capa de caché in-memory para las lecturas frecuentes.
- C) Amazon ElastiCache for Redis como base de datos principal con persistencia AOF habilitada y réplicas de lectura en múltiples AZs.
- D) Amazon DynamoDB con modo de capacidad Provisioned y Auto Scaling, sin capa de caché adicional, usando Global Tables para distribución geográfica.

---

### Pregunta 6

Una empresa financiera tiene una aplicación analítica que ejecuta consultas SQL complejas sobre 15 TB de datos transaccionales históricos. Las consultas involucran JOINs entre 8-10 tablas con agregaciones, y actualmente tardan entre 30 segundos y 5 minutos en su base de datos PostgreSQL on-premises. Simultáneamente, la aplicación OLTP debe seguir procesando 5,000 transacciones por segundo con latencia inferior a 10 milisegundos. Los datos históricos se actualizan cada hora con nuevas transacciones. ¿Cuál es la arquitectura que optimiza ambas cargas de trabajo?

- A) Amazon Aurora PostgreSQL para OLTP con réplicas de lectura dedicadas exclusivamente para las consultas analíticas, usando endpoints personalizados para separar el tráfico.
- B) Amazon Aurora PostgreSQL para OLTP con zero-ETL integration hacia Amazon Redshift para las consultas analíticas, proporcionando datos casi en tiempo real sin pipelines de ETL.
- C) Amazon RDS PostgreSQL Multi-AZ para OLTP con exportación periódica de snapshots a Amazon S3 y Amazon Athena para consultas analíticas sobre archivos Parquet.
- D) Amazon Aurora PostgreSQL para OLTP y una réplica de lectura promovida a un clúster independiente para analítica, con AWS DMS para replicación continua de cambios.

---

## Tarea 3.4 — Determinar arquitecturas de red escalables o de alto rendimiento

### Pregunta 7

Una empresa global de streaming de video sirve contenido a usuarios en 50 países. La aplicación tiene un origen en us-east-1 que genera streams de video adaptativos (HLS/DASH). Los usuarios reportan buffering frecuente durante las horas pico regionales. El equipo necesita reducir la latencia del primer byte a menos de 100 milisegundos para el 95% de los usuarios globales y soportar picos de 500 Gbps de tráfico de salida. ¿Cuál es la solución de red más adecuada?

- A) AWS Global Accelerator con endpoints en múltiples regiones para enrutar el tráfico por la red de AWS y reducir la latencia del primer byte.
- B) Amazon CloudFront con Origin Shield habilitado, Lambda@Edge para personalización de contenido, y caché de segmentos de video con TTL optimizado por tipo de contenido.
- C) Desplegar la aplicación en 5 regiones adicionales con Amazon Route 53 usando política de enrutamiento por latencia para dirigir usuarios al origen más cercano.
- D) Configurar un Network Load Balancer con cross-zone load balancing y AWS Direct Connect en las regiones principales para reducir la latencia de conexión.

---

### Pregunta 8

Una empresa de servicios financieros necesita conectar su centro de datos on-premises con sus VPCs en AWS. Los requisitos son: 10 Gbps de ancho de banda garantizado, latencia predecible inferior a 5 milisegundos, y cifrado de datos en tránsito. Además, necesitan acceder a servicios públicos de AWS (S3, DynamoDB) a través de la misma conexión privada sin que el tráfico pase por internet. El diseño debe tolerar la pérdida de un enlace físico sin interrupción del servicio. ¿Cuál es la arquitectura de red que cumple todos los requisitos?

- A) Dos conexiones AWS Direct Connect de 10 Gbps en ubicaciones físicas diferentes con VPN de sitio a sitio sobre cada conexión para cifrado, usando una Virtual Private Gateway con interfaces virtuales públicas para acceder a servicios públicos de AWS.
- B) Una conexión AWS Direct Connect de 10 Gbps con una VPN de sitio a sitio como respaldo sobre internet, usando VPC endpoints de gateway para acceder a S3 y DynamoDB de forma privada.
- C) AWS Site-to-Site VPN con dos túneles IPsec redundantes usando AWS Transit Gateway, con VPC endpoints de interfaz para todos los servicios requeridos.
- D) AWS Direct Connect con un Link Aggregation Group (LAG) de 2×10 Gbps en una sola ubicación con MACsec para cifrado a nivel de capa 2, y una interfaz virtual de tránsito para enrutar a múltiples VPCs.

---

## Tarea 3.5 — Determinar soluciones de transformación e ingesta de datos

### Pregunta 9

Una plataforma de IoT industrial recibe datos de telemetría de 100,000 sensores que envían lecturas cada segundo. Cada mensaje tiene un tamaño de 1 KB. Los datos deben procesarse en tiempo real para detectar anomalías (latencia menor a 30 segundos) y simultáneamente almacenarse en un data lake para análisis históricos con consultas SQL ad-hoc. El equipo necesita una solución que escale automáticamente con el número de sensores y minimice la gestión operativa. ¿Cuál es la arquitectura de ingesta más adecuada?

- A) Amazon Kinesis Data Streams para ingesta en tiempo real con AWS Lambda como consumidor para detección de anomalías, y Amazon Data Firehose para entregar los datos en formato Parquet a S3 donde Amazon Athena ejecuta las consultas ad-hoc.
- B) Amazon MSK (Managed Streaming for Apache Kafka) con un consumidor Kafka Streams para detección de anomalías y Kafka Connect con sink connector a S3 para el data lake.
- C) Amazon SQS FIFO para recibir los mensajes de los sensores, AWS Lambda para procesarlos y detectar anomalías, y AWS Glue Streaming ETL para escribir en S3 en formato Parquet.
- D) AWS IoT Core con reglas que envíen datos a Amazon Timestream para detección de anomalías en tiempo real y exportación periódica a S3 mediante Timestream scheduled queries.

---

### Pregunta 10

Una empresa de retail necesita construir un pipeline de datos que integre información de 15 fuentes diferentes (bases de datos relacionales, APIs REST, archivos CSV en SFTP y logs de clickstream). Los datos deben transformarse, limpiarse y cargarse en un data lake centralizado en S3 cada hora. El equipo de analítica necesita consultar los datos usando SQL estándar sin gestionar infraestructura de servidores, y los datos deben catalogarse automáticamente para ser descubiertos por otros equipos. ¿Cuál es la arquitectura ETL más adecuada?

- A) AWS Glue con crawlers para descubrimiento automático de esquemas, jobs de ETL en PySpark para transformación, y Glue Data Catalog como metastore centralizado; Amazon Athena para consultas SQL serverless sobre los datos en S3.
- B) Amazon EMR con Apache Spark para transformación de datos, Apache Hive Metastore para catalogación, y Amazon Redshift Spectrum para consultas SQL directas sobre S3.
- C) AWS Lambda con funciones programadas cada hora para extraer datos de cada fuente, transformarlos con librerías Python, y almacenarlos en S3; Amazon QuickSight para consultas directas.
- D) Amazon Kinesis Data Firehose para ingesta de todas las fuentes con transformación mediante Lambda, entrega a S3 en formato Parquet, y AWS Lake Formation para catalogación y permisos.

---

# Respuestas y Explicaciones

### Pregunta 1
**Respuesta correcta: B**
**Explicación:** Amazon FSx for Lustre es un sistema de archivos de alto rendimiento diseñado específicamente para cargas de trabajo que requieren throughput masivo y latencia sub-milisegundo. Puede proporcionar cientos de GB/s de throughput y millones de IOPS, superando ampliamente los 2 GB/s requeridos. Su integración nativa con S3 permite vincular un bucket para acceso transparente a los datos. Soporta acceso compartido POSIX desde múltiples instancias simultáneamente. La opción A (EFS Max I/O) ofrece mayor throughput que el modo General Purpose pero con latencias de milisegundos, no sub-milisegundo, y su throughput máximo es significativamente menor que FSx for Lustre. La opción C (EBS io2) no permite acceso compartido entre múltiples instancias. La opción D (S3) es almacenamiento de objetos con latencias de decenas de milisegundos, inadecuado para edición de video en tiempo real.

### Pregunta 2
**Respuesta correcta: A**
**Explicación:** AWS DataSync puede saturar una conexión de 1 Gbps y transferir 80 TB en aproximadamente 8 días con overhead de protocolo, pero con compresión y optimización puede acercarse al límite de 5 días. DataSync soporta sincronización incremental nativa que solo transfiere cambios. AWS Storage Gateway File Gateway proporciona una interfaz NFS/SMB on-premises con caché local de los archivos accedidos recientemente, permitiendo acceso de baja latencia mientras los datos residen en S3. La opción B (Snowball) resolvería la transferencia inicial más rápido pero no proporciona acceso local durante la transición. La opción C (Direct Connect) requiere semanas para aprovisionarse y tiene un costo elevado para una necesidad temporal. La opción D (Transfer Family + s3fs-fuse) no ofrece caché local eficiente ni sincronización incremental optimizada.

### Pregunta 3
**Respuesta correcta: B**
**Explicación:** Las instancias Hpc6a están optimizadas para HPC con procesadores de alto rendimiento y soporte para Elastic Fabric Adapter (EFA), que proporciona latencia de red comparable a la de un clúster HPC dedicado. Un Placement Group tipo Cluster asegura que las instancias estén físicamente próximas para minimizar latencia de red. Las instancias Spot reducen el costo hasta un 90% respecto a On-Demand, y la tolerancia a interrupciones con checkpoints en S3 hace viable su uso. La opción A (On-Demand) cumple los requisitos de rendimiento pero a un costo significativamente mayor, y C6i no está específicamente optimizada para HPC. La opción C (Fargate) no soporta EFA ni Placement Groups, eliminando la comunicación de baja latencia entre nodos. La opción D (EMR) está diseñado para procesamiento de datos distribuido (MapReduce/Spark), no para simulaciones HPC que requieren paso de mensajes MPI de baja latencia.

### Pregunta 4
**Respuesta correcta: D**
**Explicación:** AWS App Runner está diseñado para aplicaciones web y APIs que necesitan escalado automático sin gestión de infraestructura. Escala automáticamente desde cero basándose en concurrencia de solicitudes, gestiona el despliegue a partir de una imagen de contenedor o código fuente, y tiene cold starts inferiores a 3 segundos para contenedores optimizados. La opción A (Lambda) tiene un timeout máximo de 15 minutos y 10 GB de memoria, pero Provisioned Concurrency tiene un costo fijo significativo y Lambda cobra por duración × memoria, resultando muy costoso para procesamiento de 45 segundos con 2,000 solicitudes/minuto. La opción B (ECS Fargate) no soporta escalado nativo a cero sin configuraciones adicionales complejas. La opción C requiere mantener al menos una instancia activa permanentemente y gestionar grupos de Auto Scaling, AMIs y despliegues.

### Pregunta 5
**Respuesta correcta: B**
**Explicación:** Amazon DynamoDB con modo On-Demand escala automáticamente para absorber picos de 500,000 lecturas/segundo sin necesidad de planificar capacidad. El modo On-Demand es ideal para tráfico impredecible con picos extremos (10x). DynamoDB Accelerator (DAX) proporciona caché in-memory completamente administrado con latencia de microsegundos para lecturas, reduciendo la carga en DynamoDB y garantizando latencia inferior a 5 ms en p99 incluso durante picos. Con un 95% de lecturas y patrones de acceso definidos por partition key, DAX es extremadamente efectivo. La opción A (Aurora) tiene un límite práctico de réplicas y no alcanza 500,000 lecturas/segundo sin sharding complejo. La opción C (ElastiCache como BD principal) no es adecuada para persistencia primaria de datos críticos de una aplicación de 5M usuarios. La opción D (DynamoDB sin DAX) no garantizaría latencia de <5 ms en p99 bajo carga extrema de 500K lecturas/segundo sin una capa de caché.

### Pregunta 6
**Respuesta correcta: B**
**Explicación:** Aurora PostgreSQL con zero-ETL integration hacia Amazon Redshift permite que los datos transaccionales estén disponibles en Redshift para análisis casi en tiempo real sin necesidad de construir ni mantener pipelines de ETL. Aurora maneja la carga OLTP con latencia inferior a 10 ms gracias a su arquitectura de almacenamiento distribuido, mientras que Redshift está optimizado para consultas analíticas complejas con JOINs masivos y agregaciones sobre terabytes de datos, reduciendo tiempos de consulta de minutos a segundos. La opción A (réplicas de lectura para analítica) penalizaría el rendimiento OLTP y las réplicas de Aurora no están optimizadas para consultas analíticas pesadas sobre 15 TB. La opción C (Athena sobre Parquet) requiere exportación periódica con horas de retraso y Athena tiene limitaciones de rendimiento en JOINs complejos sobre grandes volúmenes. La opción D (DMS + clúster independiente) introduce complejidad operativa significativa y latencia de replicación.

### Pregunta 7
**Respuesta correcta: B**
**Explicación:** Amazon CloudFront es la solución CDN global de AWS con más de 450 ubicaciones de borde que distribuyen contenido cerca de los usuarios en 50 países. Origin Shield agrega una capa de caché adicional que reduce la carga en el origen y mejora la tasa de aciertos de caché. Para streaming de video adaptativo (HLS/DASH), CloudFront cachea los segmentos de video en el edge, eliminando la latencia al origen para contenido popular. Lambda@Edge permite personalización sin agregar latencia significativa. CloudFront soporta picos de tráfico de varios Tbps. La opción A (Global Accelerator) optimiza el enrutamiento pero no cachea contenido, por lo que cada solicitud llega al origen, sin resolver el buffering. La opción C (multi-región) requiere despliegue y sincronización compleja de contenido en múltiples regiones con alto costo. La opción D (NLB + Direct Connect) no reduce latencia para usuarios globales y Direct Connect no está disponible para usuarios finales.

### Pregunta 8
**Respuesta correcta: A**
**Explicación:** Dos conexiones Direct Connect en ubicaciones físicas diferentes proporcionan resiliencia ante la pérdida de un enlace (incluyendo fallos en la ubicación física). VPN sobre Direct Connect (VPN de sitio a sitio configurada sobre la conexión DX) proporciona cifrado IPsec del tráfico en tránsito. Las interfaces virtuales públicas sobre Direct Connect permiten acceder a los endpoints públicos de AWS (S3, DynamoDB) a través de la conexión privada sin pasar por internet. La opción B tiene un solo enlace Direct Connect sin resiliencia y la VPN sobre internet como backup no garantiza latencia predecible ni 10 Gbps. La opción C (solo VPN sobre internet) no garantiza 10 Gbps ni latencia predecible de <5 ms. La opción D (LAG en una sola ubicación) no proporciona resiliencia ante fallo de la ubicación física, y MACsec requiere soporte específico del proveedor de colocación.

### Pregunta 9
**Respuesta correcta: A**
**Explicación:** Amazon Kinesis Data Streams puede ingerir 100,000 mensajes/segundo (100 MB/s con mensajes de 1 KB) escalando los shards según la demanda. AWS Lambda como consumidor de Kinesis procesa los registros en tiempo real con latencia de segundos para detección de anomalías, escalando automáticamente los invocadores paralelos por shard. Amazon Data Firehose consume del mismo stream y entrega los datos en formato Parquet a S3 con buffering configurable, optimizando costos de almacenamiento y rendimiento de consultas. Amazon Athena proporciona consultas SQL serverless ad-hoc sobre S3 sin infraestructura. La opción B (MSK) cumple funcionalidad similar pero requiere mayor gestión operativa (configurar brokers, particiones, retención) que Kinesis Data Streams que es completamente serverless. La opción C (SQS FIFO) tiene un límite de 3,000 mensajes/segundo por grupo, insuficiente para 100,000/segundo. La opción D (IoT Core + Timestream) es viable pero Timestream tiene costos elevados para escrituras masivas y no está optimizado como data lake para consultas SQL ad-hoc de gran volumen.

### Pregunta 10
**Respuesta correcta: A**
**Explicación:** AWS Glue es un servicio ETL serverless que soporta múltiples fuentes (JDBC para bases de datos, APIs con conectores personalizados, S3 para archivos CSV, y streams). Los crawlers de Glue descubren automáticamente esquemas y los registran en el Glue Data Catalog, que actúa como metastore centralizado compatible con Apache Hive, permitiendo que otros equipos descubran los datos. Los jobs de ETL en PySpark manejan transformaciones complejas sobre grandes volúmenes de datos. Amazon Athena ejecuta consultas SQL estándar directamente sobre S3 sin servidores, integrándose nativamente con Glue Data Catalog. La opción B (EMR + Hive + Redshift Spectrum) requiere gestionar clústeres EMR y no es serverless. La opción C (Lambda) tiene límites de timeout (15 min) y memoria (10 GB) que dificultan transformaciones sobre grandes volúmenes de datos de 15 fuentes diferentes. La opción D (Firehose) está diseñado para streaming continuo, no para ingesta programada desde múltiples fuentes heterogéneas como bases de datos y APIs REST.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 3](../dominios/SAA_C03_Dominio3.md) · [Siguiente: Dominio 4](../dominios/SAA_C03_Dominio4.md)
