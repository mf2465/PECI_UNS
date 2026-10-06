# AlertUNS — Plan integral de desarrollo

## Sistema institucional de alerta y confirmación para la activación del PECI-UNS

**Plataformas:** Android · iPhone/iOS · Web

**Organización:** Universidad Nacional del Sur (UNS)

**Proyecto:** AlertUNS

**Objetivo:** disponer de un sistema institucional propio para emitir, distribuir, confirmar, escalar y auditar comunicaciones de emergencia asociadas al PECI-UNS.

---

# 1. Principio rector del proyecto

AlertUNS deberá desarrollarse utilizando **software libre, gratuito o de código abierto**, evitando licencias comerciales de software tanto como sea técnicamente posible.

La arquitectura deberá priorizar:

* software open source;
* herramientas gratuitas;
* tecnologías con comunidades activas;
* formatos y protocolos abiertos;
* ausencia de dependencia de un proveedor específico;
* posibilidad de instalar y administrar todos los componentes en infraestructura de la UNS;
* propiedad institucional del código fuente;
* propiedad institucional de las bases de datos;
* propiedad institucional de las credenciales;
* documentación completa;
* posibilidad de migrar de proveedor sin reconstruir el sistema.

## 1.1 Regla de costos

El proyecto deberá distinguir tres categorías:

### A. Software

**Objetivo: costo de licencia = $0.**

Ejemplos:

* Linux;
* PHP;
* Laravel;
* MySQL Community o MariaDB;
* Valkey;
* React;
* React Native;
* TypeScript;
* Kotlin;
* Swift;
* Nginx;
* Docker/Podman;
* Git;
* GitLab CE o Gitea;
* Prometheus;
* Grafana OSS;
* GlitchTip;
* MinIO cuando resulte conveniente;
* OpenAPI;
* herramientas de testing open source.

### B. Servicios externos

Pueden tener costo aunque el software utilizado sea gratuito:

* SMS;
* llamadas telefónicas automáticas;
* dominio si la UNS no dispone de uno;
* certificados comerciales, si fueran necesarios;
* infraestructura cloud;
* publicación en tiendas;
* servicios de terceros.

La arquitectura deberá permitir reemplazar cada uno de estos servicios.

### C. Infraestructura

Debe priorizarse:

1. infraestructura existente de la UNS;
2. servidores institucionales;
3. virtualización existente;
4. infraestructura propia;
5. únicamente en último término, servicios cloud.

---

# 2. Objetivo institucional

AlertUNS será el sistema propio de notificación masiva previsto para apoyar la activación del PECI-UNS.

El sistema deberá permitir:

* registrar personas y roles;
* registrar dispositivos;
* conocer el estado de preparación de cada dispositivo;
* recibir eventos o información meteorológica;
* generar una Ficha del Alerta;
* evaluar la situación;
* registrar recomendaciones;
* registrar la decisión de la autoridad;
* emitir alertas;
* distribuirlas por diferentes canales;
* solicitar confirmación;
* escalar automáticamente la comunicación;
* registrar entregas;
* registrar respuestas;
* registrar el cese;
* registrar rectificaciones;
* conservar una auditoría completa;
* generar informes posteriores;
* funcionar en modo simulacro;
* detectar degradación de comunicaciones;
* mantener mecanismos alternativos cuando los servicios principales no estén disponibles.

AlertUNS **no reemplaza los procedimientos institucionales**, sino que los implementa y facilita.

Tampoco reemplaza:

* RACUNS;
* radio;
* Defensa Civil;
* medios presenciales;
* megafonía;
* SMS;
* telefonía;
* otros mecanismos de contingencia.

---

# 3. Principio fundamental de diseño

La aplicación no deberá tomar decisiones de emergencia por sí misma.

La arquitectura será:

```text
INFORMACIÓN
    ↓
DETECCIÓN
    ↓
EVALUACIÓN HUMANA
    ↓
RECOMENDACIÓN
    ↓
APROBACIÓN
    ↓
EMISIÓN
    ↓
DISTRIBUCIÓN
    ↓
CONFIRMACIÓN
    ↓
ESCALAMIENTO
    ↓
CESE
    ↓
INFORME
```

El sistema ejecuta y registra decisiones humanas.

---

# 4. Referencia funcional: BomberBOT

BomberBOT se utilizará exclusivamente como **referencia funcional**.

Se tomarán como referencia conceptual capacidades públicas como:

* alarma;
* sonido;
* vibración;
* convocatorias selectivas;
* convocatorias generales;
* respuestas rápidas;
* cancelación;
* panel web;
* monitoreo;
* estado de dispositivos;
* simulacros.

No se copiarán:

* código;
* diseño;
* marca;
* sonidos;
* textos;
* arquitectura propietaria;
* componentes propietarios.

AlertUNS deberá desarrollarse independientemente y de acuerdo con el protocolo UNS.

---

# 5. Restricción tecnológica fundamental

No se deberá elegir una tecnología únicamente porque sea conocida.

Cada componente deberá evaluarse según:

1. licencia;
2. costo;
3. seguridad;
4. madurez;
5. comunidad;
6. mantenimiento;
7. documentación;
8. posibilidad de autohospedaje;
9. posibilidad de migración;
10. dependencia de proveedor.

---

# 6. Arquitectura tecnológica propuesta

## 6.1 Backend

### PHP

Versión estable soportada.

### Laravel

Framework principal.

Utilización:

* API;
* autenticación;
* autorización;
* ORM;
* colas;
* scheduler;
* eventos;
* validación;
* testing;
* consola administrativa.

Laravel deberá utilizarse únicamente en componentes cuya licencia permita el uso institucional previsto.

