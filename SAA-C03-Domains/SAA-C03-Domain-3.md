# AWS Certified Solutions Architect - Associate (SAA-C03)

# Dominio 3 - Diseño de Arquitecturas de Alto Rendimiento


**Navegación:** [Inicio](../README.md) · [Anterior: Preguntas - Dominio 2](../SAA-C03-Questions/SAA-C03-Questions-D2.md) · [Siguiente: Preguntas - Dominio 3](../SAA-C03-Questions/SAA-C03-Questions-D3.md)

---

> Plan de estudio organizado por tareas, módulos y enlaces a la
> documentación oficial de AWS.

------------------------------------------------------------------------

# Semana 1 - Tareas 3.1-3.2

## Objetivos

-   Seleccionar el servicio de almacenamiento adecuado según rendimiento
    y escalabilidad.
-   Comprender las diferencias entre almacenamiento de objetos, bloques
    y archivos.

## - Módulo 1 - Servicios de Almacenamiento

### Temas

-   Amazon S3
-   Amazon EBS
-   Amazon EFS
-   Amazon FSx
-   AWS Storage Gateway
-   AWS DataSync

### Debes dominar

-   Objeto vs Bloque vs Archivo
-   Durabilidad vs Disponibilidad
-   IOPS y Throughput
-   Intelligent-Tiering
-   Lifecycle Policies
-   Versioning
-   Multi-Part Upload

### Comparativas

-   S3 vs EBS
-   EBS vs EFS
-   EFS vs FSx
-   Storage Gateway vs DataSync

### Laboratorios

1.  S3 Intelligent-Tiering
2.  EBS gp3 vs io2
3.  EFS compartido entre EC2
4.  Migración con DataSync

### Documentación oficial

