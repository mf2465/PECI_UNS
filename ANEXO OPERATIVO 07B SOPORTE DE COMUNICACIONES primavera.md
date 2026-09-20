# ANEXO OPERATIVO 07-B – SOPORTE TÉCNICO DEL PROTOCOLO DE EMERGENCIAS METEOROLÓGICAS

**Universidad Nacional del Sur – Bahía Blanca**
**Revisión 0 – Versión 2 – Consolidado 2026**

## CONTROL DE VERSIONES

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Borrador inicial de segregación (estructura de 5 piezas definida por SHST: A, B, AT-01, AT-02, PE) |
| 0 | 2 | 09/2026 | Enriquecimiento íntegro desde PECI_UNS Rev 0 Versión 7_B (Bloques B-1 a B-4): arquitectura y capacidades técnicas, medios primarios, RACUNS, POT-RACUNS, topología, pruebas y derivación a Procedimientos Específicos |

## NOTA DE ARQUITECTURA DOCUMENTAL Y SEGREGACIÓN

El sistema documental del PECl-UNS se organiza en cinco piezas con responsabilidades diferenciadas:

| Pieza | Rol |
| --- | --- |
| Documento A – Operativo | Decide y actúa: niveles de alerta, decisiones institucionales, custodia, ventanas horarias, CDE |
| Documento B – Soporte Técnico (este documento) | Define la arquitectura y las capacidades técnicas de comunicaciones |
| AT-01 – Mantenimiento de Infraestructura | Previene y mantiene edificios y servicios esenciales |
| AT-02 – Mantenimiento de Comunicaciones | Previene y mantiene los sistemas de comunicaciones (disponibilidad, pruebas, mantenimiento) |
| PE – Procedimientos Específicos | Encuadra técnicamente los riesgos específicos de cada sector |

Este documento no establece contenidos de comunicación pública, vocería o difusión a la comunidad (Anexo Operativo 1 – Plan de Comunicaciones de la Emergencia), ni las rutinas de mantenimiento preventivo y disponibilidad de los sistemas (AT-02), ni las decisiones institucionales de alerta (Documento A / Anexo Operativo 7A).

## 1. OBJETO

Establecer la base técnica y de infraestructura de las comunicaciones que sustenta el Protocolo Operativo de Actuación ante Emergencias Meteorológicas (PECl-UNS), asegurando que las capacidades necesarias para la respuesta institucional queden definidas. El Anexo Técnico AT-02 asegurará que estén disponibles, verificadas y sujetas a un cronograma de mantenimiento preventivo.

El presente documento comprende la arquitectura de comunicaciones, la Red Alternativa de Comunicaciones de la UNS (RACUNS), los criterios técnicos de degradación y restitución de las comunicaciones, y el plan de telecomunicaciones operacionales.

## 2. ALCANCE Y DESTINATARIOS

### 2.1. Alcance territorial

Aplica a los predios alcanzados por el PECl-UNS, entre otros: Campus Altos de Palihue; Complejo Alem; San Juan 670; 12 de Octubre; Colón 80; Rondeau 29; Casa de la Cultura; Escuelas Preuniversitarias; Anexo de la Radio AM UNS; Laboratorio de Hidráulica; demás predios que sean incorporados al PECl-UNS.

### 2.2. Destinatarios obligatorios

Dirección General de Telecomunicaciones; Subsecretaría de Infraestructura y Servicios; Laboratorio de Hidráulica del Departamento de Ingeniería (LH); Jefatura de Higiene, Seguridad y Gestión Ambiental (SHST); mayordomías de todos los predios; Seguridad Patrimonial; brigadas técnicas; técnicos de Radio AM UNS designados por la Vocería.

Los sectores técnicos deberán mantener actualizada la información correspondiente a los sistemas bajo su responsabilidad.

## 3. DOCUMENTOS RELACIONADOS

- Plan Director de Emergencias de la UNS (PDE).
- Documento A / Anexo Operativo 7A – Protocolo Operativo de Actuación ante Emergencias Meteorológicas.
- Anexo Operativo 1 – Plan de Comunicaciones de la Emergencia (Pública y Vocería).
- AT-01 – Prevención de Infraestructura Edilicia y Servicios Esenciales.
- AT-02 – Prevención y Disponibilidad de los Sistemas de Comunicaciones.
- PE – Procedimientos Específicos ante Emergencias.
- Documento institucional "RACUNS – Red Alternativa de Comunicaciones de la UNS" (Noviembre 2025).
- Anexo Técnico de Radiocomunicaciones (carácter restringido).
- Ley Nacional N.º 27.287 – SINAGIR.
- Sistema de Alerta Temprana del Servicio Meteorológico Nacional.
- Plan Nacional para la Reducción del Riesgo de Desastres 2025-2029 (PNRRD).
- Plan de Coordinación Federal ENOS 2026/2027 – Anexo "POT Federal" v1.0/2026 (AFE–DNOYL).
- LICENCIA ENACOM VHF UNS – expediente CNC 11660/1998.

## 4. CRITERIOS TÉCNICOS GENERALES

La infraestructura de soporte del PECl-UNS se desarrollará bajo los siguientes principios:

- **Redundancia:** ninguna comunicación crítica dependerá de un único medio, proveedor, infraestructura o nodo.
- **Disponibilidad:** las capacidades deberán estar operativas o restituibles dentro de plazos definidos.
- **Autonomía:** operación independiente de redes comerciales y, en lo posible, de la red eléctrica.
- **Interoperabilidad:** compatibilidad con agencias y jurisdicciones (Defensa Civil/COE, UTN-FRBB, radioclubes).
- **Trazabilidad:** registro y control de comunicaciones relevantes.
- **Seguridad:** protección de datos personales (Ley 25.326) y segregación de redes de contingencia.
- **Mantenimiento preventivo:** cronogramas verificables registrados en AT-02.
- **Validación mediante pruebas:** toda capacidad deberá probarse periódicamente y tras cambios relevantes.

La continuidad técnica deberá procurar que una falla de un componente no implique automáticamente la pérdida de una capacidad crítica.

## 5. UMBRALES METEOROLÓGICOS DE REFERENCIA TÉCNICA

Los valores establecidos por el SMN constituyen referencia técnica para las acciones de comunicación y para el disparo de acciones de infraestructura de soporte.

La decisión institucional (niveles de alerta, suspensión, confinamiento) se adopta conforme al Documento A / Anexo Operativo 7A.

