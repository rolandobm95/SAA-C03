# AWS Certified Solutions Architect -- Associate (SAA-C03)

# Dominio 4 -- Diseño de Arquitecturas con Optimización de Costos

> **Progreso: 0/4 módulos completados**

**Navegación:** [🏠 Inicio](README.md) · [⬅️ Anterior: Preguntas — Dominio 3](SAA_C03_Preguntas_D3.md) · [Siguiente: Preguntas — Dominio 4 ➡️](SAA_C03_Preguntas_D4.md)

---

> Plan de estudio organizado por tareas, módulos, laboratorios y enlaces
> a la documentación oficial de AWS.

------------------------------------------------------------------------

# Semana 1 -- Tareas 4.1-4.2

## Tarea 4.1 Diseñar soluciones de almacenamiento rentables

### Objetivos

-   Seleccionar el almacenamiento con el menor costo que cumpla los
    requisitos.
-   Optimizar el ciclo de vida y la retención de datos.
-   Reducir costos de transferencia y almacenamiento.

## - [ ] Módulo 1 -- Almacenamiento Optimizado

### Temas

-   Amazon S3
-   Amazon EBS
-   Amazon EFS
-   Amazon FSx
-   AWS Storage Gateway
-   AWS DataSync
-   AWS Transfer Family

### Debes dominar

-   Clases de almacenamiento de S3
-   Lifecycle Policies
-   Intelligent-Tiering
-   Glacier Instant Retrieval
-   Glacier Flexible Retrieval
-   Glacier Deep Archive
-   Versioning
-   Requester Pays
-   gp3 vs io2 vs st1 vs sc1

### Comparativas

-   S3 Standard vs Intelligent-Tiering
-   Glacier Flexible vs Deep Archive
-   EBS SSD vs HDD
-   EFS vs FSx

### Laboratorios

1.  Configurar Lifecycle de S3.
2.  Migrar datos con DataSync.
3.  Comparar costos gp3 vs io2.
4.  Archivar objetos a Glacier.

### Documentación oficial

