# PLAN DE EMERGENCIAS CLIMÁTICAS – UNS (PECl-UNS)
## DOCUMENTO MAESTRO DE DESARROLLO SEGREGADO POR COMPONENTES
**Revisión 0 – Versión 5 | Documento de trabajo de repositorio | Universidad Nacional del Sur – Bahía Blanca**

## Control de Versiones
| Rev. | Ver. | Fecha | Motivo del Cambio |
|---|---|---|---|
| 0 | 1 | 25/08/2026 | Documento inicial de la Comisión de Plan de Emergencia |
| 0 | 2 | 2026 | Revisión integral: ventanas horarias, custodia escolar, doctrina de resguardo, canales VHF |
| 0 | 3 | 05/09/2026 | Consolidado institucional: glosario SMN, umbrales, RACUNS, capas, convenios |
| 0 | 4 | 05/09/2026 | Inserción del Sistema de Difusión y Comunicación Pública |
| 0 | 5 | 08/09/2026 | Segregación en componentes A/B/C para desarrollo paralelo; backlog de desarrollos y cronograma comprometido |

| Confeccionó: | Revisó: | Aprobó: | Aprobó: |
|---|---|---|---|
| Comisión de Plan de Emergencia | Higiene, Seguridad y Gestión Ambiental | Secretaría General de Servicios Técnicos y Transformación Digital | Rectorado |

---

## 0. REGLAS DE DESARROLLO (lectura obligatoria antes de editar)

### 0.1. Arquitectura de componentes
Este documento maestro se organiza en tres componentes desarrollables en paralelo y un componente transversal de gobernanza:
- **COMPONENTE A – PROTOCOLO OPERATIVO:** lo que todo actor de la comunidad debe saber y hacer. Lidera: SHST (Guillermo Dominella) con Rectorado.
- **COMPONENTE B – ANEXO TÉCNICO (INFRAESTRUCTURA, ENERGÍA Y RACUNS):** ingeniería, infraestructura y radiocomunicaciones. Lideran: Telecomunicaciones + Laboratorio de Hidráulica (Miguel Flores / Pablo Abalo).
- **COMPONENTE C – MANUAL DE COMUNICACIÓN PÚBLICA Y VOCERÍA:** difusión, plantillas y medios. Lidera: Prensa (Marcelo Tedesco).
- **COMPONENTE D – GOBERNANZA, PLAN Y MEJORA:** roles, líneas de trabajo, cronograma, backlog y ciclo PDCA. Lidera: Rectorado / Comisión.

Al aprobarse por el Comité, cada componente se extraerá como documento oficial independiente (Documentos A, B y C); este maestro permanecerá como trazabilidad del repositorio.

### 0.2. Convención de marcado
- `[DESARROLLAR · Lx · RESPONSABLE: área]` → sección awaiting content production by the responsible specialist. Incluye el alcance mínimo esperado.
- `[PENDIENTE · RESPONSABLE: área · COMPROMISO: fecha o evento]` → insumo externo aguardado (prueba, convenio, resolución). No editar hasta cargar el insumo.
- Texto sin marcador → contenido consolidado y validado en Rev 0 v4; modificable solo con acuerdo de Comisión.

### 0.3. Reglas de edición y merge
1. Cada responsable edita exclusivamente su componente.
2. Toda modificación a la base normativa compartida (A.4 y A.5) requiere acuerdo previo de Comisión.
3. Todo merge actualiza el Control de Versiones y el Backlog (D.4).
4. Consolidación trimestral y revisión integral previa a la temporada primavera-verano.

---

## COMPONENTE A – PROTOCOLO OPERATIVO

### A.1. Objetivo
Sistematizar y coordinar las acciones institucionales de anticipación, mitigación, alerta temprana, preparación y respuesta ante eventos meteorológicos severos o extremos, a fin de proteger a la comunidad universitaria, salvaguardar el patrimonio institucional y asegurar la continuidad operativa de la UNS.
Objetivos específicos: (1) salvaguardar la vida; (2) garantizar la toma de decisiones anticipada mediante ventanas horarias; (3) estandarizar pautas de protección y confinamiento; (4) proteger infraestructura y recursos críticos; (5) asegurar la resiliencia de las comunicaciones (RACUNS); (6) fortalecer la articulación interinstitucional; (7) promover la cultura de autoprotección; (8) garantizar la mejora continua (PDCA).

### A.2. Alcance
Aplica a todos los niveles educativos dependientes de la UNS (Inicial, Primario, Secundario/Preuniversitario, Grado y Posgrado), al personal docente, nodocente, investigadores, becarios, pasantes y estudiantes, en sedes, campus, actividades extracurriculares y salidas de campo.
**[Alcance Especial]:** disposiciones de cumplimiento obligatorio para custodia, resguardo y retiro de menores en Escuelas Preuniversitarias (Escuela de Agricultura y Ganadería, Escuela Superior de Comercio, Escuela de Ciclo Básico Común e Instituto Inicial y Primario), y para población flotante y asistentes a eventos masivos en predios universitarios.

### A.3. Documentos relacionados
1. PLAN DIRECTOR DE EMERGENCIAS (UNS). 2. ANEXOS OPERATIVOS 01, 02, 03, 05 y 06. 3. Documento institucional RACUNS (noviembre 2025). 4. Ley 27.287 (SINAGIR). 5. SMN – SAT Módulos "Preguntas Frecuentes y Definiciones" y "Umbrales para los Alertas" (2.ª ed., julio 2024). 6. Plan Municipal de Gestión del Riesgo – Defensa Civil Bahía Blanca (articulación en curso).

