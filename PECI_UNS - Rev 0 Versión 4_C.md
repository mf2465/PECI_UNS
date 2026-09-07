# ANEXO OPERATIVO 07-C – MANUAL DE COMUNICACIÓN PÚBLICA Y VOCERÍA (PECl-UNS)

## DOCUMENTO C – COMUNICACIÓN

**Revisión 0 – Versión 1 (Consolidado Institucional 2026)**
**Universidad Nacional del Sur – Bahía Blanca**

## Control de Versiones del Documento

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Segregación del PECl-UNS Rev 0 V4: contenido de comunicación pública, vocería y difusión (Documento C) |

*El presente documento integra el contenido de comunicación pública y vocería del protocolo. Los aspectos operativos de decisión y custodia se rigen por el Documento A (Protocolo Operativo); los aspectos de infraestructura, energía e ingeniería de radiocomunicaciones se rigen por el Documento B (Anexo Técnico RACUNS).*

## 1. OBJETO Y ALCANCE

### 1.1. Objeto

Definir los principios, la organización, los canales, los formatos de mensaje y los procedimientos de comunicación pública e interna de la UNS ante emergencias meteorológicas, garantizando que toda la comunidad universitaria y la población de Bahía Blanca reciban información oficial oportuna, veraz, clara y accesible, emitida por una única voz institucional.

### 1.2. Alcance y destinatarios

Este documento es de uso obligatorio para: Dirección de Comunicación Institucional (Vocería), community managers y equipos de redes sociales, diseñadores gráficos, operadores de Radio AM UNS, responsables de web y Moodle (en coordinación con Telecomunicaciones), y enlaces de comunicación de las Escuelas Preuniversitarias. Audiencias alcanzadas: estudiantes, docentes, nodocentes, familias de alumnos de escuelas preuniversitarias, proveedores y contratistas en predios, medios de comunicación y población general.

### 1.3. Documentos relacionados

1. DOCUMENTO A – PROTOCOLO OPERATIVO DE EMERGENCIAS METEOROLÓGICAS (PECl-UNS).
2. DOCUMENTO B – ANEXO TÉCNICO DE INFRAESTRUCTURA Y COMUNICACIONES (RACUNS).
3. PLAN DIRECTOR DE EMERGENCIAS (UNS) y ANEXO OPERATIVO 01 – PLAN DE COMUNICACIONES DE EMERGENCIA.
4. SMN – SAT MÓDULO "PREGUNTAS FRECUENTES Y DEFINICIONES" (2.ª edición, julio 2024).
5. PLAN NACIONAL DE LENGUAJE CLARO (criterios de redacción).
6. NORMA ISO 7010 (símbolos y señales de seguridad).

## 2. PRINCIPIOS RECTORES DE LA COMUNICACIÓN DE EMERGENCIA

1. **Voz oficial única:** toda comunicación de emergencia será emitida exclusivamente por el Vocero Institucional, sobre la base de la resolución del Rectorado y la información técnica del SMN y del Nodo Central. Ningún otro miembro de la comunidad emitirá declaraciones en nombre de la UNS durante una emergencia.
2. **Máximo alcance efectivo:** la Vocería adoptará en cada situación los medios que resulten más efectivos para la difusión de la novedad, ya sean digitales, radiales, audiovisuales, redes sociales, sonoros, gráficos o cualquier otro que garantice que la información llegue a toda la comunidad en tiempo oportuno. El listado de canales de este manual constituye un mínimo obligatorio, no un límite.
3. **Redundancia:** toda decisión (suspensión, confinamiento, reanudación) se difundirá en forma simultánea por al menos tres canales independientes entre sí (Sección 8).
4. **Lenguaje claro y señaletica universal:** los mensajes se redactarán conforme a los criterios del Plan Nacional de Lenguaje Claro y se acompañarán con pictogramas universales (Secciones 6 y Anexo B).
5. **Accesibilidad:** toda novedad crítica contará con versión sonora (radio, megafonía) y versión visual de alto contraste (pantallas, redes, cartelería), para personas con discapacidad visual o auditiva.
6. **Repetición y vigencia:** todo mensaje indicará hora de emisión, vigencia y hora de la próxima actualización; se repetirá según la matriz del punto 8.
7. **Veracidad y gestión de rumores:** no se difundirá información no verificada; ante ausencia de datos confirmados se informará expresamente que no hay información confirmada y se indicará la hora del próximo parte; todo rumor detectado será desmentido por canal oficial dentro de los 60 minutos de su detección (plantilla M6).

## 3. ORGANIZACIÓN Y ROLES DE COMUNICACIÓN

### 3.1. Vocero Institucional