**Importante:** este documento no debe convertirse en un segundo protocolo operativo. Los niveles de alerta y las decisiones institucionales han sido definidos en el Anexo Operativo 7A.

Para precipitaciones y viento se utilizarán los umbrales técnicos establecidos en el documento fuente (SMN, 2.ª edición 2024), sujetos a actualización cuando corresponda; Telecomunicaciones y LH verificarán periódicamente su vigencia.

## 6. INFRAESTRUCTURA CRÍTICA DE COMUNICACIONES

Se consideran infraestructura y sistemas críticos, entre otros:

- **Aplicación ALERTHOR** (o quien la sustituya) como medio de información institucional primaria.
- **Centro de Datos (Telecomunicaciones):** servidores institucionales con Grupo Electrógeno exclusivo de 100 kVA con Panel de Transferencia Automático (ATS) y bancos de UPS para transición de carga.
- **Generador Móvil de Respaldo (100 kVA):** emplazado habitualmente en proximidades de San Juan 670, sobre plataforma móvil, para soporte de infraestructura crítica con desconexión prolongada.
- **Nodo Central 24/7 (Oficina de Recepción de Avisos):** su régimen funcional, rutinas y responsabilidades se rigen por el Anexo Operativo 7A. Este documento define su soporte técnico: emplazamiento en Mayordomía San Juan 670 (BASE CENTRAL); UPS dedicada (1 a 2 kVA) para Base VHF, telefonía y cargadores; acometida exterior con tablero de transferencia manual para acople rápido del generador móvil; fuentes redundantes de consulta del SAT (web oficial, aplicación oficial SMN con notificación por zona, y correo).
- **Respaldo DC en sitio del repetidor VHF (Complejo Alem – BBYF):** fuente con cargador flotante y banco de baterías de ciclo profundo (12 V AGM/Gel 100 Ah), autonomía de 24 a 48 horas.
- **Radiobase VHF del Laboratorio de Hidráulica (BASE LH):** equipo fijo existente en el LH del Departamento de Ingeniería; opera como nodo técnico de la red y respaldo del troncal.
- **Nodo Meshtastic Palihue:** nodo único de malla LoRa desplegado en Campus Palihue, de ubicación estratégica en Bahía Blanca y autonomía energética solar.

**Nota de remisión:** la protección de laboratorios, cadena de frío, sustancias químicas y materiales biológicos se rige por el **PE-02**; la protección de archivos, bibliotecas y patrimonio por el **PE-03**; la infraestructura edilicia y los servicios esenciales (energía de respaldo edilicia, bombeo, gas, ascensores) por el **AT-01**. Este documento define únicamente la infraestructura que sostiene las comunicaciones.

## 7. ARQUITECTURA DE COMUNICACIONES

### 7.1. Medios de comunicación primarios del proceso (comerciales e institucionales)

Los medios descritos en esta sección constituyen el método principal para la transmisión de la información del proceso de emergencia entre los distintos actores intervinientes, en modalidad punto a punto o grupal, en condiciones normales y de degradación parcial.

El sistema RACUNS es el sistema alternativo de comunicaciones: pasa a ser medio principal únicamente ante la declaración del Estado de Comunicaciones Degradadas (ECD) o ante falla de los medios primarios conforme a 7.5.

Ninguna decisión crítica del proceso dependerá de un único medio, canal o proveedor externo. Todo flujo crítico contará con al menos un medio de respaldo de naturaleza distinta (red de datos, red celular, voz conmutada o radio).

### 7.2. Inventario de medios y administración

| Medio | Naturaleza | Modalidad | Administración responsable | Uso principal en el proceso | Dependencia externa | Limitación / consideración |
| --- | --- | --- | --- | --- | --- | --- |
| Alerthor | Servicio de notificación masiva de terceros (contratado) | Masiva y por segmentos | SHST (administración y operación) con Vocería (contenidos) | Aviso masivo inmediato al CDE y a actores internos; novedades críticas | Proveedor + internet/red celular | Riesgo de cautividad; migración prevista al sistema propio (7.6) |
| Sistema propio (en desarrollo) | Sistema institucional de notificación masiva | Masiva y por segmentos | SHST / Telecomunicaciones | Asumir las funciones de Alerthor con datos y padrón propios | Internet/red celular | Objetivo a mediano plazo; entrada en operación sujeta a pruebas y migración (7.6) |
| WhatsApp | Mensajería instantánea comercial | Punto a punto y grupal | Administrador designado por grupo oficial | Coordinación operativa por público; reportes de estado | Proveedor + datos/celular | Congestión en eventos masivos; sin garantía de entrega; carácter informal |
| Telegram | Mensajería instantánea comercial | Punto a punto, grupal y canal | Administrador designado por grupo oficial | Respaldo de grupos WhatsApp; difusión uno-a-muchos por canal | Proveedor + datos/celular | Menor penetración en algunos públicos |
| Correo institucional | Correo electrónico institucional | Punto a punto y listas de distribución | Telecomunicaciones | Formalización de recomendaciones, decisiones y actas con trazabilidad | Servicio de correo + internet | Latencia; no es canal de confirmación inmediata |
| SMS masivo | Mensajería de red celular | Masiva y punto a punto | Telecomunicaciones (contrato con operador) / SHST | Aviso masivo ante caída de datos; públicos sin smartphone | Operador celular | Costo por envío; longitud de mensaje; dependencia del operador |
| Llamadas celulares | Voz conmutada de red celular | Punto a punto | Cada actor (padrón oficial vigente) | Confirmación de recepción, escalamiento y coordinación punto a punto | Operador celular | Congestión con alta demanda; comunicación secuencial |
| Futuros desarrollos | A definir | A definir | Telecomunicaciones / SHST | Incorporación sujeta a los criterios de 7.6 | A evaluar | No se utilizarán en operación real antes de su adopción formal y prueba |

### 7.3. Flujos del proceso y medios por actor

