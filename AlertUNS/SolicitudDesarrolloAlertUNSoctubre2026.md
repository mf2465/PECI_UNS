# SOLICITUD DE DESARROLLO: Sistema AlertUNS

## Sistema institucional de alerta, confirmación y escalamiento para la activación del PECl-UNS

**Solicitante:** Universidad Nacional del Sur (UNS) — Bahía Blanca

**Destinatario:** Equipo de desarrollo de AlertUNS

**Tipo de documento:** Especificación técnica de la tarea (documento de definiciones)

**Plataformas:** Android · iPhone/iOS · Web

**Versión:** 1.0 (borrador para revisión)

**Fecha de emisión:** 6 de octubre de 2026

**Basado en:** Anexos Operativos 07-A, 07-B, 07-C · AT-01 · AT-02 · referencia funcional pública de app BomberBOT (https://bomberbot.com.ar)

---

## 0. CÓMO LEER ESTE DOCUMENTO

### 0.1. Qué es y qué no es este documento

Este documento **solicita** el desarrollo de AlertUNS y define **qué debe construirse, bajo qué reglas y cómo se verificará**. Está redactado como tarea para un grupo de desarrolladores.

- **No fija plazos ni estimaciones.** El trabajo se organiza en **Fases** con **compuertas de salida** (sección 17). Los plazos se acordarán entre la UNS y el equipo una vez cerrada la Fase 0.
- **No pide construir toda la aplicación ahora.** La primera entrega es la **Fase 0** (viabilidad, arquitectura y prueba de concepto de la alarma crítica). Recién con la compuerta G0 aprobada se autoriza el desarrollo del MVP.
- **No reemplaza el trabajo del equipo.** Las arquitecturas, los modelos de datos definitivos, los ADR y los resultados de las PoC son **entregables que el equipo debe producir**; aquí solo se definen los requisitos y las restricciones.
- **No inventa requisitos institucionales.** Todo lo que no está respaldado por un documento de la UNS se marca como propuesta o como pendiente.

### 0.2. Leyenda de prioridad

| Ícono | Prioridad | Significado |
|:-----:|-----------|-------------|
| 🔴 | **Alta** | Imprescindible. Su falla compromete la función crítica del sistema o su seguridad. Bloquea la liberación |
| 🟡 | **Media** | Necesaria para la operación completa. Puede entregarse después del MVP si así se acuerda |
| 🟢 | **Baja** | Deseable o diferida. No debe retrasar el núcleo |

### 0.3. Leyenda de origen de cada requisito

| Etiqueta | Significado |
|----------|-------------|
| **PROTOCOLO** | Surge de los Anexos del PECl-UNS (07-A, 07-B, 07-C, AT-01, AT-02) |
| **PROYECTO** | Surge de los documentos de planificación del proyecto. Requiere validación institucional cuando así se indica |
| **A CONFIRMAR** | Dato no confirmado. El equipo **no debe asumirlo**: debe solicitar verificación |

### 0.4. Convenciones

- Identificadores de código, tablas, endpoints y claves en **inglés**; documentación y comentarios en **español**.
- Los valores numéricos de desempeño (segundos, porcentajes) son **objetivos de diseño a validar con mediciones reales**, no garantías.
- Cuando dos documentos se contradicen, la contradicción **no se resuelve en silencio**: se registra y se decide mediante un ADR (sección 2.3).

---

## 1. OBJETO Y ALCANCE

### 1.1. Qué se solicita

Diseñar, construir, probar y poner en operación **AlertUNS**: el sistema institucional propio que permite que, cuando la autoridad de la UNS activa el protocolo de emergencia, la comunicación llegue de forma rápida, segmentada, trazable y redundante a las personas que corresponden, con una señal de atención inequívoca cuando corresponda, confirmación de recepción, escalamiento y registro completo.

Componentes solicitados:

| Componente | Descripción | Prioridad |
|------------|-------------|:---------:|
| **Backend / API** | Núcleo de reglas, estados, autorización, auditoría y despacho | 🔴 Alta |
| **Aplicación Android** | Recepción de alertas críticas, alarma, confirmación y estado de preparación | 🔴 Alta |
| **Aplicación iOS** | Ídem, con Critical Alerts sujeto a aprobación de Apple | 🔴 Alta |
| **Consola web** | Operación del Nodo Central: Ficha, decisión, emisión, monitoreo, cese, auditoría | 🔴 Alta |
| **Despacho multicanal** | Push (APNs/FCM), SMS, voz, correo, con escalamiento | 🔴 Alta |
| **Auditoría y observabilidad** | Trazabilidad encadenada, métricas, canarios | 🔴 Alta |
| **Alta disponibilidad y recuperación** | Sitios, réplica, despachador mínimo de contingencia, backups | 🔴 Alta |
| **Integración asistida con el SMN** | Ingesta de información como borrador de alerta | 🟡 Media |
| **Módulos posteriores** | Custodia escolar, checklists, offline, integraciones | 🟢 Baja |

### 1.2. Qué es AlertUNS en el PECl-UNS

AlertUNS es el **«sistema propio»** previsto en el Documento B (Anexo 07-B, §7.6), cuyo alcance objetivo es: padrón multi-público propio; emisión multicanal (notificación push, SMS, correo y voz); registro de entregas y confirmaciones; propiedad local de datos y padrones; interfaces documentadas **[PROTOCOLO]**.

Según el mismo apartado, su **entrada en operación requiere prueba exitosa en al menos un simulacro integral y un ciclo de operación en paralelo con Alerthor**, y debe cumplir los criterios de adopción (a)–(g):

| Criterio (Doc B §7.6) | Cómo debe verificarse en AlertUNS |
|-----------------------|-----------------------------------|
| (a) Redundancia con medios existentes | Canal adicional; no reemplaza SMS, telefonía ni radio |
| (b) Trazabilidad y registro | Auditoría encadenada, entregas y confirmaciones registradas |
| (c) Accesibilidad | Tres formatos por mensaje; WCAG 2.2 AA |
| (d) Protección de datos personales | Sección 13; Ley 25.326 |
| (e) Operación probada en al menos un simulacro | Compuerta G3 |
| (f) Administración y costo sostenibles | Sección 19 |
| (g) Sin dependencia de proveedor único | Sección 10.4 |

### 1.3. Qué no es AlertUNS (fuera de alcance)

- **No reemplaza** a RACUNS, la radio, Defensa Civil, la megafonía, la telefonía ni los medios presenciales. Tampoco reemplaza los procedimientos institucionales: los **implementa y facilita**.
- **No controla ni escucha** la red de radio. Solo registra lo que declara el operador. La integración con RACUNS queda como interfaz futura (sección 10.4).
- **No toma decisiones de emergencia por sí mismo.** Ejecuta y registra decisiones humanas.
- **No localiza personas de forma continua.**
- **No es una aplicación comercial** ni una copia de BomberBOT.

### 1.4. Principio rector

AlertUNS **no se diseña como un sistema de notificaciones push**. Se diseña como un:

> **Sistema de despacho institucional de comunicaciones críticas con trazabilidad, redundancia, confirmación y continuidad operativa.**

Orden de prioridades de ingeniería (de mayor a menor), que rige toda decisión de diseño:

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

---

## 2. DOCUMENTACIÓN DE REFERENCIA

### 2.1. Documentos entregados al equipo

| Documento | Naturaleza | Uso en esta solicitud |
|-----------|------------|-----------------------|
| **Anexo Operativo 07-A** (Documento A) | Normativo — protocolo operativo | Cadena de decisión, umbrales, ventanas horarias, Ficha del Alerta, niveles, custodia escolar, roles del CDE |
| **Anexo Operativo 07-B** (Documento B) | Normativo — soporte técnico | Medios de comunicación, flujos F1–F8, ECD, sistema propio (§7.6), RACUNS |
| **Anexo Operativo 07-C** (Documento C) | Normativo — comunicación en emergencia | Voz oficial, formatos accesibles, plantillas M1–M8, registro de difusión |
| **AT-01** | Normativo — mantenimiento de infraestructura | Checklists e infraestructura (módulos posteriores) |
| **AT-02** | Normativo — mantenimiento de comunicaciones | Pruebas, indicadores y registros de comunicaciones (módulos posteriores) 
| **BomberBOT** (sitio público) | Referencia funcional | Solo capacidades declaradas públicamente (sección 4.2) |

### 2.2. Regla de uso

1. Los **Anexos del PECl-UNS** definen el comportamiento institucional. AlertUNS debe **implementarlos**, no modificarlos.
2. Los **documentos de planificación** describen el sistema a construir. Donde proponen algo que el protocolo no define (por ejemplo, los niveles de audiencia T0–T3), la propuesta debe validarse con la UNS antes de congelarse.
3. El equipo **no debe inventar** requisitos institucionales. Todo vacío se eleva como consulta (sección 21).


---

## 3. PRINCIPIOS DE DESARROLLO (OBLIGATORIOS)

| Principio | Requisito | Origen | Prioridad |
|-----------|-----------|--------|:---------:|
| **El humano decide** | Separación estricta entre detección, evaluación, recomendación, decisión y difusión. El sistema nunca decide por sí mismo | PROTOCOLO + PROYECTO | 🔴 Alta |
| **Verdad operativa** | `ENVIADO ≠ ENTREGADO ≠ LEÍDO ≠ CONFIRMADO ≠ SEGURO`. Cada estado es independiente. Nunca informar «enviado» si solo está «en cola» | PROYECTO | 🔴 Alta |
| **Redundancia** | Ninguna decisión crítica depende de un único medio, canal, proveedor o sitio. Toda decisión se difunde simultáneamente por al menos tres canales independientes | PROTOCOLO (Doc A §10; Doc B §7.1) | 🔴 Alta |
| **Mensaje oficial único** | Solo tienen validez los mensajes originados en el Nodo Central o en la Vocería | PROTOCOLO (Doc B §7.4) | 🔴 Alta |
| **No prometer lo que el sistema operativo no garantiza** | Android e iOS no permiten «ignorar cualquier configuración del teléfono». Se trabaja con capacidad disponible + permiso del usuario + estado del dispositivo + canales alternativos | PROYECTO | 🔴 Alta |
| **Propiedad institucional** | Código, repositorios, dominios, credenciales, cuentas de Apple/Google/Firebase, servidores, bases, backups y certificados son propiedad y control de la UNS. Ninguna dependencia de una persona | PROYECTO | 🔴 Alta |
| **Software libre / costo de licencia $0** | Todo componente de software debe ser gratuito y de código abierto siempre que sea técnicamente posible. Los costos inevitables se limitan a servicios operativos aprobados por la UNS (sección 19) | PROYECTO | 🔴 Alta |
| **Independencia de proveedores** | Ningún componente externo es indispensable para conservar usuarios, roles, alertas, decisiones, auditoría, confirmaciones e historial | PROYECTO | 🔴 Alta |
| **Minimización de datos** | Mínima recolección, mínimo privilegio, retención definida, auditoría. Sin geolocalización continua | PROTOCOLO (Doc B §7.4.5) + PROYECTO | 🔴 Alta |
| **No fallar en silencio** | Todo error de fuente, proveedor o parser debe ser visible para el Nodo Central | PROYECTO | 🔴 Alta |
| **No inventar** | Lo no confirmado se marca como tal. Lo que depende de Apple, Google, hosting o terceros se indica y se verifica | PROYECTO | 🔴 Alta |
| **Núcleo pequeño** | El MVP incluye solo lo necesario para demostrar `ALERTA → ALARMA → CONFIRMACIÓN → ESCALAMIENTO → AUDITORÍA` | PROYECTO | 🔴 Alta |

---

## 4. FUNCIONES REQUERIDAS

### 4.1. Catálogo funcional

| Módulo | Descripción | Prioridad | Origen |
|--------|-------------|:---------:|--------|
| **Alerta crítica con alarma** | Notificación que suena, vibra y muestra pantalla de alarma aun con la app cerrada y el teléfono en silencio, dentro de lo que cada sistema operativo permite | 🔴 Alta | PROYECTO |
| **Despacho multicanal** | Push (APNs, FCM), SMS, voz automatizada, correo. Colas por prioridad y adaptadores de canal desacoplados | 🔴 Alta | PROTOCOLO (Doc B §7.6) |
| **Confirmaciones** | Respuesta con un toque; registro con marca de tiempo oficial del servidor | 🔴 Alta | PROYECTO |
| **Escalamiento configurable** | Reintentos, canal secundario, SMS, voz, suplente, reporte operativo; parámetros versionados | 🔴 Alta | PROTOCOLO + PROYECTO |
| **Cadena de decisión** | `DETECTED → ASSESSED → RECOMMENDED → APPROVED → DISPATCHING → ACTIVE → UPDATED → CEASED → CLOSED` | 🔴 Alta | PROTOCOLO |
| **Ficha del Alerta digital** | Con validación de campos obligatorios y lectura obligatoria de línea de tiempo | 🔴 Alta | PROTOCOLO (Doc A §6.3, Anexo B) |
| **Regla de dos personas** | Para niveles y audiencias críticas | 🔴 Alta | PROYECTO |
| **RBAC con ámbito y suplencias** | Roles como datos configurables; varios roles por persona | 🔴 Alta | PROTOCOLO + PROYECTO |
| **Padrón y dispositivos** | Personas, roles, dispositivos y estado de preparación (*readiness*) | 🔴 Alta | PROTOCOLO (Doc B §7.4.1) |
| **Auditoría encadenada** | Cadena criptográfica de registros | 🔴 Alta | PROYECTO |
| **Consola web del Nodo Central** | Dashboard, Ficha, decisión, emisión, tablero en vivo, cese, auditoría | 🔴 Alta | PROYECTO |
| **Modo simulacro** | Inequívocamente distinguible de una emergencia real | 🔴 Alta | PROTOCOLO (Doc A §11) |
| **Canario** | Dispositivos fijos de prueba permanente | 🔴 Alta | PROYECTO |
| **Alta disponibilidad y contingencia** | Sitios primario/espejo, despachador mínimo, hoja de contingencia | 🔴 Alta | PROYECTO |
| **Alertas manuales** | Creación de emergencia por el Nodo Central | 🔴 Alta | PROYECTO |
| **Cese y rectificación** | Sin sobrescribir la comunicación original | 🔴 Alta | PROTOCOLO + PROYECTO |
| **Ingesta asistida del SMN** | Genera borrador de alerta; nunca envía a la comunidad por sí sola | 🟡 Media | PROYECTO |
| **Plantillas M1–M8** | Texto, audio y visual de alto contraste; contenido sustantivo bloqueado | 🟡 Media | PROTOCOLO (Doc C Anexo C) |
| **Registro de difusión por capa** | Incluye canales manuales asentados por el operador | 🟡 Media | PROTOCOLO (Doc C Anexo B) |
| **Apoyo al ECD** | Asiste al operador; no declara | 🟡 Media | PROTOCOLO (Doc B §7.5) |
| **Informe post-activación** | Automático al cierre; vista web, PDF, CSV y JSON | 🟡 Media | PROTOCOLO (informe en ≤72 h) + PROYECTO |
| **Indicadores** | Preparación, entrega, confirmación, canarios, disponibilidad | 🟡 Media | PROYECTO |
| **Mensajería interna** | Comunicados por audiencia | 🟢 Baja | PROYECTO |
| **Custodia y retiro escolar** | Escuelas Preuniversitarias | 🟢 Baja | PROTOCOLO (Doc A §8) |
| **Checklists AT-01 / AT-02** | Mantenimiento de infraestructura y comunicaciones | 🟢 Baja | PROTOCOLO (AT-01, AT-02) |
| **Modo offline completo** | Sincronización posterior | 🟢 Baja | PROYECTO |
| **Mapas de predios y zonas** | Vulnerabilidades, confinamiento, puntos de encuentro | 🟢 Baja | PROTOCOLO (AT-01 §3) |
| **Integraciones futuras** | Moodle, megafonía, pantallas, RACUNS, sensores, Telegram | 🟢 Baja | PROYECTO |
| **Idiomas adicionales** | Inglés y portugués | 🟢 Baja | PROYECTO |

### 4.2. Referencia funcional de BomberBOT

BomberBOT se usa **exclusivamente como referencia funcional**, sobre lo que su sitio público declara. **No se debe copiar** código, diseño propietario, marca, textos, sonidos, interfaz, recursos gráficos ni implementación interna. La solución es un desarrollo independiente a partir del protocolo de la UNS.

| Capacidad declarada públicamente | Decisión para AlertUNS | Prioridad |
|----------------------------------|------------------------|:---------:|
| Alarma con sonido, vibración y voz con la app cerrada | Núcleo. Implementación nativa (sección 7) | 🔴 Alta |
| Convocatoria general, selectiva y por departamento | Núcleo. Audiencias por predio, rol, turno y escuela | 🔴 Alta |
| Sonidos diferenciados por tipo de emergencia | Núcleo. Sonido por nivel y por tipo de mensaje | 🔴 Alta |
| Respuesta con un toque | Núcleo, con el set de respuestas de la sección 6.8 | 🔴 Alta |
| Cancelación de emergencia | Núcleo (cese y rectificación) | 🔴 Alta |
| Monitoreo de respuestas en vivo | Núcleo (tablero de confirmaciones) | 🔴 Alta |
| Panel web | Núcleo (consola) | 🔴 Alta |
| Monitoreo de dispositivos (online, último ping, versión) | Núcleo, como estado de preparación, **sin ubicación** | 🔴 Alta |
| Simulador de alertas | Núcleo (modo simulacro) | 🔴 Alta |
| Mensajería interna | Posterior | 🟡 Media |
| Chequeos digitales con funcionamiento offline | Posterior (AT-01 / AT-02) | 🟢 Baja |
| Análisis con IA | **No se incorpora** | 🟢 Baja |
| Tareas de limpieza, guardias, encuestas, suscripción | **No aplica** | 🟢 Baja |
| Código de invitación de 6 dígitos | **Se reemplaza** por identidad institucional (sección 13) | 🔴 Alta |

> Antes de usar la aplicación de BomberBOT como banco de comparación, la UNS debe revisar sus términos de uso con Asesoría Legal **[A CONFIRMAR]**.

### 4.3. Qué NO debe entrar en el MVP

| Exclusión | Motivo |
|-----------|--------|
| IA, chatbot, reconocimiento automático de situaciones | Riesgo de falsas alarmas sin beneficio para el núcleo |
| Localización permanente de personas | Desproporcionado frente a la finalidad |
| Mapas complejos, analítica avanzada | No aportan a la demostración del circuito crítico |
| Custodia escolar, checklists, calendarios, encuestas, tareas, mantenimiento, PPO | Módulos posteriores |
| Integración profunda con Moodle | Posterior |
| Automatizaciones que puedan producir falsas alarmas | Prohibidas sin decisión institucional explícita |
| Envío automático masivo desde el SMN | Prohibido sin decisión institucional explícita (sección 8) |

---

## 5. ACTORES, AUDIENCIAS Y ROLES

### 5.1. Actores del protocolo

Rectorado (decide) · Comité de Dirección de la Emergencia — CDE (recomienda) · Nodo Central / Oficina de Recepción de Avisos (opera de forma permanente) · SHST · Vocería / DCI (comunicación pública) · Telecomunicaciones · Infraestructura · mayordomos de edificios · decanos y directores de departamento · directores administrativos · directores de escuelas · docentes y nodocentes · estudiantes · familias (escuelas) · brigadas **[PROTOCOLO: Doc A §9]**.

> Nombres y cargos: el sistema **no debe incorporar nombres de personas en el código**. Los integrantes del CDE y sus suplentes son **datos** administrables.

### 5.2. Niveles de audiencia

Los niveles T0–T3 son una **propuesta del proyecto** que debe validar el CDE (decisión D-05). No figuran en el protocolo.

| Nivel | Quiénes | Entrega | Confirmación | Prioridad |
|-------|---------|---------|--------------|:---------:|
| **T0 — Mando** | CDE y suplentes, Rectorado, operadores del Nodo Central, Vocería | Alarma crítica + SMS + voz | Obligatoria | 🔴 Alta |
| **T1 — Coordinación** | Mayordomías, decanos, directores, Telecomunicaciones, Infraestructura, brigadas, responsables operativos | Alarma crítica + SMS | Obligatoria | 🔴 Alta |
| **T2 — Comunidad laboral** | Docentes, nodocentes, investigadores | Notificación prioritaria + correo | «Recibido» | 🟡 Media |
| **T3 — Comunidad general** | Estudiantes, familias, visitantes | Push estándar + web + Moodle + canales abiertos (Telegram cuando corresponda) | Opcional | 🟢 Baja |

**Criterio de diseño:** la alarma estruendosa se reserva a T0/T1 y a niveles críticos. Usarla de forma indiscriminada genera fatiga y puede perjudicar la aprobación de Apple (sección 7.3).

### 5.3. Control de acceso (RBAC)

| Requisito | Prioridad |
|-----------|:---------:|
| RBAC real: `roles`, `permissions`, `scope`, `assignments`, `deputies`, `validity`. **Prohibido** codificar condiciones del tipo `if user == "admin"` | 🔴 Alta |
| Una persona puede tener varios roles, con diferentes ámbitos, suplentes y vigencias | 🔴 Alta |
| Los roles y las audiencias son **datos configurables**, no código | 🔴 Alta |
| Identidad institucional por OIDC o SAML; LDAP como alternativa si la UNS lo dispone. **No** se usan códigos de invitación como identidad principal | 🔴 Alta |
| MFA obligatorio (preferentemente TOTP) para quienes aprueban, emiten, modifican o administran | 🔴 Alta |
| Sesión corta y reautenticación para acciones críticas en T0/T1 | 🔴 Alta |

---

## 6. PROCESO FUNCIONAL

### 6.1. Cadena de decisión

```text
DETECTED       → evento o alerta detectada (SMN, manual, otra fuente)
   ↓
ASSESSED       → el operador lee el detalle zonal y la línea de tiempo y completa la Ficha
   ↓
RECOMMENDED    → CDE / SHST recomiendan; el sistema muestra la acción sugerida por la matriz
   ↓
APPROVED       → Rectorado (o delegado/suplente) decide; queda registro
   ↓
DISPATCHING    → emisión en curso
   ↓
ACTIVE
   ↓
UPDATED        → actualizaciones (pueden repetirse)
   ↓
CEASED         → cese comunicado
   ↓
CLOSED         → informe post-activación
```

**Requisitos:** 🔴 nadie puede saltar etapas sin autorización · 🔴 cada transición queda auditada · 🔴 no se emite sin audiencia, prioridad, contenido, responsable, aprobación y marca de tiempo.

El flujo sigue la cadena del protocolo: el Nodo Central abre y lee la línea de tiempo, el CDE recomienda, el Rectorado decide, se difunde por al menos tres canales independientes, se ejecuta, se cesa y se informa **[PROTOCOLO: Doc A Anexo A y §10; Doc B §7.3 F1–F4]**.

### 6.2. Conceptos que nunca deben mezclarse

| Concepto | Qué representa |
|----------|----------------|
| **Evento** | Algo detectado (SMN, manual, sensor futuro) |
| **Alerta evaluada** | Ficha completada por el operador |
| **Recomendación** | Opinión técnica del CDE / SHST |
| **Decisión aprobada** | Resolución de la autoridad |
| **Emisión** (*broadcast*) | Mensaje oficial emitido (inicial, actualización, cese, rectificación) |
| **Entrega** (*delivery*) | Un intento por persona, dispositivo/canal |
| **Confirmación** (*ack*) | Respuesta de la persona |
| **Escalamiento** | Acción ante falta de confirmación |

Estados de una entrega: `queued · sent · provider_accepted · delivered · failed · expired · acknowledged`. Cada uno se informa por separado.

### 6.3. Ficha del Alerta

La Ficha debe contener, como mínimo, los campos del **Anexo B del Documento A** y no permitir el despacho si faltan campos obligatorios **[PROTOCOLO]**:

| Campo (Doc A Anexo B) | Obligatorio |
|-----------------------|:-----------:|
| N.º de ficha / fecha y hora de recepción | 🔴 |
| Fuente (web SMN / app SMN / Defensa Civil) | 🔴 |
| Evento (alerta / advertencia / ACP) | 🔴 |
| Fenómeno | 🔴 |
| Nivel (amarillo / naranja / rojo / violeta) | 🔴 |
| Zona afectada (nomenclatura SMN) | 🔴 |
| Vigencia desde / hasta | 🔴 |
| Rangos diarios intersectados | 🔴 |
| Turnos UNS intersectados | 🔴 |
| Umbrales aplicables a la región | 🔴 |
| Eventos simultáneos en la zona (línea de tiempo) | 🔴 |
| Acción recomendada según matriz | 🔴 |
| Operador que completa | 🔴 |
| Notificados (CDE) / hora / medios utilizados | 🔴 |

**Campos adicionales requeridos por el sistema** **[PROYECTO]:** recomendación, responsable, aprobador, segundo aprobador, mensaje, audiencia, canales, estado, modo (real o simulacro). La lectura de la línea de tiempo y del detalle zonal debe quedar registrada antes de permitir avanzar.

### 6.4. Reglas del protocolo que el sistema debe implementar

| Regla | Descripción | Fuente | Prioridad |
|-------|-------------|--------|:---------:|
| **Lectura obligatoria** | Antes de decidir, abrir detalle de zona y línea de tiempo; no decidir solo por el color del mapa | Doc A §4.1, §6.3 | 🔴 Alta |
| **Eventos simultáneos** | Una zona puede tener varios alertas, advertencias y ACP vigentes; no son excluyentes. El sistema mantiene eventos independientes | Doc A §4.3 | 🔴 Alta |
| **Línea de tiempo** | Evolución a 72 h en 4 rangos diarios de 6 h (madrugada, mañana, tarde, noche) | Doc A §4.2 | 🔴 Alta |
| **Ventanas horarias de decisión** | Turno Mañana: 22:00 del día anterior · Turno Tarde: 10:00 · Turno Noche: 16:00 | Doc A §6.1 | 🔴 Alta |
| **Regla de oro** | Si el SMN emite Naranja o Roja dentro de un turno activo, la suspensión se decide y difunde antes de la hora correspondiente; vencido el horario con el fenómeno en desarrollo, la decisión pasa de «suspensión» a «confinamiento en sede» | Doc A §6.1 | 🔴 Alta |
| **Matriz por nivel** | Verde, Amarillo, Naranja (antes del corte / durante cursada), Rojo, violeta, temperaturas | Doc A §7.8 | 🔴 Alta |
| **Resguardo vs. evacuación** | Criterios de resguardo/confinamiento frente a evacuación | Doc A §7.7 | 🔴 Alta |
| **ACP** | Aviso a muy corto plazo: protocolo específico | Doc A §7.5 | 🔴 Alta |
| **Temperaturas extremas** | Protocolo específico | Doc A §7.6 | 🟡 Media |
| **Umbrales regionales** | Lluvias/tormentas, viento (sostenido/ráfagas) y otros para la región de Bahía Blanca, como **catálogo versionado** | Doc A §5 | 🔴 Alta |
| **Rutina de monitoreo** | Tareas del operador por horario, con check y observaciones | Doc A §6.2 | 🟡 Media |
| **Redundancia de difusión** | Toda decisión de suspensión, confinamiento o reanudación se difunde simultáneamente por al menos tres canales independientes | Doc A §10 | 🔴 Alta |
| **Informe post-evento** | Informe de activación | Doc A / Doc B | 🟡 Media |

**Todos los umbrales, ventanas, matrices, plantillas y roles deben ser catálogos versionados.** Cada modificación crea una nueva versión (el protocolo se gestiona con control de versiones y mejora continua, Doc A §12). **Prohibido** dejar estos valores fijos en el código.

### 6.5. Regla de dos personas

| Requisito | Prioridad |
|-----------|:---------:|
| Para alertas críticas y audiencias masivas: `Operador prepara → Responsable aprueba → Segundo responsable confirma → Despacho` | 🔴 Alta |
| El sistema **impide la emisión** si la política exige dos personas y falta la segunda aprobación | 🔴 Alta |
| Registrar usuario, rol, IP, fecha, hora, acción, contenido, versión de plantilla y versión del protocolo | 🔴 Alta |
| Qué niveles y audiencias la exigen (por ejemplo Rojo, ACP, evacuación, confinamiento masivo) lo define la UNS (D-06, D-11). Excepciones solo por procedimiento institucional explícito | 🔴 Alta |

### 6.6. Alertas manuales

El Nodo Central debe poder crear una emergencia manual. Tipos propuestos **[PROYECTO]**: puntual, general, climática, infraestructura, sanitaria, evacuación, confinamiento, comunicaciones, simulacro, otro. Los tipos deben ser un **catálogo configurable**.

### 6.7. Modo simulacro

| Requisito | Prioridad |
|-----------|:---------:|
| Existen dos modos: **PRODUCCIÓN** y **SIMULACRO** | 🔴 Alta |
| Toda notificación de simulacro está inequívocamente identificada; nunca se mezcla con una real | 🔴 Alta |
| El simulacro registra actividad, mide tiempos, entregas y confirmaciones, y genera informe | 🔴 Alta |
| Entorno seguro para probar alarma, confirmación, escalamiento, tablero, SMS, voz y canario | 🔴 Alta |

### 6.8. Respuestas rápidas

Set propuesto **[PROYECTO — validar con el CDE]**:

| Código | Texto | Quién | Uso |
|--------|-------|-------|-----|
| `RECEIVED` | «Recibido y comprendido» | Todos | Confirmación (obligatoria en T0/T1) |
| `SAFE` | «Estoy a salvo» | Todos, opcional | Estado del personal |
| `SHELTERED` | «Confinamiento cumplido» | Mayordomías, escuelas, docentes a cargo | Reporte operativo |
| `NEED_HELP` | «Necesito asistencia» | Todos | Escala al Nodo Central. Ubicación **solo** si la persona la adjunta |
| `UNAVAILABLE_ROLE` | «No puedo cumplir mi rol» | T0/T1 | Activa al suplente |

Requisitos: 🔴 respuesta con un toque desde la pantalla de alarma · 🟡 desde la notificación cuando el sistema operativo lo permita (a verificar en PoC) · 🔴 registrar `client_timestamp`, `server_timestamp`, dispositivo, usuario, alerta, emisión y respuesta · 🔴 **la marca de tiempo oficial es la del servidor**.

### 6.9. Escalamiento

El escalamiento debe ser **configurable y versionado**. Valores iniciales de referencia **[PROYECTO]**:

| Tiempo | Acción |
|--------|--------|
| T+0 | Push crítico |
| T+60 s | Reintento o canal secundario |
| T+2 min | SMS |
| T+5 min | Voz |
| T+15 min | Suplente |
| T+30 min | Reporte operativo |

Prioridad 🔴 Alta. **No se codifican estos valores.** Debe resolverse la contradicción **C-02** (sección 2.3) antes de congelarlos: el protocolo exige acuse dentro de 15 minutos y luego escalar al medio de respaldo y, de persistir, al enlace radial RACUNS del destinatario **[PROTOCOLO: Doc B §7.4.3]**.

SMS y voz dependen de la red celular; ante ECD con Pilar 2 caído no están disponibles y el sistema debe indicarlo.

### 6.10. Cese y rectificación

| Requisito | Prioridad |
|-----------|:---------:|
| **Cese (M6):** comunica la finalización de la emergencia | 🔴 Alta |
| **Rectificación:** cubre error, falsa alarma, cambio de condiciones o modificación de instrucciones (plantilla a definir: C-01) | 🔴 Alta |
| Toda comunicación puede cesarse, rectificarse, actualizarse y cerrarse; se registra quién, cuándo, por qué, qué mensaje, qué población y qué canales | 🔴 Alta |
| La rectificación **conserva el historial** y nunca sobrescribe la comunicación original | 🔴 Alta |

### 6.11. Defensa contra duplicación

| Requisito | Prioridad |
|-----------|:---------:|
| Cada alerta tiene `public_id`, identificador interno (UUID/ULID), `idempotency_key` y versión | 🔴 Alta |
| Una emisión no puede ejecutarse dos veces por doble clic, recarga, *timeout*, reintento o *worker* duplicado | 🔴 Alta |
| Todas las operaciones de emisión y de confirmación soportan clave de idempotencia | 🔴 Alta |

### 6.12. Plantillas M1–M8

Las plantillas están definidas en el **Anexo C del Documento C** **[PROTOCOLO]**. El sistema debe implementarlas como catálogo versionado, con **tres formatos por mensaje**: texto simple, versión sonora y versión visual de alto contraste (formatos accesibles, Doc C). El **contenido sustantivo, el alcance, la vigencia y las instrucciones no pueden ser modificados** por las unidades que difunden; solo se editan los campos variables.

| Código | Plantilla | Observación |
|--------|-----------|-------------|
| M1 | Preventivo (SMN Amarillo) | — |
| M2 | Suspensión (SMN Naranja/Rojo) | — |
| M3 | Evacuación | Solo por orden del CDE |
| M4 | Confinamiento (SMN Rojo) | Ver Anexo 2, observación A-5 |
| M5 | Custodia escolar (Naranja) | Módulo posterior |
| M6 | Cese (Verde) | — |
| M7 | Rumor | Ver contradicción C-01 |
| M8 | Parte prolongado | — |

---

## 7. NOTIFICACIÓN CRÍTICA

### 7.1. Requisito central

La alarma es **la función más importante del proyecto**. No se acepta como requisito «enviar una notificación push». La prueba real es la cadena completa:

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

**No se debe continuar agregando funcionalidades hasta que esta cadena funcione de forma repetible, medible y auditable** en dispositivos reales. Es la condición de la compuerta G0.

### 7.2. Android

| Requisito | Detalle | Prioridad |
|-----------|---------|:---------:|
| Capa crítica **nativa en Kotlin** | La alarma no puede depender únicamente de React Native | 🔴 Alta |
| Mensajes FCM de **datos**, prioridad alta | Procesados por el servicio de mensajería aunque la app esté cerrada | 🔴 Alta |
| Canal de notificación dedicado de alarma | Importancia alta, atributos de audio de tipo alarma | 🔴 Alta |
| Servicio en primer plano cuando corresponda | Declarar el tipo de servicio en Play Console para destinos Android 14+ | 🔴 Alta |
| Pantalla completa sobre el bloqueo (*full-screen intent*) | **Solo cuando sea legal y técnicamente viable.** Desde Android 14 el permiso no se concede por defecto a toda app: puede requerir declaración y permiso del usuario | 🔴 Alta |
| Acceso a «No Molestar» | Permiso que debe otorgar el usuario; guiar y verificar | 🔴 Alta |
| Gestión de Doze y de optimización de batería | Guías por fabricante; estado visible en la preparación | 🔴 Alta |
| Comportamiento tras reinicio | Servicio restaurado | 🔴 Alta |
| Repetición hasta confirmar | Parámetros configurables (valores de ver1: cada 30 s hasta confirmar o tiempo máximo) | 🟡 Media |
| Dispositivos sin servicios de Google | Fuera del MVP; se cubren con SMS/voz | 🟢 Baja |
| `minSdk` | A definir con datos reales de los equipos del padrón (ver1 sugiere Android 8 por canales de notificación) | 🟡 Media |

**No se asume** que todos los fabricantes se comportan igual. Fabricantes mínimos a probar: Samsung, Xiaomi/Redmi, Motorola, Google Pixel, Oppo/Realme y un equipo económico.

### 7.3. iOS

| Requisito | Detalle | Prioridad |
|-----------|---------|:---------:|
| Capa crítica **nativa en Swift** | APNs directo, UserNotifications, extensión de servicio de notificación | 🔴 Alta |
| **Critical Alerts** (camino primario) | Requiere el entitlement `com.apple.developer.usernotifications.critical-alerts`, que se solicita a Apple por formulario; el usuario además debe autorizarlo. **Solicitar desde el inicio del proyecto** | 🔴 Alta |
| **Time Sensitive** (camino secundario) | Alternativa si Apple no concede Critical Alerts | 🔴 Alta |
| **SMS** (camino terciario) y **voz automatizada** | Canales adicionales de respaldo | 🔴 Alta |
| Sonidos críticos preempaquetados | El sonido es un archivo de la app; audios por nivel y tipo de mensaje | 🔴 Alta |
| **Prohibido** PushKit/VoIP como mecanismo artificial | No se evaden restricciones de Apple | 🔴 Alta |
| Manejo de Focus y modo silencio | Documentar el comportamiento real en cada caso | 🔴 Alta |
| Distribución | Evaluar distribución no listada para app institucional; preparar cuenta de demostración para App Review **[A CONFIRMAR]** | 🟡 Media |

**Si Apple no concede Critical Alerts**, el sistema **no debe fingir** que garantiza el comportamiento. Debe:

1. registrar la limitación;
2. mostrarla en la consola;
3. informar al usuario;
4. activar los canales alternativos;
5. mantener el sistema operativo funcional;
6. documentar el nivel real de disponibilidad.

```text
Critical Alerts
      ↓
NO DISPONIBLE
      ↓
Time Sensitive + SMS + voz + procedimiento alternativo
```

### 7.4. Estado de preparación del dispositivo (*readiness*)

Cada dispositivo informa al iniciar y periódicamente. **No se registra ubicación.**

| Dato | Prioridad |
|------|:---------:|
| `platform`, `os_version`, `app_version`, `manufacturer`, `model` | 🔴 Alta |
| `push_token` (almacenado cifrado), `last_seen` | 🔴 Alta |
| `notification_permission`, `critical_alert_permission`, `do_not_disturb_permission`, `full_screen_permission` | 🔴 Alta |
| `battery_optimization`, `foreground_service`, `network` | 🔴 Alta |
| `last_alarm_test`, `last_alarm`, `last_ack` | 🟡 Media |
| `critical_ready` y estado global | 🔴 Alta |

Estados: `READY` · `DEGRADED` · `NOT_READY` · `UNKNOWN`.

La consola debe mostrar el porcentaje de preparación por nivel (T0, T1, T2, T3), por predio y por rol, y detectar:

```text
NO PREPARADO · TOKEN INVÁLIDO · APP DESACTUALIZADA · SIN PERMISO
SIN CONECTIVIDAD · NO REPORTA · CRITICAL ALERT NO APROBADO · BATERÍA NO CONFIGURADA
```

La aplicación debe mostrar al usuario una lista clara de pasos pendientes para quedar en estado `READY`.

### 7.5. Canales y respaldo

| Canal | Función | MVP | Prioridad |
|-------|---------|:---:|:---------:|
| **FCM** | Push Android (y secundario iOS) | Sí | 🔴 Alta |
| **APNs** | Push iOS (primario) | Sí | 🔴 Alta |
| **SMS** | Escalamiento y respaldo ante caída de datos | Sí | 🔴 Alta |
| **Voz automatizada** | Escalamiento a T0/T1 | Sí | 🔴 Alta |
| **Correo institucional** | Formalización y T2 | Sí | 🟡 Media |
| **Web Push** | Escritorio; **no es canal crítico en iOS** | No | 🟢 Baja |
| **Telegram** | Canal abierto / respaldo de grupos | No | 🟢 Baja |
| **Moodle, megafonía, pantallas, RACUNS** | Integraciones futuras | No | 🟢 Baja |

**WhatsApp y Telegram** figuran en el Documento B como medios «informales, sin garantía de entrega»: no pueden considerarse canal garantizado **[PROTOCOLO: Doc B §7.2]**.

### 7.6. Colas

| Requisito | Prioridad |
|-----------|:---------:|
| Colas separadas por prioridad: `critical`, `high`, `normal`, `bulk` | 🔴 Alta |
| Un envío masivo (por ejemplo correo) **nunca** debe bloquear una alerta crítica; los *workers* críticos tienen prioridad | 🔴 Alta |
| Detección y visualización de caída de FCM, APNs, SMS, voz, correo, SMN, cola y base de datos | 🔴 Alta |

### 7.7. Consola web y alarma del operador

Alarma sonora propia en la consola del Nodo Central ante una nueva alerta; notificación persistente; *Wake Lock* mientras haya una alerta activa **[PROYECTO]**. El comportamiento en cada navegador debe verificarse (Chrome, Edge, Firefox, Safari, Brave, Opera).

### 7.8. Diseño de la pantalla de alarma

Debe ser **deliberadamente simple**: qué ocurre, dónde, cuándo, qué hacer, confirmar, pedir ayuda.

```text
ALERTA UNS
NARANJA
TORMENTA SEVERA
BAHÍA BLANCA
Vigencia: (desde – hasta)

INSTRUCCIÓN:
(texto de la plantilla aprobada)

[ RECIBIDO ]   [ ESTOY A SALVO ]   [ NECESITO ASISTENCIA ]
```

Diseñar para estrés, poca iluminación, visión reducida, uso con una mano y adultos mayores. Objetivo de accesibilidad **WCAG 2.2 AA**: alto contraste, textos grandes, pictogramas (ISO 7010), lenguaje claro, no depender solo del color, soporte sonoro y lectores de pantalla **[PROTOCOLO: Doc C §Lenguaje, Formatos]**.

---

## 8. INTEGRACIÓN CON EL SMN

### 8.1. Estado de la información

| Aspecto | Estado |
|---------|--------|
| API o *feed* oficial documentado (por ejemplo CAP) para los alertas del sistema de alerta temprana | **A CONFIRMAR** — no se verificó su existencia |
| Términos de uso del sitio del SMN | **A CONFIRMAR** |
| Fuentes previstas por el protocolo | Web oficial del SMN, aplicación oficial con notificación por zona, correo (Doc B §6) **[PROTOCOLO]** |

El equipo **no debe asumir** que existe un API: debe solicitar la verificación y documentar el resultado.

### 8.2. Requisitos

| Requisito | Prioridad |
|-----------|:---------:|
| Capas separadas: `SMN → INGESTA → NORMALIZACIÓN → VALIDACIÓN → BORRADOR → EVALUACIÓN HUMANA → DECISIÓN UNS → ALERTUNS`. **No** existe el camino directo `SMN → usuarios` en el MVP | 🔴 Alta |
| Modo asistido: la ingesta genera un **borrador de alerta**; el operador verifica. No hay envío automático masivo sin decisión institucional explícita | 🔴 Alta |
| Cada captura registra: fuente, fecha y hora, estado HTTP, contenido original, **SHA-256**, parser y su versión, resultado | 🔴 Alta |
| Si el formato cambia, **no fallar en silencio**: generar `SMN SOURCE ERROR` y notificar al Nodo Central | 🔴 Alta |
| Alarma «fuente SMN sin datos» ante falta de respuesta o datos inválidos (umbral configurable) y paso a consulta manual, ya prevista por el protocolo | 🔴 Alta |
| Modelo interno compatible con CAP (evento, severidad, urgencia, certeza, área, vigencia) para futura interoperabilidad con Defensa Civil | 🟡 Media |
| Pruebas de contrato con muestras reales | 🟡 Media |
| Frecuencia de consulta configurable (distinta para ACP y el resto) | 🟡 Media |
| Gestión formal ante el SMN para un canal estructurado | 🟡 Media |

El **modo B automático** para ACP (dispararía el mensaje sin intervención del operador) **no se implementa** salvo autorización escrita del Rectorado (decisión D-07).

---

## 9. ESTADO DE COMUNICACIONES DEGRADADAS (ECD)

El ECD se **declara de forma obligatoria** cuando el operador del Nodo Central verifica la **Regla de los 2 de 3 Pilares** durante **15 minutos continuos**; antes debe ejecutar el protocolo de triangulación (la causal técnica se configura si el 70 % de los intentos fallan); se levanta cuando al menos dos pilares se restablecen y se mantienen estables **30 minutos** **[PROTOCOLO: Doc B §7.5.2 a §7.5.5]**.

| Pilar | Descripción |
|-------|-------------|
| Pilar 1 | Datos/Internet |
| Pilar 2 | Voz/SMS comercial |
| Pilar 3 | Energía de red |

**AlertUNS asiste; no declara.**

| Requisito | Prioridad |
|-----------|:---------:|
| Panel de triangulación con cronómetro y cálculo del porcentaje de fallas; el operador registra cada intento (ping interno, ping externo, llamada de control) | 🟡 Media |
| Sondas automáticas de FCM, APNs, SMS, voz y conectividad al SMN, como **evidencia** para la decisión humana | 🟡 Media |
| Asiento en libro de guardia digital, exportable a PDF para el libro físico | 🟡 Media |
| Visualización del estado por pilar (`OK` / `FAIL`) | 🟡 Media |
| Al declararse el ECD: modo mínimo que oculta canales dependientes de internet/SMS y muestra el texto estandarizado y la lista de bases a confirmar | 🟡 Media |
| El sistema **no declara automáticamente** el ECD | 🔴 Alta |

---

## 10. ARQUITECTURA DE REFERENCIA Y TECNOLOGÍA

> Esta sección fija **restricciones y una arquitectura de referencia**. El **diseño de arquitectura definitivo, el stack final y los ADR son entregables de la Fase 0** del equipo.

### 10.1. Arquitectura de referencia

```text
                         ALERTUNS
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
          ANDROID          iOS          WEB
              │             │             │
              └─────────────┼─────────────┘
                            │ HTTPS
                            ▼
                    ┌────────────────┐
                    │  API (Laravel) │  RBAC · MFA · motor de estados
                    └───────┬────────┘
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼
          MySQL       Valkey / Redis    Almacenamiento
             │          (colas)           de objetos
             └──────┬───────┘
                    ▼
               DISPATCHER (workers por canal)
        ┌───────────┼───────────────┐
        ▼           ▼               ▼
       APNs         FCM       SMS / VOZ / CORREO
        │           │               │
       iOS       Android        Respaldo
```

### 10.2. Tecnología

El criterio general es **software libre, gratuito o de código abierto**, con comunidad activa, formatos y protocolos abiertos, posibilidad de autohospedaje y de migración, y sin dependencia de un proveedor específico. Cada componente se evalúa por licencia, costo, seguridad, madurez, comunidad, mantenimiento, documentación, autohospedaje, migración y dependencia de proveedor.

| Capa | Base propuesta | Estado de la decisión | Prioridad |
|------|----------------|-----------------------|:---------:|
| Backend | PHP (versión estable soportada por el hosting) + **Laravel** (LTS vigente) | Base propuesta; ADR | 🔴 Alta |
| API | REST versionada (`/api/v1/`), documentada con **OpenAPI** | Fijo | 🔴 Alta |
| Base de datos | **MySQL 8** (Community) o **MariaDB**; sin lógica crítica que impida migrar entre motores compatibles | ADR (D-10) | 🔴 Alta |
| Cola / caché / locks | **Valkey** o **Redis**  | ADR | 🔴 Alta |
| Tiempo real | WebSockets (Laravel Reverb o equivalente) con alternativa por sondeo | ADR | 🟡 Media |
| Servidor web | **Nginx** sobre Linux (Apache si la infraestructura de la UNS lo hace más conveniente) | Propuesto | 🟡 Media |
| Contenedores | Docker o Podman cuando la infraestructura lo permita; debe poder ejecutarse sin plataforma cloud específica | Propuesto | 🟡 Media |
| Android | **Kotlin**, Android Studio, Android SDK | Fijo (capa crítica) | 🔴 Alta |
| iOS | **Swift**, Xcode | Fijo (capa crítica) | 🔴 Alta |
| UI móvil | **React Native** para navegación, formularios, estado, perfil, preparación, historial e información. **No** para la capa crítica | ADR (D-09) | 🟡 Media |
| Consola web | **React + TypeScript** o **Vue + TypeScript** | ADR en Fase 0 | 🟡 Media |
| Identidad | OIDC o SAML contra la infraestructura institucional; LDAP como alternativa | A CONFIRMAR (D-04) | 🔴 Alta |
| Código fuente | **Git** en servidor institucional  | Propuesto | 🔴 Alta |
| Monitoreo | **Prometheus**, **Grafana OSS**, **GlitchTip**, logs estructurados, autohospedados | Propuesto | 🔴 Alta |
| Almacenamiento de objetos | Autohospedado compatible con S3 (por ejemplo MinIO) cuando resulte conveniente | Propuesto | 🟢 Baja |
| Pruebas | PHPUnit/Pest, Vitest/Jest, Playwright, AndroidX Test, XCTest | Propuesto | 🔴 Alta |

> **Regla:** React Native no se asume capaz de resolver por sí solo alarmas críticas, audio especial, permisos, servicios de Android, Critical Alerts, extensiones de iOS ni el comportamiento con pantalla bloqueada. Esa capa es nativa.

### 10.3. Estructura de repositorio (monorepo institucional)

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

El repositorio es **institucional**. No debe depender de la cuenta personal de un desarrollador.

### 10.4. Independencia de proveedores e interfaces futuras

Definir una interfaz `NotificationChannel` que permita incorporar o reemplazar, **sin modificar el dominio principal**:

```text
Alert → Broadcast → Dispatcher → Channel Adapter
                                   ├── APNs
                                   ├── FCM
                                   ├── SMS (proveedor A / B)
                                   ├── Voz (proveedor A / B)
                                   ├── Correo
                                   └── Telegram
```

Dejar preparada (sin implementarla en el MVP) la interfaz `EmergencyCommunicationAdapter` para una futura integración con RACUNS. **La aplicación no debe asumir que puede controlar una radio si técnicamente no existe esa interfaz.**

| Requisito de portabilidad | Prioridad |
|---------------------------|:---------:|
| Exportación periódica de padrón y registros (evitar cautividad, Doc B §7.6) | 🔴 Alta |
| Dos caminos para iOS (APNs directo y FCM) | 🟡 Media |
| Posibilidad de dos proveedores de SMS y de voz para T0 | 🟡 Media |

### 10.5. Auditoría del hosting (obligatoria antes de desarrollar)

La UNS dispone de hosting y bases de datos, pero **sus capacidades no están documentadas**. Si el hosting es compartido y no permite *workers*, Redis/Valkey, WebSockets o procesos persistentes, **no se debe forzar la arquitectura**: se propone VPS o infraestructura equivalente.

Verificar y documentar (entregable de Fase 0):

- [ ] **Tipo de hosting** (compartido, VPS, servidor propio, virtualización)
- [ ] **CPU, RAM, SSD** disponibles
- [ ] **Sistema operativo**
- [ ] **Versión de PHP** y extensiones
- [ ] **Versión y motor de base de datos** (MySQL / MariaDB)
- [ ] **Redis / Valkey** instalable
- [ ] **Docker / Podman**
- [ ] **Acceso SSH** y privilegios
- [ ] **Cron** y **Supervisor** (procesos persistentes)
- [ ] **WebSockets** y puertos habilitados
- [ ] **TLS** (certificados) y **DNS**
- [ ] **Backups** existentes
- [ ] **Firewall / WAF**
- [ ] **IPv4 / IPv6**
- [ ] **Salida HTTPS** a FCM, APNs y a proveedores SMS/voz
- [ ] **Limitaciones** y quién opera el servidor
- [ ] **Segundo sitio** (réplica) y punto fuera de Bahía Blanca

**Punto de partida de capacidad (a verificar con pruebas de carga):** 4 vCPU, 8 GB de RAM y 100 GB de SSD por entorno productivo inicial **[PROYECTO]**.

### 10.6. Entornos

`DEV` · `STAGING` (proveedores en *sandbox*) · `PRODUCTION` · `DR`. **Nunca** se desarrolla sobre producción.

### 10.7. Alta disponibilidad y recuperación

| Requisito | Prioridad |
|-----------|:---------:|
| Arquitectura objetivo: sitio primario (Alem), espejo (Palihue) y **despachador mínimo de contingencia fuera de Bahía Blanca**, capaz de emitir la última decisión aprobada ante una caída importante | 🔴 Alta |
| Objetivos iniciales de recuperación: **RPO ≤ 5 min** y **RTO ≤ 15 min**. Son objetivos de diseño: deben confirmarlos Telecomunicaciones según la infraestructura disponible (el Doc B asigna esa definición a Telecomunicaciones) | 🔴 Alta |
| Backup diario cifrado, retención mínima de 30 días, copia independiente | 🔴 Alta |
| **Restauración probada periódicamente y registrada.** Un backup nunca restaurado no se considera validado | 🔴 Alta |
| Hoja de contingencia imprimible (contactos, procedimientos, plantillas, canales, responsables) para el caso de caída total, coherente con el libro de guardia físico | 🔴 Alta |
| Modo contingencia: ante `AlertUNS NO DISPONIBLE` se activa el procedimiento físico + radio + telefonía + SMS + otros canales | 🔴 Alta |

---

## 11. DATOS

### 11.1. Principios

| Principio | Prioridad |
|-----------|:---------:|
| **Sin `ENUM`** para dominios que pueden cambiar (roles, tipos, canales, niveles): catálogos versionados o `VARCHAR` con restricción | 🔴 Alta |
| Una persona con **varias asignaciones de rol** y **varios dispositivos** | 🔴 Alta |
| Separar claramente **decisión, emisión, entrega y confirmación** | 🔴 Alta |
| Datos sensibles cifrados a nivel de aplicación (por ejemplo DNI, tokens push) | 🔴 Alta |
| Auditoría encadenada por hash | 🔴 Alta |
| Particionado y retención para las tablas de mayor crecimiento (entregas, capturas de fuente) | 🟡 Media |

### 11.2. Entidades principales

La lista siguiente es la **referencia mínima** de los planes del proyecto. El diseño definitivo (`DATABASE_DESIGN.md`) es entregable del equipo. 

| Entidad | Propósito |
|---------|-----------|
| `persons`, `users` | Personas del padrón y cuentas de acceso |
| `roles`, `permissions`, `role_assignments`, `deputies` | RBAC con ámbito, vigencia y suplencia |
| `sites`, `buildings`, `departments` | Predios, edificios, dependencias |
| `devices`, `device_readiness` | Dispositivos y su estado de preparación |
| `alerts`, `alert_sources`, `alert_decisions` | Ficha, fuentes y pasos de decisión |
| `broadcasts`, `broadcast_audiences` | Emisiones y audiencias |
| `deliveries` | Un intento por persona, dispositivo/canal |
| `acks` | Confirmaciones |
| `escalations` | Escalamientos ejecutados |
| `templates`, `template_versions`, `protocol_versions`, `catalogs` | Plantillas, protocolo y catálogos versionados |
| `smn_snapshots` (fuentes externas) | Capturas crudas con SHA-256 |
| `audit_logs` | Cadena de auditoría |
| `channels`, `providers`, `provider_events`, `notifications` | Canales, proveedores y eventos |
| `canary_tests`, `canary_devices` | Canario |
| `simulations` | Simulacros |
| `ecd_events` | Eventos del ECD |
| `reports` | Informes |

### 11.3. Auditoría

```text
hash = SHA256(previous_hash + content)
```

Cada registro guarda actor, acción, entidad, identificador, marca de tiempo, IP, contenido, `previous_hash` y `hash`. Debe permitir demostrar **quién hizo qué, cuándo, desde dónde y con qué información**. Se recomienda conservar copia periódica del último hash fuera del sistema. Prioridad 🔴 Alta.

---

## 12. API

Base: `/api/v1/` · REST sobre HTTPS · JSON · documentada con **OpenAPI**.

| Grupo | Endpoints mínimos (referencia) | Prioridad |
|-------|--------------------------------|:---------:|
| Sesión | `/auth` (login/callback institucional, refresh) | 🔴 Alta |
| Usuarios y roles | `/users`, `/roles`, `/role-assignments`, `/people` | 🔴 Alta |
| Dispositivos | `/devices` (registro, `me`, heartbeat), `/readiness` | 🔴 Alta |
| Alertas | `/alerts`, `/alerts/{id}`, `/alerts/{id}/assess`, `/recommend`, `/approve`, `/cease` | 🔴 Alta |
| Emisiones | `/alerts/{id}/broadcasts`, `/broadcasts`, `/broadcasts/{id}`, `/broadcasts/{id}/status` | 🔴 Alta |
| Confirmaciones | `/broadcasts/{id}/ack` | 🔴 Alta |
| Entregas y escalamiento | `/deliveries`, `/escalations` | 🔴 Alta |
| Catálogos y plantillas | `/catalogs`, `/templates` | 🟡 Media |
| SMN | `/smn` | 🟡 Media |
| ECD | `/ecd` | 🟡 Media |
| Informes | `/reports`, `/reports/post-activation/{alertId}` | 🟡 Media |
| Canario y salud | `/canary`, `/canary/status`, `/health` | 🔴 Alta |

**Reglas transversales** (prioridad 🔴 Alta):

- idempotencia (`Idempotency-Key`) en emisión y confirmación;
- limitación de tasa (*rate limiting*);
- toda mutación escribe en `audit_logs`;
- la confirmación acepta `client_timestamp`, pero ordena por `server_timestamp`;
- control de acceso por rol **y** por ámbito (prevención de IDOR);
- autenticación por token de corta vida; MFA para roles críticos.

---

## 13. SEGURIDAD Y PRIVACIDAD

### 13.1. Amenazas y controles requeridos

| Amenaza | Controles mínimos | Prioridad |
|---------|-------------------|:---------:|
| **Falsa alarma o alarma maliciosa** (cuenta comprometida, uso indebido interno) | MFA; sesión corta; reautenticación en acciones críticas; control de dispositivo; **regla de dos personas**; límites por rol y audiencia; alerta cuando se emite fuera de ventana; rectificación en un clic; auditoría | 🔴 Alta |
| Suplantación de la API de envío | Credenciales en gestor de secretos; orígenes permitidos; firma de solicitudes; rotación | 🔴 Alta |
| Alteración de registros | Auditoría encadenada; copia externa del último hash | 🔴 Alta |
| Filtración de padrón, DNI o datos de menores | Cifrado en tránsito y reposo; cifrado de campos sensibles; acceso por rol; registro de accesos | 🔴 Alta |
| Ingesta envenenada (fuente alterada) | Validación de esquema; límites de cordura; confirmación humana; alarma ante fuente sin datos | 🔴 Alta |
| Abuso de la app o tokens robados | Tokens de corta vida; verificación de integridad de la app (Play Integrity / App Attest) **[A CONFIRMAR]**; limitación de tasa | 🟡 Media |
| Denegación de servicio | WAF/CDN; colas con prioridad; cola dedicada al camino crítico | 🟡 Media |
| Cautividad de proveedor | Interfaces desacopladas; doble camino; exportación de datos | 🟡 Media |
| Cadena de suministro | SBOM; análisis de dependencias; revisión de librerías de notificaciones | 🟡 Media |
| Repetición de solicitudes (*replay*), SSRF, XSS, CSRF, inyección SQL | Controles estándar; pruebas específicas | 🔴 Alta |

### 13.2. Estándares y prácticas

OWASP ASVS (backend) y OWASP MASVS (apps) como referencia · mínimo privilegio · TLS, HSTS, CSP, CORS restrictivo · validación de entrada · consultas preparadas / ORM · SAST, análisis de dependencias y DAST en el pipeline · **prueba de penetración antes de la compuerta G3** · corrección de vulnerabilidades críticas antes de producción.

**Nunca** en el repositorio: claves privadas de FCM/APNs, contraseñas de base o SMTP, claves de SMS/voz, secretos de firma. Se usan variables de entorno y/o gestor de secretos, con rotación.

### 13.3. Datos personales (Ley 25.326)

> Guía técnica. Debe validarla Asesoría Legal de la UNS.

| Requisito | Prioridad |
|-----------|:---------:|
| Finalidad única: emergencias, simulacros y pruebas (Doc B §7.4.5) | 🔴 Alta |
| Aviso y consentimiento al alta, con versión registrada | 🔴 Alta |
| **Sin geolocalización continua.** Si en el futuro se implementa ubicación: consentimiento, finalidad, retención, acceso y auditoría | 🔴 Alta |
| Retención definida por tabla (decisión D-12); simulacros con plazo distinto | 🔴 Alta |
| Procedimiento de acceso, rectificación y supresión | 🟡 Media |
| FCM y APNs procesan tokens de dispositivo fuera del país: documentar y evaluar con Legal **[A CONFIRMAR]** | 🟡 Media |
| Evaluar la inscripción de la base de datos ante la autoridad de protección de datos **[A CONFIRMAR]** | 🟡 Media |
| Datos de menores y familias (módulo escolar): acceso restringido y cifrado; solo en módulo posterior | 🟡 Media |
| Plan de respuesta a incidentes de seguridad con contactos definidos | 🟡 Media |

---

## 14. OBSERVABILIDAD Y OBJETIVOS DE SERVICIO

### 14.1. Observabilidad

Software autohospedado: **Prometheus, Grafana OSS, GlitchTip y logs estructurados**. No depender de servicios comerciales para métricas básicas.

| Métrica | Prioridad |
|---------|:---------:|
| Alertas emitidas / activas / cerradas | 🔴 Alta |
| Tiempo de despacho y de entrega; confirmaciones | 🔴 Alta |
| Fallos por canal, proveedor, fabricante y versión | 🔴 Alta |
| Tokens inválidos; dispositivos offline y no preparados | 🔴 Alta |
| SMS enviados; llamadas realizadas | 🟡 Media |
| Errores de APNs y FCM; estado del SMN | 🔴 Alta |
| Estado del backend, base de datos, Redis/Valkey, colas y *workers* | 🔴 Alta |
| Resultado del canario | 🔴 Alta |

**Alertas de monitoreo por un canal externo al propio sistema.**

### 14.2. Canario

| Requisito | Prioridad |
|-----------|:---------:|
| Dispositivos institucionales dedicados y permanentes: **mínimo 2 Android y 2 iPhone** | 🔴 Alta |
| Flujo: prueba automática → push → alarma → confirmación automática → registro | 🔴 Alta |
| Estado visible en la consola: `CANARIO OK` / `CANARIO WARNING` / `CANARIO FAILED`; si falla, **alerta operativa** | 🔴 Alta |

### 14.3. Objetivos de servicio (SLO)

Siempre distinguir **objetivo**, **medición** y **garantía**. No se afirma que una notificación móvil se entregará en X segundos como garantía absoluta: depende de los proveedores y del dispositivo.

| Indicador | Objetivo de diseño | Prioridad |
|-----------|-------------------:|:---------:|
| Disponibilidad del camino crítico | 99,9 % | 🔴 Alta |
| Aprobación → entregado al proveedor push | ≤ 30 s | 🔴 Alta |
| Confirmación T0 en 5 min | ≥ 95 % | 🔴 Alta |
| Preparación T0/T1 | ≥ 98 % | 🔴 Alta |
| Falsas emisiones masivas | 0 | 🔴 Alta |
| Éxito del canario | ≥ 99,5 % | 🟡 Media |
| Emisiones con auditoría completa | 100 % | 🔴 Alta |

Estos valores se validan con pruebas reales y pueden modificarse durante la ingeniería.

### 14.4. Informe post-emergencia e indicadores

Al cerrar una emergencia se genera automáticamente un informe con: identificador, fecha, duración, tipo, nivel, decisión, responsables, audiencias, cantidad de dispositivos, enviados, entregados, fallidos, confirmados, escalados, SMS, voz, canales, tiempos, incidentes, actualizaciones, cese y observaciones. Formatos: vista web, PDF, CSV y JSON. El protocolo prevé el informe de activación posterior al evento (Doc B §9.9; AT-02 §10) **[PROTOCOLO]**.

Indicadores a implementar (🟡 Media): porcentaje de dispositivos preparados · porcentaje de alertas entregadas · porcentaje de confirmaciones · tiempo medio de confirmación · tiempo de entrega · fallos por fabricante / proveedor / versión · alertas por predio y por nivel · cantidad de simulacros · éxito de canarios · disponibilidad · incidentes.

---

## 15. CALIDAD Y PRUEBAS

### 15.1. Estrategia

| Nivel | Qué se prueba | Prioridad |
|-------|---------------|:---------:|
| **Unitarias** | Reglas del protocolo, máquina de estados, permisos, escalamiento, plantillas, parser SMN | 🔴 Alta |
| **Integración** | API, base de datos, cola, proveedores (en *sandbox*) | 🔴 Alta |
| **Contrato** | Parser SMN con muestras reales; APNs/FCM | 🟡 Media |
| **E2E** | `crear alerta → evaluar → aprobar → enviar → recibir → confirmar → escalar → cerrar`, con dispositivos reales | 🔴 Alta |
| **Carga** | Envío masivo en ráfaga y recepción de confirmaciones en ráfaga; escalones progresivos (100, 500, 1.000, 5.000 y, si el padrón lo justifica, 10.000 usuarios/dispositivos simulados). No asumir usuarios reales hasta comprobar la infraestructura | 🔴 Alta |
| **Seguridad** | SAST, análisis de dependencias, DAST, autenticación, IDOR, XSS, CSRF, SSRF, replay, escalamiento de privilegios, exposición de secretos; penetración | 🔴 Alta |
| **Laboratorio de dispositivos** | Matriz móvil (15.2) | 🔴 Alta |
| **Canario** | Continuo | 🔴 Alta |
| **Campañas de preparación** | «Prueba de alarma» periódica a los distintos niveles | 🟡 Media |
| **Simulacros** | De mesa, de difusión masiva e integral (Doc A §11; Doc C) | 🔴 Alta |
| **Recuperación** | Caída de servicios, de canales y restauración de backup | 🔴 Alta |

**Regla de pruebas:** no se considera terminado nada que solo funcione en emulador. Se prueba con **teléfonos reales**.

La prueba de AlertUNS debe integrarse a la tabla de pruebas del Documento B (§11) y registrarse junto con la prueba radial semanal (AT-02 §7) **[PROTOCOLO: Doc B §7.6 «incorporación»; AT-02 §7]**.

### 15.2. Matriz de pruebas móviles

**Android — estados y condiciones a verificar:**

| # | Condición | Aprobado |
|---|-----------|:--------:|
| A-01 | App cerrada (deslizada) | ☐ |
| A-02 | App en segundo plano | ☐ |
| A-03 | App abierta | ☐ |
| A-04 | Pantalla bloqueada | ☐ |
| A-05 | Pantalla apagada | ☐ |
| A-06 | Modo silencio | ☐ |
| A-07 | No Molestar | ☐ |
| A-08 | Ahorro de batería | ☐ |
| A-09 | Doze | ☐ |
| A-10 | Batería muy baja | ☐ |
| A-11 | Reinicio del dispositivo | ☐ |
| A-12 | App recién instalada y permisos | ☐ |
| A-13 | Wi-Fi / 4G / 5G / pérdida de red / recuperación (la entrega tardía debe marcarse como tardía) | ☐ |
| A-14 | Volumen mínimo y máximo; vibración; repetición hasta confirmar | ☐ |
| A-15 | Auriculares y Bluetooth (comportamiento por modelo) | ☐ |
| A-16 | Permiso de acceso a No Molestar; pantalla completa denegada (flujo de guía) | ☐ |

**iOS:**

| # | Condición | Aprobado |
|---|-----------|:--------:|
| I-01 | App cerrada, bloqueada | ☐ |
| I-02 | Interruptor de silencio | ☐ |
| I-03 | Focus / No Molestar | ☐ |
| I-04 | Critical Alert (si fue aprobado por Apple) | ☐ |
| I-05 | Time Sensitive como respaldo | ☐ |
| I-06 | Permiso crítico denegado por el usuario → degradación y aviso a la consola | ☐ |
| I-07 | Low Power Mode | ☐ |
| I-08 | Wi-Fi / celular / pérdida de red | ☐ |
| I-09 | Sonido por nivel; extensión de servicio de notificación | ☐ |
| I-10 | Diferentes generaciones de iPhone | ☐ |

**Web:** Chrome, Edge, Firefox, Safari · Service Worker · Web Push · Web Audio · Wake Lock.

**Transversales:** tokens inválidos o app desinstalada · escalamiento por SMS y voz · auditoría verificable · regla de dos personas · alarma por fuente SMN sin datos · restauración de backup.

### 15.3. Laboratorio de dispositivos

| Etapa | Android | iPhone |
|-------|---------|--------|
| **Inicial (PoC)** | 6 o más: Samsung, Xiaomi/Redmi, Motorola, Pixel, Oppo/Realme y gama baja | 3 o más |
| **Ampliado** | 15–20 dispositivos en total, con distintas versiones de Android y distintas generaciones de iPhone (antiguo soportado, intermedio, actual) | |

Cada equipo se prueba en estado «limpio» y en estados «hostiles»: pantalla bloqueada, silencio, No Molestar/Focus, batería baja, ahorro energético, Wi-Fi, 4G, 5G, sin conectividad, app cerrada, app en segundo plano y tras reinicio.

| Dispositivo | SO | Estado | Resultado |
|-------------|----|--------|-----------|
| Samsung | Android | silencio | ☐ |
| Xiaomi | Android | No Molestar | ☐ |
| Motorola | Android | bloqueado | ☐ |
| Pixel | Android | batería | ☐ |
| iPhone | iOS | silencio | ☐ |
| iPhone | iOS | Focus | ☐ |

### 15.4. Criterios que bloquean una versión

**No se libera una versión si ocurre cualquiera de lo siguiente** (🔴 Alta):

- [ ] Falla la alarma crítica en los dispositivos de referencia.
- [ ] Falla la confirmación (ACK) o el escalamiento.
- [ ] Se puede emitir sin autorización, o falla la regla de dos personas.
- [ ] Se puede duplicar una alerta accidentalmente.
- [ ] La Ficha no valida campos obligatorios.
- [ ] La auditoría está incompleta o se pierde la trazabilidad.
- [ ] Falla el backup o su restauración.
- [ ] El canario falla.
- [ ] Existen vulnerabilidades críticas abiertas o secretos expuestos.
- [ ] Critical Alerts de Apple no están aprobados **y** no existe alternativa vigente.
- [ ] Android presenta fallas graves sin advertencia en el estado de preparación.
- [ ] Un proveedor push está caído sin mecanismo alternativo.
- [ ] El simulacro integral falla.

---

## 16. DEVOPS Y LICENCIAS

### 16.1. Entrega continua

```text
commit → lint → pruebas unitarias → pruebas de integración → controles de seguridad
→ build → staging → pruebas E2E → aprobación → producción
```

| Requisito | Prioridad |
|-----------|:---------:|
| Git institucional; ramas protegidas; *pull requests* con revisión de código | 🔴 Alta |
| CI/CD con SAST, análisis de dependencias, versionado semántico, *changelog* y **plan de reversión** | 🔴 Alta |
| Aplicaciones firmadas con claves custodiadas por la UNS; distribución de pruebas (TestFlight, pruebas cerradas de Play) | 🔴 Alta |
| Versión mínima de app forzable desde el servidor | 🟡 Media |
| Infraestructura como código y *runbooks* (caída de FCM/APNs, caída de SMS, falla de ingesta SMN, conmutación de sitio, restauración, rotación de claves) | 🔴 Alta |
| Congelamiento de despliegues cuando haya alerta activa o prevista de nivel crítico | 🟡 Media |

### 16.2. Control de dependencias y SBOM

Antes de incorporar cualquier dependencia:

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

Cada dependencia se registra en `docs/software-bill-of-materials.md`: nombre, versión, licencia, URL oficial, función, dependencia, riesgo y alternativa disponible. El SBOM se actualiza automáticamente en CI/CD cuando sea posible. Prioridad 🔴 Alta.

**No deben incorporarse:** frameworks comerciales, IDE comerciales, bases de datos comerciales, plataformas de monitoreo de pago, plataformas propietarias de notificaciones como dependencia única, SaaS obligatorio, servicios que bloqueen la exportación de datos, licencias por usuario o por dispositivo.

### 16.3. Desarrollo asistido por IA

Se puede usar IA para acelerar código, pruebas, documentación, análisis y migraciones. **Ningún código generado por IA entra en producción sin revisión humana y pruebas automatizadas.** Prioridad 🔴 Alta.

---

## 17. FASES DE TRABAJO Y COMPUERTAS

> **Sin plazos.** Las fases definen el **orden lógico** y las **condiciones de salida**. Pueden solaparse cuando no exista dependencia, pero **ninguna fase se da por cerrada sin cumplir su compuerta**. Los plazos se acordarán después de la Fase 0.

### 17.1. Resumen de fases

| Fase | Nombre | Objetivo | Compuerta de salida | Prioridad |
|:----:|--------|----------|:-------------------:|:---------:|
| **F0** | Viabilidad y reducción de riesgo | Demostrar que la alarma crítica es técnicamente viable y fijar la arquitectura | **G0** | 🔴 Alta |
| **F1** | Infraestructura | Entornos, repositorio, CI/CD, base, colas, backups, monitoreo | — | 🔴 Alta |
| **F2** | Backend | Núcleo de reglas, estados, RBAC, padrón, dispositivos, despacho, ACK, escalamiento, auditoría, simulacros | — | 🔴 Alta |
| **F3** | Aplicación Android | Alarma nativa, registro, preparación, confirmación, historial | — | 🔴 Alta |
| **F4** | Aplicación iOS | APNs, Critical Alerts / Time Sensitive, pantalla de alarma, confirmación | — | 🔴 Alta |
| **F5** | Consola web | Dashboard, Ficha, aprobación, emisión, tablero, cese, usuarios, auditoría, informes | **G1** | 🔴 Alta |
| **F6** | Integraciones | SMN asistido, SMS, voz, correo (otros canales no bloquean el MVP) | — | 🟡 Media |
| **F7** | Seguridad y pruebas | Unitarias, integración, carga, seguridad, laboratorio móvil, recuperación | — | 🔴 Alta |
| **F8** | Piloto | Grupos progresivos de personas reales | **G2** | 🔴 Alta |
| **F9** | Simulacro integral | Con Nodo Central, CDE, SHST, Telecomunicaciones, Infraestructura, DCI y autoridades | **G3** | 🔴 Alta |
| **F10** | Producción por niveles | T0 → T1 → T2 → T3 | **G4** | 🔴 Alta |
| **F11** | Expansión | Módulos posteriores priorizados por el CDE | — | 🟢 Baja |

> F1 a F4 pueden avanzar en paralelo una vez aprobada G0. G1 exige el circuito completo funcionando de punta a punta.

### 17.2. Fase 0 — Primera entrega solicitada

**No construir todavía toda la aplicación.** La primera entrega es:

> **Un PoC funcional de alarma crítica + arquitectura técnica + auditoría de infraestructura + matriz de licencias gratuitas + modelo de seguridad.**

La PoC debe responder una pregunta concreta:

> **¿Podemos conseguir, con las restricciones actuales de Android e iOS, una alarma institucional suficientemente confiable para el uso previsto por la UNS y cuáles son exactamente sus límites?**

Solo si la respuesta es positiva se avanza al desarrollo completo.

**Entregables de la Fase 0:**

| # | Entregable | Prioridad |
|---|------------|:---------:|
| 1 | **Informe de viabilidad** (incluye viabilidad de Android e iOS y estrategia de Critical Alerts y de respaldo) | 🔴 Alta |
| 2 | `ARCHITECTURE.md` — arquitectura propuesta | 🔴 Alta |
| 3 | `THREAT_MODEL.md` — modelo de amenazas | 🔴 Alta |
| 4 | `MVP.md` — alcance del MVP | 🔴 Alta |
| 5 | `NOTIFICATIONS.md` — diseño de notificaciones | 🔴 Alta |
| 6 | `DEVICE_READINESS.md` — estado de preparación | 🔴 Alta |
| 7 | `DATABASE_DESIGN.md` — modelo de datos | 🔴 Alta |
| 8 | `API_DESIGN.md` — contratos de API | 🟡 Media |
| 9 | `DEVOPS.md` — entornos y pipeline | 🟡 Media |
| 10 | `TEST_PLAN.md` — plan de pruebas | 🟡 Media |
| 11 | **ADR** de las decisiones tecnológicas (ver 17.4) | 🔴 Alta |
| 12 | **Auditoría de infraestructura** (sección 10.5) | 🔴 Alta |
| 13 | **Matriz de licencias** y SBOM inicial | 🔴 Alta |
| 14 | **Matriz de riesgos** actualizada | 🟡 Media |
| 15 | **PoC**: Android, iOS, APNs, FCM, alarma y ACK, con mediciones | 🔴 Alta |
| 16 | **Matriz de dispositivos** con resultados | 🔴 Alta |

**Actividades de Fase 0:**

- [ ] Crear el repositorio institucional y definir responsables.
- [ ] Auditar hosting, servidor, dominios, certificados y base de datos.
- [ ] Validar licencias de todas las tecnologías.
- [ ] Crear cuentas institucionales de **Apple Developer** y **Google Play Console** a nombre de la UNS.
- [ ] **Iniciar la solicitud del entitlement de Critical Alerts** a Apple.
- [ ] Crear proyecto Firebase y credenciales APNs institucionales.
- [ ] Probar FCM y APNs (comparar APNs directo con FCM para iOS).
- [ ] Probar la alarma con app cerrada, pantalla bloqueada, silencio y No Molestar.
- [ ] Definir la matriz de dispositivos y reunir el laboratorio inicial.
- [ ] Definir roles y política de aprobación con la UNS.
- [ ] Iniciar la consulta formal al SMN sobre un canal estructurado.

**Circuito mínimo a demostrar (resultado esperado de la primera etapa):**

```text
PRUEBA ALARMA → SERVIDOR → FCM / APNs → Android / iPhone → ALARMA → ACK → API
```

**Si esta prueba no funciona correctamente, no se debe continuar agregando funcionalidades.**

### 17.3. Compuertas

**G0 — Autoriza el desarrollo del MVP:**

- [ ] Hosting validado (o alternativa aprobada)
- [ ] Arquitectura validada
- [ ] Licencias revisadas
- [ ] Repositorio institucional
- [ ] Android PoC
- [ ] iOS PoC
- [ ] FCM probado
- [ ] APNs probado
- [ ] Alarma con app cerrada probada
- [ ] Pantalla bloqueada probada
- [ ] Silencio probado
- [ ] No Molestar probado
- [ ] Matriz de dispositivos definida
- [ ] Modelo de amenazas aprobado
- [ ] Roles definidos
- [ ] Cuentas institucionales creadas

**G1 — Circuito de punta a punta:**

```text
alerta → aprobación → emisión → recepción → ACK → escalamiento → cese → auditoría
```

- [ ] Funcionando con dispositivos reales y consola
- [ ] Canario estable
- [ ] Auditoría encadenada verificable
- [ ] Restauración de backup probada

**G2 — Piloto:**

- [ ] Simulacro de mesa con el Nodo Central usando solo AlertUNS
- [ ] Piloto con un grupo de personas (se propone progresión: 30 → 100 → 200 → grupo institucional definido)
- [ ] SMN asistido operando
- [ ] Al menos tres canales independientes en uso
- [ ] ACK y auditoría validados

**G3 — Habilita la producción:**

- [ ] **Simulacro integral exitoso**
- [ ] Ciclo de operación **en paralelo con Alerthor** cumplido (criterio a definir: D-14)
- [ ] Seguridad validada (penetración sin críticos abiertos)
- [ ] Backup restaurado
- [ ] Canario estable
- [ ] Piloto satisfactorio
- [ ] Criterios de bloqueo (15.4) en verde
- [ ] Procedimientos documentados; revisión legal cerrada

**G4 — Operación:**

- [ ] Altas por niveles completas: `T0 → T1 → T2 → T3`, **sin activación masiva sin comprobar antes la preparación**
- [ ] Manuales y capacitación entregados
- [ ] Aprobación del CDE
- [ ] Actualización documental del Documento B (§7.2, §7.3, §11)
- [ ] AlertUNS queda como plataforma institucional operativa; Alerthor permanece como respaldo mientras la UNS lo decida

### 17.4. ADR requeridos

| ADR | Tema | Prioridad |
|-----|------|:---------:|
| ADR-001 | Backend y stack | 🔴 Alta |
| ADR-002 | Notificaciones (arquitectura push) | 🔴 Alta |
| ADR-003 | iOS Critical Alerts | 🔴 Alta |
| ADR-004 | Alarma en Android | 🔴 Alta |
| ADR-005 | Autenticación e identidad | 🔴 Alta |
| ADR-006 | Base de datos | 🟡 Media |
| ADR-007 | Alta disponibilidad y recuperación | 🔴 Alta |
| ADR-008 | Integración SMN | 🟡 Media |
| ADR-009 | Mensajería y proveedores SMS/voz | 🟡 Media |
| ADR-010 | Cola y caché (Valkey/Redis) | 🟡 Media |
| ADR-011 | Framework móvil y consola web | 🟡 Media |
| ADR-012 | Escalamiento (reintentos vs. escalación del protocolo) y plantilla de rectificación | 🔴 Alta |

### 17.5. Orden de implementación (una vez aprobada G0)

```text
 1. Repositorio              12. Escalamiento
 2. Infraestructura          13. Auditoría
 3. Base de datos            14. Consola web
 4. Autenticación            15. Canario
 5. RBAC                     16. Monitoreo
 6. Dispositivos             17. Ingesta SMN
 7. Preparación (readiness)  18. Simulacro
 8. Despachador              19. Endurecimiento de seguridad
 9. Alarma Android           20. Pruebas de carga
10. Alarma iOS               21. Piloto
11. ACK                      22. Producción
```

### 17.6. Regla de desarrollo incremental

No se entregan miles de líneas de código de una sola vez. **Cada incremento** debe incluir: código · pruebas · documentación · migraciones · configuración · criterios de aceptación; y explicar qué se modificó, por qué, cómo probarlo y qué queda pendiente.

---

## 18. EQUIPO Y RESPONSABILIDADES

### 18.1. Roles del equipo de desarrollo

| Rol | Responsabilidad principal |
|-----|---------------------------|
| **Líder técnico / backend** | Arquitectura, motor de estados, seguridad de diseño, ADR |
| **Desarrollador Android (Kotlin)** | Capa nativa de alarma, FCM, permisos, fabricantes |
| **Desarrollador iOS (Swift)** | APNs, Critical Alerts / Time Sensitive, extensión de servicio |
| **Desarrollador full stack / UI móvil** | Interfaz de las apps, asistente de permisos |
| **Desarrollador web** | Consola, SSO, reportes |
| **DevOps / SRE** | Infraestructura, alta disponibilidad, observabilidad, CI/CD, canario |
| **QA con laboratorio de dispositivos** | Matriz de pruebas, campañas de preparación |
| **UX / accesibilidad** | Pantalla de alarma, WCAG, pictogramas |
| **Seguridad** (consultoría y penetración) | Modelo de amenazas, pruebas de seguridad |
| **Apoyo legal** | Ley 25.326, términos, transferencias de datos |

La dedicación de cada rol se define en el acuerdo de trabajo; **este documento no la estima**.

### 18.2. Responsables institucionales

| Responsable | Función respecto del proyecto | Origen |
|-------------|-------------------------------|--------|
| **SHST** | Responsable funcional; criterios de aceptación; simulacros | PROYECTO |
| **Telecomunicaciones** | Responsable técnico; infraestructura, contratos de SMS/voz, cuentas | PROYECTO |
| **DCI / Vocería** | Plantillas y formatos accesibles | PROTOCOLO |
| **CDE** | Aprobación del uso institucional; validación de audiencias y política de aprobación | PROTOCOLO + PROYECTO |
| **Asesoría Legal** | Protección de datos y términos | PROYECTO |

Las designaciones concretas de personas son la decisión D-01 y D-02.

---

## 19. RECURSOS Y SERVICIOS EXTERNOS

La regla de costos separa tres categorías. **No se estiman montos en este documento.** Todo costo inevitable debe ser **explícitamente aprobado por la UNS**.

| Categoría | Contenido | Objetivo |
|-----------|-----------|----------|
| **A. Software** | Linux, PHP, Laravel, MySQL/MariaDB, Valkey/Redis, Nginx, React/Vue, React Native, Kotlin, Swift, Git, GitLab CE/Gitea, Prometheus, Grafana OSS, GlitchTip, herramientas de prueba | Costo de licencia **$0** |
| **B. Servicios externos** | SMS, voz automatizada, publicación en tiendas, dominio y certificados si fueran necesarios, infraestructura cloud, servicios de terceros | Pueden tener costo; deben ser **reemplazables** |
| **C. Infraestructura** | 1) existente de la UNS; 2) servidores institucionales; 3) virtualización existente; 4) infraestructura propia; 5) cloud solo en último término | Priorizar el orden indicado |