El Director de Comunicación Institucional ejerce la Vocería Institucional y es la única voz autorizada. Su suplencia se designa conforme al mecanismo de suplentes del Comité de Dirección de la Emergencia (Documento A, Sección 10.1). Durante una emergencia, el Vocero integra la Sala de Crisis (primaria Colón 80 / alternativa San Juan 670).

### 3.2. Equipo de Comunicación de Emergencia

1. Community managers: operación de redes sociales oficiales, monitoreo de rumores y fijado de publicaciones oficiales.
2. Diseñadores: producción de piezas gráficas, cartelería y pictogramas conforme al Anexo B.
3. Operadores de Radio AM UNS: emisión de comunicados y partes; enlace técnico con la FM UTN-FRBB (Sección 5).
4. Responsables de web y Moodle: banner institucional, avisos destacados y estado de servicios (en coordinación con Telecomunicaciones).
5. Enlaces de comunicación de Escuelas Preuniversitarias: difusión a familias y confirmación de recepción (en coordinación con los establecimientos).

### 3.3. Insumos y flujo de entrada

La Vocería solo emite sobre la base de: (1) resolución del Rectorado; (2) Ficha del Alerta completada por el Nodo Central (Documento A, Anexo B); (3) directivas del CDE. El flujo completo de difusión se representa en el Anexo E.

### 3.4. Sala de prensa

Durante emergencias con impacto público prolongado, se habilitará sala de prensa en la Sala de Crisis activa, con registro de medios acreditados (Anexo D) y partes de prensa a horarios fijos (Sección 9.2).

## 4. ARQUITECTURA DE CANALES POR CAPAS

| Capa | Canales | Uso principal | Respaldo ante caída |
| --- | --- | --- | --- |
| 1 – Digital institucional | Web con banner, Moodle, correo masivo, WhatsApp/Telegram de públicos internos, redes sociales oficiales | Suspensión anticipada, avisos y reanudación | Capa 4 – Datos (Starlink) de RACUNS (Documento B) para emisión web |
| 2 – Radial y televisiva | Radio AM UNS; FM UTN-FRBB (convenio dúplex); radios y TV locales de Bahía Blanca | Alcance masivo a la comunidad y familias | Receptores a batería/pila |
| 3 – Sonora/visual en predios | Megafonía y megáfonos de mayordomías, cartelería digital y pantallas, alarmas | Aviso inmediato en el lugar | Vocería presencial de brigadistas |
| 4 – Telefonía | SMS masivo, líneas de emergencia | Notificación directa al celular | RACUNS para coordinación interna |
| 5 – RACUNS | CH1–CH3, Bases y handies (Documento B) | Coordinación operativa y enlace con Defensa Civil | Capas 2–4 |
| 6 – Presencial | Mayordomos, brigadistas, docentes capacitados | Confirmación en escuelas y sectores sin cobertura | — |

### 4.1. Reglas de uso por capa

1. La Capa 5 (RACUNS) es un canal de coordinación operativa interna y enlace interinstitucional; no se utiliza para difusión pública ni masiva.
2. Toda emisión por Capa 2 (radio) utilizará exclusivamente las plantillas M1–M7 leídas por el Vocero o por operador autorizado con texto aprobado.
3. La Capa 3 se activa en forma inmediata ante ACP o confinamiento, sin esperar la emisión digital.
4. La Capa 6 es obligatoria para confirmación de recepción en Escuelas Preuniversitarias en niveles Naranja y Rojo.

## 5. CONVENIO DE TRANSMISIÓN DÚPLEX AM–FM (UNS – UTN-FRBB)

### 5.1. Objeto y estado

Se encuentra en curso de establecimiento un convenio de colaboración con la Universidad Tecnológica Nacional – Facultad Regional Bahía Blanca, en virtud del cual, en situaciones de emergencia declarada, la emisora FM de la UTN-FRBB transmitirá en dúplex el contenido y los comunicados oficiales de la Radio AM de la UNS, ampliando el alcance radial de la voz oficial universitaria. El edificio de la FRBB, vecino a las Escuelas Medias en calle 11 de Abril, refuerza la cobertura sobre la población escolar y sus familias.

### 5.2. Procedimiento operativo de enlace

1. Declarada la emergencia por el CDE, el Vocero solicita al Nodo Central la activación del enlace AM–FM.
2. El operador de Radio AM UNS contacta al responsable de turno de la FM UTN-FRBB por teléfono institucional y, como respaldo, por CH4 o el medio disponible.
3. La FM UTN-FRBB toma la señal de la AM UNS en dúplex durante el período que fije el Vocero; cada transmisión abre y cierra con identificación de ambas emisoras.
4. Finalizada la emergencia, el Vocero comunica el cese de la transmisión en dúplex y lo asienta en el Registro de Difusión (Anexo C).
5. La Vocería y la Dirección de Telecomunicaciones realizarán pruebas trimestrales de transmisión conjunta, con registro de resultado.

