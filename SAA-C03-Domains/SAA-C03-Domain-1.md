# AWS Certified Solutions Architect - Associate (SAA-C03)

# Dominio 1 - Diseño de Arquitecturas Seguras


**Navegación:** [Inicio](../README.md) · [Siguiente: Preguntas - Dominio 1](../SAA-C03-Questions/SAA-C03-Questions-D1.md)

---

# Semana 1 - Tarea 1.1 Diseñar un acceso seguro a los recursos de AWS

## Objetivos

-   Diseñar acceso seguro a recursos AWS.
-   Implementar autenticación y autorización.
-   Diseñar arquitecturas multi-cuenta.

## - Módulo 1 - Arquitectura Multi-Cuenta

### Temas

-   AWS Organizations
-   Organizational Units (OU)
-   AWS Control Tower
-   Landing Zone
-   Service Control Policies (SCP)
-   Cross-Account Access
-   Delegated Administrator

### Laboratorio

-   Crear una organización.
-   Crear OU Development, Production, Security e Infrastructure.
-   Aplicar SCP.
-   Validar permisos.

### Documentación oficial

-   [AWS Organizations](https://docs.aws.amazon.com/organizations/)
-   [AWS Control Tower](https://docs.aws.amazon.com/controltower/)

------------------------------------------------------------------------

## - Módulo 2 - IAM

### Temas

-   IAM Users
-   IAM Groups
-   IAM Roles
-   IAM Policies
-   Permission Boundaries
-   Resource Policies
-   Session Policies
-   Identity Policies
-   Condition Keys
-   Explicit Deny vs Implicit Deny

### Laboratorio

-   Crear usuarios.
-   Crear grupos.
-   Crear roles.
-   Crear políticas administradas por el cliente.

### Documentación oficial

-   [AWS Identity and Access Management
    (IAM)](https://docs.aws.amazon.com/IAM/)
-   [Políticas de
    IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

------------------------------------------------------------------------

## - Módulo 3 - IAM Identity Center

### Temas

-   Permission Sets
-   Active Directory
-   SAML 2.0
-   OIDC
-   Federación

### Documentación oficial

-   [AWS IAM Identity Center](https://docs.aws.amazon.com/singlesignon/)

------------------------------------------------------------------------

## - Módulo 4 - AWS STS

### Temas

-   AssumeRole
-   AssumeRoleWithSAML
-   AssumeRoleWithWebIdentity
-   GetSessionToken
-   Acceso entre cuentas

### Documentación oficial

-   [AWS Security Token Service (STS)](https://docs.aws.amazon.com/STS/)

------------------------------------------------------------------------

## - Módulo 5 - Root User y MFA

### Buenas prácticas

-   Nunca utilizar el usuario root para tareas diarias.
-   Habilitar MFA.
-   Aplicar el principio de mínimo privilegio.

### Documentación oficial

-   [Prácticas recomendadas para el usuario
    root](https://docs.aws.amazon.com/IAM/latest/UserGuide/root-user-best-practices.html)
-   [Autenticación Multifactor
    (MFA)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)
-   [Modelo de responsabilidad
    compartida](https://aws.amazon.com/compliance/shared-responsibility-model/)

------------------------------------------------------------------------

# Semana 2 - Tarea 1.2 Diseñar cargas de trabajo seguras

## - Módulo 6 - Redes Seguras

### Temas

-   Amazon VPC
-   Subnets
-   Route Tables
-   Internet Gateway
-   NAT Gateway
-   Transit Gateway
-   VPC Peering
-   AWS PrivateLink
-   VPC Endpoints

### Documentación oficial

-   [Amazon VPC](https://docs.aws.amazon.com/vpc/)
-   [Seguridad en Amazon
    VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security.html)

------------------------------------------------------------------------

## - Módulo 7 - Seguridad de Aplicaciones

### Temas

-   AWS WAF
-   AWS Shield
-   AWS Shield Advanced
-   AWS Firewall Manager

### Documentación oficial

-   [AWS WAF](https://docs.aws.amazon.com/waf/)
-   [AWS Shield](https://docs.aws.amazon.com/shield/)
-   [AWS Firewall
    Manager](https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html)

------------------------------------------------------------------------

## - Módulo 8 - Identidad y Credenciales

### Temas

-   Amazon Cognito
-   AWS Secrets Manager
-   AWS Systems Manager Parameter Store

### Documentación oficial

-   [Amazon Cognito](https://docs.aws.amazon.com/cognito/)
-   [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/)
-   [AWS Systems Manager Parameter
    Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)

------------------------------------------------------------------------

## - Módulo 9 - Servicios de Seguridad

### Temas

-   Detección de amenazas
-   Auditoría
-   Cumplimiento
-   Clasificación de datos

### Documentación oficial

-   [GuardDuty](https://docs.aws.amazon.com/guardduty/)
-   [Inspector](https://docs.aws.amazon.com/inspector/)
-   [Macie](https://docs.aws.amazon.com/macie/)
-   [Detective](https://docs.aws.amazon.com/detective/)
-   [Security Hub](https://docs.aws.amazon.com/securityhub/)
-   [AWS Config](https://docs.aws.amazon.com/config/)
-   [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/)

------------------------------------------------------------------------

# Semana 3 - Tarea 1.3 Seguridad de Datos

## - Módulo 10 - AWS KMS

### Documentación oficial

-   [AWS Key Management Service (KMS)](https://docs.aws.amazon.com/kms/)

------------------------------------------------------------------------

## - Módulo 11 - AWS Certificate Manager

### Documentación oficial

-   [AWS Certificate Manager (ACM)](https://docs.aws.amazon.com/acm/)

------------------------------------------------------------------------

## - Módulo 12 - Cifrado

### Temas

-   Datos en reposo
-   Datos en tránsito
-   SSE-S3
-   SSE-KMS
-   SSE-C
-   Client-side encryption

### Documentación oficial

-   [Cifrado en Amazon
    S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html)

------------------------------------------------------------------------

## - Módulo 13 - Backups

### Temas

-   AWS Backup
-   Snapshots
-   Cross-Region
-   Cross-Account
-   Point-in-Time Recovery

### Documentación oficial

-   [AWS Backup](https://docs.aws.amazon.com/aws-backup/)

------------------------------------------------------------------------

## - Módulo 14 - Gobernanza

### Documentación oficial

-   [AWS Lake Formation](https://docs.aws.amazon.com/lake-formation/)
-   [Amazon S3 Object
    Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html)

------------------------------------------------------------------------

# Laboratorios recomendados

- AWS Organizations
- IAM
- IAM Identity Center
- AWS STS
- AWS Control Tower
- SCP
- Diseño seguro de VPC
- Security Groups vs Network ACL
- VPC Endpoints
- AWS WAF
- GuardDuty
- Macie
- AWS Secrets Manager
- AWS KMS
- AWS Backup

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

Al finalizar este plan podrás diseñar arquitecturas seguras, seleccionar
correctamente los servicios de seguridad de AWS y resolver escenarios
reales del examen SAA-C03.

---

**Navegación:** [Inicio](../README.md) · [Siguiente: Preguntas - Dominio 1](../SAA-C03-Questions/SAA-C03-Questions-D1.md)