### A.4. Base normativa: lenguaje unificado SMN–UNS
Prevalece siempre la definición oficial del SMN.

| Producto | Definición oficial | Vigencia | Actualización |
|---|---|---|---|
| Alerta meteorológico | Mensaje preventivo ante fenómenos que podrían poner en riesgo el ambiente, la vida o los bienes | 12 h; información hasta 3 días | ~06:00 y ~18:00 h (+ extraordinarias) |
| Advertencia | Niebla, ceniza, polvo o humo que dificultan la vida social | Puede persistir varios días | ~06:00 y ~18:00 h |
| ACP | Pronóstico inmediato por tormentas fuertes/severas detectadas por radar | 1, 2 o 3 horas | En cualquier momento |

| Nivel | Lema | Significado oficial |
|---|---|---|
| VERDE | Tranquilidad | Sin riesgo; también representa el cese |
| AMARILLO | Informate | Posibles fenómenos con capacidad de daño (>90 % de los alertas) |
| NARANJA | Preparate | Fenómenos peligrosos para la sociedad, la vida, los bienes (<10 %) |
| ROJO | Seguí instrucciones oficiales | Fenómenos excepcionales con potencial de desastre (≤1 %) |

- **Línea de tiempo:** 4 rangos diarios de 6 h (Madrugada 00–06 · Mañana 06–12 · Tarde 12–18 · Noche 18–00), evolución a 72 h.
- **Zonas:** lectura zonal, no política; un partido puede quedar parcialmente incluido.
- **Simultaneidad:** pueden coexistir alertas, advertencias y ACP; el mapa muestra el color más alto; es obligatorio leer el detalle y la línea de tiempo antes de decidir.
- **SAT–Temperaturas Extremas:** actualización ~19:00 h, validez 24 h; umbrales P90/P95/P99 (calor) y P10/P5/P1 (frío); efectos sobre la salud crecientes por nivel.

### A.5. Umbrales aplicables a Bahía Blanca (región Patagonia)
| Fenómeno | Amarillo | Naranja | Rojo |
|---|---|---|---|
| Lluvias / Tormentas | 15 mm/12 h ó 30 mm/24 h | 30 mm/12 h ó 60 mm/24 h | 60 mm/12 h ó 90 mm/24 h |
| Viento (sostenido/ráfagas) | 55 / 65 km/h | 75 / 90 km/h | 90 / 110 km/h |
| Zonda (ráfagas) | Z1 ≤ 65 km/h | Z2 65–90 km/h | Z3/Z4 > 90 km/h |

Notas: amarillo/naranja evalúan acumulado en 12 h (sin descartar lluvias intensas más cortas); rojo en 24 h. Umbrales dinámicos y públicos: el Nodo Central verifica su vigencia periódicamente.

### A.6. Ventanas horarias de decisión y rutina de monitoreo
| Turno | Funcionamiento | Hora de corte de decisión y difusión |
|---|---|---|
| Mañana | 06:00–12:00 | **22:00 del día anterior** |
| Tarde | 12:00–18:00 | **10:00 del mismo día** |
| Noche | 18:00–22:00 | **16:00 del mismo día** |

**Regla de oro:** si el SMN emite Alerta Naranja o Roja cuya línea de tiempo intersecta un turno activo, la suspensión se decide y difunde **antes** de la hora de corte. Vencido el corte con el fenómeno en desarrollo, la prioridad cambia de "suspensión" a "resguardo en sede".

**Rutina de lecturas del Nodo Central:** 06:00 (SAT y turno mañana) · 10:00 (corte tarde) · 16:00 (corte noche) · 18:00 (SAT) · 19:00 (temperaturas extremas) · 22:00 (corte mañana siguiente) · extraordinaria ante actualización, advertencia o ACP.

**Ficha del Alerta (Anexo 1):** obligatoria ante todo producto SAT sobre Bahía Blanca o destino de campo; incluye lectura de línea de tiempo y productos simultáneos.

### A.7. Acciones estandarizadas por nivel
**Amarillo:** difusión preventiva; prealerta a Mayordomía, Seguridad Patrimonial y Mantenimiento (generadores, motobombas, baterías VHF, sumideros); aulas con normalidad; **suspensión de toda actividad al aire libre** y de salidas de campo con destino bajo alerta.
**Naranja:** alerta por todos los canales; activación del CDE; escucha permanente en CH1; preparación de refugios internos; suspensión del turno si el alerta se conoce antes del corte; si el fenómeno irrumpe durante actividades, **Confinamiento Seguro Interno** prioritario.
**Rojo:** alerta máxima; difusión exclusiva de instrucciones de protección por Rectorado con Defensa Civil; CDE pleno en Sala de Crisis; enlace CH4 con COE; **suspensión total automática** de actividades presenciales; cierre de accesos; asistencia a personas con necesidades especiales.

**Protocolo ACP:** (1) cese inmediato de actividades y confinamiento interno; (2) no evacuar mientras el ACP esté activo sobre Bahía Blanca, salvo colapso estructural inminente; (3) al expirar o cesar, el CDE evalúa reanudación o suspensión del resto del turno.
**Advertencias (violeta):** suspensión de salidas de campo y traslados por ruta; evaluación de demora de inicio de turnos; recomendaciones de circulación.
**Temperaturas extremas (Naranja/Rojo):** antes del corte del turno mañana, el CDE evalúa suspensión con virtualidad asincrónica o continuidad con medidas de protección (hidratación, reprogramación de actividad física, climatización, asistencia a grupos de riesgo).