---

# 7. Base de datos

La primera opción será:

```text
MySQL Community Edition
```

o, si la evaluación institucional lo determina:

```text
MariaDB
```

No se utilizará una edición comercial que introduzca costos de licencia.

La base deberá ser portable.

No deberá existir lógica crítica que impida migrar entre motores compatibles.

---

# 8. Cola de trabajos

En lugar de depender obligatoriamente de Redis, se evaluará:

```text
Valkey
```

como componente open source para:

* colas;
* cache;
* locks;
* temporizadores;
* coordinación de workers.

Esto evita introducir una dependencia innecesaria de una licencia que pueda cambiar en el futuro.

---

# 9. Servidor web

Preferentemente:

```text
Nginx
```

sobre:

```text
Linux
```

Ambos deberán ser gratuitos y de código abierto.

Alternativamente:

```text
Apache
```

si la infraestructura existente de la UNS lo hace más conveniente.

---

# 10. Contenedores

Cuando la infraestructura lo permita:

```text
Docker
```

o:

```text
Podman
```

Para maximizar independencia de proveedor, deberá ser posible ejecutar el sistema sin depender de una plataforma cloud específica.

---

# 11. Desarrollo móvil

## 11.1 Android

Lenguaje:

```text
Kotlin
```

Herramienta:

```text
Android Studio
```

SDK:

```text
Android SDK
```

Todos los componentes de desarrollo deberán utilizar herramientas gratuitas.

---

# 12. iOS

Lenguaje:

```text
Swift
```

Herramienta:

```text
Xcode
```

La interfaz podrá desarrollarse:

* nativamente;
* o mediante React Native para la interfaz general.

Sin embargo, la capa de alarma deberá mantener componentes nativos.

---

# 13. React Native

Se podrá utilizar React Native para:

* navegación;
* formularios;
* estado;
* configuración;
* perfil;
* preparación del dispositivo;
* historial;
* información institucional.

Pero no deberá asumirse que React Native puede resolver por sí solo:

* alarmas críticas;
* audio especial;
* permisos;
* servicios de Android;
* Critical Alerts;
* extensiones de iOS;
* comportamiento con pantalla bloqueada.

La capa crítica deberá implementarse mediante:

```text
Android → Kotlin

iOS → Swift
```

---

# 14. Consola web

Se utilizará:

```text
React + TypeScript
```

o:

```text
Vue + TypeScript
```

La decisión final deberá hacerse en la Fase 0.

La consola deberá ser una aplicación web institucional.

---

# 15. Control de versiones

Todo el código deberá estar en:

```text
Git
```

El servidor Git podrá ser:

```text
GitLab Community Edition
```

o:

```text
Gitea
```

instalado en infraestructura de la UNS.

No deberá dependerse de una cuenta personal de un desarrollador.

---

# 16. Repositorio

Se propone:

```text
alertuns/
│
├── api/
├── mobile/
│   ├── android/
│   └── ios/
├── web/
├── infra/
├── tests/
├── docs/
├── scripts/
└── .github/
```

Si se utiliza GitLab:

```text
alertuns/
├── api
├── mobile
├── web
├── infra
└── docs
```

El repositorio deberá ser institucional.

---

# 17. Arquitectura general

```text
                         ALERTUNS
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
          ANDROID          iOS          WEB
              │             │             │
              └─────────────┼─────────────┘
                            │
                          HTTPS
                            │
                            ▼
                    ┌──────────────┐
                    │ API Laravel  │
                    └──────┬───────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
          MySQL          Valkey       Auditoría
             │             │             │
             └─────────────┼─────────────┘
                           │
                    Motor de alertas
                           │
          ┌────────────────┼─────────────────┐
          │                │                 │
          ▼                ▼                 ▼
         FCM              APNs         Canales alternativos
          │                │                 │
       Android            iOS          SMS / voz / mail
```

---

# 18. Principio de independencia

Ningún componente externo deberá ser indispensable para conservar:

* usuarios;
* roles;
* alertas;
* decisiones;
* auditoría;
* confirmaciones;
* historial.

Por ejemplo:

```text
FCM puede fallar
        ↓
AlertUNS continúa funcionando
        ↓
APNs / SMS / correo / voz
```

---

# 19. Notificación crítica

Esta es la principal incertidumbre técnica del proyecto.

No se deberá comenzar desarrollando todo el sistema antes de resolverla.

La primera prueba será:

```text
SERVIDOR
   ↓
FCM / APNs
   ↓
TELÉFONO
   ↓
ALARMA
   ↓
ACK
```

---

# 20. Android

Deberá probarse:

* aplicación abierta;
* aplicación en segundo plano;
* aplicación cerrada;
* pantalla bloqueada;
* pantalla apagada;
* teléfono en silencio;
* No Molestar;
* ahorro de batería;
* Doze;
* Wi-Fi;
* 4G;
* 5G;
* pérdida de red;
* recuperación;
* reinicio;
* diferentes fabricantes.

Fabricantes mínimos:

* Samsung;
* Motorola;
* Xiaomi/Redmi;
* Pixel;
* Oppo/Realme cuando corresponda.

---

# 21. iOS

Deberá probarse:

* aplicación abierta;
* aplicación cerrada;
* pantalla bloqueada;
* modo silencio;
* Focus;
* No Molestar;
* Low Power Mode;
* pérdida de red;
* recuperación;
* diferentes generaciones de iPhone.

La implementación deberá solicitar y validar las capacidades de Critical Alerts cuando estén disponibles.

Si Apple no habilita Critical Alerts:

```text
Critical Alerts
      ↓
NO DISPONIBLE
      ↓
Time Sensitive
      +
SMS
      +
voz
      +
procedimiento alternativo
```