### 5.3. Plan de contingencia del enlace

Si el convenio no estuviera vigente o la FM UTN-FRBB no estuviera disponible, la Vocería activará en sustitución la coordinación con radios locales y comunitarias de Bahía Blanca previamente relevadas, manteniendo la AM UNS como emisora oficial primaria; la sustitución se registrará en el Registro de Difusión.

## 6. ESTRUCTURA ESTÁNDAR DEL MENSAJE (LENGUAJE CLARO)

### 6.1. Orden obligatorio del contenido

Todo mensaje de emergencia contendrá, en este orden: (1) fuente y hora; (2) nivel y color según SMN; (3) una única acción en verbo imperativo; (4) zona o predios alcanzados; (5) vigencia; (6) hora de próxima actualización; (7) canales oficiales de consulta.

### 6.2. Criterios de redacción

Frases cortas; voz activa; una acción por mensaje; sin tecnicismos; dato clave repetido al inicio y al final; sin especulaciones ni probabilidades; uso de los lemas oficiales del SMN (informate / preparate / seguí instrucciones oficiales / tranquilidad).

### 6.3. Señaletica universal

Se emplearán los colores oficiales del SMN y pictogramas de seguridad conforme ISO 7010, en cartelería permanente en accesos, aulas y pasillos: Amarillo = informate · Naranja = preparate · Rojo = seguí instrucciones oficiales · Verde = tranquilidad/cese. Los formatos y ubicaciones se detallan en el Anexo B.

### 6.4. Formatos accesibles

1. Versión sonora: radio AM/FM, megafonía de predios y mensajes de voz en líneas de emergencia.
2. Versión visual de alto contraste: pantallas, redes y cartelería con tipografía grande y fondo contrastado.
3. Versión textual simple: texto plano en web, Moodle, correo y SMS, sin imágenes obligatorias para comprender el mensaje.
4. Videos y piezas audiovisuales con subtítulos; intérprete de lengua de señas cuando la duración de la emergencia lo permita.

## 7. BIBLIOTECA DE MENSAJES PRE-ESTRUCTURADOS (PLANTILLAS)

**M1 – Preventivo Amarillo:** "Comunicado oficial UNS – [fecha], [hora]. El SMN emitió alerta AMARILLO por [fenómeno] para Bahía Blanca. Quedan suspendidas las actividades al aire libre. Las clases continúan con normalidad. Informate por canales oficiales."

**M2 – Suspensión anticipada de turno:** "Comunicado oficial UNS – [fecha], [hora]. El SMN emitió alerta [NARANJA/ROJO] por [fenómeno]. Se suspenden las clases y actividades del turno [mañana/tarde/noche]. No concurras a los predios universitarios. Vigencia: [hasta]. Próxima actualización: [hora]."

**M3 – Confinamiento durante cursada:** "Comunicado oficial UNS – [hora]. El SMN emitió aviso a muy corto plazo por tormenta severa. Permanecé dentro del edificio en el que estás. No salgas. Alejarse de ventanas y seguir las indicaciones del personal. Nueva información en [30 minutos / al cese del aviso]."

**M4 – Custodia escolar y retiro autorizado:** "Comunicado oficial UNS – [hora]. Por la alerta vigente, los alumnos permanecen en la escuela, cuidados por el personal. El retiro se realiza únicamente por padre, madre o tutor con DNI, por el acceso principal. No envíe menores solos."

**M5 – Reanudación / cese:** "Comunicado oficial UNS – [fecha], [hora]. El SMN cesó el alerta para Bahía Blanca. Las actividades se reanudan a partir del turno [turno/hora]. Consultá canales oficiales ante dudas."

**M6 – Desmentida de rumor:** "Comunicado oficial UNS – [fecha], [hora]. Es FALSO que [rumor detectado]. La única información válida es la de los canales oficiales: [canales]. Dato verificado: [información confirmada]."

**M7 – Parte de situación en evento prolongado:** "Comunicado oficial UNS – Parte N.º [n] – [hora]. [Estado actual del fenómeno y de los predios]. Servicios disponibles: [comedores, refugios, retiro escolar]. Próximo parte: [hora]."

## 8. MATRIZ DE DIFUSIÓN MÍNIMA POR NIVEL

