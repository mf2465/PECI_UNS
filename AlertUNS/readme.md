# AlertUNS — Plan de Desarrollo

**Sistema institucional de alerta y confirmación para la activación del PECI-UNS**
Android · iPhone · Web

| | |
|---|---|
| **Versión** | 1.0 (borrador para revisión) |
| **Fecha** | 30/09/2026 |
| **Equipo** | Ingeniería full stack, producción/SRE, seguridad, DevOps, líder técnico |
| **Insumos** | Anexos 07-A, 07-B, 07-C, AT-01, AT-02 del PECI-UNS; funciones públicas de BomberBOT (referencia); Plan ver1 (insumo de requisitos) |
| **Revisan** | SHST, Telecomunicaciones, DCI, CDE, Asesoría Legal |

---

## 1. Visión y objetivos

### 1.1 Qué es AlertUNS

AlertUNS es el **«sistema propio» de notificación masiva** previsto en el Documento B §7.6 : padrón multi-público propio, emisión multicanal (push, SMS, correo, voz), registro de entregas y confirmaciones, propiedad local de datos e interfaces documentadas. Complementa y, tras la validación, reemplaza gradualmente a Alerthor como medio primario de aviso interno, sin eliminar los medios de respaldo (SMS, telefonía, radio, presencial).

### 1.2 Problema que resuelve

Cuando el Nodo Central / Oficina de Recepción de Avisos activa el protocolo, hoy el aviso depende de un servicio de terceros con «riesgo de cautividad» [Doc B §7.2], de grupos de mensajería «informales, sin garantía de entrega» y de que cada persona mire el teléfono. AlertUNS asegura que **la decisión del Rector llegue a las personas correctas, con alarma audible aun con el teléfono en silencio, y que quede constancia de quién recibió y confirmó**.

### 1.3 Objetivos medibles

| # | Objetivo | Métrica |
|---|---|---|
| O1 | Alarma audible con app cerrada y teléfono en silencio | ≥ 98 % de dispositivos T0/T1 en estado «listo para alarma crítica» |
| O2 | Velocidad de despacho | Decisión aprobada → entregada a APNs/FCM (T0+T1) ≤ 30 s |
| O3 | Confirmación | ≥ 95 % de T0 confirma en 5 min |
| O4 | Trazabilidad | 100 % de emisiones con registro de decisión, entregas y confirmaciones |
| O5 | Independencia | Sin dependencia de un único proveedor, canal o sitio |
| O6 | Cumplimiento del protocolo | 100 % de alertas con Ficha del Alerta completa antes de emitir (Doc A §6.3) |
| O7 | Cero falsas alarmas masivas | 0 emisiones no aprobadas por la cadena de decisión |

### 1.4 No-objetivos

- No reemplaza a RACUNS ni a la radio: el software **no escucha CH1** ni opera la red de radio; solo registra lo que declara el operador.
- No es una app de gestión de cuartel de bomberos.
- No localiza personas de forma continua.
- No decide por sí mismo: ejecuta y registra decisiones humanas.

---

## 2. Referencia: lo que se toma y lo que no de la app BomberBOT

Análisis de «caja negra» sobre lo que el sitio declara. No se descompila, copia código, sonidos, textos ni marca; el desarrollo es independiente, a partir del protocolo UNS.

| Capacidad declarada por BomberBOT | Decisión para AlertUNS |
|---|---|
| Alarma que suena, vibra y habla con la app cerrada | **Núcleo.** Se implementa con canal de alarma nativo (Android) y Critical Alerts (iOS) |
| Convocatoria total / selectiva / por departamento | **Núcleo.** Audiencias por predio, rol, turno y escuela |
| Sonido por tipo de emergencia | **Núcleo.** Sonido por nivel SMN y tipo de mensaje |
| Respuesta con un toque | **Núcleo,** con respuestas propias (§5.5) |
| Aviso de emergencia cancelada | **Núcleo** (M6 Cese y rectificación) |
| Tablero en vivo de quién responde | **Núcleo** |
| Panel web, monitoreo online/último ping/versión | **Núcleo,** como «estado de preparación» del dispositivo |
| Simulador de alertas | **Núcleo** como modo simulacro |
| Mensajería interna urgente/normal | Fase 2 (contenido bloqueado en cascada, Doc C) |
| Chequeos digitales offline (unidad → contenedor → ítem) | Fase 5 (checklists AT-01/AT-02) |
| PPO (mapa de riesgo de la zona) | Fase 5 (vulnerabilidades por predio, AT-01 §3.1) |
| IA para chequeos y calendarios | No recomendado: riesgo sin beneficio para el núcleo |
| Tareas con rotación, guardias, encuestas, suscripción | No aplica |
| Código de invitación de 6 dígitos | Se reemplaza por inicio de sesión institucional + padrón |

---

## 3. Alcance por fases

### 3.1 MVP (producción)

Padrón y SSO · roles con ámbito y suplencia · registro de dispositivos y estado de preparación · alarma crítica en Android e iOS · envío segmentado con recibos · confirmaciones · escalamiento por SMS y voz · consola del Nodo Central (Ficha del Alerta, matriz de decisión, aprobación, envío, tablero, cese) · ingestión asistida del SMN · plantillas M1–M8 y formatos accesibles · registro de difusión por capa · auditoría encadenada · modo simulacro · canario · informe post-activación (borrador).

### 3.2 Post-MVP

Custodia y retiro escolar (Doc A Anexo C) · checklists e indicadores AT-01/AT-02 · modo offline completo · megafonía y pantallas de predios · integración con Moodle · EN/PT · mapas de predios y zonas de confinamiento.

---

## 4. Actores y audiencias

### 4.1 Actores del protocolo

Rector (decide) · CDE (recomienda) · Nodo Central / Oficina de Recepción de Avisos (opera 24/7) · SHST · Vocería / DCI (emite comunicación pública) · Telecomunicaciones · Infraestructura · mayordomos · decanos y directores de departamento · directores administrativos · directores de escuelas · docentes y nodocentes · estudiantes · familias (escuelas) · brigadas.

### 4.2 Niveles de audiencia 

| Nivel | Quiénes | Entrega | Confirmación |
|---|---|---|---|
| **T0 Mando** | CDE y suplentes, Rector, operadores del Nodo Central, Vocería | Alarma crítica + SMS + voz | Obligatoria; si no confirma en 15 min, pasa al suplente (Doc B, flujo F1 ) |
| **T1 Coordinación** | Mayordomos, decanos/directores, directores de escuelas, Telecomunicaciones, Infraestructura, brigadas | Alarma crítica + SMS | Obligatoria; reporte de estado cada 30 min en Naranja/Rojo (Doc B, F5 )|
| **T2 Comunidad laboral** | Docentes, nodocentes, investigadores | Notificación prioritaria + correo | «Recibido» |
| **T3 Comunidad general** | Estudiantes, familias, visitantes | Push estándar + canales abiertos (web, Moodle, redes, Telegram) | Opcional |

**Criterio de diseño:** la alarma «estruendosa» se reserva a T0/T1 y a niveles Naranja/Rojo/ACP. Ampliarla a toda la comunidad genera fatiga y puede perjudicar la aprobación de Apple (§7.2).

---

## 5. Procesos y reglas de negocio

### 5.1 Cadena de decisión 

Nodo Central lee la línea de tiempo y completa la Ficha → CDE recomienda → **Rector decide** → difusión multicanal → ejecución → cese → informe en ≤72 h (Doc A, Anexo A). La difusión es **simultánea por al menos tres canales independientes** (Doc A §10). Solo emiten mensajes oficiales el Nodo Central y la Vocería (Doc B §7.4 y Doc C §2).

### 5.2 Máquina de estados de una alerta

