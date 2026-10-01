# PROMPT MAESTRO — ALERTUNS

## Sistema Institucional de Comunicación y Activación de Emergencias de la Universidad Nacional del Sur

---

## 0. ROL QUE DEBES ASUMIR

Actuá como un **equipo senior multidisciplinario de ingeniería de software y sistemas críticos**, integrado conceptualmente por:

* Software Architect / Solution Architect.
* Senior Full Stack Developer.
* Senior Backend Developer especializado en PHP/Laravel.
* Senior Mobile Developer especializado en Android/Kotlin.
* Senior Mobile Developer especializado en iOS/Swift.
* Senior React / Web Developer.
* DevOps / SRE Engineer.
* Cloud / Infrastructure Engineer.
* Cybersecurity Engineer.
* QA Automation Engineer.
* Mobile QA especializado en notificaciones críticas.
* Database Architect.
* UX/UI Designer para sistemas de emergencia.
* Especialista en observabilidad y continuidad operativa.
* Technical Project Lead.

Tu objetivo es **diseñar y construir un sistema institucional de gestión y comunicación de emergencias para la Universidad Nacional del Sur (UNS)**, denominado provisoriamente:

# AlertUNS

El sistema debe permitir que, cuando la autoridad institucional active un protocolo de emergencia, la comunicación llegue de forma rápida, segmentada, trazable y redundante a las personas correspondientes.

El sistema debe disponer de:

* Aplicación Android.
* Aplicación iOS.
* Consola web administrativa.
* Backend/API.
* Base de datos.
* Sistema de despacho de notificaciones.
* Sistema de confirmaciones.
* Sistema de escalamiento.
* Auditoría.
* Observabilidad.
* Alta disponibilidad y recuperación.
* Integración futura con SMN.
* Integración futura con RACUNS y otros medios institucionales.
* Arquitectura preparada para crecimiento.

---

# 1. CONTEXTO INSTITUCIONAL

La aplicación será desarrollada para la:

**Universidad Nacional del Sur — Bahía Blanca, Argentina.**

No debe considerarse una aplicación comercial.

Es un sistema institucional de apoyo a la gestión de emergencias y comunicaciones críticas.

Debe respetar:

* protocolos institucionales;
* cadena de decisión;
* roles y responsabilidades;
* protección de datos personales;
* trazabilidad;
* principio de mínima información;
* separación entre detección, recomendación, decisión y difusión;
* redundancia de comunicaciones;
* continuidad operativa;
* seguridad informática.

El software **NO debe tomar decisiones de emergencia por sí mismo**.

La aplicación ejecuta las decisiones adoptadas por las personas autorizadas y registra todo el proceso.

---

# 2. REFERENCIA FUNCIONAL: BOMBERBOT

Tomá como referencia funcional las capacidades públicamente declaradas por BomberBOT:

* alarma de emergencias;
* sonido;
* vibración;
* voz;
* funcionamiento con aplicación cerrada;
* respuestas con un toque;
* convocatoria general;
* convocatoria selectiva;
* convocatoria por departamento;
* sonidos diferenciados;
* cancelación de emergencia;
* monitoreo de respuestas;
* panel web;
* monitoreo de dispositivos;
* chequeos;
* funcionamiento offline;
* mensajería interna;
* departamentos;
* simulacros.

IMPORTANTE:

No copiar código, diseño propietario, marca, textos, sonidos, interfaz, recursos gráficos ni implementación interna de BomberBOT.

La referencia es exclusivamente funcional.

La solución debe ser una implementación propia de la UNS, diseñada desde cero.

La página pública de referencia es:

https://bomberbot.com.ar/

---

# 3. DOCUMENTACIÓN BASE DEL PROYECTO

Considerá como documentación funcional primaria los archivos suministrados junto con este prompt:

1. `Plan_Desarrollo_Sistema_Emergencias_UNS(2).md`
2. `readme(1).md`

Estos documentos contienen:

* requisitos;
* actores;
* niveles T0–T3;
* arquitectura;
* MVP;
* funcionalidades futuras;
* protocolos;
* flujo de decisión;
* modelo de datos;
* seguridad;
* pruebas;
* DevOps;
* recuperación;
* observabilidad;
* pruebas de dispositivos;
* integración SMN;
* escalamiento;
* auditoría.

No inventes requisitos institucionales que no estén definidos.

Cuando exista una contradicción entre documentación, señalala y proponé una decisión técnica explícita mediante un ADR.

No ocultes contradicciones.

---

# 4. OBJETIVO PRINCIPAL

Construir un sistema denominado AlertUNS que permita:

```text
EVENTO / ALERTA
       ↓
DETECCIÓN
       ↓
EVALUACIÓN
       ↓
RECOMENDACIÓN
       ↓
APROBACIÓN HUMANA
       ↓
DESPACHO
       ↓
NOTIFICACIÓN CRÍTICA
       ↓
CONFIRMACIÓN
       ↓
ESCALAMIENTO
       ↓
ACTUALIZACIÓN / CESE
       ↓
AUDITORÍA
       ↓
INFORME POST-EVENTO
```

Cada etapa debe quedar registrada.

---

# 5. PRINCIPIO FUNDAMENTAL

La aplicación no debe ser diseñada como un simple sistema de push notifications.

Debe ser diseñada como un:

> **Sistema de despacho institucional de comunicaciones críticas con trazabilidad, redundancia, confirmación y continuidad operativa.**

El sistema debe distinguir claramente:

1. evento detectado;
2. alerta evaluada;
3. recomendación;
4. decisión aprobada;
5. emisión;
6. entrega;
7. recepción;
8. confirmación;
9. escalamiento;
10. actualización;
11. cese;
12. cierre;
13. auditoría.

Nunca mezclar estos estados.

---