### 19.1. Recursos a proveer o gestionar

| Recurso | Responsable sugerido | Prioridad |
|---------|----------------------|:---------:|
| Hosting/servidores e inventario de capacidades (sección 10.5) | Telecomunicaciones | 🔴 Alta |
| Repositorio Git institucional | Telecomunicaciones | 🔴 Alta |
| **Apple Developer Program** (organización UNS) y solicitud de **Critical Alerts** | Telecomunicaciones + Legal | 🔴 Alta |
| **Google Play Console** (organización UNS) | Telecomunicaciones | 🔴 Alta |
| Proyecto Firebase (FCM) y credenciales APNs institucionales | Telecomunicaciones | 🔴 Alta |
| Proveedor(es) de **SMS** y de **voz** automatizada | Telecomunicaciones / SHST | 🔴 Alta |
| Identidad institucional (OIDC/SAML/LDAP) | Servicios técnicos | 🔴 Alta |
| Dispositivos de laboratorio (15.3) y **canarios** (2 Android + 2 iPhone) | Telecomunicaciones | 🔴 Alta |
| Dominio institucional y certificados TLS | Telecomunicaciones | 🟡 Media |
| Prueba de penetración externa | UNS | 🟡 Media |
| Bot de Telegram y otros canales abiertos | DCI | 🟢 Baja |
| MDM para dispositivos T0/T1 (opcional) | Telecomunicaciones | 🟢 Baja |