| Flujo | Emisor → Receptor | Modalidad | Medio primario | Medio respaldo | Confirmación de recepción | Registro |
| --- | --- | --- | --- | --- | --- | --- |
| F1 Aviso de alerta | Nodo Central → CDE | Punto a punto + grupal | Alerthor + grupo WhatsApp CDE | Llamada celular a integrantes | ACK o lectura dentro de 15 min | Libro de guardia del Nodo + Ficha del Alerta |
| F2 Recomendación técnica | SHST / CDE → Rector | Punto a punto | Correo institucional + llamada | WhatsApp punto a punto | Respuesta explícita | Acta o minuta del CDE |
| F3 Decisión | Rector → Nodo Central y Vocería | Punto a punto | Llamada + correo institucional | WhatsApp punto a punto | Respuesta explícita | Registro de decisión |
| F4 Novedad operativa a áreas | Nodo Central / Vocería → Decanos, Directores, Escuelas, Mayordomías | Grupal + masiva | Alerthor + grupos WhatsApp/Telegram por público | SMS masivo | Acuse o respuesta del responsable de área | Registro de Difusión y libro del Nodo |
| F5 Reporte de estado | Mayordomías, Escuelas, Brigadas → Nodo Central | Punto a punto | WhatsApp o llamada al Nodo Central | RACUNS CH1 / CH3 | Acuse del Nodo | Libro de guardia (cada 30 min en Naranja/Rojo) |
| F6 Estado de comunicaciones | Telecomunicaciones → Nodo Central y CDE | Punto a punto + grupal | Grupo WhatsApp técnico + llamada | RACUNS CH1 | Respuesta explícita | Registro técnico de Telecomunicaciones |
| F7 Coordinación externa | UNS ↔ Defensa Civil / COE | Punto a punto | Telefonía de guardia + correo institucional | RACUNS CH4 | Respuesta explícita | Libro de guardia del Nodo |
| F8 Difusión masiva a la comunidad | Vocería → comunidad y medios | Masiva | Se rige por el Anexo Operativo 01 | Se rige por el Anexo Operativo 01 | Según Anexo Operativo 01 | Registro de Difusión |

### 7.4. Reglas de operación de los medios primarios

1. **Padrón oficial vigente.** El SHST y Telecomunicaciones administran las plataformas y los padrones de contacto; cada área es responsable de informar sus altas, bajas y cambios dentro de las 48 horas. El padrón se verifica y depura con frecuencia trimestral y antes de cada simulacro integral.
2. **Mensaje oficial único.** Solo tienen validez los mensajes originados en el Nodo Central o en la Vocería. Los grupos oficiales reenvían el texto oficial sin agregados ni interpretación propia.
3. **Confirmación de recepción y escalamiento.** Todo mensaje crítico requiere confirmación (acuse, lectura o respuesta). Sin confirmación dentro de los 15 minutos, se escala al medio de respaldo (llamada celular) y, de persistir la falta de confirmación, al enlace radial RACUNS del destinatario.
4. **Trazabilidad.** Toda emisión crítica y su confirmación se registran (fecha, hora, medio, destinatarios, operador), conforme al principio de seguridad y trazabilidad y a los registros del Anexo 7A y del Anexo 1.
5. **Protección de datos personales.** Los padrones y los datos de contacto se tratan conforme a la Ley N° 25.326 y se utilizan exclusivamente para emergencias, simulacros y pruebas.
6. **Disciplina de grupos.** Cada grupo oficial tiene administrador designado; se prohíben cadenas, contenido ajeno a la emergencia y decisiones por grupo: los grupos coordinan, no deciden.
7. **Orden de uso ante degradación parcial.** Caída de datos/internet: priorizar SMS y llamadas. Congestión de voz conmutada: llamadas breves con protocolo predefinido y confirmación por SMS.
8. **Interoperabilidad externa.** Los flujos con Defensa Civil, Municipio y otras instituciones usan los medios oficiales convenidos y, como respaldo, el enlace CH4 de RACUNS.

### 7.5. Degradación y traspaso a RACUNS

#### 7.5.1. Degradación Parcial

Se configura cuando falla un (1) solo medio primario (ej. caída exclusiva de la plataforma Alerthor o de la fibra óptica de un predio específico) o cuando la congestión de red impide el envío de datos pero permite llamadas de voz.

**Acción:** No se declara el Estado de Comunicaciones Degradadas (ECD). El Nodo Central aplica el orden de uso de respaldo (7.4.7), utiliza el medio alternativo disponible (ej. SMS o llamadas) y registra la contingencia en el Libro de Guardia. RACUNS mantiene su rol de sistema alternativo.

#### 7.5.2. Estado de Comunicaciones Degradadas (ECD) – Regla Objetiva

El ECD es una condición formal que transforma a RACUNS en el medio principal y exclusivo de mando y coordinación. Se declara obligatoriamente cuando el Nodo Central verifica el cumplimiento simultáneo de la **Regla de los 2 de 3 Pilares** durante una ventana de **15 minutos continuos**:

- **Pilar 1 (Datos/Internet):** Imposibilidad de acceder a la web del SMN, Moodle institucional o correo electrónico desde la red cableada (fibra) y redes móviles (4G/5G).
- **Pilar 2 (Voz/SMS Comercial):** Imposibilidad de cursar llamadas telefónicas o enviar SMS a través de operadores de telefonía celular comerciales.
- **Pilar 3 (Energía de Red):** Corte del suministro eléctrico comercial de la red pública que afecte a la Sede Central (SJ670) o al Repetidor Troncal (Alem), sin que los sistemas ATS/UPS logren estabilizar la infraestructura de telecomunicaciones.

Si al menos dos (2) de estos tres (3) pilares caen simultáneamente o fallan de manera intermitente pero inutilizable por más de 15 minutos, el Operador del Nodo Central tiene la obligación técnica y la autoridad para declarar el ECD, sin necesidad de esperar una resolución previa del CDE.

#### 7.5.3. Protocolo de Triangulación (Verificación Técnica)

Para evitar falsos positivos (ej. falla del equipo de un usuario o cortes localizados), el Nodo Central debe ejecutar el siguiente protocolo de triangulación antes del minuto 15:

1. **Ping Interno:** Intentar contacto vía WhatsApp/Telegram con al menos dos (2) Bases remotas (ej. BASE PALIHUE y BASE RECTORADO).
2. **Ping Externo:** Intentar acceso a la App del SMN y a la web de Defensa Civil Bahía Blanca.
3. **Llamada de Control:** Intentar llamar al teléfono de guardia de SHST o al COE de Defensa Civil.

Si el 70 % de estos intentos fallan, se configura la causal técnica para la declaración del ECD.

#### 7.5.4. Formalización y Traspaso

Declarado el ECD, el Operador del Nodo Central debe:

1. Asentar en el Libro de Guardia Radial y Físico: "HORA [XX:XX] - Verificada caída de Pilares [X e Y]. Se DECLARA Estado de Comunicaciones Degradadas."
2. Emitir por CH1 (Troncal RACUNS) el siguiente mensaje de voz estandarizado: "Atención todas las bases, Nodo Central. Se declara Estado de Comunicaciones Degradadas por caída de red externa. A partir de este momento, RACUNS CH1 es el medio principal de coordinación. Todas las bases confirmar recepción."
3. Despachar un mensaje SMS masivo (si el Pilar 2 lo permite) o utilizar el sistema Alerthor (si el Pilar 1 lo permite) con el texto: "UNS: Caída de sistemas comerciales. Coordinación operativa trasladada a red radial interna. Siga instrucciones de mayordomía."

#### 7.5.5. Restitución (Retorno a la Normalidad)

El ECD se levanta cuando al menos dos (2) de los 3 Pilares se restablecen y mantienen estables durante 30 minutos continuos. Telecomunicaciones ejecuta pruebas de enlace, notifica el cierre del ECD por CH1 y asienta el horario de retorno en el Libro de Guardia.

### 7.6. Evolución, sistema propio y adopción de nuevos medios

- **Sistema propio (en desarrollo):** alcance objetivo: padrón multi-público propio; emisión multicanal (notificación push, SMS, correo y voz); registro de entregas y confirmaciones; propiedad local de datos y padrones; interfaces documentadas. Su desarrollo e implementación constituyen un objetivo a mediano plazo. Su entrada en operación requiere prueba exitosa en al menos un simulacro integral y un ciclo de operación en paralelo con Alerthor.
- **Evitación de cautividad:** exportación periódica de padrones y registros; cláusulas de portabilidad y APIs documentadas en los contratos con terceros.
- **Criterios de adopción de futuros medios:** (a) redundancia con medios existentes; (b) trazabilidad y registro; (c) accesibilidad; (d) protección de datos personales; (e) operación probada en al menos un simulacro; (f) administración y costo sostenibles; (g) sin dependencia de proveedor único.
- **Incorporación:** todo medio nuevo se incorpora mediante actualización de esta sección (inventario y flujos), prueba conforme a la Sección 11 y comunicación formal a los actores del proceso.

## 8. RED ALTERNATIVA DE COMUNICACIONES DE LA UNS (RACUNS)

### 8.1. Definición, propósito y alcance

Red autónoma de comunicaciones basada en tecnología VHF, destinada a asegurar la conectividad institucional y operativa ante interrupciones de los servicios convencionales de telecomunicaciones y energía.

- **Propósito principal:** comunicación interna entre dependencias universitarias.
- **Propósito secundario:** integración con instituciones externas mediante convenios firmados por el Rectorado, poniendo la red a disposición de la comunidad en emergencias mayores.
- **Alcance:** Campus Palihue, Colón 80, Complejo Alem, Escuelas Medias, Anexo Radio y predios de interés.

### 8.2. Criterio de activación

RACUNS se activa como medio principal de coordinación cuando el Nodo Central verifique la caída o inutilización de los medios convencionales conforme a la Regla Objetiva de los 2 de 3 Pilares (ver 7.5.2) y asiente la declaración del Estado de Comunicaciones Degradadas en el libro de guardia. La declaración es una facultad técnica del Operador de Guardia para garantizar la inmediatez de la respuesta, debiendo notificar al CDE por la propia red RACUNS una vez asegurado el troncal.

### 8.3. Infraestructura y nodos

| Nodo / Equipamiento | Emplazamiento | Rol operativo |
| --- | --- | --- |
| Repetidor principal VHF (50 W) | Complejo Alem, edificio BBYF (torre metálica de 10 m con pararrayos y puesta a tierra; altura relativa 28 m) | Troncal CH1; antena omnidireccional de alto rendimiento, duplexor y gabinete protegido con ventilación y protección contra sobretensiones |
| BASE CENTRAL | Mayordomía San Juan 670 (24 hs) | Control troncal, libro de guardia, despacho y Sala de Crisis primaria |
| BASE RECTORADO | Colón 80 | Nodo de comando de autoridades y punto de enlace institucional |
| BASE PALIHUE | Edificio Central del Campus Palihue | Supervisión del predio abierto y accesos |
| BASE LH | Laboratorio de Hidráulica, Departamento de Ingeniería | Nodo técnico y respaldo del troncal (8.7) |
| ANEXO RADIO (Campus Radio) | Edificio Anexo de la Radio AM UNS | Radiobase fija bibanda integrada al troncal; cadena de transmisión AM con respaldo energético; Sala de Crisis alternativa; nodo de la Capa 4 de difusión masiva; portador del nodo Starlink S2 (8.9) |
| Radiobases bibanda (proyectadas) | Nodos Colón 80, Escuelas Medias y Campus Palihue | Expansión de cobertura sujeta a pruebas de campo y a la adquisición aprobada en el expediente de expansión de nodos |
| Radiobase móvil | Unidad vehicular designada | Equipo bibanda + kit Starlink S3 (8.9); repetidor temporal ante caída del troncal (8.7) |
| Nodo Meshtastic Palihue | Campus Palihue | Nodo único de malla LoRa, autónomo solar (Capa 5) |
| Flota de handies | 12 unidades bibanda operativas | Canales pregrabados con responsable por sector, rol o responsabilidad |

**Autonomía y redundancia energética por nodo:** red eléctrica (primaria) → UPS / banco de baterías 24–48 h (secundaria) → grupo electrógeno institucional o paneles solares (terciaria). El nodo Meshtastic Palihue posee autonomía solar propia. La verificación periódica de estas fuentes se rige por el AT-02.

### 8.4. Asignación de la flota de handies (12 unidades)

| ID | Puesto asignado | Misión operativa | Responsable |
| --- | --- | --- | --- |
| H-01 | Jefatura Higiene, Seguridad y Gestión Ambiental | Comando técnico y evaluación de riesgos en terreno | Titular del sector |
| H-02 | Secretaría de Servicios Técnicos y Transformación Digital | Enlace técnico-académico y con Rectorado | Titular del sector |
| H-03 | Subsecretaría de Infraestructura y Servicios | Despliegue edilicio, motobombas y cuadrillas | Titular del sector |
| H-04 | Telecomunicaciones / Data Center | Monitoreo de enlaces, repetidor, ATS y grupos | Titular del sector |
| H-05 | Mayordomía Complejo Alem | Control de accesos y confinamiento de pabellones | Titular del sector |
| H-06 | Laboratorio de Hidráulica | Generadores, bombas y asistencia técnica | Titular del sector |
| H-07 | Mayordomía Campus Palihue | Patrullaje preventivo y enlace con Base Palihue | Titular del sector |
| H-08 | Escuelas Medias (11 de Abril / Alem) | Custodia de menores y reporte de estado | Titular del sector |
| H-09 | Escuela de Agricultura y Ganadería | Custodia de menores y reporte de estado | Titular del sector |
| H-10 | Departamento de Medicina del Trabajo | Atención de lesionados, primeros auxilios y triage | Titular del sector |
| H-11 | Móvil de Cuadrilla de Mantenimiento / Obras | Desplazamiento operativo de auxilio en vehículos | Titular del sector |
| H-12 | Reserva / Respaldo Técnico | Reemplazo inmediato por falla, refuerzo, o enlace interinstitucional en COE | Telecomunicaciones |