**Doctrina de Resguardo vs. Evacuación:**
| Condición | Acción |
|---|---|
| Amenaza externa en curso (ráfagas, granizo, actividad eléctrica) | Confinamiento interno; prohibición de salida a la vía pública |
| Peligro estructural inminente, incendio incontrolable o inundación grave | Evacuación externa controlada por orden del CDE |
| Retención durante ACP | Permanencia en sectores seguros hasta expiración o cese |

### A.8. Custodia y retiro en Escuelas Preuniversitarias
1. Mismas ventanas horarias de decisión (A.6); permanencia protegida en sectores seguros durante el horario escolar.
2. **Prohibido el retiro individual** de menores sin padre, madre o tutor legal acreditado.
3. Retiro Autorizado: notificación a familias y reporte a Base Central; presentación en acceso habilitado; verificación de DNI contra listado autorizado; asiento en Registro (Anexo 3); egreso por ruta segura; reporte final de nóminas.
4. Custodia extendida ante corte prolongado de transporte o intransitabilidad: guardia docente con provisión de agua, resguardo y comunicación telefónica/radial con Base Central.

### A.9. Nodo Central de Monitoreo 24/7
Funciona en Mayordomía San Juan 670 (BASE CENTRAL), operadores rotativos 24/365. Responsabilidades: monitoreo dual SMN/Defensa Civil en paralelo al teléfono de guardia SHST; operación continua de Base Central VHF en CH1 con libro de guardia y novedades cada 30 min en Naranja/Rojo; completado y elevación de Ficha del Alerta; despacho inmediato de novedades críticas al CDE. Energía: UPS local + acople rápido al generador móvil de 100 kVA; fuentes redundantes de consulta SAT (web, app con notificación por zona, correo).
**Protocolo de transición:** hasta la formalización presupuestaria, la guardia de Seguridad Patrimonial ejerce el monitoreo con la guardia pasiva del SHST y notificaciones automáticas a celulares designados. `[DESARROLLAR · L6 · RESPONSABLE: SHST + Telecomunicaciones]` Módulo de capacitación obligatoria del nodo de transición en lectura del SAT, criterios de escalamiento y uso de fuentes (alcance mínimo: 1 sesión práctica + guía de bolsillo).

### A.10. Organización y roles
**Comité de Dirección de la Emergencia (CDE):**
| Rol | Titular | Suplencia |
|---|---|---|
| Rectorado | Daniel Vega / Andrea S. Castellano | `[DESARROLLAR D-02]` |
| Sec. Gral. Planificación y Gestión Presupuestaria | Cintia K. Martínez | `[DESARROLLAR D-02]` |
| Dirección de Comunicación Institucional (Vocería) | Marcelo Tedesco | `[DESARROLLAR D-02]` |
| Sec. Gral. Servicios Técnicos y Transformación Digital | Walter R. Cravero | `[DESARROLLAR D-02]` |
| Subsec. Infraestructura y Servicios | Gonzalo J. Gilardi | `[DESARROLLAR D-02]` |
| Sec. Gral. Bienestar Universitario | Ana Paula Murray | `[DESARROLLAR D-02]` |
| Sec. Gral. Académica | Mariano E. Garrido | `[DESARROLLAR D-02]` |
| Jefatura SHST | Guillermo E. Dominella | `[DESARROLLAR D-02]` |
| Jefatura Medicina del Trabajo | Jorge Ignacio Frizza | `[DESARROLLAR D-02]` |
| Dirección de Sanidad | Walter Villalba | `[DESARROLLAR D-02]` |

**Sala de Crisis:** primaria Colón 80 (BASE RECTORADO); alternativa San Juan 670 (BASE CENTRAL).
**Jefes de la Emergencia:** Directores Decanos y Directores Administrativos en sus dependencias; docentes y nodocentes capacitados para guiar, identificar zonas seguras y asistir; Brigadas de Primera Intervención voluntarias.

### A.11. Procesos operativos (P1→P10)
| # | Proceso | Responsable | Entrada | Salida | Redundancia |
|---|---|---|---|---|---|
| P1 | Monitoreo 24/7 | Nodo SJ670 (Op. A) + guardia SHST (Op. B) | SAT web/app | Libro de guardia | Doble operador y doble fuente |
| P2 | Recepción y validación | Op. de guardia | Alerta/Advertencia/ACP | Ficha (Anexo 1) | Web + app + correo |
| P3 | Cruce vigencia × turnos × cortes | Op. + SHST | Ficha | Turnos intersectados | Matriz de cortes |
| P4 | Recomendación técnica | CDE (SHST eleva) | Ficha + cruce | Dictamen al Rector | Reunión presencial/virtual/WhatsApp |
| P5 | Decisión | Rector | Dictamen | Resolución | Suplente designado |
| P6 | Difusión | Vocero | Resolución | Comunicado ×3 canales | Digital → AM/FM → RACUNS → megafonía |
| P7 | Ejecución por nivel | Decanos/Directores/Mayordomías | Resolución | Acciones en predios | CH1–CH3, megáfonos |
| P8 | Custodia y resguardo | Directores de escuela/docentes | Nivel durante cursada | Menores custodiados | H-08/H-09 → Base Central; Anexo 3 |
| P9 | Cese y reanudación | Rector (sobre cese SMN) | Verde/cese | Resolución de reanudación | Mismos canales de P6 |
| P10 | Informe y mejora | SHST + Comité | Novedades | Informe 72 h | Archivo + Moodle |