# 6. ARQUITECTURA GENERAL

Proponé inicialmente una arquitectura:

```text
                 ┌──────────────────────┐
                 │      ALERTUNS        │
                 │     WEB / API        │
                 └──────────┬───────────┘
                            │
             ┌──────────────┼───────────────┐
             │              │               │
             ▼              ▼               ▼
        Android           iOS          Consola Web
             │              │               │
             └──────────────┼───────────────┘
                            │
                         HTTPS
                            │
                    ┌───────▼────────┐
                    │  Laravel API   │
                    │  RBAC + MFA    │
                    │ Motor alertas  │
                    └───────┬────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
           MySQL          Redis       Object Storage
              │             │
              │          Queues
              │             │
              └──────┬──────┘
                     ▼
                 Dispatcher
                     │
       ┌─────────────┼──────────────────┐
       │             │                  │
       ▼             ▼                  ▼
      APNs           FCM             SMS/VOICE
       │             │                  │
       ▼             ▼                  ▼
      iOS          Android          Respaldo
```

Agregar posteriormente:

* email;
* Telegram;
* web push;
* Moodle;
* RACUNS;
* megafonía;
* pantallas;
* sistemas institucionales;
* SMN;
* Defensa Civil;
* otros canales.

---

# 7. STACK TECNOLÓGICO BASE

Salvo que exista una razón técnica documentada para modificarlo:

## Backend

* PHP 8.3+ o versión estable compatible con hosting.
* Laravel LTS vigente.
* REST API.
* OpenAPI/Swagger.
* Laravel Queue.
* Redis.
* WebSockets mediante Laravel Reverb o alternativa equivalente.
* MySQL 8.
* Laravel Sanctum u OAuth2/OIDC según arquitectura de identidad.
* PHPUnit/Pest.

## Frontend Web

Preferentemente:

* React + TypeScript

o:

* Vue + TypeScript

La decisión debe documentarse.

La consola debe ser responsive.

## Mobile

Usar:

* React Native para UI y lógica compartida.

Pero NO depender exclusivamente de React Native para la alarma crítica.

La capa crítica debe disponer de código nativo:

### Android

* Kotlin.
* Firebase Cloud Messaging.
* Notification Channels.
* Foreground Service cuando corresponda.
* integración con capacidades nativas del sistema.
* mecanismos de alta prioridad.
* full-screen intent solamente cuando sea legal/técnicamente viable.
* gestión de Doze.
* gestión de batería.
* fabricante/OEM readiness.

### iOS

* Swift.
* APNs directo.
* UserNotifications.
* Critical Alerts cuando Apple conceda el entitlement.
* Time Sensitive como fallback.
* Notification Service Extension.
* sonidos críticos preempaquetados.
* manejo de Focus.
* manejo de silencio.

---

# 8. REQUISITO CRÍTICO: ALARMA

La alarma es la función más importante del proyecto.

NO aceptes como requisito simplemente:

> "Enviar una notificación push."

La prueba real debe ser:

```text
Servidor
   ↓
Proveedor push
   ↓
Sistema operativo
   ↓
Dispositivo
   ↓
Alarma audible
   ↓
Vibración
   ↓
Pantalla / interacción
   ↓
Confirmación
```

---

# 9. NO PROMETER CAPACIDADES QUE EL SISTEMA OPERATIVO NO GARANTIZA

Antes de comenzar el desarrollo completo debes realizar una **PoC específica de notificaciones críticas**.

## Android

Probar:

* aplicación abierta;
* background;
* aplicación cerrada;
* pantalla bloqueada;
* pantalla apagada;
* modo silencio;
* No Molestar;
* ahorro de batería;
* Doze;
* reinicio;
* batería baja;
* WiFi;
* 4G;
* 5G;
* pérdida de conectividad;
* recuperación.

Probar como mínimo:

* Samsung;
* Xiaomi/Redmi;
* Motorola;
* Google Pixel;
* Oppo/Realme;
* dispositivo Android económico.

Verificar:

* FCM;
* prioridad;
* canal de alarma;
* vibración;
* audio;
* pantalla;
* full-screen intent;
* permisos;
* exclusión de optimización de batería;
* Foreground Service;
* comportamiento después de reiniciar.

NO asumir que todos los fabricantes se comportan igual.

El estado de preparación del dispositivo debe quedar registrado.

---

# 10. iOS — CRITICAL ALERTS

El objetivo es conseguir:

```text
Alerta crítica
      ↓
APNs
      ↓
Critical Alert
      ↓
Sonido aun con silencio/Focus
```

Solicitar desde el inicio el entitlement correspondiente de Apple.

La solución debe contemplar:

### Camino primario

Critical Alerts.

### Camino secundario

Time Sensitive Notification.

### Camino terciario

SMS.

### Camino adicional

Llamada de voz automatizada.

Si Apple no concede Critical Alerts, el sistema NO debe fingir que puede garantizar el comportamiento.

Debe:

1. registrar la limitación;
2. mostrar el estado en consola;
3. informar al usuario;
4. activar canales alternativos;
5. mantener el sistema operativo funcional;
6. documentar el nivel real de disponibilidad.

No utilizar PushKit/VoIP como mecanismo artificial para evadir las restricciones de Apple.

---

# 11. MÉTRICA DE "DEVICE READINESS"

Cada dispositivo debe informar:

```text
platform
app_version
os_version
manufacturer
model
push_token
last_seen
notification_permission
critical_alert_permission
do_not_disturb_permission
full_screen_permission
battery_optimization
foreground_service
network
last_alarm_test
critical_ready
```

La consola debe poder mostrar:

```text
T0 preparados:       98 %
T1 preparados:       96 %
T2 preparados:       87 %
T3 preparados:       75 %
```

Y detectar:

```text
NO PREPARADO
TOKEN INVÁLIDO
APP DESACTUALIZADA
SIN PERMISO
SIN CONECTIVIDAD
NO REPORTA
CRITICAL ALERT NO APROBADO
BATERÍA NO CONFIGURADA
```

---

# 12. NIVELES DE AUDIENCIA

Implementar:

## T0 — Mando

* Rector.
* CDE.
* Nodo Central.
* Operadores.
* Vocería.
* Suplentes.

Características:

* alarma crítica;
* SMS;
* voz;
* confirmación obligatoria;
* escalamiento;
* MFA.

## T1 — Coordinación

* Mayordomías.
* Decanos.
* Directores.
* Infraestructura.
* Telecomunicaciones.
* Brigadas.

Características:

* alarma crítica;
* SMS;
* confirmación;
* escalamiento.

## T2 — Comunidad laboral

* docentes;
* nodocentes;
* investigadores.

Características:

* notificación prioritaria;
* correo;
* confirmación.

## T3 — Comunidad general

* estudiantes;
* familias;
* visitantes.

Características:

* push;
* web;
* Moodle;
* Telegram;
* redes;
* canales públicos.

La alarma estruendosa no debe utilizarse indiscriminadamente.

---

# 13. ROLES Y RBAC

Implementar RBAC real.

No utilizar:

```text
if user == "admin"
```

en el código.

Utilizar:

```text
roles
permissions
scope
assignments
deputies
validity
```

Un usuario puede:

* tener varios roles;
* tener diferentes ámbitos;
* tener suplentes;
* cambiar de función;
* dejar temporalmente una función.

Los roles son datos configurables.

---

# 14. CADENA DE DECISIÓN

Implementar obligatoriamente:

```text
DETECTED
   ↓
ASSESSED
   ↓
RECOMMENDED
   ↓
APPROVED
   ↓
DISPATCHING
   ↓
ACTIVE
   ↓
UPDATED
   ↓
CEASED
   ↓
CLOSED
```

Nadie debe poder saltar etapas sin autorización.

Para alertas críticas y audiencias masivas implementar:

## Regla de dos personas

Por ejemplo:

```text
Operador prepara
      ↓
Responsable aprueba
      ↓
Segundo responsable confirma
      ↓
Despacho
```

Registrar:

* usuario;
* rol;
* IP;
* fecha;
* hora;
* acción;
* contenido;
* versión de plantilla;
* versión del protocolo.

---

# 15. ALERTAS MANUALES

El Nodo Central debe poder crear una emergencia manual.

Tipos:

* puntual;
* general;
* climática;
* infraestructura;
* sanitaria;
* evacuación;
* confinamiento;
* comunicaciones;
* simulacro;
* otro.

Nunca enviar una alerta crítica sin:

* audiencia;
* prioridad;
* contenido;
* responsable;
* aprobación;
* timestamp.

---

# 16. INTEGRACIÓN SMN

Implementar inicialmente:

## Modo asistido

El sistema consulta la información disponible del SMN y genera:

```text
BORRADOR DE ALERTA
```

No enviar automáticamente a la comunidad.

El operador debe verificar.

El sistema debe almacenar:

* fuente;
* timestamp;
* respuesta original;
* hash SHA-256;
* parser utilizado;
* resultado;
* versión del parser.

Preparar arquitectura compatible con:

* CAP;
* fuentes estructuradas;
* web oficial;
* futuras API oficiales.

Si el formato del SMN cambia:

```text
NO FALLAR SILENCIOSAMENTE
```

Debe generar:

```text
SMN SOURCE ERROR
```

y notificar al Nodo Central.

---

# 17. EVENTOS SIMULTÁNEOS

No asumir:

```text
un alerta = un fenómeno
```

Una zona puede tener:

* tormenta;
* viento;
* lluvia;
* granizo;
* ACP;
* temperaturas extremas;

simultáneamente.

El sistema debe mantener eventos independientes.

---

# 18. FICHA DEL ALERTA

Implementar una ficha digital.

Campos mínimos:

```text
ID
Fecha
Hora
Fuente
Fenómeno
Nivel
Zona
Vigencia
Línea de tiempo
Eventos simultáneos
Observaciones
Evaluación
Recomendación
Responsable
Aprobador
Segundo aprobador
Mensaje
Audiencia
Canales
Estado
```

No permitir despacho si faltan campos obligatorios.

---

# 19. RESPUESTAS RÁPIDAS

Implementar:

```text
RECEIVED
SAFE
SHELTERED
NEED_HELP
UNAVAILABLE_ROLE
```

La interfaz debe permitir responder con un toque.

Registrar:

```text
client_timestamp
server_timestamp
device
user
alert
broadcast
response
```

El timestamp oficial será el del servidor.

---

# 20. ESCALAMIENTO

Implementar configurablemente:

```text
T+0
Push crítico

T+60 s
reintento / canal secundario

T+2 min
SMS

T+5 min
voz

T+15 min
suplente

T+30 min
reporte operativo
```

No codificar estos valores directamente.

Deben ser parámetros configurables y versionados.

---

# 21. CESE Y RECTIFICACIÓN

Implementar:

### M6 — Cese

Cuando finaliza la emergencia.

### M7 — Rectificación

Cuando se produjo:

* error;
* falsa alarma;
* cambio de condiciones;
* modificación de instrucciones.

La rectificación debe conservar el historial.

Nunca sobrescribir la comunicación original.

---

# 22. AUDITORÍA

Toda operación importante debe generar auditoría.

Crear una cadena:

```text
hash = SHA256(previous_hash + content)
```

Registrar:

* actor;
* acción;
* entidad;
* ID;
* timestamp;
* IP;
* payload;
* previous_hash;
* hash.

La auditoría debe permitir demostrar posteriormente:

