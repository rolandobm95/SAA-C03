# Preguntas de Práctica - Dominio 1: Diseño de Arquitecturas Seguras

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 1](../SAA-C03-Domains/SAA-C03-Domain-1.md) · [Siguiente: Dominio 2](../SAA-C03-Domains/SAA-C03-Domain-2.md)

---

## Tarea 1.1 - Diseñar un acceso seguro a los recursos de AWS

### Pregunta 1

Una empresa tiene múltiples equipos de desarrollo trabajando en diferentes proyectos dentro de una misma cuenta de AWS. El equipo de seguridad necesita garantizar que ningún desarrollador pueda crear usuarios IAM con permisos de administrador, incluso si tienen políticas que lo permitan. ¿Cuál es la solución más adecuada?

- A) Crear una política IAM que deniegue explícitamente la acción `iam:CreateUser` y adjuntarla a todos los grupos de desarrolladores.
- B) Configurar Permission Boundaries en los roles de los desarrolladores que limiten los permisos máximos que pueden otorgar.
- C) Implementar una Service Control Policy (SCP) en AWS Organizations que restrinja la creación de usuarios con permisos administrativos.
- D) Habilitar AWS Config con una regla que detecte usuarios con permisos excesivos y los elimine automáticamente.

---

### Pregunta 2

Una organización con 50 cuentas de AWS necesita implementar una estrategia de acceso centralizado. Los empleados deben autenticarse con sus credenciales corporativas de Active Directory y acceder a las cuentas de AWS asignadas según su rol. La solución debe minimizar la sobrecarga operativa. ¿Qué enfoque cumple estos requisitos?

- A) Crear usuarios IAM en cada cuenta y sincronizarlos manualmente con Active Directory.
- B) Configurar AWS IAM Identity Center con integración a Active Directory y definir Permission Sets para cada rol.
- C) Implementar federación SAML 2.0 directamente en cada cuenta con roles IAM individuales.
- D) Utilizar AWS Cognito User Pools integrado con Active Directory para gestionar el acceso a las cuentas.

---

### Pregunta 3

Un arquitecto necesita diseñar un flujo en el que una aplicación ejecutándose en la Cuenta A acceda a un bucket de S3 en la Cuenta B. La solución debe seguir el principio de mínimo privilegio y no debe utilizar credenciales de larga duración. ¿Cuál es la mejor solución?

- A) Crear un usuario IAM en la Cuenta B con una access key y configurarla en la aplicación de la Cuenta A.
- B) Configurar un rol IAM en la Cuenta B con una política de confianza que permita a la Cuenta A asumir el rol mediante AWS STS AssumeRole.
- C) Hacer el bucket de S3 público con una política de bucket que restrinja el acceso por dirección IP de la Cuenta A.
- D) Copiar los datos del bucket a la Cuenta A usando AWS DataSync con una programación periódica.

---

## Tarea 1.2 - Diseñar cargas de trabajo y aplicaciones seguras en AWS

### Pregunta 4

Una empresa está desplegando una aplicación web de tres capas en AWS. La capa de presentación está en subnets públicas, la capa de aplicación en subnets privadas y la base de datos en subnets aisladas. El equipo de seguridad requiere que la capa de aplicación pueda descargar parches de internet pero que no sea accesible directamente desde internet. ¿Cuál es la configuración de red correcta?

- A) Colocar la capa de aplicación en subnets públicas con Security Groups que bloqueen el tráfico entrante de internet.
- B) Mantener la capa de aplicación en subnets privadas y agregar un NAT Gateway en una subnet pública con una ruta en la tabla de rutas de las subnets privadas.
- C) Configurar un Internet Gateway directamente en las subnets privadas con Network ACLs que solo permitan tráfico saliente.
- D) Utilizar VPC Peering con una VPC dedicada que tenga acceso a internet y enrutar el tráfico de salida a través de ella.

---

### Pregunta 5