### 19.2. Cuentas

Todas las cuentas (Apple, Google, Firebase, dominios, servidores, repositorios, claves de firma) deben crearse **a nombre de la UNS**, con al menos dos administradores designados. Prioridad 🔴 Alta.

---


## 20. DECISIONES Y CONSULTAS PENDIENTES

Cada decisión debe cerrarse antes de construir lo que afecta. **No se asignan fechas en este documento.**

| ID | Decisión | Opciones | Prioridad |
|----|----------|----------|:---------:|
| D-01 | Responsable funcional del proyecto | SHST (propuesto) | 🔴 Alta |
| D-02 | Responsable técnico del proyecto | Telecomunicaciones (propuesto) | 🔴 Alta |
| D-03 | Infraestructura / hosting | Servidores UNS, VPS institucional, cloud con revisión legal | 🔴 Alta |
| D-04 | Identidad institucional | OIDC, SAML, LDAP | 🔴 Alta |
| D-05 | Matriz de audiencias T0/T1/T2/T3 | Propuesta de 5.2, a validar por el CDE | 🔴 Alta |
| D-06 | Política de aprobación (niveles y audiencias que exigen dos personas) | A definir por el CDE | 🔴 Alta |
| D-07 | Política del ACP | A asistido (propuesto) / B automático por resolución / C manual | 🔴 Alta |
| D-08 | Framework móvil para la UI | React Native + módulos nativos, Flutter + plugins, nativo | 🟡 Media |
| D-9 | Motor de base de datos | MySQL Community / MariaDB | 🟡 Media |
| D-10 | Cola y caché | Valkey / Redis | 🟡 Media |
| D-11 | Retención de datos | Plazos por tabla | 🔴 Alta |
| D-12 | Política de backup y RTO/RPO | Confirmar objetivos con Telecomunicaciones | 🔴 Alta |
| D-13 | Qué cuenta como «ciclo de operación en paralelo» con Alerthor | Duración, eventos o simulacros | 🟡 Media |
| D-14 | Proveedor(es) de SMS y de voz | Uno o dos para T0 | 🔴 Alta |
| D-15 | Política de publicación móvil | Distribución pública o no listada | 🟡 Media |
| D-16 | Conjunto final de respuestas rápidas | Propuesta de 6.8, a validar por el CDE | 🟡 Media |
| D-17 | Nombre y marca institucional | «AlertUNS» u otra | 🟢 Baja |