> quién hizo qué, cuándo, desde dónde y con qué información.

---

# 23. BASE DE DATOS

Utilizar MySQL 8.

No utilizar ENUM para catálogos que puedan cambiar.

Entidades principales:

```text
persons
users
roles
permissions
role_assignments
deputies
buildings
sites
departments
devices
device_readiness
alerts
alert_sources
alert_decisions
broadcasts
broadcast_audiences
deliveries
acks
escalations
templates
template_versions
protocol_versions
catalogs
smn_snapshots
audit_logs
notifications
channels
providers
canary_tests
simulations
ecd_events
reports
```

Separar claramente:

```text
DECISION
EMISSION
DELIVERY
ACK
```

No mezclar estos conceptos.

---

# 24. API

Crear:

```text
/api/v1/
```

Documentar con OpenAPI.

Endpoints mínimos:

```text
/auth
/users
/roles
/devices
/readiness
/alerts
/alerts/{id}
/alerts/{id}/assess
/alerts/{id}/recommend
/alerts/{id}/approve
/alerts/{id}/cease
/broadcasts
/broadcasts/{id}
/broadcasts/{id}/ack
/deliveries
/escalations
/catalogs
/templates
/smn
/ecd
/reports
/canary
/health
```

Todas las operaciones de emisión deben soportar:

```text
idempotency-key
```

para evitar doble envío accidental.

---

# 25. SEGURIDAD

Diseñar utilizando:

* OWASP ASVS;
* OWASP MASVS;
* principio de mínimo privilegio;
* MFA;
* RBAC;
* rate limiting;
* protección CSRF donde corresponda;
* CORS restrictivo;
* CSP;
* HSTS;
* TLS;
* secrets management;
* rotación de credenciales;
* logs;
* detección de anomalías;
* protección de endpoints;
* validación de entrada;
* prepared statements/ORM;
* protección contra SQL Injection;
* XSS;
* SSRF;
* IDOR;
* CSRF;
* abuso de API;
* replay attacks.

Nunca almacenar:

* passwords en texto plano;
* tokens innecesarios;
* claves privadas en Git;
* credenciales de producción en código.

---

# 26. DATOS PERSONALES

Considerar especialmente:

* Ley Argentina 25.326;
* datos institucionales;
* teléfonos;
* DNI cuando corresponda;
* datos de menores en el módulo escolar;
* registros de emergencia.

Aplicar:

```text
mínima recolección
mínimo privilegio
cifrado
retención definida
auditoría
anonimización donde corresponda
```

La geolocalización NO debe ser continua.

Si en el futuro se implementa ubicación:

* consentimiento;
* finalidad;
* retención;
* acceso;
* auditoría.

---

# 27. INFRAESTRUCTURA

El proyecto dispone de:

* hosting;
* base de datos;
* dominio/institución.

Antes de desarrollar, realizar una:

# AUDITORÍA DEL HOSTING

Determinar:

```text
tipo de hosting
CPU
RAM
SSD
sistema operativo
PHP
MySQL
Redis
Docker
SSH
cron
workers
Supervisor
WebSockets
puertos
TLS
DNS
backup
firewall
WAF
IPv4
IPv6
salida HTTPS
limitaciones
```

Si el hosting es compartido y no permite:

* workers;
* Redis;
* WebSockets;
* procesos persistentes;

NO forzar la arquitectura.

Proponer:

```text
VPS
```

o infraestructura equivalente.

---

# 28. ENTORNOS

Crear:

```text
DEV
STAGING
PRODUCTION
DISASTER RECOVERY
```

Nunca desarrollar directamente sobre producción.

---

# 29. DEVOPS

Implementar:

* Git;
* GitHub/GitLab;
* ramas protegidas;
* Pull Requests;
* revisión de código;
* CI;
* CD;
* tests automáticos;
* SAST;
* análisis de dependencias;
* Docker cuando resulte conveniente;
* versionado semántico;
* changelog;
* rollback.

Pipeline:

```text
commit
 ↓
lint
 ↓
unit tests
 ↓
integration tests
 ↓
security scan
 ↓
build
 ↓
staging
 ↓
E2E
 ↓
approval
 ↓
production
```

---

# 30. SECRETOS

Nunca incluir en el repositorio:

```text
FCM_PRIVATE_KEY
APNS_PRIVATE_KEY
DB_PASSWORD
SMTP_PASSWORD
SMS_API_KEY
VOICE_API_KEY
JWT_SECRET
```

Utilizar variables de entorno y/o secret manager.

---

# 31. BACKUPS

Implementar:

* backup diario;
* backup cifrado;
* retención mínima 30 días;
* copia independiente;
* prueba mensual de restauración.

Objetivos iniciales:

```text
RPO ≤ 5 min
RTO ≤ 15 min
```

pero deben ser considerados objetivos de diseño sujetos a validación con infraestructura institucional.

---

# 32. ALTA DISPONIBILIDAD

Diseñar:

```text
PRIMARIO
   ↓
RÉPLICA
   ↓
DR
```

Idealmente:

```text
Alem
 ↓
Palihue
 ↓
sitio externo
```

Implementar un:

# DISPATCHER MÍNIMO DE CONTINGENCIA

Debe permitir enviar una última decisión aprobada aun ante una caída importante del sistema principal.

---

# 33. CANARIO

Implementar dispositivos canario.

Mínimo:

```text
2 Android
2 iPhone
```

dedicados.

Funcionamiento:

```text
prueba automática
     ↓
push
     ↓
alarma
     ↓
confirmación automática
     ↓
registro
```

Si el canario falla:

```text
ALERTA OPERATIVA
```

La consola debe mostrar:

```text
CANARIO OK
CANARIO WARNING
CANARIO FAILED
```

---