Una aplicación web expuesta públicamente a través de un Application Load Balancer está sufriendo ataques de inyección SQL y ataques DDoS de capa 7. La empresa necesita protección automatizada contra ambas amenazas con la capacidad de crear reglas personalizadas. ¿Cuál combinación de servicios es la más adecuada?

- A) AWS Shield Standard + Security Groups con reglas restrictivas.
- B) AWS WAF con reglas administradas contra SQL injection + AWS Shield Advanced para protección DDoS de capa 7 con soporte del equipo de respuesta de AWS.
- C) Amazon GuardDuty para detección de amenazas + AWS Network Firewall para bloquear tráfico malicioso.
- D) AWS Firewall Manager + Amazon Inspector para escaneo de vulnerabilidades.

---

### Pregunta 6

Una empresa está desarrollando una aplicación móvil que necesita autenticar usuarios mediante proveedores sociales (Google, Apple) y también permitir registro con email/contraseña. Además, la aplicación backend necesita acceder a credenciales de base de datos que rotan automáticamente cada 30 días. ¿Qué combinación de servicios cumple ambos requisitos?

- A) IAM Identity Center para autenticación de usuarios + AWS Systems Manager Parameter Store para las credenciales de base de datos.
- B) Amazon Cognito User Pools para autenticación de usuarios + AWS Secrets Manager con rotación automática para las credenciales de base de datos.
- C) Amazon Cognito Identity Pools únicamente para autenticación federada + AWS KMS para almacenar las credenciales de base de datos cifradas.
- D) AWS Directory Service para autenticación + AWS Systems Manager Parameter Store con tipo SecureString para las credenciales.

---

### Pregunta 7

El equipo de seguridad de una empresa necesita una solución centralizada que detecte automáticamente actividad maliciosa como criptominería en instancias EC2, accesos no autorizados a buckets S3 y comportamiento anómalo en cuentas IAM. Además requieren un panel unificado que consolide hallazgos de seguridad de múltiples servicios de AWS. ¿Qué combinación de servicios satisface estos requisitos?

- A) Amazon Inspector para detección de vulnerabilidades + AWS Config para panel de cumplimiento.
- B) Amazon GuardDuty para detección de amenazas + AWS Security Hub para consolidación centralizada de hallazgos.
- C) AWS CloudTrail para auditoría + Amazon Macie para clasificación de datos sensibles.
- D) AWS Trusted Advisor para recomendaciones de seguridad + Amazon Detective para investigación de incidentes.

---

## Tarea 1.3 - Determinar los controles de seguridad de datos apropiados

### Pregunta 8

Una institución financiera almacena datos regulados en Amazon S3 y requiere que el cifrado sea gestionado con claves bajo su control total, incluyendo la capacidad de rotar claves según su propia política, auditar el uso de claves y deshabilitar claves inmediatamente si se detecta un compromiso. La solución debe minimizar la complejidad operativa. ¿Cuál opción de cifrado es la más adecuada?

- A) SSE-S3 (cifrado del lado del servidor con claves administradas por Amazon S3).
- B) SSE-KMS con claves administradas por AWS (aws/s3).
- C) SSE-KMS con una CMK (Customer Managed Key) creada y administrada por la empresa en AWS KMS.
- D) SSE-C (cifrado del lado del servidor con claves proporcionadas por el cliente en cada solicitud).

---

### Pregunta 9

Una empresa necesita implementar cifrado para objetos almacenados en un bucket S3. Los requisitos son: cifrado automático sin cambios en el código de la aplicación, costo mínimo y sin necesidad de gestionar claves ni auditar su uso individualmente. ¿Cuál es la opción más adecuada?

- A) SSE-KMS con una Customer Managed Key para tener control total sobre las claves.
- B) Cifrado del lado del cliente (Client-Side Encryption) usando el AWS Encryption SDK.
- C) SSE-S3 (cifrado del lado del servidor con claves administradas por S3) configurado como cifrado predeterminado del bucket.
- D) SSE-C proporcionando una clave de cifrado en cada solicitud PUT y GET.