-   [Amazon S3](https://docs.aws.amazon.com/s3/)
-   [Amazon EBS](https://docs.aws.amazon.com/ebs/)
-   [Amazon EFS](https://docs.aws.amazon.com/efs/)
-   [Amazon FSx](https://docs.aws.amazon.com/fsx/)
-   [AWS Storage Gateway](https://docs.aws.amazon.com/storagegateway/)
-   [AWS DataSync](https://docs.aws.amazon.com/datasync/)
-   [AWS Transfer Family](https://docs.aws.amazon.com/transfer/)

## Tarea 4.2 Diseñar soluciones de computación rentables

## - [ ] Módulo 2 -- Computación Optimizada

### Temas

-   Amazon EC2
-   AWS Lambda
-   AWS Fargate
-   Auto Scaling
-   AWS Outposts

### Debes dominar

-   On-Demand
-   Spot Instances
-   Reserved Instances
-   Savings Plans
-   Horizontal vs Vertical Scaling
-   Hibernación de EC2
-   Rightsizing

### Comparativas

-   EC2 vs Lambda
-   Lambda vs Fargate
-   Spot vs Reserved
-   Savings Plans vs Reserved Instances

### Laboratorios

1.  Auto Scaling basado en CPU.
2.  Migrar EC2 a Lambda.
3.  Simular ahorro con Spot.

### Documentación oficial

-   [Amazon EC2](https://docs.aws.amazon.com/ec2/)
-   [AWS Lambda](https://docs.aws.amazon.com/lambda/)
-   [AWS
    Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html)
-   [Amazon EC2 Auto
    Scaling](https://docs.aws.amazon.com/autoscaling/ec2/)
-   [AWS Outposts](https://docs.aws.amazon.com/outposts/)

------------------------------------------------------------------------

# Semana 2 -- Tarea 4.3 Diseñar soluciones de bases de datos rentables

## - [ ] Módulo 3 -- Bases de Datos

### Temas

-   Amazon RDS
-   Amazon Aurora
-   Amazon DynamoDB
-   Amazon ElastiCache
-   Amazon RDS Proxy

### Debes dominar

-   Read Replicas
-   Multi-AZ
-   Aurora Serverless
-   DynamoDB On-Demand vs Provisioned
-   Backup y Retención
-   Caché con Redis

### Comparativas

-   Aurora vs RDS
-   DynamoDB vs Aurora
-   Provisioned vs On-Demand
-   ElastiCache vs RDS Proxy

### Laboratorios

1.  DynamoDB Auto Scaling.
2.  Aurora Serverless.
3.  Redis Cache.

### Documentación oficial

-   [Amazon RDS](https://docs.aws.amazon.com/rds/)
-   [Amazon
    Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)
-   [Amazon DynamoDB](https://docs.aws.amazon.com/dynamodb/)
-   [Amazon ElastiCache](https://docs.aws.amazon.com/elasticache/)
-   [Amazon RDS
    Proxy](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy.html)

------------------------------------------------------------------------

# Semana 3 -- Tarea 4.4 Diseñar arquitecturas de redes con optimización de costos

## - [ ] Módulo 4 -- Redes

### Temas

-   NAT Gateway
-   NAT Instance
-   Amazon CloudFront
-   AWS Global Accelerator
-   AWS Direct Connect
-   AWS Site-to-Site VPN
-   AWS Transit Gateway
-   VPC Peering
-   AWS PrivateLink
-   Amazon Route 53

### Debes dominar

-   Costos de transferencia entre AZ y regiones
-   NAT Gateway vs NAT Instance
-   CDN y caché perimetral
-   VPC Endpoints para reducir tráfico NAT
-   Direct Connect vs VPN

### Comparativas

-   NAT Gateway vs NAT Instance
-   Direct Connect vs VPN
-   Transit Gateway vs VPC Peering
-   CloudFront vs S3 directo

### Laboratorios

1.  VPC Endpoint para S3.
2.  CloudFront delante de S3.
3.  Comparar costos NAT.

### Documentación oficial

-   [Amazon CloudFront](https://docs.aws.amazon.com/cloudfront/)
-   [AWS Global
    Accelerator](https://docs.aws.amazon.com/global-accelerator/)
-   [AWS Direct Connect](https://docs.aws.amazon.com/directconnect/)
-   [AWS Site-to-Site VPN](https://docs.aws.amazon.com/vpn/)
-   [AWS Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/)
-   [AWS
    PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/)
-   [Amazon Route 53](https://docs.aws.amazon.com/route53/)

## Herramientas de Administración de Costos

### Debes dominar

-   AWS Cost Explorer
-   AWS Budgets
-   AWS Cost and Usage Report (CUR)
-   Cost Allocation Tags
-   Consolidated Billing
-   AWS Trusted Advisor
-   AWS Compute Optimizer

### Documentación oficial

-   [AWS Cost
    Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)
-   [AWS
    Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
-   [AWS Cost and Usage Report](https://docs.aws.amazon.com/cur/)
-   [AWS Trusted
    Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)
-   [AWS Compute
    Optimizer](https://docs.aws.amazon.com/compute-optimizer/)

------------------------------------------------------------------------

# Laboratorios recomendados

- [ ] Lifecycle en S3
- [ ] Glacier Deep Archive
- [ ] Rightsizing EC2
- [ ] Spot Instances
- [ ] Savings Plans
- [ ] DynamoDB On-Demand
- [ ] Aurora Serverless
- [ ] CloudFront + S3
- [ ] VPC Endpoints
- [ ] Cost Explorer + Budgets

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

Al finalizar este dominio podrás seleccionar la arquitectura con el
menor costo posible sin comprometer disponibilidad, rendimiento ni
seguridad, optimizando almacenamiento, cómputo, bases de datos y redes
para los escenarios evaluados en el examen SAA-C03.

---

**Navegación:** [🏠 Inicio](README.md) · [⬅️ Anterior: Preguntas — Dominio 3](SAA_C03_Preguntas_D3.md) · [Siguiente: Preguntas — Dominio 4 ➡️](SAA_C03_Preguntas_D4.md)