-   [Amazon S3](https://docs.aws.amazon.com/s3/)
-   [Amazon EBS](https://docs.aws.amazon.com/ebs/)
-   [Amazon EFS](https://docs.aws.amazon.com/efs/)
-   [Amazon FSx](https://docs.aws.amazon.com/fsx/)
-   [AWS Storage Gateway](https://docs.aws.amazon.com/storagegateway/)
-   [AWS DataSync](https://docs.aws.amazon.com/datasync/)

## - Módulo 2 - Computación

### Temas

-   Amazon EC2
-   EC2 Auto Scaling
-   AWS Auto Scaling
-   AWS Lambda
-   Amazon ECS
-   Amazon EKS
-   AWS Fargate
-   AWS Batch
-   Amazon EMR

### Debes dominar

-   Horizontal vs Vertical Scaling
-   Instancias Spot
-   Savings Plans
-   Tipos de instancias EC2
-   Stateless vs Stateful
-   Escalado basado en métricas

### Comparativas

-   EC2 vs Lambda
-   ECS vs EKS
-   ECS vs Fargate
-   Lambda vs Fargate
-   Batch vs EMR

### Laboratorios

1.  Auto Scaling
2.  ECS Fargate
3.  Lambda + API Gateway
4.  EMR para Big Data

### Documentación oficial

-   [Amazon EC2](https://docs.aws.amazon.com/ec2/)
-   [Amazon EC2 Auto
    Scaling](https://docs.aws.amazon.com/autoscaling/ec2/)
-   [AWS Auto Scaling](https://docs.aws.amazon.com/autoscaling/)
-   [AWS Lambda](https://docs.aws.amazon.com/lambda/)
-   [Amazon ECS](https://docs.aws.amazon.com/ecs/)
-   [Amazon EKS](https://docs.aws.amazon.com/eks/)
-   [AWS
    Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html)
-   [AWS Batch](https://docs.aws.amazon.com/batch/)
-   [Amazon EMR](https://docs.aws.amazon.com/emr/)

---

# Semana 2 - Tareas 3.3-3.4

## - Módulo 3 - Bases de Datos

### Temas

-   Amazon RDS
-   Amazon Aurora
-   Amazon DynamoDB
-   Amazon ElastiCache
-   Amazon MemoryDB
-   Amazon Redshift

### Debes dominar

-   Multi-AZ
-   Read Replicas
-   Aurora Global Database
-   Aurora Serverless
-   DAX
-   RDS Proxy
-   Caching
-   Particionamiento

### Comparativas

-   Aurora vs RDS
-   DynamoDB vs Aurora
-   ElastiCache vs DAX
-   Relacional vs NoSQL

### Laboratorios

1.  Aurora Read Replica
2.  DynamoDB Auto Scaling
3.  ElastiCache Redis

### Documentación oficial

-   [Amazon RDS](https://docs.aws.amazon.com/rds/)
-   [Amazon
    Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)
-   [Amazon DynamoDB](https://docs.aws.amazon.com/dynamodb/)
-   [Amazon ElastiCache](https://docs.aws.amazon.com/elasticache/)
-   [Amazon MemoryDB](https://docs.aws.amazon.com/memorydb/)
-   [Amazon Redshift](https://docs.aws.amazon.com/redshift/)

## - Módulo 4 - Redes

### Temas

-   Amazon CloudFront
-   AWS Global Accelerator
-   Elastic Load Balancing
-   AWS Direct Connect
-   AWS VPN
-   AWS PrivateLink
-   Amazon Route 53

### Debes dominar

-   ALB vs NLB vs GWLB
-   Anycast
-   Latency Routing
-   Geo Routing
-   Multi-Region
-   Híbrido

### Laboratorios

1.  CloudFront + S3
2.  ALB con Auto Scaling
3.  Direct Connect + VPN

### Documentación oficial

-   [Amazon CloudFront](https://docs.aws.amazon.com/cloudfront/)
-   [AWS Global
    Accelerator](https://docs.aws.amazon.com/global-accelerator/)
-   [Elastic Load
    Balancing](https://docs.aws.amazon.com/elasticloadbalancing/)
-   [AWS Direct Connect](https://docs.aws.amazon.com/directconnect/)
-   [AWS Site-to-Site VPN](https://docs.aws.amazon.com/vpn/)
-   [AWS
    PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/)
-   [Amazon Route 53](https://docs.aws.amazon.com/route53/)

---

# Semana 3 - Tarea 3.5

## - Módulo 5 - Analítica e Ingesta

### Temas

-   Amazon Kinesis
-   AWS Glue
-   Amazon Athena
-   AWS Lake Formation
-   Amazon QuickSight
-   AWS DataSync
-   AWS Storage Gateway

### Debes dominar

-   ETL
-   Data Lake
-   Streaming
-   Batch
-   CSV vs Parquet
-   Ingesta segura

### Laboratorios

1.  Kinesis Data Streams
2.  Glue ETL
3.  Athena sobre S3
4.  Lake Formation
5.  QuickSight Dashboard

### Documentación oficial

-   [Amazon Kinesis](https://docs.aws.amazon.com/kinesis/)
-   [AWS Glue](https://docs.aws.amazon.com/glue/)
-   [Amazon Athena](https://docs.aws.amazon.com/athena/)
-   [AWS Lake Formation](https://docs.aws.amazon.com/lake-formation/)
-   [Amazon QuickSight](https://docs.aws.amazon.com/quicksight/)
-   [AWS DataSync](https://docs.aws.amazon.com/datasync/)

------------------------------------------------------------------------

# Laboratorios recomendados

- S3 + CloudFront
- EFS + EC2
- ECS vs EKS
- Lambda + API Gateway
- Aurora Read Replicas
- DynamoDB + DAX
- ElastiCache Redis
- Route 53 + Global Accelerator
- Direct Connect
- Kinesis + Glue + Athena

---

# Notas Personales

## Conceptos Clave
<!-- Anota aquí los conceptos más importantes que debes recordar para el examen -->
- 

## Áreas de Mejora
<!-- Registra los temas donde te sientes menos seguro y necesitas repasar -->
- 

## Trucos para el Examen
<!-- Anota patrones de preguntas, palabras clave que identifican servicios, o atajos para resolver escenarios -->
- 

------------------------------------------------------------------------

# Recursos Oficiales

-   [AWS Well-Architected
    Framework](https://docs.aws.amazon.com/wellarchitected/)
-   [AWS Architecture Center](https://aws.amazon.com/architecture/)
-   [AWS Whitepapers](https://docs.aws.amazon.com/whitepapers/)
-   [AWS Skill Builder](https://explore.skillbuilder.aws/)
-   [AWS Solutions Architect Associate Exam
    Guide](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)

------------------------------------------------------------------------

# Objetivo

Al finalizar este dominio podrás diseñar soluciones de alto rendimiento
optimizando almacenamiento, cómputo, bases de datos, redes y plataformas
de analítica, seleccionando el servicio adecuado para cada escenario del
examen SAA-C03.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Preguntas - Dominio 2](../SAA-C03-Questions/SAA-C03-Questions-D2.md) · [Siguiente: Preguntas - Dominio 3](../SAA-C03-Questions/SAA-C03-Questions-D3.md)