# 34. OBSERVABILIDAD

Implementar:

* Prometheus;
* Grafana;
* logs estructurados;
* Sentry o GlitchTip;
* métricas de API;
* métricas de Redis;
* métricas de DB;
* métricas de notificaciones.

Métricas:

```text
alertas emitidas
alertas activas
alertas cerradas
tiempo de despacho
tiempo de entrega
confirmaciones
fallos
SMS enviados
voz enviada
push enviados
tokens inválidos
dispositivos preparados
canario
CPU
RAM
DB
Redis
colas
workers
```

---

# 35. SLO INICIALES

Objetivos:

```text
Disponibilidad camino crítico: 99,9 % mensual

Aprobación → proveedor push:
≤ 30 segundos

Confirmación T0:
≥ 95 % en 5 minutos

Preparación T0/T1:
≥ 98 %

Falsas emisiones:
0

Canario:
≥ 99,5 %
```

Distinguir siempre:

```text
objetivo
medición
garantía
```

No afirmar que una notificación móvil será entregada en X segundos como garantía absoluta.

---

# 36. CONSOLA WEB

Crear un dashboard institucional.

Debe mostrar:

```text
┌─────────────────────────────────────┐
│ ALERTUNS                            │
├─────────────────────────────────────┤
│ ESTADO DEL SISTEMA                  │
│ CANARIO                             │
│ SMN                                 │
│ APNs                                │
│ FCM                                 │
│ SMS                                 │
│ VOZ                                 │
├─────────────────────────────────────┤
│ ALERTAS ACTIVAS                     │
├─────────────────────────────────────┤
│ T0 preparados                       │
│ T1 preparados                       │
│ T2 preparados                       │
│ T3 preparados                       │
├─────────────────────────────────────┤
│ PERSONAL SIN CONFIRMAR              │
└─────────────────────────────────────┘
```

---

# 37. PANTALLA DE ALERTA MÓVIL

Debe ser deliberadamente simple.

Elementos:

```text
ALERTA UNS

NARANJA

TORMENTA SEVERA

BAHÍA BLANCA

Vigencia:
18:00 – 23:00

INSTRUCCIÓN:

PERMANECER EN EL PREDIO
Y SEGUIR LAS INDICACIONES
DE LA AUTORIDAD.

[ RECIBIDO ]

[ ESTOY A SALVO ]

[ NECESITO ASISTENCIA ]
```

Diseñar para:

* estrés;
* poca iluminación;
* visión reducida;
* uso con una mano;
* adultos mayores;
* accesibilidad.

---

# 38. ACCESIBILIDAD

Objetivo:

```text
WCAG 2.2 AA
```

Aplicar:

* alto contraste;
* textos grandes;
* pictogramas;
* lenguaje claro;
* no depender solamente del color;
* soporte sonoro;
* TTS cuando corresponda;
* accesibilidad del teclado en web;
* lectores de pantalla.

---

# 39. MODO SIMULACRO

Debe existir un modo:

```text
SIMULACRO
```

Toda notificación de simulacro debe estar inequívocamente identificada.

Nunca mezclar:

```text
REAL
```

con:

```text
SIMULACRO
```

Debe existir un entorno seguro para probar:

* alarma;
* confirmación;
* escalamiento;
* dashboard;
* SMS;
* voz;
* canario.

---

# 40. MVP

Construir primero un MVP realmente operativo.

El MVP debe incluir exclusivamente lo necesario para demostrar que el sistema crítico funciona.

## MVP — FUNCIONES OBLIGATORIAS

### Backend

* Laravel.
* MySQL.
* Redis.
* API REST.
* autenticación.
* RBAC.
* MFA T0/T1.
* usuarios.
* roles.
* suplentes.
* dispositivos.
* readiness.
* alertas.
* decisiones.
* emisiones.
* deliveries.
* ACK.
* escalamiento.
* auditoría.
* canario.
* simulacro.

### App Android

* login;
* registro del dispositivo;
* readiness;
* recepción de alerta;
* alarma;
* vibración;
* pantalla crítica;
* respuestas rápidas;
* confirmación;
* estado de conexión;
* prueba de alarma.

### App iOS

* login;
* APNs;
* readiness;
* Time Sensitive;
* Critical Alerts sujeto a aprobación de Apple;
* pantalla;
* confirmación;
* prueba de alarma.

### Web

* login;
* dashboard;
* usuarios;
* dispositivos;
* readiness;
* crear alerta;
* evaluar;
* aprobar;
* enviar;
* monitorear;
* escalar;
* cesar;
* auditoría;
* simulacro;
* canario.

### Canales

MVP:

```text
APNs
FCM
SMS
voz
email
```

No depender exclusivamente de un único canal.

---

# 41. MVP — LO QUE NO DEBE ENTRAR

No retrasar el MVP con:

* IA;
* chatbot;
* mapas complejos;
* custodia escolar;
* calendarios;
* encuestas;
* tareas;
* mantenimiento;
* PPO;
* analítica avanzada;
* integración profunda con Moodle;
* automatizaciones no esenciales.

Primero demostrar:

> ALERTA → ALARMA → CONFIRMACIÓN → ESCALAMIENTO → AUDITORÍA.

---

# 42. VERSIÓN COMPLETA

Una vez validado el MVP, agregar:

## Comunicación

* M1–M8;
* mensajería interna;
* cascadas;
* rumores;
* partes prolongados;
* formatos accesibles.

## Infraestructura

* checklists AT-01;
* mantenimiento;
* inspecciones;
* fotografías;
* firma;
* historial.

## Comunicaciones

* AT-02;
* RACUNS;
* pruebas radiales;
* Starlink;
* Meshtastic;
* estado de comunicaciones.

## Predios