```text
SMN / manual 
      │
      ▼
 DETECTED  → alarma al Nodo Central; se crea borrador de Ficha
      ▼
 ASSESSED     el operador abre detalle zonal y línea de tiempo y completa la Ficha
      ▼        (bloqueo si faltan campos obligatorios; Doc A §6.3)
 RECOMMENDED  CDE / SHST recomiendan; el sistema sugiere la acción de la matriz (Doc A §7.8)
      ▼
 APPROVED     Rector, delegado o suplente decide; queda registro (Doc B, flujo F3)
      ▼
 DISPATCHING → ACTIVE → UPDATED* → CEASED (M6) → CLOSED (informe ≤72 h)
      │
      └─ rectificación / falsa alarma (M7 + corrección en un clic)
```

### 5.3 Vía rápida para ACP (vigencia 1–3 h)

| Modo | Descripción | Riesgo |
|---|---|---|
| **A. Asistido (propuesto)** | Alarma al Nodo Central; un toque del operador confirma y envía M4 precompuesto | Segundos de latencia humana |
| **B. Automático por resolución** | Con autorización escrita del Rectorado, el ACP sobre Bahía Blanca dispara M4 | Falsa alarma por error de lectura; exige umbral de confianza y *kill-switch* |
| **C. Solo manual** | El operador redacta y envía | Lento |

Se decide en **D-04**. Hasta entonces rige el modo A.

### 5.4 Reglas del protocolo que el motor implementa

1. **Ventanas de decisión:** Turno Mañana 22:00 del día anterior · Tarde 10:00 · Noche 16:00 (Doc A §6.1).
2. **Regla de oro:** vencida la hora de corte con el fenómeno en desarrollo, la decisión cambia de «suspensión» a «confinamiento en sede».
3. **ACP:** cese inmediato y confinamiento; no se evacúa salvo riesgo inminente de colapso estructural (Doc A §7.5).
4. **Simultaneidad:** una zona puede tener varios alertas, advertencias y ACP a la vez; el sistema los lista todos y no decide por el color del mapa (Doc A §4.3).
5. **Temperaturas extremas:** sin línea de tiempo; evaluación antes de la hora de corte del Turno Mañana (Doc A §7.6).
6. **Matriz por nivel** (Verde, Amarillo, Naranja antes/después del corte, Rojo, violeta, temperaturas) con mensaje sugerido (Doc A §7.8; Doc C Anexo C).
7. **Umbrales regionales (Patagonia)** cargados como catálogo versionado (Doc A §5): lluvia 15/30/60 mm en 12 h (amarillo/naranja/rojo), viento sostenido 55/75/90 km/h, ráfagas 65/90/110 km/h.
8. **Rutina del operador:** tareas con check y observación a las 06:00, 10:00, 16:00, 18:00, 19:00, 22:00 y extraordinarias (Doc A §6.2).
9. **Los catálogos son datos versionados** (ventanas, umbrales, plantillas, roles), porque el protocolo se gestiona con control de versiones y PDCA (Doc A §12).

### 5.5 Respuestas de las personas

| Código | Texto | Quién | Uso |
|---|---|---|---|
| `RECEIVED` | «Recibido y comprendido» | Todos | Confirmación (obligatoria en T0/T1) |
| `SAFE` | «Estoy a salvo» | Todos, opcional | Estado del personal |
| `SHELTERED` | «Confinamiento cumplido en [predio]» | Mayordomías, escuelas, docentes a cargo | Reporte operativo (Doc A §7.7) |
| `NEED_HELP` | «Necesito asistencia» | Todos | Escala al Nodo Central; ubicación solo si la persona la adjunta |
| `UNAVAILABLE_ROLE` | «No puedo cumplir mi rol» | T0/T1 | Activa al suplente |

Se responde desde la notificación y desde la pantalla de alarma. Se valida en la PoC qué acciones permite cada sistema operativo desde el bloqueo.

### 5.6 Escalamiento por defecto

| Tiempo | T0 / T1 | T2 / T3 |
|---|---|---|
| T+0 | Push crítico (camino primario) | Push prioritario |
| T+60 s | Sin recibo de entrega: reenvío por camino secundario | — |
| T+2 min | SMS a quienes no confirmaron | — |
| T+5 min | Llamada de voz automática a T0/T1 sin confirmar | SMS/correo si no hubo recibo |
| T+15 min | Aviso al suplente y al Nodo Central | — |
| T+30 min (Naranja/Rojo) | Pedido de reporte de estado a mayordomías | — |

SMS y voz dependen de la red celular; en ECD (Pilar 2 caído) no están disponibles y el sistema lo indica.

### 5.7 Apoyo al Estado de Comunicaciones Degradadas (ECD)

La declaración del ECD es una **facultad del Operador de Guardia** (Regla de los 2 de 3 Pilares durante 15 min, triangulación con 70 % de intentos fallidos, restitución tras 30 min estables; Doc B §7.5). AlertUNS **asiste, no declara**:

- panel de triangulación con cronómetro y cálculo del porcentaje, donde el operador registra cada intento (ping interno a bases, ping externo a SMN y Defensa Civil, llamada de control);
- sondas automáticas de FCM, APNs, proveedor SMS y conectividad al SMN, como evidencia;
- asiento automático en el libro de guardia digital (exportable a PDF para el libro físico);
- al declararse, **modo mínimo**: oculta canales dependientes de internet/SMS y muestra el texto estandarizado para CH1 y la lista de bases a confirmar;
- cálculo automático del indicador «100 % de declaraciones ECD con triangulación documentada» (AT-02 §9).

---

## 6. Arquitectura

### 6.1 Vista general

```text
 CLIENTES                         NÚCLEO (activo en Alem, espejo en Palihue)                PROVEEDORES DE CANAL
┌───────────────┐            ┌────────────────────────────────────────────┐           ┌───────────────────┐
│ App Android   │──HTTPS───► │ API (Laravel) · RBAC · SSO · MFA           │           │ APNs (iOS directo)│
│ App iOS       │──HTTPS───► │ Motor de estados de alerta                 │ ────────► │ FCM (Android/iOS) │
│ Consola web   │──HTTPS+WS─►│ Dispatcher (colas Redis, workers/canal)    │           │ Gateway SMS       │
└───────────────┘            │ Escalador (timers) · Auditoría (hash)      │           │ Voz automatizada  │
                             │ MySQL 8 + réplica · Redis · Objetos        │           │ Correo · Telegram │
                             │ Ingestor SMN (60 s ACP / 5 min resto)      │           └───────────────────┘
                             └──────────────┬─────────────────────────────┘
                                            │ réplica + enlace de contingencia (Starlink S1, Doc B §8.9)
                                            ▼
                    ESPEJO EN PALIHUE  +  DESPACHADOR MÍNIMO FUERA DE BAHÍA BLANCA 
        Canario: 2 Android + 2 iPhone fijos que confirman solos · Vigilancia externa por canal independiente
```

### 6.2 Pila tecnológica

| Capa | Elección | Motivo |
|---|---|---|
| Móvil | React Native (*development build*) para la interfaz + **módulos nativos propios en Kotlin y Swift** para la capa de alarma | La alarma exige servicio en primer plano, canales y extensiones de notificación que no se resuelven con librerías genéricas. Se confirma al cerrar la PoC (D-06) |
| Backend | Laravel (versión LTS vigente) + MySQL 8 + Redis | Aprovecha el hosting y las bases ya disponibles |
| Tiempo real | WebSockets (Reverb) con respaldo por sondeo | La consola debe funcionar si falla el WebSocket |
| Push Android | FCM, mensajes de datos de prioridad alta | Estándar de Android |
| Push iOS | **APNs directo** (primario) + FCM (secundario) | Control del payload y de la prioridad; independencia ante una caída de FCM |
| Consola | SPA (React o Vue) servida por el backend | — |
| SMS / voz | Proveedor(es) con API y cobertura Argentina; contrato a cargo de Telecomunicaciones [Doc B §7.2] | Escalamiento y ECD parcial; idealmente dos proveedores para T0 |
| Objetos | Almacenamiento propio compatible con S3 (p. ej. MinIO) | Datos personales en jurisdicción propia [?] |
| Observabilidad | Prometheus + Grafana + logs estructurados + Sentry o GlitchTip | — |
| Identidad | OIDC/SAML contra el proveedor institucional [?] | Reemplaza códigos de invitación |