**Consultas abiertas de este documento (no resueltas, no inventadas):** viabilidad real de cada capacidad de Android/iOS (se determina con la PoC); existencia de un API oficial del SMN; capacidades del hosting actual; tamaño real del padrón por nivel; elegibilidad de la UNS para exenciones de cuota de Apple; requisitos legales de registro de la base de datos.

---

## 21. REGLAS DE TRABAJO PARA EL EQUIPO

| Regla | Detalle | Prioridad |
|-------|---------|:---------:|
| **No inventar** | Si no se sabe, no se afirma. Una API no confirmada se marca como tal. Si una función depende de permisos, de Apple, de Google o del hosting, se indica y se solicita verificación | 🔴 Alta |
| **Fuentes oficiales** | Toda afirmación técnica sobre Android, iOS, Google Play, Apple, APNs y FCM se basa preferentemente en **documentación oficial vigente**. No se usan blogs como autoridad principal para restricciones críticas | 🔴 Alta |
| **No evadir restricciones** | Prohibidos los mecanismos no documentados para evadir restricciones del sistema operativo | 🔴 Alta |
| **Código no frágil** | Sin *hacks*, *sleeps* arbitrarios, credenciales fijas, lógica duplicada, dependencias abandonadas. Preferir código simple, modular, testeable, mantenible, observable y documentado | 🔴 Alta |
| **Señalar contradicciones** | No se ocultan. Se registran y se resuelven por ADR | 🔴 Alta |
| **Propiedad institucional** | Código, cuentas y credenciales bajo control de la UNS desde el primer día | 🔴 Alta |
| **Trabajo incremental** | Según 17.6 | 🟡 Media |
| **Documentación** | Mantener `docs/` actualizado (sección 23) | 🟡 Media |