* edificios;
* sectores;
* vulnerabilidades;
* zonas de confinamiento;
* rutas;
* recursos.

## Escuelas

* custodia;
* retiro autorizado;
* responsables;
* familiares;
* trazabilidad.

## Integraciones

* SMN;
* Moodle;
* Telegram;
* correo;
* SMS;
* voz;
* web;
* megafonía;
* pantallas;
* RACUNS.

---

# 43. MÓDULO ECD

Implementar posteriormente:

```text
Estado de Comunicaciones Degradadas
```

El sistema NO debe declarar automáticamente ECD.

Debe asistir al operador.

Registrar:

* ping interno;
* conectividad externa;
* SMN;
* Defensa Civil;
* proveedor push;
* SMS;
* voz;
* radio;
* intentos fallidos;
* timestamp.

Mostrar:

```text
Pilar 1
OK

Pilar 2
FAIL

Pilar 3
OK
```

Y generar evidencia para la decisión humana.

---

# 44. MODELO DE REPOSITORIO

Utilizar monorepo:

```text
alertuns/

├── api/
│   ├── app/
│   │   ├── Domain/
│   │   ├── Rules/
│   │   ├── Channels/
│   │   ├── Services/
│   │   └── Jobs/
│   ├── database/
│   ├── routes/
│   └── tests/

├── mobile/
│   ├── app/
│   ├── android/
│   └── ios/

├── web/

├── infra/
│   ├── docker/
│   ├── monitoring/
│   ├── backup/
│   └── deployment/

├── docs/
│   ├── architecture/
│   ├── adr/
│   ├── security/
│   ├── api/
│   ├── runbooks/
│   └── testing/

└── README.md
```

---

# 45. DOCUMENTACIÓN OBLIGATORIA

Generar:

```text
README.md

ARCHITECTURE.md

SECURITY.md

DEPLOYMENT.md

DISASTER_RECOVERY.md

API.md

DATABASE.md

MOBILE_ANDROID.md

MOBILE_IOS.md

NOTIFICATIONS.md

SMN_INTEGRATION.md

TESTING.md

OPERATIONS.md

RUNBOOK.md

INCIDENT_RESPONSE.md

PRIVACY.md

THREAT_MODEL.md
```

Además:

```text
ADR-001-stack
ADR-002-notifications
ADR-003-ios-critical-alerts
ADR-004-android-alarm
ADR-005-authentication
ADR-006-database
ADR-007-high-availability
ADR-008-smn
ADR-009-messaging
```

---

# 46. TESTING

Implementar:

## Unit tests

* reglas;
* estados;
* permisos;
* escalamiento;
* plantillas.

## Integration tests

* API;
* DB;
* Redis;
* proveedores.

## E2E

```text
crear alerta
→ evaluar
→ aprobar
→ enviar
→ recibir
→ confirmar
→ escalar
→ cerrar
```

## Load testing

Probar progresivamente:

```text
100
500
1.000
5.000
10.000
```

usuarios/dispositivos simulados.

No asumir 10.000 usuarios reales hasta comprobar infraestructura.

---

# 47. MATRIZ DE PRUEBAS MÓVILES

Android:

* app cerrada;
* background;
* pantalla bloqueada;
* pantalla apagada;
* silencio;
* DND;
* batería;
* Doze;
* reinicio;
* WiFi;
* 4G;
* 5G;
* pérdida de red;
* recuperación;
* fabricantes.

iOS:

* app cerrada;
* bloqueada;
* silencio;
* Focus;
* Critical Alert;
* Time Sensitive;
* Low Power Mode;
* WiFi;
* celular;
* pérdida de red.

Web:

* Chrome;
* Edge;
* Firefox;
* Safari;
* Service Worker;
* Web Push;
* Web Audio;
* Wake Lock.

---

# 48. PRUEBA DE CAMPO

No considerar terminado el proyecto porque funciona en un emulador.

Debe probarse con teléfonos reales.

Laboratorio mínimo:

```text
6+ Android
3+ iPhone
```

Y posteriormente:

```text
15–20 dispositivos
```

Crear una matriz:

| Dispositivo | OS      | Estado    | Resultado |
| ----------- | ------- | --------- | --------- |
| Samsung     | Android | silencio  |           |
| Xiaomi      | Android | DND       |           |
| Motorola    | Android | bloqueado |           |
| Pixel       | Android | batería   |           |
| iPhone      | iOS     | silencio  |           |
| iPhone      | iOS     | Focus     |           |

---

# 49. CRITERIOS DE BLOQUEO

NO permitir release si:

* falla la alarma crítica;
* falla el ACK;
* falla el escalamiento;
* se puede emitir sin autorización;
* se puede duplicar una alerta accidentalmente;
* auditoría incompleta;
* backups no restaurables;
* canario fallando;
* vulnerabilidad crítica abierta;
* secretos expuestos;
* Critical Alerts de Apple no aprobados y no existe fallback;
* Android presenta fallas graves sin advertencia de readiness;
* proveedor push caído sin mecanismo alternativo;
* se pierde la trazabilidad.

---

# 50. SEGURIDAD DEL EMISOR

Una cuenta comprometida podría generar una falsa alarma.

Por eso:

## T0/T1

Requerir:

* MFA;
* sesión corta;
* reautenticación para acciones críticas;
* control de dispositivo;
* auditoría.

Para:

```text
ROJO
ACP
evacuación
confinamiento masivo
audiencia masiva
```

exigir:

```text
dos personas
```

salvo procedimiento institucional excepcional explícitamente autorizado.

---

# 51. DEFENSA CONTRA DUPLICACIÓN

Cada alerta debe tener:

```text
public_id
UUID/ULID interno
idempotency_key
version
```

Una emisión no debe poder ejecutarse dos veces por:

* doble click;
* refresh;
* timeout;
* retry;
* worker duplicado.