Regla de lectura: secuencia P1→P9 en toda activación; P10 tras cada evento real o simulacro; P7 y P8 pueden correr en paralelo.

### A.12. Diagramas operativos
```
┌───────────────────────────────────────────────────────────┐
│                    SMN - SAT (fuente única)               │
│      Alertas 06/18 h · Temperaturas 19 h · ACP 24/7       │
└─────────────────────────────┬─────────────────────────────┘
                              ▼
              [1] MONITOREO 24/7  (SJ670 + SHST · doble operador)
                              ▼
              [2] FICHA DEL ALERTA (fenómeno·nivel·zona·desde·hasta)
                              ▼
              [3] CRUCE CON CORTES  22:00 · 10:00 · 16:00
                              ▼
              [4] CDE recomienda ──► [5] RECTOR decide
                              ▼
              [6] DIFUSIÓN MULTICANAL
                  digital │ si cae → RACUNS VHF/UHF │ AM–FM │ megafonía
                              ▼
              [7] EJECUCIÓN POR NIVEL
                  Amarillo · Naranja · Rojo · ACP (confinamiento)
                              ▼
              [8] CESE / REANUDACIÓN ──► [9] INFORME 72 h → MEJORA
```
```
Alerta Naranja/Roja o ACP durante horario escolar
        ▼
Permanencia protegida en sectores seguros │ prohibido retiro individual
        ▼
¿Adulto autorizado presente? ─ NO → custodia extendida (agua, resguardo, comunicación)
        │ SÍ
        ▼
Verificación DNI vs. listado autorizado ► firma Registro de Retiro (Anexo 3)
        ▼
Egreso por ruta segura ► reporte a Base Central (CH1 / H-08·H-09)
```

### A.13. Protocolos operativos a desarrollar
- `[DESARROLLAR · L5 · RESPONSABLE: SHST + Sec. Académica]` **D-05 Salidas de campo:** registro obligatorio 48 h previas, validación de zona destino contra SAT, equipamiento de comunicación del grupo, procedimiento de retorno/rescate.
- `[DESARROLLAR · L5 · RESPONSABLE: SHST + Extensión]` **D-06 Eventos masivos (>200 personas):** evaluación meteorológica 24 h antes, plan de confinamiento/egreso del predio, coordinación con Base Central.
- `[DESARROLLAR · L5 · RESPONSABLE: Bienestar + SHST]` **D-07 Asistencia a personas con discapacidad:** registro actualizado, personal designado y capacitado, equipamiento, señalética accesible, simulacro específico.
- `[DESARROLLAR · L5 · RESPONSABLE: Sec. Académica]` **D-09 Continuidad académica:** virtualidad asincrónica de emergencia, reprogramación de exámenes y mesas, criterios de comunicación a cátedras.
- `[DESARROLLAR · L6 · RESPONSABLE: Sanidad + Bienestar]` **D-17 Contención psicológica post-evento:** equipo profesional, seguimiento de afectados, debriefing de equipos operativos.

---

## COMPONENTE B – ANEXO TÉCNICO: INFRAESTRUCTURA, ENERGÍA Y RACUNS

### B.1. Objeto y alcance
Define la ingeniería de infraestructura crítica, respaldo energético y la Red Alternativa de Comunicaciones de la UNS (RACUNS), así como los procedimientos técnicos de prevención y recuperación edilicia. Alcance: Campus Palihue, Colón 80, Complejo Alem, San Juan/12 de Octubre, Rondeau 29, Casa de la Cultura, Escuelas Preuniversitarias y predios de interés.

### B.2. Riesgos, vulnerabilidades e infraestructura crítica
**Amenazas principales:** vientos extremos y ráfagas (voladura de cubiertas, caída de árboles y postes); tormentas severas con granizo y actividad eléctrica; precipitaciones torrenciales e inundación urbana (subsuelos, salas de máquinas, accesos); olas de calor/frío; reducción de visibilidad.

| Predio / Sede | Vulnerabilidades críticas | Directiva de prevención |
|---|---|---|
| Campus Altos de Palihue | Campo abierto a vientos SO/NO; arbolado añejo sobre sendas y estacionamientos; cubiertas livianas; anegamiento de accesos | Poda semestral; clausura de sendas arboladas en Naranja/Rojo; confinamiento en pabellones de hormigón; resguardo vehicular fuera de proyección de arbolado |
| Complejo Alem / San Juan / 12 de Octubre | Altura (San Juan 670, 7 pisos); grandes vidriados; anegamiento de subsuelos y calderas; alta densidad | Bombas y sumideros verificados; cortinas y ventanales cerrados; confinamiento en pasillos internos y plantas bajas; ascensores OFF en Rojo |
| Colón 80 / Rondeau 29 / Casa de la Cultura | Patrimonio histórico; cubiertas tradicionales; Sala de Crisis y archivos | Sellado de cubiertas y desagües; activación de Base VHF de comando; protección de archivos |
| Escuelas Preuniversitarias | Menores; dependencia de transporte y retiro de tutores; talleres y galpones (Agraria) | Protocolo de custodia (A.8); enlace handy con Base Central |

**Infraestructura crítica y respaldo:** Centro de Datos con grupo electrógeno exclusivo de 100 kVA (ATS) y UPS; generador móvil de 100 kVA próximo a San Juan 670; UPS dedicada 1–2 kVA en Mayordomía SJ670 con acometida de acople rápido; respaldo DC en repetidor Alem–BBYF (baterías 12 V AGM/Gel 100 Ah, autonomía 24–48 h); laboratorios con sustancias químicas/biológicas con protocolos ante cortes prolongados (conservación, N líquido).