---

## 22. ENTREGABLES FINALES

El MVP se considera terminado **únicamente** cuando existan, funcionando:

```text
Backend + Base de datos + Consola web + Android real + iPhone real
+ APNs/FCM + ACK + Escalamiento + Auditoría + Canario + Backup
+ Monitoreo + Pruebas + Documentación + Simulacro exitoso
```

### 22.1. Entrega completa

- [ ] Código fuente
- [ ] Base de datos y migraciones
- [ ] Docker / infraestructura como código si corresponde
- [ ] CI/CD
- [ ] OpenAPI
- [ ] Manual de administrador
- [ ] Manual de usuario
- [ ] Manual de operación
- [ ] Manual de contingencia
- [ ] *Runbooks*
- [ ] Modelo de amenazas
- [ ] SBOM
- [ ] Resultados de pruebas de penetración
- [ ] Resultados de pruebas
- [ ] Matriz de dispositivos
- [ ] Plan de backup
- [ ] Plan de recuperación
- [ ] Plan de actualización
- [ ] Política de logs
- [ ] Política de retención
- [ ] Documentación de Apple
- [ ] Documentación de Android

### 22.2. Documentación en el repositorio (`docs/`)

```text
architecture.md · threat-model.md · api.md · database.md · deployment.md
backup.md · disaster-recovery.md · mobile-testing.md · security.md
runbook.md · incident-response.md · protocol.md · changelog.md
software-bill-of-materials.md
```