### 8.5. Plan de canales y régimen del Anexo Técnico restringido

| Canal | Modo | Uso operativo y disciplina |
| --- | --- | --- |
| CH1 | Repetidor Alem (semidúplex) | Troncal de Mando y Emergencia: exclusivo directivas del CDE, novedades de Bases y reportes críticos. Escucha permanente en Naranja/Rojo. Prohibido el tráfico secundario |
| CH2 | Simplex operativo | Coordinación logística y cuadrillas: mantenimiento edilicio, choferes, maniobras de generadores y grupos técnicos |
| CH3 | Simplex local | Coordinación interna de predio: mayordomos, brigadistas y personal de seguridad dentro del campus |
| CH4 | Enlace | Interoperabilidad con el COE de Defensa Civil Bahía Blanca |
| Simplex de contingencia | Simplex pregrabado | Frecuencia de contingencia ante caída del repetidor (8.7) |
| Memorias adicionales | Simplex | Frecuencias pregrabadas por grupos operativos (mantenimiento, SHST, eléctricos, autoridades, brigadistas, logística) |

**Régimen del Anexo Técnico de Radiocomunicaciones:** los valores de frecuencias, canales, códigos y subtonos constituyen el Anexo Técnico de Radiocomunicaciones, documento de carácter RESTRINGIDO: no se publica en repositorios abiertos ni se difunde fuera de los destinatarios del punto 2.2. La versión pública de este documento omite dichos valores; cada equipo se entrega programado por Telecomunicaciones contra acta de entrega.

### 8.6. Metodología bibanda y subcapas de retransmisión

- **Canal principal VHF:** enlace por línea de vista, libre de interferencia por obstáculos (árboles, edificios de hormigón), para troncal y enlaces entre nodos.
- **Canal secundario UHF:** conectividad en espacios cerrados o por rebotes, donde VHF no alcanza.
- **Subcapa de retransmisión:** todo mensaje recibido por UHF en un nodo que no alcance punto a punto su destino será retransmitido por el operador del nodo en VHF hacia el siguiente nodo; en tránsito entre nodos, si VHF no fuera posible, se intentará UHF por proximidad.
- Los handies permanecerán en escucha del canal troncal e interactuarán con el sistema según su posición lo favorezca.

### 8.7. Procedimiento de degradación del troncal y caída del repetidor

| Paso | Acción |
| --- | --- |
| Detección | La BASE CENTRAL advierte la caída del repetidor por ausencia de retorno en CH1 o por reporte de dos o más estaciones sin acceso al troncal |
| Migración inmediata | Todas las estaciones y handies migran a la frecuencia simplex de contingencia pregrabada (Anexo Técnico restringido), que pasa a operar como canal troncal provisional de mando y emergencia |
| Repetidor temporal | Si la caída se prolonga más allá de 30 minutos y existe disponibilidad, la radiobase móvil se despliega y asume el rol de repetidor temporal; hasta su puesta en servicio, la BASE LH y la BASE ANEXO RADIO sostienen el control del troncal provisional por turnos definidos por Telecomunicaciones |
| Restitución | Verificada la recuperación del repetidor principal, Telecomunicaciones ordena el regreso a CH1 y asienta el evento, la duración y las estaciones afectadas en el Libro de Prueba Radial |
| Prueba | El procedimiento completo se ejercita con frecuencia trimestral conforme al plan de pruebas del AT-02 y de la Sección 11 |

### 8.8. Arquitectura en capas (redundancia funcional)

| Capa | Tecnología | Rol | Estado | Fortalezas / límites |
| --- | --- | --- | --- | --- |
| 1 – Troncal | VHF repetidora (Alem, 50 W) + bases fijas (SJ670, Colón 80, Palihue, LH, Anexo Radio) | Mando y emergencia (CH1) | Operativa | Línea de vista, cobertura urbana; ante caída del repetidor opera 8.7 |
| 2 – Proximidad | UHF simplex / rebotes | Interior de edificios, sombra radioeléctrica | Operativa | Penetra hormigón; menor alcance |
| 3 – Datos | Starlink en tres modalidades: S1 respaldo fijo, S2 nodo Anexo Radio, S3 kit móvil (8.9) | Internet de contingencia; réplica de servidores Alem↔Palihue; emisión de comunicados web; enlace alternativo AM–FM | Operativa | Satelital, independiente; requiere apuntamiento y energía; conmutación manual en S1 |
| 4 – Difusión masiva | Radio AM UNS (Anexo Radio) + FM UTN-FRBB (convenio) | Comunicados a la comunidad cuando cae todo lo digital | Operativa (AM) / convenio en curso (FM) | Alcance masivo; unidireccional |
| 5 – Malla | Meshtastic / LoRa – nodo único en Campus Palihue, autónomo solar | Mensajería de texto sin infraestructura; último recurso de brigadas y puestos de terreno | Operativa (nodo único) | Autónoma, bajo consumo, ubicación estratégica; sin voz; cobertura limitada al nodo |

**Nota de accesibilidad:** los criterios de formatos accesibles (sonoro, visual de alto contraste, textual simple) de los mensajes y alarmas se rigen por el Anexo Operativo 1; este documento provee el soporte técnico de megafonía, alarmas en predios y emisión radial.

**Nota de continuidad (Capa 3):** los objetivos de recuperación (RTO/RPO) del enlace de respaldo S1 y del Centro de Datos serán definidos por la Dirección General de Telecomunicaciones dentro de los 60 días hábiles posteriores a la aprobación de este documento, con alcance limitado a servidores y su infraestructura informática. Hasta dicha definición rige como criterio mínimo: réplica diaria de servicios críticos y enlace satelital de contingencia disponible y probado.

### 8.9. Enlace satelital de contingencia (Starlink): tres modalidades