### B.3. RACUNS – Red Alternativa de Comunicaciones
**B.3.1. Definición y propósito:** red autónoma VHF para conectividad institucional ante interrupción de servicios convencionales; propósito principal comunicación interna; secundario integración interinstitucional por convenios del Rectorado.
**B.3.2. Antecedentes:** temporal e inundación 07/03/2025, tornado 17/12/2023, apagón 16/06/2019 (caída simultánea de energía, celular e internet); monitoreo UNS del arroyo Napostá Grande (Unidad Remota Puente Canessa) y Complejo Alem como centro de acopio en 2025; piloto validado en Feria Gastronómica 2025 (20.000 asistentes, colapso celular, operación efectiva de handies por operadores sin experiencia).
**B.3.3. Criterio de activación:** caída verificada de telefonía celular, internet y/o energía de red + declaración de **Estado de Comunicaciones Degradadas** por el CDE, asentada en libro de guardia.
**B.3.4. Infraestructura:** repetidor VHF 50 W en Complejo Alem (edificio BBYF, torre 10 m con pararrayos y puesta a tierra, altura relativa 28 m), antena omnidireccional, duplexor y gabinete protegido; BASE CENTRAL SJ670 (24 h); BASE RECTORADO Colón 80; BASE PALIHUE; radiobases bibanda proyectadas en Colón 80, Escuelas Medias y Palihue; radiobase móvil vehicular con kit Starlink (área proveedora por resolución del CDE); flota de 12 handies bibanda con responsable por sector.
**B.3.5. Plan de canales:**
| Canal | Modo | Uso |
|---|---|---|
| CH1 | Repetidor Alem (semidúplex) | Troncal de mando y emergencia; escucha permanente en Naranja/Rojo; prohibido tráfico secundario |
| CH2 | Simplex operativo | Logística y cuadrillas; generadores; choferes |
| CH3 | Simplex local | Coordinación interna de predio |
| CH4 | Enlace | Interoperabilidad con COE Defensa Civil |
| Memorias adicionales | Simplex | Grupos operativos (mantenimiento, SHST, eléctricos, autoridades, brigadistas, logística) según Anexo Técnico de Radiocomunicaciones |
**B.3.6. Flota de handies:** H-01 SHST · H-02 Sec. Servicios Técnicos · H-03 Subsec. Infraestructura · H-04 Telecom/Data Center · H-05 Mayordomía Alem · H-06 Lab. Hidráulica · H-07 Mayordomía Palihue · H-08 Escuelas Medias · H-09 Escuela Agraria · H-10 Medicina del Trabajo · H-11 Móvil cuadrilla · H-12 Reserva/enlace COE.
**B.3.7. Metodología bibanda:** VHF principal por línea de vista; UHF secundario en interiores y rebotes; subcapa de retransmisión nodo a nodo (UHF recibido → retransmitido en VHF); handies en escucha del troncal.
**B.3.8. Arquitectura en capas:** 1 Troncal VHF · 2 Proximidad UHF · 3 Malla Meshtastic/LoRa (a incorporar) · 4 Datos Starlink móvil · 5 Difusión masiva AM UNS + FM UTN-FRBB.
**B.3.9. Disciplina radial, prueba semanal y capacitación:** indicativo del puesto en toda transmisión; mensajes breves con colación; prioridad absoluta de CH1; prueba radial semanal con reporte de ubicación, estado y batería asentado en libro de guardia y fallas informadas en 24 h; capacitación obligatoria para operadores no especializados (protocolo de enlace, brevedad, disciplina de escucha, reporte de emergencias) dictada por Telecomunicaciones con SHST.
**B.3.10. Marco regulatorio:** licencia ENACOM VHF vigente (expediente CNC 11660/1998); uso UHF en frecuencia fuera de la reserva de radioaficionados, sujeto a regularización. `[DESARROLLAR · L7 · RESPONSABLE: Telecomunicaciones]` **D-03** trámite de regularización/verificación ante ENACOM.
**B.3.11. Redundancia energética por nodo:** red → UPS/baterías 24–48 h → grupo electrógeno o paneles solares.
**B.3.12. Mantenimiento:** inspección mensual de antena y conexiones; verificación semestral de baterías y protecciones; actualización de firmware; prueba semanal. Unidad técnica: Laboratorio de Hidráulica con apoyo de Telecomunicaciones.

### B.4. Prueba de campo de radiobases
`[PENDIENTE · RESPONSABLE: Lab. Hidráulica + Telecomunicaciones (P. Abalo / M. Flores) · COMPROMISO: semana del 22/09/2026]`
**Objetivo:** validar cobertura real del repetidor Alem y de las radiobases proyectadas en Colón 80, Campus Palihue y Escuelas Medias; identificar sombras radioeléctricas y puntos de conmutación VHF/UHF; verificar tiempos de enlace y retransmisión nodo a nodo.
**Metodología mínima:** barrido por puntos fijos y móviles con registro de intensidad de señal por canal; prueba de interiores (hormigón, subsuelos); prueba de subcapa de retransmisión; prueba con energía degradada (baterías).
**Entregable esperado:** informe de cobertura con mapa de sombras, ajustes de emplazamiento/potencia y conclusiones para el Anexo Técnico de Radiocomunicaciones.
**Estado:** prueba planificada; **sin resultados cargados**. Los resultados se incorporarán aquí tras la ejecución, sin modificar el resto del componente.