### 6.3 Estructura del repositorio (monorepo)

```text
alertuns/
├─ api/                 # Laravel: dominio, workers, ingestor SMN
│  ├─ app/Domain/       # Alert, Decision, Broadcast, Delivery, Ack, Audit, Roster
│  ├─ app/Channels/     # ApnsChannel, FcmChannel, SmsChannel, VoiceChannel, MailChannel, TelegramChannel
│  ├─ app/Rules/        # ventanas horarias, regla de oro, matriz de decisión, umbrales
│  └─ database/         # migraciones y seeds de catálogos (roles, M1–M8, umbrales)
├─ mobile/
│  ├─ app/              # React Native (UI, navegación, estado)
│  ├─ android/          # módulo nativo de alarma (Kotlin)
│  └─ ios/              # módulo nativo + extensión de servicio de notificación (Swift)
├─ web/                 # consola del Nodo Central
├─ infra/               # IaC, contenedores, runbooks, monitoreo
└─ docs/                # ADRs, modelo de amenazas, manuales, OpenAPI
```

### 6.4 Alta disponibilidad y recuperación

- **Primario** en el Centro de Datos de Alem (grupo electrógeno exclusivo con ATS y UPS [Doc B §6]); **espejo** en Palihue (réplica diaria de servicios críticos prevista [Doc B §8.8]); **despachador mínimo fuera de Bahía Blanca** capaz de enviar la última decisión aprobada si ambos sitios caen.
- Replicación asíncrona de la base; copias diarias cifradas con retención de 30 días y **restauración probada cada mes**.
- Objetivos propuestos: RTO ≤ 15 min y RPO ≤ 5 min para el camino de alerta. El Doc B asigna a Telecomunicaciones definir RTO/RPO dentro de 60 días hábiles; estos valores son una entrada.
- **Hoja de contingencia imprimible** en el Nodo Central, con M1–M8 y contactos actualizados, para el caso de caída total (coherente con el libro de guardia físico).

### 6.5 Objetivos de servicio (SLO) 

| Métrica | Objetivo |
|---|---|
| Disponibilidad del camino de alerta | 99,9 % mensual |
| Aprobado → entregado a APNs/FCM (T0+T1) | ≤ 30 s |
| Entrega al dispositivo (p95, conectividad normal) | ≤ 30 s, **medida** (no la garantiza el sistema) |
| Confirmación T0 en 5 min | ≥ 95 % |
| Preparación para alarma crítica | T0/T1 ≥ 98 %; T2 ≥ 85 % |
| Falsos positivos de ingestión que lleguen a la comunidad | 0 |
| Éxito del canario | ≥ 99,5 % semanal |

---

## 7. Notificación crítica: diseño por plataforma

### 7.1 Android

- **Mensajes solo de datos**, prioridad alta y TTL corto (p. ej. 300 s); un servicio de mensajería los procesa aunque la app esté cerrada.
- **Canal dedicado `uns_critical`**, importancia alta, atributos de audio de tipo alarma. En el alta se pide el permiso de acceso a *No Molestar*, que el usuario debe otorgar.
- **Servicio en primer plano** que reproduce la alarma por el flujo de alarma, con repetición cada 30 s hasta confirmar o 5 min y patrón de vibración propio. Se declara el tipo de servicio en Play Console para destinos Android 14+.
- **Pantalla completa sobre el bloqueo:** desde Android 14, el permiso `USE_FULL_SCREEN_INTENT` se concede por defecto solo a apps de llamadas o alarmas; el resto requiere permiso del usuario y declaración en Play Console. Se declara la función de alarma y, si no se acepta, se guía al usuario a habilitarlo (se verifica con `canUseFullScreenIntent()`).
- **Optimización de batería y fabricantes:** guías por marca (Samsung, Xiaomi, Motorola, Oppo/Realme, Pixel) y estado de preparación visible.
- Equipos sin servicios de Google no reciben FCM: quedan fuera del MVP y se cubren con SMS/voz.
- `minSdk` propuesto: Android 8 (canales de notificación); se ajusta con datos reales de los equipos del padrón.

### 7.2 iOS

- **Critical Alerts** requiere el entitlement `com.apple.developer.usernotifications.critical-alerts`, que se **solicita a Apple por formulario**; permite sonido aun con el equipo bloqueado, en silencio o con No Molestar/Focus, con sonido y volumen propios. El usuario además debe aceptarlo por separado.
- **Sin plazo ni garantía:** hay casos de desarrolladores sin respuesta durante semanas. Se solicita en la **semana 1**, con justificación de seguridad pública (alertas meteorológicas severas institucionales, confinamiento, suspensión de actividades).
- **Plan B sin aprobación:** *Time Sensitive* (atraviesa Focus pero no el interruptor de silencio) más escalamiento por SMS y voz, y guía al usuario.
- **Sonido:** archivo empaquetado en la app, de duración limitada; no hay voz dinámica con la app cerrada. Se incluyen audios pregrabados por nivel y por tipo de mensaje; el TTS dinámico solo con la app abierta.
- **Extensión de servicio de notificación** para enriquecer el contenido (pictograma, texto accesible) y registrar el recibo.
- **No se usa PushKit/VoIP** (reservado a llamadas reales).
- Evaluar distribución «no listada» para una app institucional; preparar cuenta de demostración para la revisión de Apple.

### 7.3 Web (consola y PWA)

- Consola con alarma sonora (Web Audio), notificación persistente y bloqueo de pantalla apagada (Wake Lock) mientras haya alerta activa.
- Web Push para escritorio como canal adicional; en iPhone solo con la PWA instalada; **no es canal crítico en iOS**.

### 7.4 Cargas útiles de referencia

**Android (FCM v1, solo datos):**

```json
{
  "message": {
    "token": "<device_token>",
    "android": { "priority": "HIGH", "ttl": "300s" },
    "data": { "type": "alert", "alert_id": "UNS-2027-0001", "level": "orange", "template": "M2", "requires_ack": "1" }
  }
}
```

**iOS (APNs; cabeceras `apns-priority: 10`, `apns-push-type: alert`, `apns-expiration`, `apns-collapse-id`):**

```json
{
  "aps": {
    "alert": { "title": "UNS · ALERTA NARANJA", "body": "Suspendidas actividades presenciales en la sede indicada." },
    "sound": { "critical": 1, "name": "uns_orange.caf", "volume": 1.0 },
    "interruption-level": "critical",
    "mutable-content": 1,
    "category": "UNS_ALERT_ACK",
    "thread-id": "UNS-2027-0001"
  },
  "alert_id": "UNS-2027-0001"
}
```

### 7.5 Preparación del dispositivo (*readiness*)

Cada dispositivo informa al iniciar la app y periódicamente: versión de app y sistema, permisos (notificaciones, críticas, No Molestar, pantalla completa, exclusión de batería), fabricante y último contacto. La consola calcula el porcentaje de personal «listo» por predio y rol, y la app muestra al usuario una lista de pasos pendientes. **No se registra ubicación.**

---

## 8. Ingesta de alertas del SMN