| Nivel / situación | Plantilla | Canales mínimos simultáneos | Repetición |
| --- | --- | --- | --- |
| Amarillo | M1 | Web + Moodle + correo + redes + cartelería en predios | Una emisión + recordatorio en cada hora de corte |
| Naranja (suspensión anticipada) | M2 | Todos los digitales + AM UNS + FM UTN-FRBB + SMS + megafonía de mayordomías | Al decidir + cada 30 min mientras dure el evento |
| Rojo | M2 / M3 | Todos los anteriores + alarmas en predios + confirmación presencial en escuelas | Cada 30 min hasta el cese |
| ACP durante cursada | M3 | Megafonía + WhatsApp interno + AM/FM + pantallas | Inmediata + cada 30 min |
| Custodia escolar | M4 | Canales del nivel vigente + enlaces de escuelas + confirmación presencial | Al decidir + ante cada cambio de estado |
| Evento prolongado (>2 h) | M7 | Canales del nivel vigente | Cada 60 min como parte de situación |
| Rumor detectado | M6 | Canal donde circula el rumor + canales oficiales | Inmediata + verificación a los 60 min |
| Cese / reanudación | M5 | Mismos canales del comunicado de suspensión | Una emisión + confirmación a escuelas |

## 9. PROTOCOLO DE COMUNICACIÓN DE CRISIS

### 9.1. Activación y organización

Declarada la emergencia por el CDE, el Vocero activa el Equipo de Comunicación de Emergencia, constituye la sala de prensa (3.4) y centraliza toda emisión. Durante nivel Rojo o eventos prolongados, se emitirán partes de prensa a horarios fijos anunciados en el propio parte.

### 9.2. Relación con medios de comunicación

1. Solo el Vocero brinda declaraciones; los medios se atienden en sala de prensa o por los contactos del Anexo D.
2. No se especula: ante pregunta sin respuesta confirmada se declara "no hay información confirmada en este momento; el próximo parte será a las [hora]".
3. Se prioriza la difusión de acciones de protección por sobre el detalle técnico del fenómeno.

### 9.3. Redes sociales y gestión de rumores

1. Monitoreo continuo de redes durante la vigencia de alertas Naranja/Roja y ACP.
2. Fijado (pin) del comunicado oficial vigente en todos los perfiles; unificación de texto e imagen conforme al Anexo B.
3. Todo rumor con circulación relevante se desmiente con plantilla M6 dentro de los 60 minutos de detectado, sin amplificarlo: se cita el dato falso una sola vez y se lo reemplaza por el dato verificado.

### 9.4. Comunicación con familias de personas lesionadas o afectadas

1. La notificación a familias es presencial o telefónica y previa a toda difusión pública, a cargo de Medicina del Trabajo, Dirección de Sanidad o Bienestar Universitario, según corresponda.
2. Se designa un punto de contacto único por familia y se garantiza reserva de identidad y datos personales.
3. La Vocería no confirma identidades ni estados de salud por canales públicos.

### 9.5. Comunicación durante confinamiento prolongado

Se emiten partes M7 con información de servicios (agua, alimentos, refugios, retiro escolar), instrucciones de calma y horarios de próxima actualización; la megafonía de predios repite los puntos clave entre partes.

### 9.6. Comunicación de reanudación y post-evento

1. Emitido el cese por el SMN, se difunde M5 por los mismos canales de la suspensión.
2. Dentro de las 72 horas, la Vocería incorpora al informe post-activación (Documento A) las lecciones aprendidas de comunicación: tiempos de emisión, cobertura efectiva, rumores gestionados y fallas de canales.

## 10. COMUNICACIÓN INTERNA A LA COMUNIDAD UNIVERSITARIA

1. Cascada oficial: Vocero → Decanos, Directores Administrativos y Directores de Escuelas → mayordomías, jefaturas y cátedras → estudiantes y familias.
2. Grupos institucionales de WhatsApp/Telegram por público (docentes, nodocentes, jefes de departamento, escuelas): solo reenvían texto oficial del Vocero; prohibido agregar interpretación propia.
3. Moodle y correo institucional replican el texto oficial completo, sin recortes.
4. Proveedores y contratistas con tareas en predios reciben la novedad por el enlace administrativo del contrato y por cartelería de accesos.

## 11. PRUEBAS, EJERCICIOS E INDICADORES

1. Prueba trimestral de difusión masiva con verificación de recepción en todos los predios y escuelas.
2. Prueba trimestral de transmisión conjunta AM UNS – FM UTN-FRBB (Sección 5.2).
3. Participación de la Vocería en el simulacro integral anual y en los ejercicios de mesa trimestrales.
4. Indicadores: tiempo decisión→difusión (antes de la hora de corte del turno); canales efectivos por emisión (mínimo 3); confirmación de recepción en escuelas al 100 %; rumores desmentidos dentro de los 60 minutos al 100 %.