Adicionalmente: `README.md`, `ARCHITECTURE.md`, `SECURITY.md`, `DEPLOYMENT.md`, `DISASTER_RECOVERY.md`, `API.md`, `DATABASE.md`, `MOBILE_ANDROID.md`, `MOBILE_IOS.md`, `NOTIFICATIONS.md`, `SMN_INTEGRATION.md`, `TESTING.md`, `OPERATIONS.md`, `RUNBOOK.md`, `INCIDENT_RESPONSE.md`, `PRIVACY.md`, `THREAT_MODEL.md`.

---

## 23. VERIFICACIONES EXTERNAS Y PENDIENTES

### 23.1. Verificado durante la preparación de este documento

El equipo debe **volver a verificar** estos puntos contra la documentación oficial vigente al momento de implementar.

| Tema | Resultado verificado | Fuente |
|------|----------------------|--------|
| Apple — Critical Alerts | El entitlement permite sonido con el equipo bloqueado, en silencio o con No Molestar/Focus; se solicita a Apple | https://developer.apple.com/documentation/bundleresources/entitlements/com.apple.developer.usernotifications.critical-alerts |
| Apple — foros de desarrolladores | Hay casos de solicitudes del entitlement sin respuesta durante semanas | https://developer.apple.com/forums/thread/106042 |
| Google Play — Android 14 | Declaración de servicios en primer plano y de *full-screen intent*; el permiso se concede por defecto solo a apps de llamadas o alarmas | https://support.google.com/googleplay/android-developer/answer/13392821 |
| Android (AOSP) | Límites de *full-screen intent* y verificación `canUseFullScreenIntent()` | https://source.android.com/docs/core/permissions/fsi-limits |