No se deberá afirmar que un iPhone puede superar el silencio sin la autorización/capacidad correspondiente.

---

# 22. Regla fundamental sobre las plataformas móviles

No se deberá diseñar el sistema suponiendo:

> "la aplicación puede ignorar cualquier configuración del teléfono".

Eso no es técnicamente válido.

La arquitectura deberá trabajar con:

```text
capacidad disponible
        +
permiso del usuario
        +
estado del dispositivo
        +
canales alternativos
```

---

# 23. Estado de preparación del dispositivo

Cada dispositivo deberá tener un estado:

```text
READY
DEGRADED
NOT_READY
UNKNOWN
```

Y almacenar:

* plataforma;
* versión;
* fabricante;
* modelo;
* versión de aplicación;
* token push;
* última conexión;
* permisos;
* Critical Alerts;
* Full Screen Intent cuando corresponda;
* batería;
* optimización de batería;
* conectividad;
* última prueba;
* última alarma;
* último ACK;
* versión del sistema;
* estado de preparación.

---

# 24. Indicador de preparación

Ejemplo:

```text
Miguel Flores
Android
Samsung

✓ Aplicación instalada
✓ Push habilitado
✓ Sonido crítico habilitado
✓ Vibración habilitada
✓ Permiso necesario habilitado
✓ Último heartbeat: 2 min
✓ Última prueba: correcta

ESTADO: READY
```

---

# 25. Actores

Se contemplan:

* Rector;
* CDE;
* Nodo Central;
* Oficina de Recepción de Avisos;
* SHST;
* DCI;
* Vocería;
* Telecomunicaciones;
* Infraestructura;
* mayordomos;
* decanos;
* directores;
* docentes;
* nodocentes;
* estudiantes;
* familias;
* brigadas.

---

# 26. Niveles de audiencia

## T0 — Mando

Incluye:

* CDE;
* suplentes;
* Rector;
* operadores del Nodo Central;
* Vocería.

Canales:

* alarma crítica;
* SMS;
* voz.

Confirmación:

```text
OBLIGATORIA
```

---

# 27. T1 — Coordinación

Incluye:

* mayordomos;
* decanos;
* directores;
* Telecomunicaciones;
* Infraestructura;
* brigadas;
* responsables operativos.

Canales:

* alarma;
* SMS.

Confirmación:

```text
OBLIGATORIA
```

---

# 28. T2 — Comunidad laboral

Incluye:

* docentes;
* nodocentes;
* investigadores.

Canales:

* notificación prioritaria;
* correo.

Confirmación:

```text
RECIBIDO
```

---

# 29. T3 — Comunidad general

Incluye:

* estudiantes;
* familias;
* visitantes.

Canales:

* push estándar;
* web;
* Moodle;
* canales abiertos;
* Telegram cuando corresponda.

---

# 30. Cadena de decisión

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

No se podrá emitir una alerta crítica masiva sin pasar por las reglas de autorización correspondientes.

---

# 31. Ficha del Alerta

Antes de emitir deberá completarse la Ficha del Alerta.

Como mínimo:

* fecha;
* hora;
* fuente;
* zona;
* fenómeno;
* nivel;
* descripción;
* vigencia;
* población afectada;
* acción recomendada;
* autoridad;
* canales;
* plantilla;
* responsables;
* observaciones.

Los campos obligatorios deberán ser validados por el sistema.

---

# 32. Regla de dos personas

Para determinados eventos críticos:

```text
OPERADOR
    ↓
CREA
    ↓
RESPONSABLE
    ↓
APRUEBA
    ↓
EMITE
```

La aplicación deberá impedir la emisión si la política exige dos personas y la segunda aprobación no existe.

---

# 33. Respuestas rápidas

Se implementarán:

```text
RECEIVED
SAFE
SHELTERED
NEED_HELP
UNAVAILABLE_ROLE
```

Ejemplo:

```text
RECEIVED
"Recibido y comprendido"

SAFE
"Estoy a salvo"

SHELTERED
"Confinamiento cumplido"

NEED_HELP
"Necesito asistencia"

UNAVAILABLE_ROLE
"No puedo cumplir mi rol"
```

---

# 34. Escalamiento

Configuración inicial:

```text
T+0
Push

T+60 s
reintento

T+2 min
SMS

T+5 min
voz

T+15 min
suplente

T+30 min
reporte operativo
```

Los tiempos deberán ser configurables.

---

# 35. Cese

Toda alerta deberá poder:

* cesarse;
* rectificarse;
* actualizarse;
* cerrarse.

Debe quedar registrada:

* quién;
* cuándo;
* por qué;
* qué mensaje;
* qué población;
* qué canales.

---

# 36. Simulacro

El sistema deberá disponer de:

```text
MODO PRODUCCIÓN
MODO SIMULACRO
```

El modo simulacro debe:

* impedir confusión con una emergencia real;
* registrar la actividad;
* medir tiempos;
* medir entregas;
* medir confirmaciones;
* generar informe.

---

# 37. Canario

Se deberán disponer dispositivos institucionales permanentes:

```text
2 Android
2 iPhone
```

como mínimo.

Deberán:

* permanecer conectados;
* recibir mensajes de prueba;
* confirmar automáticamente cuando corresponda;
* informar estado;
* detectar degradación.

---

# 38. Base de datos

Entidades principales:

```text
users
persons
roles
permissions
role_assignments
deputies
sites
buildings
departments
devices
device_readiness
alerts
alert_decisions
broadcasts
audiences
deliveries
acks
escalations
templates
template_versions
sources
source_snapshots
audit_logs
providers
provider_events
canary_devices
simulations
ecd_events
reports
```