- **Estado:** no se confirmó un API o feed oficial documentado (p. ej. CAP) para los alertas del SAT. El Doc B ya prevé fuentes redundantes: web oficial, app oficial del SMN con notificación por zona y correo [§6].
- **Plan:**
  1. **Gestión formal** ante el SMN para un canal estructurado (idealmente CAP, estándar de OASIS). Largo plazo; empezar ya.
  2. **Ingesta técnica interina** sobre los endpoints públicos del SAT, **solo como asistencia**: genera borrador de Ficha y alarma al Nodo Central; no envía a la comunidad por sí sola (salvo modo B de D-04).
  3. Cada captura se guarda **cruda con hash** para auditoría.
  4. **Frecuencia:** 60 s para ACP; 5 min para el resto.
  5. ***Dead-man switch:*** si la fuente no responde o devuelve datos inválidos por más de 10 min, alarma «fuente SMN sin datos» y consulta manual (el protocolo ya la prevé).
  6. Pruebas de contrato con muestras reales: si el formato cambia, el parser **falla visiblemente**.
  7. Revisión de términos de uso del SMN.
- **Modelo interno** compatible con CAP (evento, severidad, urgencia, certeza, área, vigencia) para interoperar con Defensa Civil y la plataforma municipal «Alerta Bahía».

---

## 9. Modelo de datos (MySQL 8)

**Principios:** sin `ENUM` para dominios que cambian; un usuario con varias asignaciones de rol y varios dispositivos; separar *decisión*, *emisión*, *entrega* y *confirmación*; datos sensibles cifrados a nivel de aplicación; auditoría encadenada por hash.

```sql
CREATE TABLE person (
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  public_id CHAR(26) NOT NULL UNIQUE,                 -- ULID para la API
  institutional_email VARCHAR(190) NOT NULL UNIQUE,
  full_name VARCHAR(190) NOT NULL,
  phone_e164 VARCHAR(20) NULL,                        -- SMS y voz
  national_id_enc VARBINARY(256) NULL,                -- DNI cifrado; solo donde el protocolo lo exige
  status VARCHAR(16) NOT NULL DEFAULT 'active',
  consent_version VARCHAR(16) NULL,
  consent_at DATETIME(3) NULL,
  created_at DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  CONSTRAINT chk_person_status CHECK (status IN ('active','suspended','left'))
);

CREATE TABLE role_assignment (                        -- roles con ámbito y suplencia
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  person_id BIGINT UNSIGNED NOT NULL,
  role_code VARCHAR(40) NOT NULL,
  tier TINYINT NOT NULL,                              -- 0..3
  scope_type VARCHAR(20) NULL, scope_id BIGINT UNSIGNED NULL,
  deputy_of_id BIGINT UNSIGNED NULL,
  valid_from DATE NOT NULL, valid_to DATE NULL,
  FOREIGN KEY (person_id) REFERENCES person(id),
  FOREIGN KEY (deputy_of_id) REFERENCES role_assignment(id),
  KEY idx_role_scope (role_code, scope_type, scope_id)
);

CREATE TABLE device (
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  person_id BIGINT UNSIGNED NOT NULL,
  platform VARCHAR(10) NOT NULL,                      -- android | ios | web
  push_token_hash CHAR(64) NOT NULL,
  push_token_enc VARBINARY(1024) NOT NULL,
  app_version VARCHAR(20), os_version VARCHAR(20), oem VARCHAR(40),
  readiness JSON NULL, critical_ready BOOLEAN NOT NULL DEFAULT FALSE,
  last_seen_at DATETIME(3) NULL, revoked_at DATETIME(3) NULL,
  UNIQUE KEY uq_token (push_token_hash),
  FOREIGN KEY (person_id) REFERENCES person(id)
);

CREATE TABLE alert (                                  -- Ficha del Alerta, compatible con CAP
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  public_id VARCHAR(20) NOT NULL UNIQUE,              -- UNS-YYYY-NNN
  kind VARCHAR(12) NOT NULL,                          -- alert | warning | acp | manual | drill
  source VARCHAR(20) NOT NULL,                        -- smn_web | smn_app | civil_defense | manual | sensor
  phenomenon VARCHAR(24) NOT NULL,
  level VARCHAR(10) NOT NULL,                         -- yellow | orange | red | violet | acp
  zone VARCHAR(200) NOT NULL,
  effective_from DATETIME NOT NULL, effective_to DATETIME NOT NULL,
  timeline JSON NOT NULL,                             -- 72 h en rangos de 6 h
  simultaneous_events JSON NOT NULL,
  status VARCHAR(16) NOT NULL, is_drill BOOLEAN NOT NULL DEFAULT FALSE,
  created_at DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3)
);

CREATE TABLE alert_decision (
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  alert_id BIGINT UNSIGNED NOT NULL,
  step VARCHAR(16) NOT NULL,                          -- assessed | recommended | approved | ceased
  actor_id BIGINT UNSIGNED NOT NULL, deputy_for BIGINT UNSIGNED NULL,
  notes TEXT NULL, decided_at DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  FOREIGN KEY (alert_id) REFERENCES alert(id)
);

CREATE TABLE broadcast (                              -- emisión (inicial, actualización, cese, rectificación)
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  alert_id BIGINT UNSIGNED NOT NULL,
  template_code VARCHAR(4) NOT NULL,                  -- M1..M8
  content_version INT NOT NULL,
  text_plain TEXT NOT NULL, text_audio_ref VARCHAR(200), text_highcontrast_ref VARCHAR(200),
  audience_spec JSON NOT NULL,
  approved_by BIGINT UNSIGNED NOT NULL, second_approver BIGINT UNSIGNED NULL,
  created_at DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  FOREIGN KEY (alert_id) REFERENCES alert(id)
);

CREATE TABLE delivery (                               -- una fila por persona, canal e intento
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  broadcast_id BIGINT UNSIGNED NOT NULL, person_id BIGINT UNSIGNED NOT NULL,
  device_id BIGINT UNSIGNED NULL,
  channel VARCHAR(12) NOT NULL,                       -- push_apns | push_fcm | sms | voice | email | web | telegram
  attempt SMALLINT NOT NULL DEFAULT 1,
  status VARCHAR(12) NOT NULL,                        -- queued | sent | delivered | failed | expired
  provider_msg_id VARCHAR(120) NULL, error_code VARCHAR(40) NULL,
  queued_at DATETIME(3), sent_at DATETIME(3), delivered_at DATETIME(3),
  KEY idx_bc_person (broadcast_id, person_id), KEY idx_bc_status (broadcast_id, status)
);

CREATE TABLE ack (
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  broadcast_id BIGINT UNSIGNED NOT NULL, person_id BIGINT UNSIGNED NOT NULL,
  device_id BIGINT UNSIGNED NULL,
  kind VARCHAR(20) NOT NULL,                          -- RECEIVED | SAFE | SHELTERED | NEED_HELP | UNAVAILABLE_ROLE
  client_ts DATETIME(3) NULL, server_ts DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  site_id BIGINT UNSIGNED NULL,                       -- predio declarado, no geolocalización
  UNIQUE KEY uq_ack (broadcast_id, person_id, kind)
);

CREATE TABLE source_snapshot (
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  source VARCHAR(20) NOT NULL, fetched_at DATETIME(3) NOT NULL,
  http_status SMALLINT, payload_sha256 CHAR(64) NOT NULL, payload MEDIUMBLOB
);

CREATE TABLE audit_log (                              -- encadenada: hash = SHA-256(prev_hash || contenido)
  id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  at DATETIME(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  actor_id BIGINT UNSIGNED NULL, action VARCHAR(60) NOT NULL,
  entity VARCHAR(40) NOT NULL, entity_id BIGINT UNSIGNED NULL,
  payload JSON NULL, ip VARBINARY(16) NULL,
  prev_hash CHAR(64) NOT NULL, hash CHAR(64) NOT NULL
);
```

**Notas:** particionar `delivery` y `source_snapshot` por mes y definir retención · catálogos (roles, plantillas M1–M8, umbrales, ventanas) en tablas versionadas · los integrantes del CDE son **datos** en `person`/`role_assignment`, no código · custodia escolar y checklists se modelan en Fase 5 con el mismo estilo.