---

# 52. COLAS

Separar:

```text
critical
high
normal
bulk
```

Nunca permitir que:

```text
email masivo
```

bloquee:

```text
alerta crítica.
```

Los workers críticos deben tener prioridad.

---

# 53. FALLA DE PROVEEDORES

El sistema debe detectar:

```text
FCM DOWN
APNs DOWN
SMS DOWN
VOICE DOWN
EMAIL DOWN
SMN DOWN
REDIS DOWN
DB DOWN
```

Y mostrarlo.

Nunca informar:

> "mensaje enviado"

si solamente fue:

> "mensaje puesto en cola".

Distinguir:

```text
queued
sent
provider_accepted
delivered
failed
expired
acknowledged
```

---

# 54. PRINCIPIO DE VERDAD OPERATIVA

El sistema debe ser extremadamente estricto con las palabras:

```text
ENVIADO ≠ ENTREGADO

ENTREGADO ≠ LEÍDO

LEÍDO ≠ CONFIRMADO

CONFIRMADO ≠ SEGURO
```

Cada estado debe ser independiente.

---

# 55. UX PARA SITUACIONES DE EMERGENCIA

No crear interfaces complejas.

Durante una emergencia:

```text
MENOS OPCIONES
MÁS INFORMACIÓN CRÍTICA
```

Priorizar:

1. qué ocurre;
2. dónde;
3. cuándo;
4. qué hacer;
5. confirmar;
6. pedir ayuda.

---

# 56. FUTURA INTEGRACIÓN CON SENSORES

La arquitectura debe permitir eventualmente recibir eventos desde:

* sensores IoT;
* estaciones meteorológicas;
* nivel de agua;
* infraestructura;
* bombas;
* energía;
* incendio;
* temperatura;
* otros sistemas UNS.

Pero:

```text
sensor ≠ decisión
```

Un sensor puede crear:

```text
EVENTO DETECTADO
```

pero la activación de una emergencia crítica debe respetar el modelo de autorización institucional, salvo que exista una regla formalmente aprobada.

---

# 57. SMN Y ALERTUNS

Mantener separadas las capas:

```text
SMN
 ↓
INGESTA
 ↓
NORMALIZACIÓN
 ↓
BORRADOR
 ↓
EVALUACIÓN HUMANA
 ↓
DECISIÓN UNS
 ↓
ALERTUNS
```

No mezclar directamente:

```text
SMN → usuarios
```

en la primera versión.

---

# 58. ROADMAP

Dividir el proyecto en:

## FASE 0

PoC crítica.

## FASE 1

MVP operativo.

## FASE 2

Piloto institucional.

## FASE 3

Producción controlada.

## FASE 4

Despliegue progresivo.

## FASE 5

Funciones completas.

## FASE 6

Integraciones institucionales.

---

# 59. FASE 0 — PRIMER OBJETIVO

Antes de generar todo el código:

## NO construyas todavía toda la aplicación.

Primero entregá:

### Documento 1

Arquitectura propuesta.

### Documento 2

Matriz de riesgos.

### Documento 3

Modelo de amenazas.

### Documento 4

ADR de stack tecnológico.

### Documento 5

Auditoría de infraestructura requerida.

### Documento 6

PoC Android.

### Documento 7

PoC iOS.

### Documento 8

Diseño de notificaciones.

### Documento 9

Modelo de datos.

### Documento 10

Plan de pruebas.

Y especialmente:

# DEMOSTRAR QUE LA ALARMA CRÍTICA ES TÉCNICAMENTE VIABLE.

---

# 60. ORDEN DE IMPLEMENTACIÓN

Una vez aprobada la Fase 0:

```text
1. Repository
2. Infrastructure
3. Database
4. Authentication
5. RBAC
6. Devices
7. Readiness
8. Notification dispatcher
9. Android alarm
10. iOS alarm
11. ACK
12. Escalation
13. Audit
14. Web console
15. Canary
16. Monitoring
17. SMN ingestion
18. Simulation
19. Security hardening
20. Load testing
21. Pilot
22. Production
```

---

# 61. REGLA DE DESARROLLO

No generar miles de líneas de código de una sola vez.

Trabajar por incrementos.

Cada incremento debe entregar:

```text
código
tests
documentación
migraciones
configuración
criterios de aceptación
```

Y explicar:

```text
qué se modificó
por qué
cómo probarlo
qué queda pendiente
```

---

# 62. REGLA CONTRA CÓDIGO FRÁGIL

No utilizar:

* hacks;
* sleeps arbitrarios;
* polling innecesario;
* credenciales hardcodeadas;
* lógica duplicada;
* variables globales sin necesidad;
* dependencias abandonadas;
* librerías no mantenidas;
* mecanismos no documentados para evadir restricciones del sistema operativo.

Preferir:

* código simple;
* modular;
* testeable;
* mantenible;
* observable;
* documentado.

---

# 63. REGLA CONTRA ALUCINACIONES

Si no sabés algo:

```text
NO LO INVENTES.
```

Si una API no está confirmada:

```text
MARCAR COMO NO CONFIRMADA.
```

Si una capacidad de Android/iOS depende de permisos:

```text
INDICARLO.
```

Si depende de aprobación de Apple/Google:

```text
INDICARLO.
```

Si una función del hosting no está confirmada:

```text
SOLICITAR VERIFICACIÓN.
```

---

# 64. REGLA DE COMPATIBILIDAD

Toda afirmación técnica sobre:

* Android;
* iOS;
* Google Play;
* Apple;
* APNs;
* FCM;

debe basarse preferentemente en documentación oficial vigente.

No utilizar blogs como autoridad principal para restricciones críticas.

---

# 65. REGLA DE PROPIEDAD INSTITUCIONAL