**S1 – Respaldo fijo (Dirección General de Telecomunicaciones)**
- **Función:** enlace de respaldo entre los servidores del Complejo Alem y su respaldo en Campus Palihue ante degradación o caída del enlace de fibra óptica actual.
- **Alcance:** exclusivamente servidores y su infraestructura informática; no transporta tráfico administrativo ordinario.
- **Conmutación MANUAL:** ante degradación de la fibra, la conmutación al enlace S1 es manual y se ejecuta conforme al siguiente procedimiento:
  1. **Detección:** monitoreo del Centro de Datos / Telecomunicaciones advierte degradación o caída del enlace de fibra.
  2. **Decisión:** la Dirección General de Telecomunicaciones (o el responsable designado) dispone la conmutación al enlace S1.
  3. **Ejecución:** conmutación manual de los servicios de réplica y respaldo al enlace S1 y verificación de la replicación Alem↔Palihue.
  4. **Registro:** asiento en libro de guardia con fecha, hora, causa, operador y servicios conmutados.
  5. **Retorno:** restitución manual a la fibra una vez verificada su estabilidad, con registro.
- **Prueba:** simulacro trimestral de conmutación manual con medición de tiempos, conforme al AT-02.

**S2 – Nodo de Radio AM (Anexo Radio)**
- **Función:** nodo Starlink en el Anexo Radio para transmisión de novedades a la comunidad (soporte de emisión de la Capa 4) y como enlace alternativo para la interconexión con la FM de la UTN-FRBB.
- **Dominio y destino:** la Vocería Institucional o el CDE definen su destino fijo o itinerante según necesidad operativa.
- **Operación:** lo operan los técnicos designados por la Vocería, en coordinación con Telecomunicaciones para contrato, cuenta y ciberseguridad.
- **Prueba:** prueba trimestral de emisión vía S2 y del enlace alternativo con la FM, conforme al AT-02.

**S3 – Kit móvil en vehículo (radiobase móvil)**
- **Función:** asistencia en campo: Sala de Crisis alternativa, tienda de campaña en territorio, consulta de radares meteorológicos y emisión de comunicados web.
- **Operadores:** mínimo dos operadores entrenados por turno potencial (Telecomunicaciones o LH); tiempo objetivo de puesta en servicio menor a 30 minutos.
- **Rol radial:** ante caída del repetidor principal asume el rol de repetidor temporal (8.7).

**Disposiciones comunes a S1, S2 y S3**
- **Titularidad y contrato:** la cuenta, el contrato de servicio y el equipamiento son administrados por la Dirección General de Telecomunicaciones, con responsable titular y suplente designados.
- **Ciberseguridad básica:** red de contingencia segregada de la red institucional; contraseña única y distinta de la de fábrica; firmware actualizado antes de cada prueba; sin exposición de servicios de gestión desde internet; registro de accesos durante la emergencia.
- **Pruebas y mantenimiento:** cada modalidad se prueba con frecuencia trimestral con registro de resultado y tiempos, conforme al plan de pruebas y al checklist del AT-02.

### 8.10. Disciplina radial, prueba semanal y capacitación

- **Protocolo de enlace:** identificación con el indicativo del puesto asignado en toda transmisión; mensajes breves, claros y estructurados; confirmación de recepción por repetición (colación).
- **Disciplina de canales:** prioridad absoluta de CH1 para mando y emergencia; el tráfico de trabajo, logístico o rutinario se cursará estrictamente por CH2/CH3 o por las memorias de grupo pregrabadas.
- **Prueba radial semanal:** día y hora definidos por la Dirección de Telecomunicaciones; cada Base (incluidas BASE LH y BASE ANEXO RADIO) y handy reportará ubicación, estado del equipo y nivel de batería. El resultado será asentado en el Libro de Prueba Radial y cualquier falla deberá ser reportada a Telecomunicaciones dentro de las 24 horas para su inmediata subsanación. El registro sistemático y el checklist asociado se rigen por el AT-02.
- **Capacitación para operadores no especializados:** la Dirección de Telecomunicaciones, en articulación con el SHST, dictará módulos de instrucción práctica obligatoria destinados a todo el personal asignado a la flota de handies que no posea formación técnica previa en radiocomunicaciones. Contenido mínimo: protocolo básico de enlace, códigos de brevedad, disciplina de escucha (pensar antes de transmitir), procedimiento de caída del repetidor (8.7), procedimiento de declaración de ECD (7.5) y procedimientos específicos para reportar emergencias.

### 8.11. Marco regulatorio

- **Licencia ENACOM vigente** para banda VHF (expediente CNC 11660/1998). Telecomunicaciones mantendrá el expediente técnico y la documentación de la licencia actualizados y disponibles para auditoría.
- **Uso de UHF:** se realizará en frecuencia fuera de la reservada para uso de radioaficionados. El trámite de regularización ante ENACOM será iniciado por la Dirección General de Telecomunicaciones dentro de los 60 días hábiles posteriores a la aprobación de este documento; su completamiento constituye tarea de mediano plazo con reporte periódico al CDE hasta su cierre.

### 8.12. Proyecciones del sistema

- **Radioclubes locales:** en Bahía Blanca operan dos radioclubes; la vinculación mediante convenio de colaboración técnica se proyecta como tarea de mediano plazo, orientada a enlaces HF de contingencia y soporte de operadores habilitados en emergencias de magnitud excepcional. A la fecha de esta versión no existe convenio iniciado.
- **Digitalización:** evaluación de migración parcial o dualidad tecnológica hacia DMR o TETRA si se requirieran trunking, cifrado o gestión avanzada de canales.
- **Expansión de nodos:** radiobases bibanda proyectadas en Colón 80, Escuelas Medias y Campus Palihue, sujetas a resultado de las pruebas de campo y a la adquisición aprobada en el expediente de expansión; evaluación de nodos Meshtastic adicionales sujeta a prueba del nodo único existente.
- **Notificaciones masivas:** se registra el servicio Alerthor (tercero) y el proyecto de desarrollo de un sistema propio de similares características para evitar cautividad tecnológica (objetivo a mediano plazo, ver 7.6).

## 9. PLAN DE TELECOMUNICACIONES OPERACIONALES (POT-RACUNS)

**Marco de referencia:** Anexo "Plan de Telecomunicaciones Operacionales para Apoyo Federal" v1.0/2026 del Plan de Coordinación Federal ENOS 2026/2027 (Agencia Federal de Emergencias – DNOYL), adaptado al ámbito, los niveles de gestión y los medios de la UNS, en consonancia con la Ley N° 27.287 (SINAGIR) y el PNRRD 2025-2029.