---

# 39. Auditoría

Toda modificación importante deberá generar un registro.

La auditoría deberá utilizar encadenamiento criptográfico:

```text
hash_actual =
SHA256(
    hash_anterior
    +
    contenido
)
```

De esta manera podrá detectarse manipulación posterior.

---

# 40. API

Base:

```text
/api/v1/
```

Ejemplos:

```text
POST /auth/login
POST /auth/refresh

GET /devices/me
POST /devices/register

GET /alerts
POST /alerts

POST /alerts/{id}/assess
POST /alerts/{id}/recommend
POST /alerts/{id}/approve
POST /alerts/{id}/cease

POST /alerts/{id}/broadcasts

GET /broadcasts/{id}/status
POST /broadcasts/{id}/ack

GET /people
GET /roles
GET /role-assignments

GET /health
GET /canary/status

GET /reports/post-activation/{alertId}
```

---

# 41. Seguridad

Aplicar:

* HTTPS;
* TLS;
* MFA;
* RBAC;
* control por ámbito;
* rate limiting;
* protección CSRF;
* protección XSS;
* protección SSRF;
* protección contra replay;
* validación de entrada;
* gestión segura de secretos;
* rotación de credenciales;
* logs;
* auditoría;
* backups;
* pruebas de penetración.

---

# 42. Identidad

Prioridad:

```text
OIDC
```

o:

```text
SAML
```

contra infraestructura institucional.

Si la UNS dispone de LDAP:

```text
LDAP
```

podrá evaluarse como alternativa.

No se utilizarán códigos de invitación como mecanismo principal de identidad.

---

# 43. MFA

Los usuarios con capacidad de:

* aprobar;
* emitir;
* modificar;
* administrar;

deberán tener MFA.

Preferentemente:

```text
TOTP
```

mediante aplicaciones autenticadoras gratuitas.

---

# 44. Protección de datos

El sistema deberá aplicar:

* minimización;
* necesidad;
* control de acceso;
* retención;
* eliminación cuando corresponda;
* cifrado;
* auditoría.

La información personal no deberá utilizarse para:

* localización permanente;
* seguimiento continuo;
* análisis no relacionado con la emergencia.

---

# 45. Monitoreo

Software propuesto:

```text
Prometheus
Grafana OSS
GlitchTip
logs estructurados
```

Todo autohospedado.

No depender de servicios comerciales para obtener métricas básicas.

---

# 46. Métricas

Se deberán medir:

```text
alertas emitidas
entregas
ACK
latencia
errores
tokens inválidos
dispositivos offline
dispositivos no preparados
escalamientos
SMS enviados
llamadas realizadas
canarios
errores de APNs
errores de FCM
estado del SMN
estado del backend
estado de las colas
```

---

# 47. Objetivos iniciales

Como objetivos de diseño:

| Indicador                | Objetivo |
| ------------------------ | -------: |
| Disponibilidad           |   99,9 % |
| Aprobación → proveedor   |   ≤ 30 s |
| Confirmación T0 en 5 min |   ≥ 95 % |
| Preparación T0/T1        |   ≥ 98 % |
| Falsas emisiones masivas |        0 |
| Canario                  | ≥ 99,5 % |
| Auditoría de emisiones   |    100 % |

Estos valores deberán validarse mediante pruebas reales y podrán modificarse durante la ingeniería.

---

# 48. Alta disponibilidad

Arquitectura objetivo:

```text
                ALERTUNS
                   │
          ┌────────┴────────┐
          │                 │
        ALEM             PALIHUE
       PRIMARIO           ESPEJO
          │                 │
          └────────┬────────┘
                   │
             contingencia
                   │
                   ▼
        DESPACHADOR EXTERNO
```

---

# 49. Recuperación

Objetivos iniciales:

```text
RPO ≤ 5 minutos
RTO ≤ 15 minutos
```

Estos valores deberán ser confirmados por Telecomunicaciones según la infraestructura disponible.

---

# 50. Backups

Realizar:

* backup diario;
* cifrado;
* retención mínima de 30 días;
* copia separada;
* restauración mensual;
* registro de cada restauración.

Un backup que nunca fue restaurado no deberá considerarse validado.

---

# 51. Infraestructura mínima

Como punto de partida:

```text
4 vCPU
8 GB RAM
100 GB SSD
```

por entorno productivo inicial.

Esto deberá verificarse mediante pruebas de carga.

---

# 52. Entornos

Se deberán separar:

```text
DEV
STAGING
PRODUCTION
DR
```

No se deberá desarrollar directamente sobre producción.

---

# 53. CI/CD

Cada modificación deberá pasar por:

```text
commit
 ↓
lint
 ↓
tests
 ↓
security checks
 ↓
build
 ↓
staging
 ↓
pruebas
 ↓
aprobación
 ↓
production
```

---

# 54. Herramientas gratuitas

Se priorizará:

| Necesidad         | Herramienta               |
| ----------------- | ------------------------- |
| SO                | Linux                     |
| Código            | Git                       |
| Repositorio       | GitLab CE / Gitea         |
| Backend           | PHP + Laravel             |
| DB                | MySQL Community / MariaDB |
| Cache/colas       | Valkey                    |
| Web server        | Nginx                     |
| Contenedores      | Docker / Podman           |
| Frontend          | React / Vue               |
| Mobile            | React Native              |
| Android           | Kotlin + Android Studio   |
| iOS               | Swift + Xcode             |
| API               | OpenAPI                   |
| Monitoring        | Prometheus                |
| Dashboards        | Grafana OSS               |
| Error tracking    | GlitchTip                 |
| Automatización CI | GitLab CE                 |
| Tests API         | PHPUnit                   |
| Tests JS          | Vitest/Jest               |
| E2E Web           | Playwright                |
| Android tests     | AndroidX                  |
| iOS tests         | XCTest                    |