---

### Pregunta 10

Una empresa opera bases de datos RDS en múltiples regiones de AWS y necesita una estrategia de respaldo que cumpla con: retención de backups por 7 años, copias automáticas en una región secundaria para recuperación ante desastres, y la capacidad de restaurar cualquier base de datos a un punto específico en el tiempo. La solución debe funcionar de forma centralizada para todas las cuentas de la organización. ¿Cuál es la solución más apropiada?

- A) Configurar snapshots manuales de RDS con un script de Lambda que copie los snapshots a otra región semanalmente.
- B) Habilitar backups automáticos de RDS con retención máxima de 35 días y replicar con AWS DataSync.
- C) Implementar AWS Backup con un plan de respaldo que incluya reglas de retención de 7 años, copia cross-region y point-in-time recovery, gestionado a nivel de organización.
- D) Utilizar Amazon S3 Cross-Region Replication para copiar exports de base de datos con una lifecycle policy de 7 años.

---

# Respuestas y Explicaciones

### Pregunta 1
**Respuesta correcta: B**
**Explicación:** Permission Boundaries es un mecanismo de IAM diseñado específicamente para limitar los permisos máximos que una entidad IAM puede tener, independientemente de las políticas que se le adjunten. Cuando se aplica un Permission Boundary a los desarrolladores, incluso si ellos crean políticas con permisos de administrador, los permisos efectivos nunca excederán lo definido en el boundary. La opción C (SCP) sería válida en un contexto multi-cuenta pero el escenario describe una sola cuenta. La opción A deniega la creación de usuarios pero no evita que otorguen permisos excesivos por otros medios. La opción D es reactiva, no preventiva.

### Pregunta 2
**Respuesta correcta: B**
**Explicación:** AWS IAM Identity Center (anteriormente AWS SSO) es el servicio recomendado por AWS para gestionar acceso centralizado a múltiples cuentas de una organización. Permite integración nativa con Active Directory, define Permission Sets que se asignan a usuarios/grupos para cuentas específicas y genera credenciales temporales automáticamente. La opción A no escala y usa credenciales de larga duración. La opción C requiere configuración individual en cada cuenta, aumentando la sobrecarga operativa. La opción D (Cognito) está diseñada para autenticación de usuarios de aplicaciones, no para acceso a cuentas de AWS.

### Pregunta 3
**Respuesta correcta: B**
**Explicación:** El patrón recomendado para acceso cross-account es crear un rol IAM en la cuenta destino con una política de confianza que permita a la cuenta origen asumir ese rol mediante STS AssumeRole. Esto genera credenciales temporales (sin credenciales de larga duración) y permite aplicar mínimo privilegio definiendo permisos específicos en la política del rol. La opción A viola el requisito de no usar credenciales de larga duración. La opción C expone el bucket públicamente, violando las mejores prácticas de seguridad. La opción D no proporciona acceso directo y agrega latencia innecesaria.

### Pregunta 4
**Respuesta correcta: B**
**Explicación:** Un NAT Gateway permite que las instancias en subnets privadas inicien conexiones salientes a internet (para descargar parches) sin ser accesibles directamente desde internet. El NAT Gateway se despliega en una subnet pública y la tabla de rutas de las subnets privadas dirige el tráfico 0.0.0.0/0 hacia él. La opción A expone la capa de aplicación en subnets públicas, violando el principio de defensa en profundidad. La opción C es técnicamente incorrecta ya que un Internet Gateway se asocia a nivel de VPC, no de subnet. La opción D agrega complejidad innecesaria.