### B.5. Desarrollos técnicos a producir
- `[DESARROLLAR · L4 · RESPONSABLE: Departamentos + SHST]` **D-08 Laboratorios críticos:** procedimiento de corte programado de energía, preservación de cultivos/muestras/animales, gestión de residuos peligrosos durante confinamiento prolongado.
- `[DESARROLLAR · L4 · RESPONSABLE: Infraestructura]` **D-13 Corte preventivo de gas:** procedimiento y personal habilitado para calderas y cocinas en Naranja/Rojo.
- `[DESARROLLAR · L4 · RESPONSABLE: Telecomunicaciones]` **D-14 Evaluación de ampliación de flota de handies** (cobertura de decanatos, comedor, residencias, biblioteca, polideportivo) a definir con resultados de B.4.
- `[DESARROLLAR · L3 · RESPONSABLE: Telecomunicaciones + LH]` **D-15 Piloto Meshtastic/LoRa** como capa 3 de mensajería de terreno.
- `[PENDIENTE · RESPONSABLE: CDE · COMPROMISO: resolución]` **D-16 Designación del área proveedora** de la unidad vehicular con radiobase móvil y kit Starlink.

---

## COMPONENTE C – MANUAL DE COMUNICACIÓN PÚBLICA Y VOCERÍA

### C.1. Propósito y principios
Máximo alcance efectivo (el listado de canales es mínimo, no límite); voz oficial única (Vocero Institucional sobre resolución del Rectorado e información técnica del SMN y Nodo Central); redundancia mínima de tres canales independientes; lenguaje claro y señalética universal; accesibilidad sonora y visual de alto contraste; repetición con vigencia y próxima actualización.

### C.2. Arquitectura de canales por capas
| Capa | Canales | Uso principal | Respaldo |
|---|---|---|---|
| 1 Digital | Web con banner, Moodle, correo masivo, WhatsApp/Telegram internos, redes oficiales | Suspensión anticipada, avisos, reanudación | Capa 4 Datos (Starlink) |
| 2 Radial/TV | AM UNS; FM UTN-FRBB (convenio dúplex); radios y TV locales | Alcance masivo a comunidad y familias | Receptores a batería |
| 3 Sonora/visual en predios | Megafonía, megáfonos, cartelería digital, alarmas | Aviso inmediato en el lugar | Vocería presencial de brigadistas |
| 4 Telefonía | SMS masivo, líneas de emergencia | Notificación directa | RACUNS |
| 5 RACUNS | CH1–CH3, bases y handies | Coordinación operativa y enlace DC | Capas 2–4 |
| 6 Presencial | Mayordomos, brigadistas, docentes | Confirmación en escuelas y sectores sin cobertura | — |

### C.3. Convenio dúplex AM–FM (UNS – UTN-FRBB)
En curso de establecimiento: en emergencia declarada, la FM de la UTN-FRBB transmitirá en dúplex el contenido de la AM UNS, reforzando cobertura sobre las Escuelas Medias (edificio FRBB vecino en calle 11 de Abril). Pruebas trimestrales conjuntas de transmisión.
`[DESARROLLAR · L7 · RESPONSABLE: Prensa + Telecomunicaciones]` **D-04** procedimiento operativo de enlace (quién solicita, cómo se conmuta, señal de inicio/fin, registro) y firma del convenio.

### C.4. Estructura estándar del mensaje (lenguaje claro)
Orden obligatorio: (1) fuente y hora; (2) nivel y color SMN; (3) una única acción en imperativo; (4) zona o predios; (5) vigencia; (6) próxima actualización; (7) canales oficiales. Criterios: frases cortas, voz activa, una acción por mensaje, sin tecnicismos, dato clave repetido al inicio y al final. Señalética: colores SMN + pictogramas ISO 7010 en cartelería permanente (Amarillo = informate · Naranja = preparate · Rojo = seguí instrucciones oficiales · Verde = cese).

### C.5. Biblioteca de mensajes pre-estructurados
- **M1 Preventivo Amarillo:** "Comunicado oficial UNS – [fecha], [hora]. El SMN emitió alerta AMARILLO por [fenómeno] para Bahía Blanca. Quedan suspendidas las actividades al aire libre. Las clases continúan con normalidad. Informate por canales oficiales."
- **M2 Suspensión anticipada:** "Comunicado oficial UNS – [fecha], [hora]. El SMN emitió alerta [NARANJA/ROJO] por [fenómeno]. Se suspenden las clases y actividades del turno [mañana/tarde/noche]. No concurras a los predios universitarios. Vigencia: [hasta]. Próxima actualización: [hora]."
- **M3 Confinamiento:** "Comunicado oficial UNS – [hora]. El SMN emitió aviso a muy corto plazo por tormenta severa. Permanecé dentro del edificio en el que estás. No salgas. Alejarse de ventanas y seguir las indicaciones del personal. Nueva información en [30 minutos / al cese]."
- **M4 Custodia escolar:** "Comunicado oficial UNS – [hora]. Por la alerta vigente, los alumnos permanecen en la escuela, cuidados por el personal. El retiro se realiza únicamente por padre, madre o tutor con DNI, por el acceso principal. No envíe menores solos."
- **M5 Reanudación/cese:** "Comunicado oficial UNS – [fecha], [hora]. El SMN cesó el alerta para Bahía Blanca. Las actividades se reanudan a partir del turno [turno/hora]. Consultá canales oficiales ante dudas."