## 12. MEJORA CONTINUA

1. Toda falla detectada en pruebas o activaciones reales se registrará en el Registro de Difusión (Anexo C) y se tratará conforme al ciclo PDCA del protocolo (Documento A).
2. El informe post-activación de 72 horas incluirá el análisis de comunicación y las acciones correctivas de este manual.
3. Control de versiones: toda modificación generará nueva revisión/versión con tabla de cambios, responsable y fecha. Revisión ordinaria anual.
4. Interpretación: toda interpretación divergente de este manual deberá ser consultada al Vocero Institucional y al Nodo Central, únicos órganos autorizados para emitir aclaraciones.

## ANEXO A – MATRIZ DE CONSULTA RÁPIDA POR NIVEL

| Nivel SMN | Mensaje clave estándar | Plantilla | Repetición |
| --- | --- | --- | --- |
| Amarillo | Actividades al aire libre suspendidas; clases normales | M1 | Una emisión + recordatorio por corte |
| Naranja conocido antes del corte | Turno suspendido; no concurrir | M2 | Al decidir + cada 30 min |
| Naranja/Rojo o ACP durante cursada | Permanecer dentro del edificio; no salir | M3 | Inmediata + cada 30 min |
| Escuelas con alumnos presentes | Alumnos custodiados; retiro solo con DNI | M4 | Al decidir + cada cambio |
| Rojo | Suspensión total; seguir instrucciones oficiales | M2/M3 + alarmas | Cada 30 min hasta cese |
| Evento prolongado | Parte de situación y servicios | M7 | Cada 60 min |
| Rumor | Desmentida con dato verificado | M6 | Inmediata + 60 min |
| Cese | Reanudación por turno | M5 | Una emisión + confirmación |

## ANEXO B – SEÑALETICA Y CARTELERÍA (ISO 7010 + COLORES SMN)

| Elemento | Diseño | Ubicación |
| --- | --- | --- |
| Cartel de nivel SMN | Cuatro franjas de color con lemas: Amarillo informate · Naranja preparate · Rojo seguí instrucciones oficiales · Verde tranquilidad | Accesos principales, aulas, pasillos, escuelas |
| Pictograma de advertencia (ISO 7010) | Triángulo amarillo con símbolo de tormenta/viento | Accesos, predios abiertos, Palihue |
| Pictograma de prohibición (ISO 7010) | Círculo rojo: prohibido salir al exterior durante confinamiento | Salidas a patios, terrazas y predios abiertos |
| Pictograma de condición segura (ISO 7010) | Rectángulo verde: zona de refugio / punto de encuentro interno | Pasillos centrales, plantas bajas, gimnasios, comedores |
| Cartel de retiro escolar | Texto claro: retiro solo con padre/madre/tutor con DNI por acceso principal | Accesos de Escuelas Preuniversitarias |
| Pie de mensaje oficial | Logo UNS + "Única información oficial: canales UNS" + hora de actualización | Toda pieza gráfica y digital |

## ANEXO C – REGISTRO DE DIFUSIÓN (PLANTILLA)

| Fecha | Hora | ID mensaje | Plantilla (M1–M7) | Canales utilizados | Confirmación de recepción | Operador | Observaciones |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |

## ANEXO D – REGISTRO DE MEDIOS Y SALA DE PRENSA (PLANTILLA)

| Medio | Contacto | Teléfono / correo | Acreditación (S/N) | Hora de parte recibido | Observaciones |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

## ANEXO E – DIAGRAMA DE FLUJO DE DIFUSIÓN

```
[RESOLUCIÓN RECTORADO] + [FICHA DEL ALERTA] ──► [VOCERO] (voz única)
        │
        ▼
[REDACCIÓN M1–M7] ──► [FORMATOS ACCESIBLES] (sonoro / visual / texto simple)
        │
        ├──► Capa 1 digital (web, Moodle, correo, redes)
        ├──► Capa 2 radial (AM UNS → FM UTN-FRBB dúplex; radios locales)
        ├──► Capa 3 en predios (megafonía, pantallas, alarmas)
        ├──► Capa 4 telefonía (SMS masivo)
        └──► Capa 6 presencial (mayordomías, escuelas, brigadas)
        │
        ▼
[CONFIRMACIÓN DE RECEPCIÓN] ──► [REGISTRO DE DIFUSIÓN]
        │
        ▼
[REPETICIÓN SEGÚN MATRIZ] ──► [CESE M5] ──► [INFORME 72 h]
```