---

# 55. Componentes que NO deben incorporarse por costo de licencia

Evitar:

* frameworks comerciales;
* IDE comerciales;
* bases de datos comerciales;
* plataformas de monitoreo de pago;
* plataformas propietarias de notificaciones como dependencia única;
* SaaS obligatorio;
* servicios que bloqueen la exportación de datos;
* licencias por usuario;
* licencias por dispositivo.

---

# 56. Servicios que pueden tener costos inevitables

El proyecto debe reconocer que "software gratuito" no significa que toda la infraestructura sea gratuita.

Pueden existir costos por:

```text
Apple Developer
Google Play Console
SMS
telefonía
voz automatizada
hosting adicional
dominio
servicios cloud
```

Estos costos deberán ser considerados como **servicios operativos**, no como licencias de software.

---

# 57. Estrategia para minimizar costos

Primera opción:

```text
Infraestructura UNS
+
Software Open Source
+
FCM
+
APNs
+
correo institucional
```

Segunda capa:

```text
SMS
```

Tercera capa:

```text
voz
```

Los servicios de pago deberán utilizarse únicamente cuando aporten una capacidad que no pueda resolverse razonablemente con infraestructura gratuita/open source.

---

# 58. Integración SMN

El SMN deberá tratarse como una fuente de información.

Arquitectura:

```text
SMN
 ↓
INGESTA
 ↓
NORMALIZACIÓN
 ↓
VALIDACIÓN
 ↓
BORRADOR
 ↓
EVALUACIÓN HUMANA
 ↓
DECISIÓN UNS
 ↓
ALERTUNS
```

No deberá existir envío automático masivo en el MVP sin una decisión institucional explícita.

---

# 59. Snapshot de fuentes

Cada información externa deberá registrar:

* fuente;
* fecha/hora;
* HTTP status;
* contenido;
* SHA-256;
* versión;
* resultado de procesamiento.

Esto permitirá demostrar posteriormente qué información estaba disponible cuando se tomó una decisión.

---

# 60. Alertas meteorológicas

Los umbrales y catálogos deberán ser configurables.

No deberán quedar "hardcodeados".

Ejemplo:

```text
catalogo_alertas
catalogo_umbrales
catalogo_plantillas
catalogo_canales
catalogo_roles
catalogo_ventanas
```

Cada modificación deberá crear una nueva versión.

---

# 61. Plantillas M1–M8

Se implementarán:

```text
M1 Preventivo
M2 Suspensión
M3 Evacuación
M4 Confinamiento
M5 Custodia escolar
M6 Cese
M7 Rumor / rectificación
M8 Parte prolongado
```

Cada mensaje deberá disponer de:

```text
texto
audio
visual alto contraste
```

---

# 62. Accesibilidad

La interfaz deberá apuntar a:

```text
WCAG 2.2 AA
```

La alarma deberá priorizar:

* alto contraste;
* tipografía grande;
* lenguaje claro;
* pictogramas;
* vibración;
* sonido;
* lectura de pantalla cuando corresponda;
* botones grandes;
* mínimo número de acciones.

---

# 63. Modo ECD

AlertUNS deberá asistir al operador durante comunicaciones degradadas.

El sistema deberá registrar:

* intentos;
* resultados;
* porcentaje de fallos;
* tiempo;
* pilares afectados;
* declaración;
* recuperación.

AlertUNS no deberá declarar unilateralmente el ECD.

---

# 64. Modo contingencia

Si falla el sistema:

```text
AlertUNS
   ↓
NO DISPONIBLE
   ↓
procedimiento físico
   +
radio
   +
telefonía
   +
SMS
   +
otros canales
```

Deberá existir una hoja imprimible con:

* contactos;
* procedimientos;
* plantillas;
* canales;
* responsables.

---

# 65. Pruebas

## Pruebas unitarias

Backend:

```text
PHPUnit
```

Frontend:

```text
Vitest/Jest
```

---

# 66. Pruebas de API

Probar:

* autenticación;
* autorización;
* idempotencia;
* rate limiting;
* creación de alertas;
* aprobación;
* emisión;
* ACK;
* cese;
* auditoría.

---

# 67. Pruebas de seguridad

Realizar:

* SAST;
* análisis de dependencias;
* DAST;
* pruebas de autenticación;
* IDOR;
* XSS;
* CSRF;
* SSRF;
* replay;
* escalamiento de privilegios;
* exposición de secretos.

---

# 68. Pruebas de carga

Probar progresivamente:

```text
100 usuarios
500 usuarios
1.000 usuarios
5.000 usuarios
```

y ajustar al padrón real de la UNS.

---

# 69. Laboratorio móvil

Mínimo:

```text
15–20 dispositivos
```

incluyendo:

### Android

* Samsung;
* Motorola;
* Xiaomi/Redmi;
* Pixel;
* gama baja;
* diferentes versiones Android.

### iOS

* iPhone antiguo soportado;
* iPhone intermedio;
* iPhone actual.

---

# 70. Estados hostiles

Cada dispositivo deberá probarse en:

```text
pantalla bloqueada
silencio
No Molestar
Focus
batería baja
ahorro energético
Wi-Fi
4G
5G
sin conectividad
app cerrada
app en segundo plano
reinicio
```

---

# 71. Criterios de bloqueo de una versión

No se deberá liberar una versión si:

* falla la alarma crítica;
* falla el ACK;
* falla la auditoría;
* falla la aprobación;
* falla el escalamiento;
* falla el backup;
* falla la restauración;
* existen vulnerabilidades críticas abiertas;
* falla el canario;
* el simulacro integral falla.

---

# 72. Plan de trabajo

El proyecto se desarrollará en fases.

```text
FASE 0
Reducción de riesgo

FASE 1
Infraestructura

FASE 2
Backend

FASE 3
Aplicaciones

FASE 4
Consola

FASE 5
Integraciones

FASE 6
Pruebas

FASE 7
Piloto

FASE 8
Producción

FASE 9
Expansión
```

---

# 73. FASE 0 — Viabilidad

Duración estimada:

```text
2–3 semanas
```

Objetivos:

* auditar hosting;
* seleccionar tecnologías;
* definir arquitectura;
* crear repositorio;
* validar licencias;
* crear PoC;
* probar FCM;
* probar APNs;
* probar alarmas;
* iniciar solicitud de Critical Alerts;
* definir dispositivos;
* definir roles;
* definir amenazas.

## Resultado

```text
INFORME DE VIABILIDAD
+
ARQUITECTURA
+
POC
+
MATRIZ DE RIESGOS
```

---

# 74. FASE 1 — Infraestructura

Duración:

```text
2 semanas
```

Entregables:

* Linux;
* Nginx;
* PHP;
* Laravel;
* MySQL/MariaDB;
* Valkey;
* Git;
* CI/CD;
* DEV;
* STAGING;
* PROD;
* backups;
* monitoreo.

---

# 75. FASE 2 — Backend

Duración:

```text
4–6 semanas
```

Desarrollar:

* usuarios;
* roles;
* permisos;
* padrón;
* dispositivos;
* readiness;
* alertas;
* decisiones;
* broadcasts;
* deliveries;
* ACK;
* escalamiento;
* auditoría;
* simulacros.

---

# 76. FASE 3 — Aplicación Android

Duración:

```text
3–5 semanas
```

Desarrollar:

* login;
* registro;
* permisos;
* estado;
* alarma;
* sonido;
* vibración;
* ACK;
* historial;
* readiness;
* actualización remota de configuración.

---

# 77. FASE 4 — Aplicación iOS

Duración:

```text
3–5 semanas
```

Desarrollar:

* login;
* registro;
* APNs;
* Critical Alerts;
* Time Sensitive;
* pantalla de alarma;
* ACK;
* readiness;
* historial.

---

# 78. FASE 5 — Consola web

Duración:

```text
4–5 semanas
```

Desarrollar:

* dashboard;
* mapa lógico;
* alertas;
* Ficha;
* aprobación;
* emisión;
* entregas;
* ACK;
* escalamiento;
* usuarios;
* dispositivos;
* auditoría;
* reportes.

---

# 79. FASE 6 — Integraciones

Desarrollar:

```text
SMN
correo
FCM
APNs
SMS
voz
Telegram
```

No todos deben estar terminados para declarar operativo el MVP.

---

# 80. FASE 7 — Seguridad y pruebas

Duración:

```text
3–4 semanas
```

Realizar:

* pruebas unitarias;
* integración;
* carga;
* seguridad;
* laboratorio móvil;
* pruebas de recuperación;
* pruebas de caída;
* pruebas de canales.

---

# 81. FASE 8 — Piloto

Primero:

```text
30 personas
```

Luego:

```text
100 personas
```

Luego:

```text
200 personas
```

Finalmente:

```text
grupo institucional definido
```

---

# 82. FASE 9 — Simulacro integral

Participarán:

* Nodo Central;
* CDE;
* SHST;
* Telecomunicaciones;
* Infraestructura;
* DCI;
* autoridades;
* usuarios T0/T1;
* usuarios piloto.

Se medirán:

* tiempo de emisión;
* recepción;
* ACK;
* escalamiento;
* cese;
* recuperación;
* auditoría.

---

# 83. FASE 10 — Producción

Despliegue progresivo:

```text
T0
 ↓
T1
 ↓
T2
 ↓
T3
```

No se realizará una activación masiva sin comprobar primero la preparación.

---

# 84. Cronograma orientativo

| Fase               |    Duración |
| ------------------ | ----------: |
| F0 Viabilidad      | 2–3 semanas |
| F1 Infraestructura |   2 semanas |
| F2 Backend         | 4–6 semanas |
| F3 Android         | 3–5 semanas |
| F4 iOS             | 3–5 semanas |
| F5 Web             | 4–5 semanas |
| F6 Integraciones   | 2–4 semanas |
| F7 Seguridad/QA    | 3–4 semanas |
| F8 Piloto          | 3–4 semanas |
| F9 Simulacro       | 1–2 semanas |
| F10 Producción     | 2–3 semanas |

Las actividades pueden ejecutarse en paralelo.

---

# 85. MVP

El MVP deberá incluir:

```text
✓ Backend
✓ Base de datos
✓ autenticación
✓ MFA
✓ RBAC
✓ padrón
✓ dispositivos
✓ readiness
✓ alertas
✓ decisiones
✓ aprobación
✓ emisión
✓ Android
✓ iOS
✓ consola web
✓ FCM
✓ APNs
✓ ACK
✓ escalamiento
✓ SMS
✓ auditoría
✓ canario
✓ simulacro
✓ informes básicos
```

---

# 86. Funciones posteriores al MVP

Se incorporarán progresivamente:

```text
custodia escolar
checklists
modo offline
mapas
predios
puntos de encuentro
megafonía
pantallas
Moodle
mensajería
portugués
inglés
RACUNS
sensores
otras integraciones
```

---

# 87. Lo que NO debe entrar en el MVP