### C.6. Matriz de difusión mínima por nivel
| Nivel / situación | Canales mínimos simultáneos | Repetición |
|---|---|---|
| Amarillo | Web + Moodle + correo + redes + cartelería | Una emisión + recordatorio en cada corte |
| Naranja (suspensión anticipada) | Digitales + AM + FM FRBB + SMS + megafonía | Al decidir + cada 30 min |
| Rojo | Anteriores + alarmas + confirmación presencial en escuelas | Cada 30 min hasta el cese |
| ACP durante cursada | Megafonía + WhatsApp interno + AM/FM + pantallas | Inmediata + cada 30 min |
| Cese / reanudación | Mismos canales de la suspensión | Una emisión + confirmación a escuelas |

### C.7. Pruebas e indicadores
Prueba trimestral de difusión masiva con verificación de recepción en predios y escuelas. Indicadores: tiempo decisión→difusión (antes del corte); cobertura de canales efectivos; confirmación en escuelas al 100 %. Fallas registradas al ciclo PDCA (D.7).

### C.8. Desarrollos de comunicación a producir
- `[DESARROLLAR · L6 · RESPONSABLE: Prensa + Infraestructura]` **D-11 Plan de señalética y cartelería ISO 7010** por predio (formatos, ubicaciones, versiones accesibles).
- `[DESARROLLAR · L3 · RESPONSABLE: Prensa]` **D-12 Procedimiento de comunicación de crisis:** sala de prensa, gestión de rumores en redes, protocolo de comunicación con familias de víctimas, vocería única en terreno.

---

## COMPONENTE D – GOBERNANZA, PLAN Y MEJORA

### D.1. Marco
Gestión bajo ciclo PDCA alineada a ISO 22320 (gestión de emergencias), ISO 22301 (continuidad operativa) y Ley 27.287 (SINAGIR). Articulación permanente con Defensa Civil mediante telefonía de guardia y CH4; intercambio dinámico de información; puesta a disposición de instalaciones verificadas (gimnasios, comedores, aulas magnas) como acopio o apoyo logístico en catástrofes; convenios suscriptos por el Rectorado (UTN-FRBB, Radioclub, Defensa Civil, Municipio).

### D.2. Líneas de trabajo
| Línea | Objetivo | Responsable | Entregables | Indicador |
|---|---|---|---|---|
| L1 Gobernanza | Normativa, roles y suplentes | Rectorado / Sec. General | Resoluciones; sala primaria/alterna | 100 % roles con suplente |
| L2 Monitoreo y decisión | Nodo 24/7 y matriz de cortes | SHST + Telecomunicaciones | Nodo transitorio→oficina; fichas; libro | Detección→ficha < 15 min |
| L3 Comunicaciones | Difusión multicapa y RACUNS | Prensa + Telecom. + LH | Plan de canales; capas 1–5; convenio AM/FM | Prueba radial 100 % |
| L4 Infraestructura y energía | Predios seguros y autónomos | Infraestructura + LH | Poda; pluviales; ATS; triple energía | Checklist sin observaciones |
| L5 Custodia educativa y protocolos operativos | Menores, vulnerables, campo, eventos | Sec. Académica + Escuelas + Bienestar + SHST | Protocolos D-05 a D-09 | Simulacro por cuatrimestre |
| L6 Capacitación y ejercicios | Cultura de autoprotección | SHST + Prensa | Moodle; simulacros; informe 72 h | 1 ejercicio por cuatrimestre |
| L7 Convenios y regulatorio | Articulación externa y ENACOM | Rectorado + Telecomunicaciones | Convenios firmados; UHF regularizado | Convenios ejercitados |

### D.3. Cronograma comprometido (sujeto a confirmación del Comité)
| Hito | Fecha | Entregable | Responsable |
|---|---|---|---|
| Reunión de segregación (Zoom) | Mié 10/09/2026 | Acuerdo de arquitectura y responsables | Comisión |
| Borrador Componente A | Vie 19/09/2026 | Documento operativo circulado | SHST |
| Prueba de campo RACUNS | Semana del 22/09/2026 | Ejecución (informe posterior) | LH + Telecomunicaciones |
| Borrador Componente B | Vie 03/10/2026 | Documento técnico con resultados de prueba | Telecomunicaciones + LH |
| Borrador Componente C | Vie 10/10/2026 | Manual de comunicación | Prensa |
| Reunión de consolidación | Semana del 13/10/2026 | Tres componentes listos | Comisión |
| Aprobación por Resolución | Antes del 31/10/2026 | PECl-UNS oficial | Rectorado |