---

## 10. API (resumen de contratos)

REST sobre HTTPS, JSON, versionada (`/v1`), documentada con OpenAPI. Autenticación por token de corta vida; MFA para roles T0/T1 y consola.

| Grupo | Endpoint (ejemplos) | Quién |
|---|---|---|
| Sesión | `POST /v1/auth/oidc/callback` · `POST /v1/auth/refresh` | Todos |
| Dispositivos | `PUT /v1/devices/me` (token, readiness) · `POST /v1/devices/me/heartbeat` | App |
| Alertas | `GET /v1/alerts` · `GET /v1/alerts/{id}` · `POST /v1/alerts` (manual) · `POST /v1/alerts/{id}/assess` · `/recommend` · `/approve` · `/cease` | Nodo Central, CDE, Rector |
| Emisiones | `POST /v1/alerts/{id}/broadcasts` · `GET /v1/broadcasts/{id}/status` | Nodo Central, Vocería |
| Confirmaciones | `POST /v1/broadcasts/{id}/ack` | App |
| Padrón | `GET/POST/PATCH /v1/people` · `/v1/role-assignments` · `POST /v1/people/import` | Administración |
| Catálogos | `GET /v1/catalogs/{templates,thresholds,windows,roles}` | Consola |
| ECD | `POST /v1/ecd/checks` · `POST /v1/ecd/declare` · `POST /v1/ecd/restore` | Operador de Guardia |
| Informes | `GET /v1/reports/post-activation/{alertId}` | SHST |
| Salud | `GET /v1/health` · `GET /v1/canary/status` | Monitoreo |

**Reglas transversales:** idempotencia en `POST` de emisión y de ACK (clave de idempotencia); límites de tasa; toda mutación escribe en `audit_log`; el ACK acepta `client_ts` pero ordena por `server_ts`.

---

## 11. Experiencia de usuario

### 11.1 App móvil

1. **Alta:** inicio de sesión institucional → aviso de privacidad y consentimiento → asistente de permisos (notificaciones, críticas, No Molestar, pantalla completa, batería con guía según marca) → prueba de alarma guiada.
2. **Inicio:** estado del sistema, estado de preparación del dispositivo, última alerta, botón de prueba.
3. **Pantalla de alarma:** a pantalla completa, alto contraste, pictograma ISO 7010, texto corto en lenguaje claro, botones de respuesta grandes, botón «silenciar y confirmar».
4. **Detalle de alerta:** nivel, zona, vigencia, instrucciones, versión sonora y visual, historial de actualizaciones (M6, M7, M8).
5. **Mi rol:** suplente, predios y audiencias; reporte de estado (`SHELTERED`).
6. **Ayuda:** guías por marca y contacto de soporte.

### 11.2 Consola del Nodo Central

1. **Cola de alertas** con borrador de Ficha y alarma sonora propia.
2. **Ficha del Alerta:** campos del Anexo B del Doc A, con línea de tiempo de 72 h visible y bloqueo hasta leerla; umbrales y matriz precargados.
3. **Decisión:** pasos de recomendación y aprobación con identidad, hora y, si corresponde, segunda aprobación.
4. **Emisión:** plantilla M1–M8 con campos editables y contenido sustantivo bloqueado; los tres formatos (sonoro, visual de alto contraste, texto simple); selección de audiencia y verificación de ≥3 canales independientes.
5. **Tablero en vivo:** entregas por canal, confirmaciones, no confirmados con botón de escalar, estado de preparación por predio.
6. **Cese y rectificación:** M6 y M7 con un clic; informe post-activación en borrador.
7. **Rutina de guardia:** tareas 06/10/16/18/19/22 h con check y observaciones.
8. **ECD:** panel de triangulación y libro de guardia digital.
9. **Registro de difusión** por capa, incluyendo canales manuales (radio, megafonía, presencial) que el operador asienta [Doc C Anexo B].

### 11.3 Accesibilidad

Tres formatos obligatorios por mensaje, lenguaje claro y pictogramas ISO 7010; consola conforme a WCAG 2.2 AA; tamaños y contrastes revisados en dispositivos reales; subtítulos en videos de capacitación.

---

## 12. Seguridad y privacidad

### 12.1 Amenazas y controles

| Amenaza | Controles |
|---|---|
| **Alerta falsa o maliciosa** (cuenta comprometida, insider) | MFA para emisores; **regla de dos personas** en Rojo/ACP y audiencias grandes; límites por rol; alarma cuando se emite fuera de ventana; rectificación en un clic |
| Suplantación de la API de envío | Credenciales en bóveda de secretos; lista de orígenes permitidos; rotación |
| Alteración de registros | Auditoría encadenada; copia periódica del último hash fuera del sistema |
| Filtración de padrón, DNI o datos de menores | Cifrado en tránsito y reposo; DNI cifrado por la aplicación; acceso por rol; registro de accesos |
| Ingesta envenenada | Validación de esquema, límites de cordura, confirmación humana, *dead-man switch* |
| Abuso de la app o tokens robados | Tokens de corta vida; verificación de integridad de app (Play Integrity / App Attest); límites de tasa |
| Denegación de servicio | CDN/WAF; colas con prioridad (T0 primero) y cola dedicada al camino crítico |
| Cautividad de proveedor | Doble camino iOS; dos proveedores SMS para T0; exportación periódica de padrón y registros [Doc B §7.6] |
| Cadena de suministro | SBOM, escaneo de dependencias, revisión de librerías de notificaciones |

### 12.2 Estándares de trabajo 

OWASP ASVS (nivel 2) para el backend y OWASP MASVS para las apps · SAST/DAST en CI · **prueba de penetración externa antes de la compuerta G3** · corrección de críticos antes de producción · secretos solo en servidor.

### 12.3 Datos personales (Ley 25.326)

> Guía técnica; debe validarla Asesoría Legal de la UNS.

- Finalidad única: comunicación de emergencia.
- Aviso y consentimiento al alta, con versión registrada.
- Evaluar la inscripción de la base ante la autoridad de protección de datos.
- Ubicación: no se captura de forma continua; solo si la persona la adjunta en `NEED_HELP`.
- Menores y familias (escuelas): datos de adultos autorizados y alumnos con acceso restringido y cifrado, solo en Fase 5.
- FCM y APNs procesan tokens de dispositivo fuera del país por diseño: documentar y evaluar con Legal.
- Plazos de retención por tabla a definir por SHST y Legal (D-09); simulacros con plazo menor.
- Procedimiento de acceso, rectificación y supresión desde la consola.
- Plan de respuesta a incidentes de seguridad con contactos definidos.

---

## 13. Calidad y pruebas

### 13.1 Estrategia

| Nivel | Qué | Cuándo |
|---|---|---|
| Unitarias e integración | Motor de estados, reglas del protocolo (ventanas, regla de oro, simultáneos), escalador, parser SMN | Cada commit |
| Contrato | Parser SMN con muestras reales; APNs/FCM en *sandbox* | Cada commit y semanal |
| E2E | Alerta → decisión → emisión → confirmación en *staging* con dispositivos reales | Cada release |
| Carga | Envío masivo en ráfaga y recepción de ACK en ráfaga con padrón sintético | Antes de G2 y G3 |
| Seguridad | SAST/DAST continuo; pentest externo | Antes de G3 |
| Laboratorio de dispositivos | Matriz de §13.2 | Antes de cada release |
| **Canario** | Alerta de prueba automática a dispositivos fijos | Continuo |
| **Campaña de preparación** | «Prueba de alarma» a T0/T1 y mensual a T2 | Mensual |
| **Simulacros** | Mesa trimestral, difusión masiva trimestral, integral anual (Doc A §11 y Doc C §9) | Según calendario |