### 9.1. Datos generales y encuadre institucional

- **Institución:** Universidad Nacional del Sur.
- **Área responsable:** Dirección General de Telecomunicaciones, con unidad técnica de apoyo en el Laboratorio de Hidráulica (LH).
- **Área de cobertura:** predios UNS de Bahía Blanca y enlaces interinstitucionales con el COE de Defensa Civil Bahía Blanca.
- **Encuadre:** Ley N° 27.287 (SINAGIR); Documento A / Anexo Operativo 7A (decisión y custodia); Anexo Operativo 1 (difusión pública).

### 9.2. Objetivo general

Garantizar la continuidad, disponibilidad y confiabilidad de las comunicaciones durante operaciones de emergencia, asegurando la coordinación efectiva entre los distintos niveles de respuesta (táctico, operativo y estratégico) de la UNS y con los organismos externos de protección civil.

### 9.3. Principios operativos

| Principio | Definición (marco federal) | Aplicación en RACUNS |
| --- | --- | --- |
| REDUNDANCIA | Toda comunicación crítica debe contar con medios alternativos | Arquitectura en 5 capas (8.8); energía triple por nodo (8.3); simplex de contingencia y repetidor temporal (8.7); respaldo satelital (8.9) |
| PRIORIDAD | Jerarquización del tráfico según criticidad operativa | Prioridad absoluta de CH1 para mando y emergencia; tráfico de trabajo en CH2/CH3 y memorias de grupo (8.10) |
| INTEROPERABILIDAD | Compatibilidad entre agencias y jurisdicciones | Enlace CH4 con COE Defensa Civil (8.5); convenio AM–FM UTN-FRBB (Anexo Operativo 1); proyección de radioclubes (8.12) |
| SEGURIDAD Y TRAZABILIDAD | Registro y control de comunicaciones relevantes | Anexo Técnico restringido (8.5); Libro de Prueba Radial; libro de guardia y registros de difusión (Anexos 7A y 1); actas de entrega de equipos (8.4) |
| AUTONOMÍA OPERATIVA | Capacidad de operar en forma independiente en entornos adversos | Red VHF propia con baterías 24–48 h, grupo electrógeno o paneles solares (8.3); enlace satelital autónomo (8.9) |

### 9.4. Estructura operativa en tres niveles

| Nivel | Función principal | Nodos y medios asociados en la UNS |
| --- | --- | --- |
| Estratégico (Sala de Crisis / CDE) | Toma de decisiones y coordinación interinstitucional | Sala de Crisis primaria SJ670 y alternativa Anexo Radio (8.3); BASE CENTRAL y BASE RECTORADO; troncal CH1; enlace satelital Starlink (8.9); difusión masiva AM/FM (Capa 4, 8.8); telefonía institucional |
| Operativo (Nodo Central / mayordomías) | Coordinación táctica de personal y recursos; tráfico y registro | Nodo Central 24/7 (BASE CENTRAL); BASE PALIHUE; BASE LH; radiobases bibanda proyectadas; CH1–CH3; UHF de proximidad y subcapa de retransmisión (8.6) |
| Táctico (cuadrillas y brigadas en terreno) | Comunicación entre equipos de intervención propios y externos | Flota de 12 handies (8.4); simplex CH2/CH3; subcapa de retransmisión (8.6); radiobase móvil como repetidor temporal (8.7) |

### 9.5. Protocolos operativos básicos (activaciones)

- **Refuerzo del Nodo Central:** ante alerta Naranja/Roja o declaración de Estado de Comunicaciones Degradadas, el Nodo Central reforzará medios y personal para garantizar el servicio de turno 24 hs, los 7 días de la semana.
- **Activación del troncal RACUNS:** apertura de escucha permanente en CH1 y registro en libro de guardia (8.2, 8.10).
- **Activación del enlace CH4** con el COE de Defensa Civil Bahía Blanca ante declaración de emergencia (8.5).
- **Escalonamiento externo:** ante catástrofes que superen la capacidad universitaria, se solicitará la activación del servicio de radioaficionados a través de ENACOM y de los convenios con radioclubes (8.12), conforme al principio de subsidiariedad del SINAGIR.
- **Redundancias progresivas:** las activaciones responden a establecer todas las redundancias posibles ante un incremento de la crisis o necesidad de escalonamiento operacional (8.7, 8.8, 8.9).

### 9.6. Roles y responsabilidades

| Rol (marco federal) | Funciones principales | Titular en la UNS |
| --- | --- | --- |
| Coordinador técnico de Comunicaciones | Dirige y administra el sistema de telecomunicaciones; coordina actividades técnicas con otros organismos; asegura redundancias de canales y energía; coordina requerimientos con las autoridades | Director General de Telecomunicaciones |
| Operador de Central de tráfico (24/7) | Obtiene, registra y distribuye mensajes de alerta y alarma; valida información junto a operaciones; monitorea eventos y canales alternativos; sigue y soporta al personal desplegado; declara el ECD conforme a 7.5 | Operadores del Nodo Central / Oficina de Recepción de Avisos (Anexo Operativo 7A) |
| Jefe / coordinador en campo o Brigada | Cumple protocolos de comunicaciones en terreno; utiliza medios técnicos para compartir información | Mayordomos, jefes de brigada y portadores de handies H-01…H-11 |
| Soporte técnico y logístico de campo | Provee repuestos, energía y equipamiento; administra servicios especiales (satelital, telefonía, drones); contribuye al mantenimiento de equipos | Laboratorio de Hidráulica + Subsecretaría de Infraestructura y Servicios, con apoyo de Telecomunicaciones |

### 9.7. Plan de contingencia de comunicaciones

Ante la necesidad de contar con mayor respaldo ante la caída de la red principal, se procederá de la siguiente manera:

- Activar red de respaldo satelital o móvil ante caída de la red principal → enlace Starlink (8.9) y radiobase móvil (8.7).
- Reasignar frecuencias si hay interferencia → migración al simplex de contingencia y memorias alternativas del Anexo Técnico restringido (8.7).
- Enviar equipos portátiles de reemplazo a zonas críticas → reserva H-12 con acta de entrega (8.4).
- Reportar daños y priorizar comunicaciones de mando y rescate → prioridad de CH1 y registro de novedades (8.10 y 9.9).
- Activación del servicio de radioaficionados a través de ENACOM → convenios con radioclubes locales (8.12).