No incorporar inicialmente:

* IA para tomar decisiones;
* reconocimiento automático de situaciones;
* localización permanente;
* funcionalidades sociales;
* módulos innecesarios;
* analítica compleja;
* automatizaciones que puedan producir falsas alarmas.

El núcleo debe ser pequeño y extremadamente confiable.

---

# 88. Organización del equipo

Equipo ideal:

| Rol                   |            Dedicación |
| --------------------- | --------------------: |
| Líder técnico/backend |                     1 |
| Android/iOS           |                     1 |
| Full Stack            |                     1 |
| Web                   |                     1 |
| DevOps/SRE            |                   0,5 |
| QA                    |                   0,5 |
| UX/accesibilidad      |                   0,3 |
| Seguridad             |               puntual |
| Legal                 |               puntual |
| SHST                  | responsable funcional |
| Telecomunicaciones    |   responsable técnico |

---

# 89. Desarrollo asistido por IA

La IA podrá utilizarse para acelerar:

* generación de código;
* tests;
* documentación;
* análisis;
* refactorizaciones controladas;
* consultas SQL;
* generación de migraciones;
* documentación API;
* análisis de logs;
* generación de casos de prueba.

Pero deberá existir una regla:

> Ningún código generado por IA entra en producción sin revisión humana y pruebas automatizadas.

---

# 90. Repositorio documental

Debe existir:

```text
docs/
├── architecture.md
├── threat-model.md
├── api.md
├── database.md
├── deployment.md
├── backup.md
├── disaster-recovery.md
├── mobile-testing.md
├── security.md
├── runbook.md
├── incident-response.md
├── protocol.md
└── changelog.md
```

---

# 91. ADR

Cada decisión tecnológica importante deberá documentarse:

```text
ADR-001 Backend
ADR-002 Database
ADR-003 Queue
ADR-004 Mobile framework
ADR-005 Push architecture
ADR-006 Authentication
ADR-007 Storage
ADR-008 Monitoring
ADR-009 Disaster Recovery
ADR-010 SMS/Voice
```

---

# 92. Criterios de éxito

AlertUNS no será considerado exitoso por la cantidad de funcionalidades.

Será exitoso si puede demostrar:

```text
RELIABILIDAD
+
SEGURIDAD
+
TRAZABILIDAD
+
REDUNDANCIA
+
OPERABILIDAD
+
MANTENIBILIDAD
```

---

# 93. Primera compuerta G0

Antes de desarrollar el MVP deberá cumplirse:

```text
[ ] Hosting validado
[ ] Arquitectura validada
[ ] Licencias revisadas
[ ] Repositorio institucional
[ ] Android PoC
[ ] iOS PoC
[ ] FCM probado
[ ] APNs probado
[ ] Alarma con app cerrada probada
[ ] Pantalla bloqueada probada
[ ] Silencio probado
[ ] No Molestar probado
[ ] Matriz de dispositivos definida
[ ] Modelo de amenazas aprobado
[ ] Roles definidos
[ ] Cuentas institucionales creadas
```

---

# 94. Segunda compuerta G1

Debe existir:

```text
alerta
 ↓
aprobación
 ↓
emisión
 ↓
recepción
 ↓
ACK
 ↓
escalamiento
 ↓
cese
 ↓
auditoría
```

funcionando de punta a punta.

---

# 95. Tercera compuerta G2

Debe realizarse:

```text
simulacro de mesa
+
piloto 100–200 usuarios
+
SMN asistido
+
tres canales
+
ACK
+
auditoría
```

---

# 96. Cuarta compuerta G3

Debe existir:

```text
simulacro integral exitoso
+
seguridad validada
+
backup restaurado
+
canario estable
+
piloto satisfactorio
+
procedimientos documentados
```

---

# 97. Quinta compuerta G4

Finalmente:

```text
T0
 ↓
T1
 ↓
T2
 ↓
T3
```

y AlertUNS queda operativo como plataforma institucional.

---

# 98. Riesgos principales

| Riesgo                               | Mitigación                                             |
| ------------------------------------ | ------------------------------------------------------ |
| Apple no habilita Critical Alerts    | Time Sensitive + SMS + voz + procedimiento alternativo |
| Android limita Full Screen Intent    | permisos + canales críticos + SMS/voz                  |
| fabricantes restringen segundo plano | laboratorio por marca                                  |
| caída FCM                            | APNs/SMS/otros canales                                 |
| caída APNs                           | FCM/otros canales                                      |
| caída de Internet                    | canales alternativos                                   |
| caída del servidor                   | DR                                                     |
| falsa alarma                         | doble aprobación                                       |
| filtración de datos                  | minimización + cifrado + RBAC                          |
| hosting insuficiente                 | auditoría temprana                                     |
| dependencia de proveedor             | arquitectura desacoplada                               |
| fatiga de alarmas                    | T0/T1/T2/T3                                            |
| error humano                         | Ficha + validaciones                                   |
| pérdida de información               | backups + auditoría                                    |

---

# 99. Decisiones iniciales

Las siguientes decisiones deberán cerrarse antes del desarrollo definitivo:

```text
D-01
Responsable funcional

D-02
Responsable técnico

D-03
Infraestructura

D-04
Identidad institucional

D-05
Matriz T0/T1/T2/T3

D-06
Política de aprobación

D-07
Política ACP

D-08
Framework móvil

D-09
Motor de base de datos

D-10
Proveedor SMS

D-11
Proveedor de voz

D-12
Retención de datos

D-13
Política de backup

D-14
RTO/RPO

D-15
Política de publicación móvil
```

---

# 100. Semana 1 — Trabajo concreto