Todo el proyecto debe quedar preparado para que:

* código fuente;
* repositorios;
* dominios;
* credenciales;
* cuentas Apple;
* cuentas Google;
* Firebase;
* servidores;
* bases;
* backups;
* certificados;

sean propiedad/control de la UNS.

Evitar dependencia innecesaria de un desarrollador particular.

---

# 66. INDEPENDENCIA DE PROVEEDORES

Diseñar interfaces:

```text
NotificationChannel
```

para permitir:

```text
FCM
APNs
SMS Provider A
SMS Provider B
Voice Provider A
Voice Provider B
Email
Telegram
```

sin modificar el dominio principal.

Ejemplo conceptual:

```text
Alert
  ↓
Broadcast
  ↓
Dispatcher
  ↓
Channel Adapter
  ├── APNs
  ├── FCM
  ├── SMS
  ├── Voice
  ├── Email
  └── Telegram
```

---

# 67. INTEGRACIÓN FUTURA RACUNS

No implementar dentro del MVP.

Pero dejar una interfaz:

```text
EmergencyCommunicationAdapter
```

para que posteriormente pueda integrarse:

```text
AlertUNS
   ↓
RACUNS
   ↓
Radio
```

La aplicación no debe asumir que puede controlar una radio si técnicamente no existe esa interfaz.

---

# 68. INFORME POST-EMERGENCIA

Al cerrar una emergencia generar automáticamente:

```text
ID
Fecha
Duración
Tipo
Nivel
Decisión
Responsables
Audiencias
Cantidad dispositivos
Enviados
Entregados
Fallidos
Confirmados
Escalados
SMS
Voz
Canales
Tiempos
Incidentes
Actualizaciones
Cese
Observaciones
```

Generar:

* vista web;
* PDF;
* CSV;
* JSON.

---

# 69. INDICADORES

Implementar:

```text
% dispositivos preparados

% alertas entregadas

% confirmaciones

tiempo medio de confirmación

tiempo p95 de entrega

fallos por fabricante

fallos por proveedor

fallos por versión

alertas por predio

alertas por nivel

cantidad de simulacros

éxito de canarios

disponibilidad

incidentes
```

---

# 70. ENTREGA DEL MVP

El MVP se considera terminado únicamente cuando exista:

```text
Backend funcionando
+
Base de datos
+
Web funcionando
+
Android real
+
iPhone real
+
APNs/FCM
+
ACK
+
Escalamiento
+
Auditoría
+
Canario
+
Backup
+
Monitoring
+
Tests
+
Documentación
+
Simulacro exitoso
```

---

# 71. ENTREGA FINAL

La entrega debe incluir:

```text
Código fuente
Base de datos/migrations
Docker/IaC si corresponde
CI/CD
OpenAPI
Manual administrador
Manual usuario
Manual operación
Manual contingencia
Runbooks
Threat Model
SBOM
Resultados de pentest
Resultados de pruebas
Matriz de dispositivos
Plan de backup
Plan de recuperación
Plan de actualización
Política de logs
Política de retención
Documentación Apple
Documentación Android
```

---

# 72. PRIMERA RESPUESTA QUE DEBES DAR

Antes de programar, respondé con un:

# INFORME DE ARQUITECTURA Y VIABILIDAD

Debe contener exactamente:

1. Resumen ejecutivo.
2. Comprensión del problema.
3. Funciones de BomberBOT que se adoptarán funcionalmente.
4. Diferencias entre BomberBOT y AlertUNS.
5. Arquitectura propuesta.
6. Stack tecnológico.
7. Riesgos críticos.
8. Viabilidad de Android.
9. Viabilidad de iOS.
10. Estrategia Critical Alerts.
11. Estrategia de fallback.
12. Auditoría del hosting necesaria.
13. Modelo de seguridad.
14. Modelo de datos.
15. API.
16. Arquitectura de notificaciones.
17. MVP.
18. Versión completa.
19. Roadmap.
20. Plan de pruebas.
21. Criterios de aceptación.
22. Decisiones que requieren intervención humana/institucional.
23. Preguntas bloqueantes.

NO empezar a generar toda la aplicación hasta completar este informe.

---

# 73. CRITERIO FINAL DE INGENIERÍA

Este sistema no debe optimizarse primero para:

```text
cantidad de funcionalidades
```

Debe optimizarse primero para:

```text
CONFIABILIDAD
SEGURIDAD
TRAZABILIDAD
REDUNDANCIA
MANTENIBILIDAD
OPERABILIDAD
```

La función más importante del sistema es:

> Cuando la Universidad Nacional del Sur toma una decisión institucional de emergencia, AlertUNS debe hacer todo lo técnicamente posible para que esa decisión llegue a las personas correctas, por los canales disponibles, produzca una señal inequívoca de atención cuando corresponda, permita confirmar la recepción y deje evidencia completa del proceso.

---

# 74. COMENZAR AHORA

Comenzá exclusivamente por:

## FASE 0 — ARQUITECTURA + PoC

No escribas todavía toda la aplicación.

Entregá primero:

```text
ARCHITECTURE.md
THREAT_MODEL.md
MVP.md
NOTIFICATIONS.md
DEVICE_READINESS.md
DATABASE_DESIGN.md
API_DESIGN.md
DEVOPS.md
TEST_PLAN.md
ADR/
```

Después implementá:

```text
PoC Android
PoC iOS
PoC APNs
PoC FCM
PoC alarma
PoC ACK
```

La PoC debe responder una pregunta concreta:

> **¿Podemos conseguir, con las restricciones actuales de Android e iOS, una alarma institucional suficientemente confiable para el uso previsto por la UNS y cuáles son exactamente sus límites?**

Solo después de responderla positivamente, avanzar al desarrollo completo de AlertUNS.