### 9.8. Agenda interna de contacto operativo

Telecomunicaciones mantendrá una Agenda Interna de Contacto Operativo actualizada y de distribución restringida a los destinatarios del punto 2.2, que incluirá: área, función, nombre, teléfono, correo y enlaces institucionales (COE Defensa Civil, UTN-FRBB, radioclubes). La plantilla, el registro y la verificación se rigen por el AT-02 (sección 8 y su Anexo); la verificación se ejecuta durante la prueba radial semanal (8.10) y la actualización debe efectuarse dentro de las 24 horas de todo cambio de personal o función.

### 9.9. Registro y mejora continua

- **Registrar las comunicaciones críticas:** libro de guardia radial, libro de guardia del Nodo Central (Anexo Operativo 7A) y registros de difusión (Anexo Operativo 1).
- **Realizar revisiones post-incidente** para identificar oportunidades de mejora: informe post-activación de 72 horas (Anexo Operativo 7A) con análisis técnico de comunicaciones.
- **Alimentar los indicadores** definidos en el AT-02 (sección 9) y la revisión anual del presente documento mediante control de versiones.

## 10. TOPOLOGÍA DE LA RED

```text
                      [REPETIDOR VHF ALEM – BBYF]
                           (50 W · torre 10 m · 28 m)
                                       │  CH1 semidúplex
          ┌──────────────┬─────────────┼─────────────┬──────────────┐
          ▼              ▼             ▼             ▼              ▼
     [BASE CENTRAL] [BASE RECTORADO] [BASE      [BASE LH]     [RADIOBASES
      SJ670 24 h     Colón 80        PALIHUE]    Lab. Hidr.    BIBANDA
      Sala de Crisis nodo de comando Ed.Central  nodo técnico  PROYECTADAS:
      primaria       de autoridades  predio                    Colón 80, Esc.
          │              │             │             │         Medias, Palihue]
          └──────────────┴─────────────┼─────────────┴──────────────┘
                                       │  CH2 / CH3 simplex
                                       │  UHF proximidad / subcapa de retransmisión
                           [FLOTA 12 HANDIES  H-01 … H-12]
                                       │  CH4 enlace
                           [COE DEFENSA CIVIL BAHÍA BLANCA]
     [ANEXO RADIO – Radio AM UNS] ── Sala de Crisis alternativa · Capa 4 (AM)
           enlace VHF al troncal · Starlink S2 (nodo Vocería, fijo o itinerante)
           enlace alternativo con FM UTN-FRBB
     [RADIOBASE MÓVIL] ── camioneta + Starlink S3 (Capa 3) ·
           repetidor temporal ante caída del troncal (8.7)
     [ENLACE S1] ── servidores Alem ↔ respaldo Palihue ·
           conmutación MANUAL ante degradación de fibra (8.9)
     [NODO MESH PALIHUE] ── Capa 5 · único · autónomo solar (8.8)
```

## 11. PRUEBAS Y VALIDACIÓN

Se establece como régimen mínimo de validación de la arquitectura el siguiente cuadro. Los procedimientos de ejecución, checklists y plantillas de registro corresponden al AT-02 (secciones 4 a 7 y su Anexo); los resultados alimentan los indicadores del AT-02 (sección 9).

| Prueba | Frecuencia | Responsable |
| --- | --- | --- |
| Prueba Alerthor | Semanal | SHST + Telecomunicaciones |
| Prueba radial (8.10) | Semanal | Telecomunicaciones |
| Caída de repetidor y migración (8.7) | Trimestral | Telecomunicaciones |
| Starlink S1 – conmutación manual (8.9) | Trimestral | Telecomunicaciones |
| Starlink S2 – emisión y enlace alternativo FM (8.9) | Trimestral | Vocería + Telecomunicaciones |
| Starlink S3 – despliegue y apuntamiento (8.9) | Trimestral | Telecomunicaciones |
| Conmutación energética de nodos críticos | Semestral | Telecomunicaciones + Infraestructura (según AT-02) |
| Meshtastic Palihue (8.8) | Semestral | Telecomunicaciones + LH |
| Prueba de campo integral | Según programa | Telecomunicaciones + predios |
| Simulacro de declaración de ECD con Regla de los 2 de 3 Pilares y Triangulación (7.5) | Trimestral | Telecomunicaciones + Nodo Central |
| Simulacro integral RACUNS / POT-RACUNS / Nodo Central | Anual | Comité + Telecomunicaciones |

Los valores e indicadores ya establecidos incluyen 100 % de pruebas programadas, ≥95 % de fallas radiales resueltas en 24 h, 100 % de cobertura crítica, ≥24 h de autonomía y 100 % de declaraciones ECD con triangulación documentada.

## 12. DERIVACIÓN A PROCEDIMIENTOS ESPECÍFICOS

Cuando una amenaza, instalación, servicio o actividad requiera medidas técnicas u operativas particulares que excedan el alcance del presente Anexo, el sector responsable deberá desarrollar y mantener vigente el correspondiente Procedimiento Específico ante Emergencias (PE), el cual deberá integrarse al PECl-UNS mediante las referencias y mecanismos de coordinación establecidos en el Anexo Operativo 7A.

Procedimientos inicialmente identificados:

- **PE-01 – Continuidad de servicios informáticos y ciberseguridad.** Responsable: Dirección de Gestión y Seguridad de la Información / Dirección General de Sistemas de Información. Articula con las disposiciones de segregación de redes de contingencia de 8.9.
- **PE-02 – Laboratorios, sustancias químicas y materiales biológicos.** Responsable: Unidad Académica / sector responsable, con intervención del SHST.
- **PE-03 – Protección de archivos, bibliotecas y patrimonio.** Responsable: sector responsable del patrimonio documental / archivos.
- **PE-04 – Flota institucional en tránsito.** Responsable: área responsable de vehículos institucionales; articula con el reporte a Base Central por CH2 o celular (8.5).
- **PE-05 – Otros sistemas o actividades críticas.** Cada área responsable deberá identificar aquellos procesos cuya interrupción pueda generar riesgo adicional, comprometer personas, afectar infraestructura crítica, producir pérdida de información, muestras o materiales, o impedir la continuidad de una función esencial.

La incorporación de un tema al registro de PE no libera al sector responsable de desarrollarlo, mantenerlo actualizado y verificarlo. El Documento A (Anexo Operativo 7A) solamente deberá referenciarlo y establecer la coordinación operativa necesaria.