### 23.2. No confirmado (el equipo no debe asumirlo)

- API o *feed* oficial del SMN y sus términos de uso.
- Términos de uso de BomberBOT.
- Capacidades del hosting actual de la UNS.
- Comportamiento exacto de cada capacidad de alarma por fabricante y versión (se determina con la PoC).
- Qué acciones de respuesta permite cada sistema operativo desde la pantalla de bloqueo.
- Voz dinámica con la app cerrada en iOS.
- Versión mínima de Web Push en iPhone.
- Exención de cuota de Apple para instituciones educativas.
- Requisitos de inscripción de la base de datos.
- Existencia de difusión celular de alertas locales.
- Tamaño real del padrón por nivel.

---

## ANEXO: Glosario

| Término | Significado |
|---------|-------------|
| **ACP** | Aviso a Muy Corto Plazo |
| **ACK** | Confirmación de recepción |
| **CDE** | Comité de Dirección de la Emergencia |
| **DCI** | Dirección de Comunicación Institucional |
| **ECD** | Estado de Comunicaciones Degradadas |
| **ORAE / Nodo Central** | Oficina de Recepción de Avisos de Emergencia; en el Doc B, Nodo Central (misma función) |
| **PECl-UNS** | Protocolo de Actuación ante Emergencias de la UNS |
| **RACUNS** | Red Alternativa de Comunicaciones de la UNS |
| **SAT / SMN** | Sistema de Alerta Temprana / Servicio Meteorológico Nacional |
| **SHST** | Servicio de Higiene y Seguridad del Trabajo |
| **T0–T3** | Niveles de audiencia propuestos (sección 5.2) |
| **PoC** | Prueba de concepto |
| **ADR** | Registro de decisión de arquitectura |
| **SBOM** | Lista de materiales de software |
| **Readiness** | Estado de preparación del dispositivo para recibir una alarma crítica |


---

*Fin del documento. Todo lo marcado **[PROYECTO]** requiere validación institucional cuando así se indica, y todo lo marcado **[A CONFIRMAR]** debe verificarse antes de asumirse.*