La primera semana deberá producir resultados reales.

## Día 1–2

```text
[ ] Crear repositorio institucional
[ ] Definir responsables
[ ] Auditar servidor
[ ] Auditar hosting
[ ] Inventariar dominios
[ ] Inventariar certificados
[ ] Inventariar base de datos
```

## Día 3–4

```text
[ ] Crear Laravel
[ ] Crear API
[ ] Crear MySQL
[ ] Crear Valkey
[ ] Crear Android PoC
[ ] Crear iOS PoC
```

## Día 5

```text
[ ] FCM funcionando
[ ] APNs funcionando
[ ] alarma Android
[ ] alarma iOS
[ ] ACK
[ ] medición de tiempos
```

---

# 101. Resultado esperado de la primera semana

Al finalizar la primera semana deberá existir algo extremadamente pequeño pero real:

```text
┌──────────────────┐
│    AlertUNS      │
│                  │
│  PRUEBA ALARMA   │
└────────┬─────────┘
         │
         ▼
      SERVIDOR
         │
      ┌──┴──┐
      ▼     ▼
    FCM    APNs
      │     │
      ▼     ▼
 Android   iPhone
      │     │
      └──┬──┘
         ▼
        ACK
         │
         ▼
       API
```

Si esta prueba no funciona correctamente, **no se debe continuar agregando funcionalidades**.

---

# 102. Principio final

AlertUNS deberá construirse bajo la siguiente prioridad:

```text
1. SEGURIDAD
2. CONFIABILIDAD
3. ALARMA
4. ENTREGA
5. CONFIRMACIÓN
6. ESCALAMIENTO
7. AUDITORÍA
8. RECUPERACIÓN
9. USABILIDAD
10. FUNCIONALIDADES ADICIONALES
```

Nunca al revés.

---

# 103. Resultado final esperado

La UNS deberá disponer de una plataforma propia capaz de:

```text
                 ┌──────────────────────┐
                 │    DECISIÓN UNS      │
                 └──────────┬───────────┘
                            │
                            ▼
                     ┌─────────────┐
                     │  ALERTUNS   │
                     └──────┬──────┘
                            │
           ┌────────────────┼─────────────────┐
           │                │                 │
           ▼                ▼                 ▼
        ANDROID            iOS              WEB
           │                │                 │
           └────────────────┼─────────────────┘
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
              PUSH              CANALES ALTERNATIVOS
                 │                     │
                 │               SMS / VOZ / MAIL
                 │                     │
                 └──────────┬──────────┘
                            ▼
                       CONFIRMACIÓN
                            │
                            ▼
                       ESCALAMIENTO
                            │
                            ▼
                          CESE
                            │
                            ▼
                         AUDITORÍA
                            │
                            ▼
                         INFORME
```

El objetivo no es desarrollar una aplicación móvil aislada, sino construir una **infraestructura institucional de comunicaciones de emergencia**, propiedad de la Universidad Nacional del Sur, basada en software libre/open source, estándares abiertos, infraestructura controlada por la institución y mecanismos redundantes de comunicación.

---

# 104. Condición de licenciamiento del proyecto

Antes de incorporar cualquier dependencia deberá ejecutarse:

```text
DEPENDENCIA
     ↓
¿Licencia identificada?
     ↓
¿Permite uso institucional?
     ↓
¿Costo de licencia = $0?
     ↓
¿Permite redistribución/modificación cuando corresponda?
     ↓
¿Tiene mantenimiento activo?
     ↓
¿Existe alternativa open source?
     ↓
APROBACIÓN
```

Cada dependencia deberá quedar registrada en:

```text
docs/software-bill-of-materials.md
```

con:

* nombre;
* versión;
* licencia;
* URL oficial;
* función;
* dependencia;
* riesgo;
* alternativa disponible.

---

# 105. Software Bill of Materials

El proyecto deberá mantener un SBOM.

Ejemplo:

```text
Laravel
PHP
React
React Native
TypeScript
Kotlin
Swift
MySQL/MariaDB
Valkey
Nginx
Prometheus
Grafana
GlitchTip
Playwright
PHPUnit
Docker/Podman
GitLab CE/Gitea
```

El SBOM deberá actualizarse automáticamente en CI/CD cuando sea posible.

---

# 106. Regla de oro de costos

El proyecto deberá intentar que:

```text
CÓDIGO
+
BACKEND
+
BASE DE DATOS
+
WEB
+
MONITOREO
+
CI/CD
+
TESTING
+
DOCUMENTACIÓN
+
SERVIDORES
```

puedan funcionar sin pagar licencias de software.

Los costos inevitables deberán limitarse a:

```text
PUBLICACIÓN MÓVIL
+
SMS
+
VOZ
+
INFRAESTRUCTURA ADICIONAL
```

y deberán ser explícitamente aprobados por la UNS.

---

# 107. Conclusión operativa

El proyecto deberá comenzar por la **Fase 0 y no por el desarrollo completo**.

El primer objetivo no será tener una aplicación bonita.

El primer objetivo será demostrar:

```text
UNS
 ↓
AlertUNS
 ↓
Android/iPhone
 ↓
ALARMA
 ↓
USUARIO
 ↓
ACK
 ↓
AlertUNS
```

de forma repetible, medible y auditable.

Una vez validado ese circuito, se construirá progresivamente el resto de la plataforma.

**La primera entrega del proyecto deberá ser, por lo tanto, un PoC funcional de alarma crítica + arquitectura técnica + auditoría de infraestructura + matriz de licencias gratuitas + modelo de seguridad.**

Ese resultado constituirá la **Compuerta G0** para autorizar el desarrollo del MVP completo.
