# AWS Certified Solutions Architect -- Associate (SAA-C03)

# Dominio 2 -- Diseño de Arquitecturas Resistentes


**Navegación:** [Inicio](../README.md) · [Anterior: Preguntas — Dominio 1](../preguntas/SAA_C03_Preguntas_D1.md) · [Siguiente: Preguntas — Dominio 2](../preguntas/SAA_C03_Preguntas_D2.md)

---

> Plan de estudios enfocado en resiliencia, escalabilidad y alta
> disponibilidad.

------------------------------------------------------------------------

# Semana 1 -- Tarea 2.1 (Parte 1)

## Objetivos

-   Diseñar aplicaciones escalables.
-   Reducir el acoplamiento entre componentes.
-   Seleccionar correctamente servicios administrados de AWS.

------------------------------------------------------------------------

## - [ ] Módulo 1 -- Arquitecturas Basadas en Eventos

### Temas

-   Amazon EventBridge
-   Amazon SQS
-   Amazon SNS
-   Amazon MQ
-   AWS Step Functions
-   Patrones Publish/Subscribe
-   Event-driven Architecture

### Laboratorio

-   API Gateway → EventBridge → Lambda
-   SNS → SQS → Lambda
-   Step Functions para orquestación

### Documentación oficial

-   [Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/)
-   [Amazon SQS](https://docs.aws.amazon.com/sqs/)
-   [Amazon SNS](https://docs.aws.amazon.com/sns/)
-   [AWS Step Functions](https://docs.aws.amazon.com/step-functions/)

------------------------------------------------------------------------

## - [ ] Módulo 2 -- Microservicios

### Temas

-   Stateless vs Stateful
-   API Gateway
-   Service Discovery
-   Backend for Frontend (BFF)
-   Circuit Breaker
-   Retry Pattern

### Documentación oficial

-   [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/)
-   [AWS Prescriptive Guidance -
    Microservices](https://docs.aws.amazon.com/prescriptive-guidance/latest/microservices-on-aws/)

------------------------------------------------------------------------

## - [ ] Módulo 3 -- Contenedores

### Temas

-   Amazon ECS
-   Amazon EKS
-   AWS Fargate
-   Amazon ECR

### Laboratorio

-   Desplegar aplicación en ECS Fargate.
-   Comparar ECS vs EKS.

### Documentación oficial

-   [Amazon ECS](https://docs.aws.amazon.com/ecs/)
-   [Amazon EKS](https://docs.aws.amazon.com/eks/)
-   [AWS
    Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html)
-   [Amazon ECR](https://docs.aws.amazon.com/ecr/)

------------------------------------------------------------------------

---

# Semana 2 -- Tarea 2.1 (Parte 2)

## - [ ] Módulo 4 -- Serverless

### Temas

-   AWS Lambda
-   API Gateway
-   Step Functions
-   EventBridge

### Documentación oficial

-   [AWS Lambda](https://docs.aws.amazon.com/lambda/)
-   [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/)
-   [AWS Step Functions](https://docs.aws.amazon.com/step-functions/)

------------------------------------------------------------------------

## - [ ] Módulo 5 -- Balanceo de Carga y Escalabilidad

### Temas

-   Application Load Balancer
-   Network Load Balancer
-   Gateway Load Balancer
-   Elastic Load Balancing
-   Auto Scaling
-   Horizontal vs Vertical Scaling

### Documentación oficial

-   [Elastic Load
    Balancing](https://docs.aws.amazon.com/elasticloadbalancing/)
-   [Amazon EC2 Auto
    Scaling](https://docs.aws.amazon.com/autoscaling/ec2/)

------------------------------------------------------------------------

---

# Semana 3 -- Tareas 2.1/2.2

## - [ ] Módulo 6 -- Caché y CDN

### Temas

-   Amazon CloudFront
-   Amazon ElastiCache
-   AWS Global Accelerator

### Documentación oficial

-   [Amazon CloudFront](https://docs.aws.amazon.com/cloudfront/)
-   [Amazon ElastiCache](https://docs.aws.amazon.com/elasticache/)
-   [AWS Global
    Accelerator](https://docs.aws.amazon.com/global-accelerator/)

------------------------------------------------------------------------

## - [ ] Módulo 7 -- Almacenamiento

### Temas

-   Amazon S3
-   Amazon EBS
-   Amazon EFS
-   Amazon FSx
-   Read Replicas

### Documentación oficial

-   [Amazon S3](https://docs.aws.amazon.com/s3/)
-   [Amazon EBS](https://docs.aws.amazon.com/ebs/)
-   [Amazon EFS](https://docs.aws.amazon.com/efs/)
-   [Amazon FSx](https://docs.aws.amazon.com/fsx/)
-   [Amazon RDS Read
    Replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)

------------------------------------------------------------------------

## - [ ] Módulo 8 -- Alta Disponibilidad

### Temas

-   Multi-AZ
-   Multi-Region
-   Route 53
-   Health Checks
-   Failover

### Documentación oficial

-   [Amazon Route 53](https://docs.aws.amazon.com/route53/)
-   [Amazon RDS
    Multi-AZ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html)

------------------------------------------------------------------------

---

# Semana 4 -- Tarea 2.2

## - [ ] Módulo 9 -- Disaster Recovery

### Temas

-   Backup & Restore
-   Pilot Light
-   Warm Standby
-   Multi-site Active/Active
-   RPO
-   RTO

### Documentación oficial

-   [AWS Disaster Recovery
    Guidance](https://docs.aws.amazon.com/prescriptive-guidance/latest/disaster-recovery-workloads-on-aws/)
-   [AWS Elastic Disaster Recovery](https://docs.aws.amazon.com/drs/)

------------------------------------------------------------------------

## - [ ] Módulo 10 -- Observabilidad

### Temas

-   Amazon CloudWatch
-   AWS X-Ray
-   CloudTrail
-   AWS Config

### Documentación oficial

-   [Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/)
-   [AWS X-Ray](https://docs.aws.amazon.com/xray/)
-   [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/)
-   [AWS Config](https://docs.aws.amazon.com/config/)

------------------------------------------------------------------------

## - [ ] Módulo 11 -- Servicios Administrados

### Temas

-   Amazon RDS Proxy
-   AWS Transfer Family
-   Amazon Comprehend
-   Amazon Polly

### Documentación oficial

-   [Amazon RDS
    Proxy](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy.html)
-   [AWS Transfer Family](https://docs.aws.amazon.com/transfer/)
-   [Amazon Comprehend](https://docs.aws.amazon.com/comprehend/)
-   [Amazon Polly](https://docs.aws.amazon.com/polly/)

------------------------------------------------------------------------

# Laboratorios Recomendados

- [ ] API Gateway + Lambda
- [ ] EventBridge + SQS + SNS
- [ ] Step Functions
- [ ] ECS vs EKS
- [ ] Auto Scaling
- [ ] ALB + Target Groups
- [ ] CloudFront
- [ ] ElastiCache
- [ ] Route 53 Failover
- [ ] RDS Multi-AZ
- [ ] Read Replicas
- [ ] RDS Proxy
- [ ] AWS X-Ray
- [ ] Disaster Recovery
- [ ] AWS Transfer Family

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

Al finalizar este dominio serás capaz de diseñar arquitecturas
resilientes, altamente disponibles, escalables y tolerantes a fallos
utilizando las mejores prácticas y servicios administrados de AWS.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Preguntas — Dominio 1](../preguntas/SAA_C03_Preguntas_D1.md) · [Siguiente: Preguntas — Dominio 2](../preguntas/SAA_C03_Preguntas_D2.md)