### D.4. Backlog maestro de desarrollos
| ID | Desarrollo | Comp. | Línea | Responsable | Prioridad | Estado |
|---|---|---|---|---|---|---|
| D-01 | Prueba de campo de radiobases (Colón 80, Palihue, Escuelas) | B | L3/L4 | LH + Telecomunicaciones | Alta | Planificada (sin resultados) |
| D-02 | Nombramiento de suplentes del CDE | A/D | L1 | Rectorado | Crítica | Inmediato |
| D-03 | Regularización UHF ante ENACOM | B | L7 | Telecomunicaciones | Alta | Mediano plazo |
| D-04 | Convenio AM–FM UTN-FRBB: firma + procedimiento + pruebas | C | L7 | Rectorado + Prensa + Telecom. | Alta | En curso |
| D-05 | Protocolo de salidas de campo | A | L5 | SHST + Sec. Académica | Crítica | A desarrollar |
| D-06 | Protocolo de eventos masivos (>200 personas) | A | L5 | SHST + Extensión | Alta | A desarrollar |
| D-07 | Protocolo de asistencia a personas con discapacidad | A | L5 | Bienestar + SHST | Crítica | A desarrollar |
| D-08 | Protocolo de laboratorios críticos | B | L4 | Departamentos + SHST | Media-alta | A desarrollar |
| D-09 | Continuidad académica de emergencia | A | L5 | Sec. Académica | Media-alta | A desarrollar |
| D-10 | Capacitación del nodo de transición (Seguridad Patrimonial) | A/B | L6 | SHST + Telecomunicaciones | Alta | Corto plazo |
| D-11 | Plan de señalética y cartelería ISO 7010 | C | L6 | Prensa + Infraestructura | Media | A desarrollar |
| D-12 | Procedimiento de comunicación de crisis | C | L3 | Prensa | Media-alta | A desarrollar |
| D-13 | Corte preventivo de gas | B | L4 | Infraestructura | Alta | A desarrollar |
| D-14 | Evaluación de ampliación de flota de handies | B | L4 | Telecomunicaciones | Media | Post D-01 |
| D-15 | Piloto Meshtastic/LoRa | B | L3 | Telecomunicaciones + LH | Media | Mediano plazo |
| D-16 | Designación de unidad móvil (vehículo + Starlink) | B/D | L1 | CDE | Media | Pendiente resolución |
| D-17 | Contención psicológica post-evento | A/D | L6 | Sanidad + Bienestar | Media | A desarrollar |
| D-18 | Gestión de seguros y denuncia de siniestros | D | L1 | Administración / Legal | Baja-media | A desarrollar |

### D.5. Prevención, capacitación y concientización
Plan anual de poda preventiva de arbolado (previo a primavera-verano); mantenimiento programado de pluviales y cubiertas; pruebas bajo carga de generadores (ATS) y motobombas; capacitación por roles y charlas de ingreso; instrucción práctica en comunicaciones VHF; simulacros de mesa trimestrales, integral anual y post-activación real; módulo Moodle de autoprotección con cartografía de zonas seguras.

### D.6. Mejora continua
Informe post-activación en 72 h (SHST) con lecciones aprendidas; indicadores: detección→ficha, decisión→difusión antes del corte, prueba radial semanal, cumplimiento de simulacros, observaciones cerradas; control de versiones obligatorio; interpretación divergente solo la aclaran Nodo Central y SHST.

---

## ANEXOS COMPARTIDOS

### Anexo 1 – Ficha del Alerta (plantilla)
| Campo | Contenido |
|---|---|
| N.º de ficha / Fecha y hora de recepción | |
| Fuente (web SMN / app SMN / Defensa Civil) | |
| Producto (Alerta / Advertencia / ACP) | |
| Fenómeno | |
| Nivel (amarillo / naranja / rojo / violeta) | |
| Zona afectada (nomenclatura SMN) | |
| Vigencia Desde / Hasta | |
| Rangos diarios intersectados | |
| Turnos UNS intersectados | |
| Umbrales aplicables (A.5) | |
| Productos simultáneos (línea de tiempo) | |
| Acción recomendada según matriz (A.7) | |
| Operador que completa | |
| Notificados (CDE) / Hora / Medios | |

### Anexo 2 – Diagrama técnico detallado (operativo)
```
SMN SAT ─(06h/18h; 19h temp; ACP cualquier hora)─► [NODO 24/7 SJ670]
    Op.A Mayordomía │ Op.B SHST (redundancia de personas)
                            │
                            ▼
    ¿Alerta/Advertencia/ACP para Bahía Blanca o destino de campo?
         │NO → registro y seguimiento
         │SÍ
         ▼
    [FICHA] ──notificación inmediata al CDE──► (WhatsApp inst. + tel. + CH1)
         │
         ├── ¿ACP vigente DURANTE cursada? ──SÍ──► [CONFINAMIENTO]
         │        (no evacuar; alejar de vidrios; docentes retienen)
         │        └─ expira ACP / cese SMN ─► reanuda o P9
         ▼
    ¿NIVEL?
    ├─ AMARILLO → suspende exteriores/campo; aulas normales;
    │             prealerta Mantenimiento; difusión preventiva
    ├─ NARANJA / ROJO → ¿ANTES del corte del turno?
    │        ├─ SÍ → CDE recomienda ► RECTOR suspende turno
    │        │       ► difusión x3 canales (repetir a los 30 min)
    │        └─ NO (durante cursada) → [CONFINAMIENTO]
    │                 └─ ¿riesgo estructural / incendio / inundación grave?
    │                       ├─ NO → mantener confinamiento hasta cese SMN
    │                       └─ SÍ → EVACUACIÓN EXTERNA controlada
    │                                (CH1 interno + CH4 Defensa Civil)
    ▼
    [EJECUCIÓN PARALELA]
    · ESCUELAS: custodia estricta; sin retiro individual de menores (H-08/H-09)
    · INFRAESTRUCTURA: generadores ATS, motobombas, cortinas, ascensores OFF (Rojo)
    · COMUNICACIONES: ¿medios tradicionales caídos? ──SÍ──► DECLARA
      "ESTADO DE COMUNICACIONES DEGRADADAS" ► activa RACUNS (capas 1→5)
    ▼
    [CESE SMN] ► RECTOR reanuda ► [INFORME 72 h] ► lecciones ► mejora del plan
```

### Anexo 3 – Registro de Retiro Autorizado (plantilla escuelas)
| Fecha | Hora | Alumno | Adulto que retira | DNI | Vínculo | Firma | Observaciones |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

---