La **prueba semanal de AlertUNS** se programa junto con la prueba radial semanal (AT-02 §7) y se registra en los mismos libros. Cuando AlertUNS entre en operación se agrega a la tabla de pruebas del Doc B §11 (hoy figura «Prueba Alerthor, semanal»).

### 13.2 Matriz de pruebas de alarma

**Android.** Estados: app cerrada, en segundo plano, abierta, pantalla bloqueada y apagada, silencio, No Molestar, ahorro de batería, Doze, reinicio del equipo, recién instalada, batería muy baja. Audio: volumen mínimo y máximo (el canal de alarma debe sonar), vibración, repetición hasta confirmar, auriculares y Bluetooth (comportamiento por modelo). Permisos: notificaciones (Android 13+), acceso a No Molestar, pantalla completa (`canUseFullScreenIntent()` falso → guía), exclusión de batería, servicio en primer plano. Fabricantes: Samsung, Xiaomi/Redmi, Motorola, Pixel, Oppo/Realme, gama baja. Red: WiFi, 4G/5G, 3G, sin red → al recuperar se entrega y se marca **tardía**.

**iOS.** Critical Alerts con app cerrada, bloqueada, con interruptor de silencio, con Focus; Time Sensitive como respaldo; permiso crítico denegado por el usuario → degradación y aviso a la consola; sonido por nivel; extensión de servicio; AirPods/altavoz; Low Power Mode; red variable.

**Web.** Notificación persistente, Service Worker, Web Audio, Wake Lock, Chrome/Firefox/Edge/Safari, Chrome móvil como PWA; en Safari de iPhone, derivar a la app.

**Transversales.** Tokens inválidos o app desinstalada (manejo y aviso), escalamiento SMS/voz, auditoría encadenada verificable, regla de dos personas, *dead-man switch*, restauración de backup.

### 13.3 Dispositivos de laboratorio

15–20 equipos: Android ≥8 (Samsung A y S, Xiaomi/Redmi, Motorola, Pixel, Oppo/Realme, uno de gama baja) y 3 iPhone (antiguo soportado, medio, reciente), cada uno en estado «limpio» y «hostil» (ahorro de batería, No Molestar/Focus, silencio, bloqueado, sin datos).

### 13.4 Criterios que bloquean una versión

- Cualquier falla de alarma crítica con app cerrada, silencio o No Molestar en los dispositivos de referencia.
- Entitlement de Critical Alerts no aprobado **y** sin plan de mitigación vigente (SMS/voz + guía).
- Entrega al proveedor > 30 s en condiciones normales.
- Ficha del Alerta que no valide campos obligatorios; falla de la regla de dos personas o de la auditoría encadenada.
- Falla del canario o de la restauración de backup en los últimos 7 días.
- Pentest con hallazgos críticos abiertos.
- Tasa de éxito global < 95 % o simulacro integrador fallido.

---

## 14. DevOps y operación

- **Entornos:** `dev`, `staging` (proveedores en *sandbox*), `prod`, `dr` (Palihue).
- **CI/CD:** compilación y pruebas por PR; apps firmadas con claves custodiadas por la UNS; despliegue *blue/green*; banderas de funcionalidad; versión mínima forzable desde el servidor.
- **Móvil:** TestFlight y pruebas internas/cerradas de Play; reportes de fallos y mapas de símbolos.
- **Infraestructura como código** y *runbooks* para: caída de FCM/APNs, caída de SMS, falla de la ingesta SMN, conmutación Alem↔Palihue, restauración y rotación de claves.
- **Backups:** diarios, cifrados, 30 días de retención, restauración mensual comprobada.
- **Monitoreo:** latencia de colas por canal, errores de APNs/FCM, tokens inválidos, preparación por predio y rol, versiones instaladas, estado del canario; alertas por un canal **externo al propio sistema**.
- **Guardia técnica** durante Naranja/Rojo y simulacros; congelamiento de despliegues con alerta Naranja/Roja activa o prevista.
- **Gestión de cambios del protocolo:** cada nueva revisión de los anexos genera una nueva versión de catálogos con tabla de cambios (Doc A §12).

---

## 15. Plan de trabajo

**Supuestos:** equipo de ~4,5–5 FTE; inicio el lunes 12/10/2026; sprints de 2 semanas; receso estival en enero–febrero con colchón (calendario académico a confirmar). Con menos de 4 FTE la duración crece proporcionalmente. Si el hosting actual no es apto, sumar 1–2 semanas a la Fase 0.

### 15.1 Fases y compuertas

| Fase | Sem. | Fechas aprox. | Objetivo | Compuerta de salida |
|---|---|---|---|---|
| **0. Cimientos y reducción de riesgo** | 1–3 | 12/10 – 30/10/2026 | Eliminar los riesgos que pueden matar el proyecto | **G0:** PoC demuestra alarma con app cerrada y silencio/No Molestar en Android (≥4 marcas) e iOS al menos en Time Sensitive; hosting apto o alternativa aprobada; decisiones D-01…D-05 cerradas; modelo de amenazas aprobado |
| **1. Núcleo de alerta** | 4–11 | 02/11 – 24/12/2026 | Alerta → alarma → confirmación → escalamiento → auditoría de punta a punta | **G1:** demo con CDE y Telecomunicaciones; canario estable 7 días; ≥95 % de confirmación T0 en pruebas; restauración de backup probada |
| **2. Protocolo UNS** | 12–17 | 28/12/2026 – 05/02/2027 | Que el sistema *sea* el protocolo | **G2:** simulacro de mesa con Nodo Central + CDE + DCI usando solo AlertUNS; piloto con 100–200 personas del staff |
| **3. Piloto en paralelo y endurecimiento** | 18–25 | 08/02 – 02/04/2027 | Cumplir las condiciones del Doc B §7.6 | **G3:** **simulacro integral exitoso** + un ciclo de operación en paralelo con Alerthor + pentest sin críticos + §13.4 en verde + legal cerrado |
| **4. Despliegue por oleadas** | 26–30 | 05/04 – 07/05/2027 | Pasar a producción por niveles | **G4:** aprobación del CDE; Alerthor queda como respaldo; Doc B actualizado (§7.2, §7.3, §11) |
| **5. Post-MVP** | desde may-2027 | trimestral | Ampliar valor | Priorizado por el CDE |

### 15.2 Plan por sprint

| Sprint | Semanas | Objetivo | Entregables principales |
|---|---|---|---|
| S0 | 1–3 | Fase 0 | Gobierno y RACI; cuentas Apple/Google a nombre de la UNS; **solicitud de Critical Alerts enviada**; PoC de alarma Android/iOS y APNs directo vs FCM; auditoría de hosting; D-01…D-06; modelo de amenazas; consulta formal al SMN |
| S1 | 4–5 | Base técnica | Monorepo, CI, entornos, esquema de datos inicial, SSO, padrón y roles con ámbito y suplencia |
| S2 | 6–7 | Dispositivos y despacho | Registro de dispositivos, preparación, dispatcher con colas, canal FCM y APNs |
| S3 | 8–9 | Alarma e interacción | Módulos nativos de alarma (Android e iOS), pantalla de alarma, confirmaciones, tablero en vivo mínimo |
| S4 | 10–11 | Escalamiento y cierre de F1 | SMS y voz, escalador, auditoría encadenada, canario, simulacro interno, **G1** |
| S5 | 12–13 | Ficha y reglas | Ficha del Alerta completa, matriz de decisión, ventanas, umbrales versionados, máquina de estados con aprobaciones |
| S6 | 14–15 | Ingesta y plantillas | Ingesta asistida SMN con *dead-man switch*, M1–M8 con contenido bloqueado, tres formatos accesibles |
| S7 | 16–17 | Cascada y ECD | Registro de difusión por capa, reportes de estado de mayordomías, apoyo ECD, rutina de guardia, **G2** (simulacro de mesa y piloto cerrado) |
| S8 | 18–19 | Piloto en paralelo | Operación junto a Alerthor, campañas de preparación, corrección de hallazgos |
| S9 | 20–21 | Carga y seguridad | Pruebas de carga, pentest externo, remediación |
| S10 | 22–23 | Capacitación y simulacros | Manuales, capacitación T0/T1, prueba de difusión masiva trimestral |
| S11 | 24–25 | Simulacro integral | **G3**, revisión legal, informe de lecciones |
| S12 | 26–27 | Oleada T2 | Altas por oleadas, soporte nivel 1 y 2 |
| S13 | 28–30 | Oleada T3 y cierre | Altas T3, ajustes, actualización del Doc B, **G4** |