### Pregunta 5
**Respuesta correcta: B**
**Explicación:** AWS WAF proporciona protección contra ataques de capa 7 como inyección SQL mediante reglas administradas y personalizadas que inspeccionan las solicitudes HTTP. AWS Shield Advanced complementa con protección DDoS avanzada en capas 3, 4 y 7, acceso al equipo de respuesta DDoS (DRT) de AWS y mitigación automática. La opción A solo protege contra DDoS básico (capa 3/4) sin protección contra SQL injection. La opción C detecta amenazas pero no las bloquea en tiempo real a nivel de aplicación web. La opción D es para gestión centralizada de reglas, no para protección directa.

### Pregunta 6
**Respuesta correcta: B**
**Explicación:** Amazon Cognito User Pools maneja la autenticación de usuarios con soporte nativo para proveedores sociales (Google, Apple, Facebook) y registro con email/contraseña, siendo ideal para aplicaciones móviles. AWS Secrets Manager almacena credenciales de forma segura y soporta rotación automática programada (cada 30 días) con integración nativa para bases de datos RDS. La opción A usa IAM Identity Center que es para acceso a cuentas AWS, no para apps móviles. La opción C usa solo Identity Pools que proporciona credenciales AWS temporales pero no gestiona la autenticación de usuarios. La opción D no soporta proveedores sociales nativamente.

### Pregunta 7
**Respuesta correcta: B**
**Explicación:** Amazon GuardDuty es un servicio de detección de amenazas que usa machine learning para identificar actividad maliciosa como criptominería, accesos no autorizados a S3 y comportamiento anómalo en IAM, analizando logs de VPC Flow, DNS y CloudTrail. AWS Security Hub consolida hallazgos de múltiples servicios (GuardDuty, Inspector, Macie, Firewall Manager) en un panel unificado con estándares de cumplimiento. La opción A no detecta amenazas en tiempo real. La opción C audita acciones pero no detecta amenazas activamente. La opción D ofrece recomendaciones generales pero no detección continua de amenazas.

### Pregunta 8
**Respuesta correcta: C**
**Explicación:** SSE-KMS con una Customer Managed Key (CMK) ofrece control total sobre las claves: rotación personalizada según políticas propias, auditoría completa del uso de claves mediante CloudTrail, y la capacidad de deshabilitar o eliminar claves inmediatamente. Además, AWS gestiona la infraestructura criptográfica, minimizando la complejidad operativa. La opción A (SSE-S3) no ofrece control ni auditoría sobre las claves. La opción B usa claves administradas por AWS que no permiten rotación personalizada ni deshabilitación. La opción D requiere que el cliente gestione y transmita las claves en cada solicitud, aumentando significativamente la complejidad operativa.

### Pregunta 9
**Respuesta correcta: C**
**Explicación:** SSE-S3 es la opción más simple y económica para cifrado en S3. No requiere cambios en el código (es transparente para la aplicación), no tiene costo adicional por gestión de claves, y al configurarlo como cifrado predeterminado del bucket, todos los objetos se cifran automáticamente sin intervención. La opción A agrega costo por cada llamada a la API de KMS y requiere gestión de claves. La opción B requiere modificar el código de la aplicación. La opción D requiere enviar la clave en cada solicitud, lo que implica cambios en el código y gestión de claves por parte del cliente.

### Pregunta 10
**Respuesta correcta: C**
**Explicación:** AWS Backup es el servicio diseñado para gestión centralizada de respaldos con soporte para retención de largo plazo (hasta perpetua), copias cross-region automáticas, y point-in-time recovery para servicios como RDS. Además, puede gestionarse a nivel de organización mediante AWS Organizations, aplicando planes de respaldo a todas las cuentas. La opción A es manual, propensa a errores y difícil de gestionar centralmente. La opción B tiene un límite de 35 días de retención para backups automáticos de RDS, insuficiente para 7 años. La opción D no soporta point-in-time recovery y requiere un proceso de export adicional.

---

**Navegación:** [Inicio](../README.md) · [Anterior: Dominio 1](../SAA-C03-Domains/SAA-C03-Domain-1.md) · [Siguiente: Dominio 2](../SAA-C03-Domains/SAA-C03-Domain-2.md)