### 15.3 Ruta crítica

1. Cuentas de tienda a nombre de la UNS (D-U-N-S y verificación) → compilaciones firmadas → pruebas en dispositivos reales.
2. Respuesta de Apple al entitlement (no controlable; hay plan B).
3. SSO con el proveedor de identidad institucional [?].
4. Capacidad de hosting.
5. Consulta/convenio con el SMN (no bloquea el MVP: hay ingesta interina y consulta manual).

### 15.4 Tareas de la semana 1

- [ ] Designar dueño de producto y dueño técnico (D-01).
- [ ] Iniciar el alta de Apple Developer y Google Play como **organización UNS**; consultar exención de cuota de Apple para instituciones educativas.
- [ ] Redactar y enviar la solicitud de Critical Alerts.
- [ ] Inventario de dispositivos para el laboratorio y lista de ~30 personas T0/T1 para PoC y piloto.
- [ ] Auditoría de hosting (§16.2).
- [ ] Consulta formal al SMN y reunión con Defensa Civil sobre interoperabilidad.

---

## 16. Recursos necesarios

### 16.1 Equipo [E]

| Rol | Dedicación | Responsabilidad |
|---|---|---|
| Líder técnico / backend senior | 1,0 | Arquitectura, motor de estados, seguridad de diseño |
| Móvil senior (Kotlin/Swift) | 1,0 | Capa de alarma, entitlement, PoC |
| Móvil / full stack | 1,0 | Interfaz de apps, alta de permisos |
| Web / full stack | 1,0 | Consola, SSO, reportes |
| DevOps / SRE | 0,5 | Alta disponibilidad, observabilidad, CI/CD, canario |
| QA con laboratorio de dispositivos | 0,5 | Matriz de pruebas, campañas de preparación |
| UX/UI y accesibilidad | 0,3 | Pantalla de alarma, WCAG, pictogramas |
| Seguridad (consultoría y pentest) | puntual | Modelo de amenazas, pentest |
| Dueños de producto (SHST) y técnico (Telecomunicaciones) | 0,2 c/u | Criterios de aceptación, simulacros |
| DCI | puntual | Plantillas y formatos accesibles |
| Asesoría Legal | puntual | Ley 25.326, términos, transferencias |

### 16.2 Infraestructura

| Pregunta de auditoría de hosting | Necesario |
|---|---|
| ¿VPS/contenedores con acceso root o hosting compartido? | VPS o similar: en hosting compartido no corren colas, WebSockets ni procesos de larga duración |
| ¿Se puede instalar Redis y un supervisor de procesos? | Sí |
| ¿Hay salida HTTPS a FCM/APNs y a proveedores SMS/voz? | Sí |
| ¿Segundo sitio (Palihue) con réplica? | Deseable desde el MVP |
| ¿Punto fuera de Bahía Blanca? | Despachador mínimo |
| ¿IP fija, WAF/CDN, límites de ancho de banda? | Definir |
| ¿Quién opera el servidor y con qué guardia? | Definir |

**Dimensionamiento inicial [E]:** 4 vCPU, 8 GB de RAM y 100 GB SSD para producción, con un *staging* equivalente, a ajustar con la prueba de carga y el tamaño real del padrón.

### 16.3 Cuentas, licencias y contratos

Apple Developer (organización UNS) · Google Play Console (organización UNS) · entitlement de Critical Alerts · proyecto Firebase y credenciales APNs · dominio institucional y TLS · proveedor de identidad (OIDC/SAML) · contrato de SMS y voz (idealmente dos proveedores para T0) · bot de Telegram (y, opcional, WhatsApp Business con costos y plantillas) · Sentry/GlitchTip y Prometheus/Grafana · pentest externo · convenio o consulta con el SMN · revisión legal.

### 16.4 Dispositivos

8–10 teléfonos para la PoC y 15–20 para el laboratorio; **2 Android + 2 iPhone institucionales dedicados** al Nodo Central y al canario, siempre en carga; opcional: MDM para dispositivos T0/T1 con permisos y exclusión de batería preconfigurados.

### 16.5 Material de comunicación

Guías de configuración por marca, videos cortos con subtítulos, pictogramas ISO 7010, textos en lenguaje claro y audios pregrabados por nivel y tipo de mensaje.

---

## 17. Esfuerzo estimado 

| Flujo de trabajo | Horas |
|---|---|
| Fase 0 (PoC, cuentas, decisiones) | 200 |
| Backend núcleo (padrón, dispatcher, confirmaciones, escalamiento, auditoría, RBAC) | 520 |
| App Android (alarma nativa + interfaz) | 360 |
| App iOS (alertas críticas/Time Sensitive + interfaz) | 300 |
| Consola web | 420 |
| Ingesta SMN + Ficha + motor de reglas | 160 |
| Plantillas, cascada y formatos accesibles | 140 |
| Seguridad y privacidad | 160 |
| DevOps, alta disponibilidad, observabilidad | 220 |
| QA y laboratorio | 360 |
| Capacitación, documentación, simulacros | 140 |
| Gestión y gobierno (~8 %) | 250 |
| **Total hasta producción** | **≈ 3.230** |
| Post-MVP (custodia, checklists, offline, sensores) | ≈ 900 |

---

## 18. Riesgos principales

| ID | Riesgo | Prob. | Impacto | Mitigación |
|---|---|---|---|---|
| R-01 | Apple no aprueba o demora Critical Alerts | Media | Alto | Solicitud en semana 1; Time Sensitive + SMS/voz; guía al usuario |
| R-02 | Google Play no concede pantalla completa ni acepta el tipo de servicio | Media | Medio | Declaración temprana; flujo de permiso manual; notificación de alta importancia |
| R-03 | Personalizaciones de fabricantes matan la app en segundo plano | Alta | Alto | Laboratorio por marca, guías, preparación visible, campaña mensual |
| R-04 | El SMN cambia o bloquea el formato público | Media | Alto | Ingesta asistida, *dead-man switch*, convenio, consulta manual |
| R-05 | Falsa alarma masiva | Baja | Muy alto | Cadena de decisión, MFA, dos personas, rectificación, simulacros |
| R-06 | Hosting inadecuado | Media | Alto | Auditoría en semana 1–2; plan alternativo |
| R-07 | Caída simultánea de Alem y Palihue | Baja | Muy alto | Despachador externo, hoja de contingencia, RACUNS y libro de guardia |
| R-08 | Fatiga de alarma | Media | Alto | Niveles T0–T3, sonidos por nivel, reglas de frecuencia |
| R-09 | Incidente de datos personales | Baja | Alto | Cifrado, minimización, pentest, plan de respuesta |
| R-10 | Dependencia de una persona | Media | Alto | Cuentas de la UNS, documentación, *runbooks*, dos responsables por función |
| R-11 | No hay evento real durante el piloto | Media | Medio | Criterio de G3 basado en simulacro (admitido por el Doc B) |
| R-12 | Inconsistencias entre documentos del protocolo que el sistema codificaría | Media | Medio | Resolver las observaciones del Anexo A antes de congelar catálogos |
| R-13 | Riesgo legal por el análisis de BomberBOT | Baja | Medio | Método de caja negra, desarrollo independiente, revisión legal |

---

## 19. Decisiones pendientes

| ID | Decisión | Opciones | Responsable | Plazo |
|---|---|---|---|---|
| D-01 | Dueños de producto y técnico | SHST / Telecomunicaciones | Rectorado | Sem. 1 |
| D-02 | Titularidad de cuentas de tienda | UNS (recomendado) | Telecom. + Legal | Sem. 1 |
| D-03 | Audiencias del MVP | T0+T1+T2 (recomendado) / incluir T3 | CDE | Sem. 2 |
| D-04 | Política del ACP | A asistido (recomendado) / B automático / C manual | Rectorado + CDE | Sem. 3 |
| D-05 | Hosting | VPS UNS / nube con revisión legal | Telecom. | Sem. 2 |
| D-06 | Pila móvil final | RN + módulos nativos / Flutter + plugins / nativo | Líder técnico | Sem. 3 |
| D-07 | Proveedor(es) SMS y voz | Uno / dos para T0 | Telecom. | Sem. 4 |
| D-08 | Identidad | OIDC/SAML / LDAP | Sistemas | Sem. 3 |
| D-09 | Retención de datos | Plazos por tabla | SHST + Legal | Sem. 6 |
| D-10 | Qué cuenta como «ciclo en paralelo» con Alerthor | Duración, eventos o simulacros | SHST | Sem. 8 |
| D-11 | Dos personas obligatorias: ¿en qué niveles y audiencias? | Rojo/ACP y > N destinatarios | CDE | Sem. 6 |
| D-12 | Nombre y marca institucional | «AlertUNS» u otra | DCI | Sem. 6 |

---

## 20. Verificaciones externas y pendientes

**Verificado:**
- Apple: el entitlement *Critical Alerts* permite sonido con el equipo bloqueado, en silencio o con No Molestar/Focus, y se solicita por formulario. https://developer.apple.com/documentation/bundleresources/entitlements/com.apple.developer.usernotifications.critical-alerts
- Foros de Apple: solicitudes del entitlement sin respuesta por semanas. https://developer.apple.com/forums/thread/106042
- Google Play: declaración de servicios en primer plano y de pantalla completa en Android 14; desde enero de 2025 solo apps de llamadas o alarmas lo tienen habilitado por defecto. https://support.google.com/googleplay/android-developer/answer/13392821
- Android Open Source Project: límites de *full-screen intent* y `canUseFullScreenIntent()`. https://source.android.com/docs/core/permissions/fsi-limits

**Pendiente de confirmar [?]:** feed oficial del SMN · términos de uso del SMN y de BomberBOT · política vigente de Apple sobre VoIP · versión mínima de Web Push en iOS · exención de cuota de Apple para la UNS · inscripción de la base de datos · difusión celular de alertas locales · tamaño real del padrón por nivel.

---

## Anexo A — Observaciones sobre los documentos fuente que afectan al diseño

Resolver antes de congelar catálogos (R-12).

| # | Observación | Dónde | Efecto |
|---|---|---|---|
| A-1 | La **Sala de Crisis primaria y alternativa** difiere: Doc A §9.2 indica primaria San Juan 670 y alternativa Anexo Campus Radio; Doc C §5 indica primaria Anexo de Agronomía y alternativa San Juan 670 | Doc A / Doc C | La consola y las plantillas deben mostrar un único dato |
| A-2 | **Capas de difusión**: Doc C Anexo B lista 1, 2, 3, 4 y **6** (falta la 5); Doc B §8.8 define Capa 3 = datos/Starlink, Capa 4 = difusión masiva AM/FM, Capa 5 = malla Meshtastic | Doc C / Doc B | El registro de difusión necesita un catálogo único |
| A-3 | Referencia rota: Doc A §8 remite al «punto 5» para las ventanas, que están en §6.1; la numeración salta del 1 al 3 | Doc A | Corregir al versionar |
| A-4 | «Alerthor; escucha permanente en CH1» mezcla un servicio de terceros con un canal de radio | Doc A §10 | AlertUNS solo registra la declaración del operador |
| A-5 | El **Cuadro de Acción Rápida** deja vacías las filas de emergencia climática, mayor y sanitaria; M4 figura como «SMN Rojo» en Doc C y como respuesta a Naranja/Rojo o ACP en Doc A §7.8 | Doc C §7 / Doc A §7.8 | Completar la matriz mensaje↔nivel↔canal |
| A-6 | Typo: «M78 – Parte prolongado» (debería ser M8) | Doc C Anexo C | Corregir |
| A-7 | AT-01 §5 remite al checklist como «Sección 11» y está en §12 | AT-01 | Corregir |
| A-8 | La Oficina de Recepción de Avisos (Doc A) y el Nodo Central 24/7 (Doc B) son la misma función con dos nombres | Doc A / Doc B | Glosario único; un solo rol en el sistema |
| A-9 | WhatsApp/Telegram son «informales, sin garantía de entrega» y a la vez se usan en la triangulación del ECD | Doc B §7.2 y §7.5.3 | Aceptable como evidencia, no como canal garantizado |

---

## Anexo B — Plantillas de mensaje (contenido sustantivo bloqueado)

Fuente: Doc C, Anexo C. Los campos editables son solo los entre paréntesis o corchetes.

| Código | Uso | Canales sugeridos |
|---|---|---|
| **M1** Preventivo | SMN Amarillo: suspensión de actividades al aire libre | Correo, redes, apps |
| **M2** Suspensión | Naranja/Rojo: suspensión de actividades presenciales en (sede/edificio) | WhatsApp/Telegram, apps, correo, web, Moodle, redes |
| **M3** Evacuación | Salida ordenada al punto de reunión; solo por orden del CDE | Megafonía, plataforma de alumnos, redes |
| **M4** Confinamiento | Permanecer dentro de los edificios hasta nuevas instrucciones | Megafonía, plataforma de alumnos, redes, medios externos |
| **M5** Custodia escolar | Aviso a familias: alumnos bajo custodia; retiro solo con DNI del adulto autorizado | Enlaces de escuelas, WhatsApp/Telegram familias, correo |
| **M6** Cese | Reanudación; mismos canales que la suspensión | Los de la suspensión |
| **M7** Rumor | Aclaración oficial con dato verificado | Redes oficiales, web |
| **M8** Parte prolongado | Servicios, retiro escolar y próxima actualización (por defecto 60 min) | Megafonía de predios, redes, web, radio |

Cada plantilla se almacena con **tres formatos** (texto simple, versión sonora, versión visual de alto contraste) y se versiona con tabla de cambios.

---

## Anexo C — Criterios de aceptación de las compuertas

**G0 (sem. 3):** PoC Android con alarma en app cerrada, bloqueada, silencio y No Molestar en ≥4 marcas · PoC iOS en Time Sensitive y, si Apple respondió, Critical Alerts · APNs directo y FCM comparados · hosting validado · D-01…D-05 cerradas · modelo de amenazas aprobado.

**G1 (sem. 11):** flujo completo con CDE y Telecomunicaciones · canario ≥7 días estable · ≥95 % de confirmación T0 · auditoría encadenada verificable · restauración de backup probada.

**G2 (sem. 17):** el Nodo Central opera Ficha y cadena de decisión solo con AlertUNS · piloto con 100–200 personas · ingesta SMN con *dead-man switch* probado · tres formatos por mensaje · registro de difusión con ≥3 canales.

**G3 (sem. 25):** simulacro integral exitoso · ciclo en paralelo con Alerthor cumplido según D-10 · pentest sin críticos · criterios de §13.4 en verde · preparación T0/T1 ≥98 % · revisión legal cerrada.

**G4 (sem. 30):** altas por oleadas completas · manual y capacitación entregados · aprobación del CDE · Doc B actualizado.

---


