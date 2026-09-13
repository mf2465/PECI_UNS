# ANEXO OPERATIVO 07-B – ANEXO TÉCNICO DE INFRAESTRUCTURA Y COMUNICACIONES (RACUNS)

## DOCUMENTO B – TÉCNICO

**Revisión 0 – Versión 4 (Consolidado Institucional 2026)**
**Universidad Nacional del Sur – Bahía Blanca**

---

## CONTROL DE VERSIONES DEL DOCUMENTO

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Segregación del PECl-UNS Rev 0 V4: contenido técnico de infraestructura, energía y radiocomunicaciones (RACUNS) |
| 0 | 2 | 09/2026 | Decisiones del comité: Sala de Crisis primaria SJ670 / alternativa Anexo Radio; nodos Anexo Radio y BASE LH; procedimiento de caída del repetidor; procedimiento satelital Starlink; Anexo Técnico de frecuencias restringido; trámite ENACOM UHF a iniciar; RTO/RPO a definir en 60 días hábiles |
| 0 | 3 | 09/2026 | Renumeración de capas (Malla a Capa 5, con nodo Meshtastic Palihue operativo y autónomo solar); Starlink en tres modalidades (S1 respaldo fijo con conmutación manual, S2 nodo Anexo Radio bajo dominio de Vocería, S3 móvil); alcance de continuidad limitado a servidores e infraestructura informática; reestructuración editorial |
| 0 | 4 | 09/2026 | Integración de la Sección 4 (Medios de Comunicación Primarios del Proceso); desplazamiento de RACUNS a la Sección 5 y renumeración subsiguiente; consolidación de flujos, padrones y administración (SHST / Telecomunicaciones) |

> **Nota de segregación:** el presente documento integra el contenido técnico y de ingeniería del protocolo. Los aspectos operativos de decisión, custodia y el régimen funcional de la Oficina de Recepción de Avisos 24/7 se rigen por el **Documento A (Protocolo Operativo)**; los aspectos de difusión, vocería, mensajes, formatos accesibles y medios comerciales de notificación masiva se rigen por el **Documento C (Manual de Comunicación Pública)**.

---

## 1. OBJETO Y ALCANCE TÉCNICO

### 1.1. Objeto

Definir la ingeniería, la infraestructura, los procedimientos técnicos y el mantenimiento de los sistemas de soporte del Protocolo de Emergencias Climáticas de la UNS: infraestructura crítica y respaldo energético, medios de comunicación primarios, red alternativa de radiocomunicaciones (RACUNS), capas complementarias de comunicación y planes de prueba y validación técnica.

### 1.2. Alcance y destinatarios

Este documento es de uso obligatorio para: **Dirección General de Telecomunicaciones**, **Subsecretaría de Infraestructura y Servicios**, **Laboratorio de Hidráulica del Departamento de Ingeniería (LH)**, **Jefatura de Higiene, Seguridad y Gestión Ambiental (SHST)**, **mayordomías de todos los predios**, **Seguridad Patrimonial**, **brigadas técnicas** y **técnicos de Radio AM UNS designados por la Vocería**.

**Predios comprendidos:** Campus Altos de Palihue, Complejo Alem, San Juan 670, 12 de Octubre, Colón 80, Centro Histórico Rondeau 29, Casa de la Cultura, Escuelas Preuniversitarias (11 de Abril y Agraria), Edificio Anexo de la Radio AM UNS (Anexo Radio) y predios de interés.

### 1.3. Documentos relacionados

1. **DOCUMENTO A** – Protocolo Operativo de Emergencias Meteorológicas (PECl-UNS).
2. **DOCUMENTO C** – Manual de Comunicación Pública y Vocería.
3. **DOCUMENTO INSTITUCIONAL "RACUNS"** – Red Alternativa de Comunicaciones de la UNS (Noviembre 2025).
4. **SMN** – SAT Módulo "Umbrales para los Alertas" (2.ª edición, julio 2024).
5. **LICENCIA ENACOM VHF UNS** – expediente CNC 11660/1998.
6. **ANEXO TÉCNICO DE RADIOCOMUNICACIONES** – documento restringido (ver 5.5).
7. **ANEXOS OPERATIVOS 01, 03 y 05** del Plan Director de Emergencias.

---

## 2. UMBRALES METEOROLÓGICOS DE REFERENCIA TÉCNICA

> **Fuente:** SMN, Módulo "Umbrales para los Alertas", 2.ª edición 2024 (umbrales de Patagonia según Anaya y otros, 2020). Estos valores constituyen la referencia técnica de disparo de las acciones de infraestructura; la decisión institucional se rige por el Documento A.

| Fenómeno | Amarillo | Naranja | Rojo |
| --- | --- | --- | --- |
| **Lluvias / Tormentas** | 15 mm en 12 h ó 30 mm en 24 h | 30 mm en 12 h ó 60 mm en 24 h | 60 mm en 12 h ó 90 mm en 24 h |
| **Viento (sostenido / ráfagas)** | 55 km/h / 65 km/h | 75 km/h / 90 km/h | 90 km/h / 110 km/h |
| **Nevadas** | En zonas bajas donde el fenómeno es raro, su ocurrencia con acumulación constituye, a priori, nivel amarillo | — | — |

**Notas técnicas:** para amarillo y naranja se considera acumulado en 12 h (sin descartar lluvias intensas en períodos más cortos); para rojo, 24 h. Los umbrales son dinámicos y públicos; **Telecomunicaciones y LH** verificarán periódicamente su vigencia en el sitio del SMN y actualizarán este cuadro mediante control de versiones.

---

## 3. VULNERABILIDADES POR PREDIO E INFRAESTRUCTURA CRÍTICA

### 3.1. Mapeo de vulnerabilidades y directivas técnicas de prevención

| Predio / Sede | Vulnerabilidades críticas | Directiva técnica específica |
| --- | --- | --- |
| **Campus Altos de Palihue** | Exposición a campo abierto frente a vientos SO/NO; arbolado de gran porte sobre sendas y estacionamientos; cubiertas livianas; riesgo de aislamiento vehicular por anegamiento de accesos | Poda preventiva semestral; clausura anticipada de sendas arboladas en Naranja/Rojo; confinamiento en pabellones centrales de hormigón; resguardo vehicular fuera de la proyección del arbolado |
| **Complejo Alem / San Juan / 12 de Octubre** | Edificaciones de gran altura (San Juan 670, 7 pisos); grandes superficies vidriadas; riesgo de anegamiento en subsuelos, depósitos y salas de calderas; alta densidad poblacional | Revisión permanente de bombas de achique y sumideros; bajada obligatoria de cortinas metálicas y cierre de ventanales; confinamiento en pasillos internos y plantas bajas; desconexión preventiva de ascensores en Rojo |
| **Sede Rectorado (Colón 80), Centro Histórico Rondeau 29 y Casa de la Cultura** | Patrimonio histórico; cubiertas y aberturas tradicionales; archivos históricos | Inspección y sellado de cubiertas y desagües pluviales; protección preventiva de archivos; nodo de comando BASE RECTORADO con respaldo energético |
| **Escuelas Preuniversitarias (11 de Abril, Agraria, etc.)** | Población de menores; dependencia de transporte público y retiro de tutores; talleres y galpones en la Escuela Agraria | Aplicación del Protocolo de Custodia (Documento A); enlace radial directo vía handy VHF con Base Central |
| **Edificio Anexo Radio AM UNS (Anexo Radio)** | Cadena de transmisión AM y nodo de comunicaciones; Sala de Crisis alternativa | Respaldo energético verificado según 5.13; inclusión en prueba radial semanal y en pruebas de campo |

### 3.2. Infraestructura crítica y respaldo energético / tecnológico

- **Centro de Datos (Telecomunicaciones):** servidores institucionales con Grupo Electrógeno exclusivo de 100 kVA con Panel de Transferencia Automático (ATS) y bancos de UPS para transición de carga.
- **Generador Móvil de Respaldo (100 kVA):** emplazado habitualmente en proximidades de San Juan 670, sobre plataforma móvil, para soporte de infraestructura crítica con desconexión prolongada.
- **Nodo Central 24/7 (Oficina de Recepción de Avisos):** su régimen funcional, rutinas y responsabilidades se rigen por el Documento A. Este documento define su soporte técnico: emplazamiento en Mayordomía San Juan 670 (BASE CENTRAL); UPS dedicada (1 a 2 kVA) para Base VHF, telefonía y cargadores; acometida exterior con tablero de transferencia manual para acople rápido del generador móvil; fuentes redundantes de consulta del SAT (web oficial, aplicación oficial SMN con notificación por zona, y correo).
- **Respaldo DC en sitio del repetidor VHF (Complejo Alem – BBYF):** fuente con cargador flotante y banco de baterías de ciclo profundo (12 V AGM/Gel 100 Ah), autonomía de 24 a 48 horas.
- **Radiobase VHF del Laboratorio de Hidráulica (BASE LH):** equipo fijo existente en el LH del Departamento de Ingeniería; opera como nodo técnico de la red y respaldo del troncal (ver 5.8).
- **Nodo Meshtastic Palihue:** nodo único de malla LoRa desplegado en Campus Palihue, de ubicación estratégica en Bahía Blanca y autonomía energética solar (ver 5.9, Capa 5).
- **Laboratorios con sustancias químicas y materiales biológicos:** protocolos específicos ante cortes prolongados de energía (conservación, disponibilidad de N líquido), a cargo de cada unidad académica con asistencia del SHST.

### 3.3. Mantenimiento preventivo de infraestructura

1. Plan anual de inspección y poda preventiva de arbolado (Palihue y predios preuniversitarios) previo a la temporada primavera-verano.
2. Mantenimiento programado de sistemas pluviales y cubiertas: limpieza de canaletas y sumideros.
3. Pruebas bajo carga de grupos electrógenos (ATS) y motobombas de achique, con registro.
4. Verificación semestral de UPS, bancos de baterías y tableros de transferencia.

### 3.4. PROTOCOLOS TÉCNICOS DE INFRAESTRUCTURA CRÍTICA, LOGÍSTICA Y SERVICIOS ESENCIALES

La resiliencia de las comunicaciones (RACUNS y medios primarios) debe estar sustentada por la integridad de la infraestructura física, los servicios esenciales y la seguridad de la información. Esta sección asigna los procedimientos técnicos preventivos y de respuesta a las direcciones específicas de la UNS, conforme a su estructura orgánica.

#### 3.4.1. Matriz de Responsabilidades Técnicas por Dirección

| Dirección / Servicio UNS | Riesgo Crítico Asociado | Directiva Técnica de Infraestructura |
| :--- | :--- | :--- |
| **Dirección de Mantenimiento** | Corte de gas, anegamientos, arbolado, flota vehicular. | Ejecución de cortes preventivos, limpieza de sumideros, balizamiento de zonas de exclusión y protocolo de choferes. |
| **Dirección General de Construcciones Universitarias** | Daño estructural, colapso de cubiertas, patrimonio histórico. | Inspección de techos, protección de archivos, y emisión del "Certificado de Aptitud de Ocupación" post-evento. |
| **Servicios de Seguridad e Higiene en el Trabajo (SHST)** | Riesgo químico/biológico, atrapamientos, EPP, primeros auxilios. | Supervisión de protocolos de laboratorios, rescate en ascensores, y coordinación de brigadas. |
| **Dirección de Gestión y Seguridad de la Información** | Ciberataques, pérdida de datos, vulnerabilidad de servidores. | Verificación de backups externos, segregación de redes de emergencia y ciberseguridad en modo contingencia. |
| **Dirección General de Sistemas de Información** | Caída de servicios digitales, Moodle, web institucional. | Conmutación a servidores de respaldo y priorización de tráfico informático crítico. |
| **Dirección General de Telecomunicaciones** | Caída de fibra óptica, redes de datos, RACUNS. | Conmutación manual a Starlink S1, soporte a Sistemas de Información y mantenimiento de RACUNS. |

#### 3.4.2. Fluidos y Servicios Esenciales (Gas, Agua y Pluviales)
1. **Corte Preventivo de Gas:** Ante Alerta Roja, Aviso a Muy Corto Plazo (ACP) por tormentas severas, o sismo, la **Dirección de Mantenimiento** procederá al corte de las válvulas maestras de gas en calderas (ej. San Juan 670, Complejo Alem) y cocinas (Comedor Universitario). La rehabilitación y purga de la red solo se ejecutará tras inspección técnica post-evento.
2. **Reserva Estratégica de Agua:** Ante Alerta Naranja/Roja prolongada, la **Subsecretaría de Infraestructura y Servicios** garantizará el stock de agua potable (mínimo 3 litros/persona/día) en los Nodos de Confinamiento, Escuelas Preuniversitarias, Residencias y Comedor, en coordinación con la Secretaría de Bienestar Universitario.
3. **Pluviales y Bombas de Achique:** La **Dirección de Mantenimiento** ejecutará la limpieza preventiva de canaletas y sumideros, y probará las motobombas en subsuelos críticos (San Juan 670, Biblioteca Central) ante todo Alerta Amarillo.

#### 3.4.3. Rescate en Ascensores y Atrapamientos
1. **Desconexión Preventiva:** En Alerta Roja, la **Dirección de Mantenimiento** bajará los ascensores a planta baja y los desconectará preventivamente.
2. **Protocolo de Rescate:** Si el corte de energía es súbito y hay personas atrapadas, el personal de mayordomía utilizará el intercomunicador de cabina para contener a los ocupantes. La **Dirección de Mantenimiento** ejecutará la maniobra de rescate manual (usando llaves de triangulación y palancas de aflojamiento de freno) o activará el SLA de emergencia con la empresa de mantenimiento externo, priorizando edificios de gran altura (San Juan 670).

#### 3.4.4. Ciberseguridad y Continuidad de Datos
1. **Respaldo y Segregación:** La **Dirección de Gestión y Seguridad de la Información** garantizará que los backups críticos estén replicados fuera del sitio o en la nube de contingencia. Durante el Estado de Comunicaciones Degradadas, la red Starlink S1 operará en una VLAN segregada, exclusiva para servidores y RACUNS, bloqueando el tráfico administrativo ordinario para evitar ciberataques oportunistas.
2. **Protección contra Descargas:** Ante Alerta por Tormentas con actividad eléctrica, Sistemas de Información y Telecomunicaciones verificarán la operatividad de los UPS y los tableros de supresión de picos en el Centro de Datos.

#### 3.4.5. Laboratorios Críticos, Cadena de Frío y Riesgo Químico
1. **Freezers y Cultivos:** Las Unidades Académicas, con asistencia técnica de la **Dirección de Mantenimiento** (soporte eléctrico) y auditoría del **SHST**, mantendrán un inventario de freezers críticos (-80°C) conectados a UPS dedicadas o con prioridad de encendido en grupos electrógenos.
2. **Contención de Residuos:** El **SHST** supervisará el protocolo de aseguramiento de reactivos químicos y materiales biológicos ante riesgo de inundación en laboratorios de planta baja o subsuelos.

#### 3.4.6. Espacio Público, Arbolado y Flota Institucional
1. **Zonas de Exclusión Vehicular:** En Campus Palihue y Alem, la **Dirección de Mantenimiento** balizará o cerrará con cadenas los estacionamientos bajo arbolado de gran porte ante Alerta Naranja, mitigando el riesgo material y legal.
2. **Flota en Tránsito:** Si un Alerta Rojo o ACP sorprende a vehículos institucionales (colectivos, móviles de mantenimiento) en la vía pública, los choferes (bajo órdenes de la **Subsecretaría de Infraestructura**) aplicarán el protocolo de "Detención en lugar seguro" (lejos de árboles y cables), confinamiento dentro de la unidad y reporte a Base Central por CH2 o celular.
3. **Remoción Post-Evento:** Mantenimiento coordinará con la aseguradora institucional y el Municipio la remoción rápida de troncos caídos que bloqueen accesos de bomberos o ambulancias.

#### 3.4.7. Evaluación Estructural Post-Evento (Aptitud de Ocupación)
1. Tras un temporal severo, sismo o incendio, ningún edificio podrá ser reocupado hasta que la **Dirección General de Construcciones Universitarias** (con apoyo técnico del Laboratorio de Hidráulica / Ingeniería Civil si se requiere) realice la inspección visual y estructural.
2. Construcciones emitirá el **"Certificado de Aptitud de Ocupación"** o dictaminará la clausura preventiva, informe que será elevado al CDE para que el Rectorado autorice la reanudación de actividades (Proceso P9).

#### 3.4.8. Soporte Edilicio a Comedor y Residencias Universitarias
1. **Comedor Universitario:** La infraestructura del Comedor será evaluada por **Construcciones y Mantenimiento** para determinar si, tras un evento, puede operar como "Centro de Acopio y Refugio Primario" para la comunidad UNS aislada, o si debe ser clausurado preventivamente por riesgo de gas/estructural.
2. **Residencias:** La **Subsecretaría de Infraestructura** garantizará que las Residencias de Bienestar Universitario cuenten con rutas de evacuación interna señalizadas, iluminación de emergencia operativa y stock de alimentos no perecederos, en articulación con la Secretaría de Bienestar Universitario.

---
### 3.3. PROTOCOLOS DE INFRAESTRUCTURA CRÍTICA, MANTENIMIENTO Y SERVICIOS ESENCIALES

La resiliencia de las comunicaciones (RACUNS y medios primarios) debe estar sustentada por la integridad de la infraestructura física, los servicios esenciales y la seguridad de la información. Esta sección unifica el mantenimiento preventivo y los protocolos de respuesta, asignándolos a las direcciones específicas de la UNS conforme a su estructura orgánica.

#### 3.3.1. Matriz de Responsabilidades Técnicas por Dirección

| Dirección / Servicio UNS | Riesgo Crítico Asociado | Directiva Técnica Principal |
| :--- | :--- | :--- |
| **Dirección de Mantenimiento** | Corte de gas, anegamientos, arbolado, flota vehicular, ascensores. | Ejecución de cortes preventivos, limpieza de sumideros, balizamiento de zonas de exclusión, protocolo de choferes y rescate en ascensores. |
| **Dirección General de Construcciones Universitarias** | Daño estructural, colapso de cubiertas, patrimonio histórico. | Inspección de techos, protección de archivos, y emisión del "Certificado de Aptitud de Ocupación" post-evento. |
| **Servicios de Seguridad e Higiene en el Trabajo (SHST)** | Riesgo químico/biológico, EPP, primeros auxilios, auditoría de laboratorios. | Supervisión de protocolos de laboratorios críticos, coordinación de brigadas y contención de residuos peligrosos. |
| **Dirección de Gestión y Seguridad de la Información** | Ciberataques, pérdida de datos, vulnerabilidad de servidores. | Verificación de backups externos, segregación de redes de emergencia y ciberseguridad en modo contingencia. |
| **Dirección General de Sistemas de Información** | Caída de servicios digitales, Moodle, web institucional. | Conmutación a servidores de respaldo y priorización de tráfico informático crítico. |
| **Dirección General de Telecomunicaciones** | Caída de fibra óptica, redes de datos, RACUNS. | Conmutación manual a Starlink S1, soporte a Sistemas de Información y mantenimiento de RACUNS. |

#### 3.3.2. Mantenimiento Preventivo de Rutina y Estacional
Las tareas de preparación previa a la temporada de riesgos (primavera-verano) y de rutina anual son ineludibles y se registran en el **Checklist de Mantenimiento Preventivo (Anexo A.3)**:
1. **Arbolado y Espacio Público:** Inspección y poda preventiva semestral en Campus Palihue y predios preuniversitarios. Balizamiento o cierre con cadenas de estacionamientos bajo arbolado de gran porte ante Alerta Naranja.
2. **Pluviales y Cubiertas:** Limpieza periódica de canaletas y sumideros; inspección y sellado de cubiertas (especialmente en patrimonio histórico y subsuelos críticos).
3. **Energía de Respaldo:** Pruebas bajo carga de grupos electrógenos (ATS) y motobombas de achique; verificación semestral de UPS, bancos de baterías y tableros de transferencia.

#### 3.3.3. Protocolos de Actuación ante Alerta y Emergencia
1. **Corte Preventivo de Gas:** Ante Alerta Roja, Aviso a Muy Corto Plazo (ACP) o sismo, la **Dirección de Mantenimiento** procederá al corte de las válvulas maestras de gas en calderas y cocinas (Comedor Universitario). La rehabilitación solo se ejecutará tras inspección técnica post-evento.
2. **Reserva Estratégica de Agua:** Ante Alerta Naranja/Roja prolongada, la **Subsecretaría de Infraestructura** garantizará el stock de agua potable (mínimo 3 litros/persona/día) en los Nodos de Confinamiento, Escuelas Preuniversitarias y Residencias.
3. **Rescate en Ascensores:** En Alerta Roja, Mantenimiento bajará los ascensores a planta baja y los desconectará. Si el corte es súbito y hay personas atrapadas, Mayordomía usará el intercomunicador para contener, y Mantenimiento ejecutará la maniobra de rescate manual o activará el SLA de emergencia con la empresa externa.
4. **Flota Institucional en Tránsito:** Si un Alerta sorprende a vehículos institucionales en la vía pública, los choferes aplicarán el protocolo de "Detención en lugar seguro" (lejos de árboles y cables), confinamiento dentro de la unidad y reporte a Base Central por CH2 o celular.
5. **Evaluación Estructural Post-Evento (Aptitud de Ocupación):** Tras un temporal severo o sismo, ningún edificio podrá ser reocupado hasta que la **Dirección General de Construcciones Universitarias** emita el "Certificado de Aptitud de Ocupación" o dicte la clausura preventiva, informe que se elevará al CDE.

#### 3.3.4. Ciberseguridad, Laboratorios Críticos y Patrimonio
1. **Respaldo y Segregación de Datos:** La **Dirección de Gestión y Seguridad de la Información** garantizará que los backups críticos estén replicados fuera del sitio. Durante el Estado de Comunicaciones Degradadas, la red Starlink S1 operará en una VLAN segregada, bloqueando el tráfico administrativo ordinario para evitar ciberataques oportunistas.
2. **Cadena de Frío y Riesgo Químico:** Las Unidades Académicas, con asistencia de **Mantenimiento** (soporte eléctrico) y auditoría del **SHST**, mantendrán un inventario de freezers críticos (-80°C) conectados a UPS dedicadas o con prioridad de encendido en grupos electrógenos. El SHST supervisará el aseguramiento de reactivos ante riesgo de inundación.
3. **Archivos y Bibliotecas:** Protocolo de "Elevación Preventiva" (tarimas) y provisión de cobertores de polietileno de emergencia en salas de archivos críticos y Biblioteca Central, con bombas de achique exclusivas para subsuelos patrimoniales.
---

## 4. MEDIOS DE COMUNICACIÓN PRIMARIOS DEL PROCESO (COMERCIALES E INSTITUCIONALES)

### 4.1. Propósito y ubicación en la arquitectura

1. Los medios descritos en esta sección constituyen el **método principal** para la transmisión de la información del proceso de emergencia (procesos P1→P10 del Documento A) entre los distintos actores intervinientes, en modalidad **punto a punto** o **grupal**, en condiciones normales y de degradación parcial.
2. El sistema **RACUNS** (Sección 5) es el sistema **alternativo** de comunicaciones: pasa a ser medio principal únicamente ante la declaración del Estado de Comunicaciones Degradadas (5.3) o ante falla de los medios primarios conforme a 4.5.
3. Ninguna decisión crítica del proceso dependerá de un único medio, canal o proveedor externo. Todo flujo crítico contará con al menos un medio de respaldo de naturaleza distinta (red de datos, red celular, voz conmutada o radio).

### 4.2. Inventario de medios y administración

| Medio | Naturaleza | Modalidad | Administración responsable | Uso principal en el proceso | Dependencia externa | Limitación / consideración |
| --- | --- | --- | --- | --- | --- | --- |
| **Alerthor** | Servicio de notificación masiva de terceros (contratado) | Masiva y por segmentos | **SHST** (administración y operación) con Vocería (contenidos) | Aviso masivo inmediato al CDE y a públicos internos; novedades críticas | Proveedor + internet/red celular | Riesgo de cautividad; migración prevista al sistema propio (4.6) |
| **Sistema propio** (en desarrollo) | Sistema institucional de notificación masiva | Masiva y por segmentos | SHST / Telecomunicaciones | Asumir las funciones de Alerthor con datos y padrón propios | Internet/red celular | Objetivo a **mediano plazo**; entrada en operación sujeta a pruebas y migración (4.6) |
| **WhatsApp** | Mensajería instantánea comercial | Punto a punto y grupal | Administrador designado por grupo oficial | Coordinación operativa por público; reportes de estado | Proveedor + datos/celular | Congestión en eventos masivos; sin garantía de entrega; carácter informal |
| **Telegram** | Mensajería instantánea comercial | Punto a punto, grupal y canal | Administrador designado por grupo oficial | Respaldo de grupos WhatsApp; difusión uno-a-muchos por canal | Proveedor + datos/celular | Menor penetración en algunos públicos |
| **Correo institucional** | Correo electrónico institucional | Punto a punto y listas de distribución | Telecomunicaciones | Formalización de recomendaciones, decisiones y actas con trazabilidad | Servicio de correo + internet | Latencia; no es canal de confirmación inmediata |
| **SMS masivo** | Mensajería de red celular | Masiva y punto a punto | Telecomunicaciones (contrato con operador) / SHST | Aviso masivo ante caída de datos; públicos sin smartphone | Operador celular | Costo por envío; longitud de mensaje; dependencia del operador |
| **Llamadas celulares** | Voz conmutada de red celular | Punto a punto | Cada actor (padrón oficial vigente) | Confirmación de recepción, escalamiento y coordinación punto a punto | Operador celular | Congestión con alta demanda; comunicación secuencial |
| **Futuros desarrollos** | A definir | A definir | Telecomunicaciones / SHST | Incorporación sujeta a los criterios de 4.6 | A evaluar | No se utilizarán en operación real antes de su adopción formal y prueba |

### 4.3. Flujos del proceso y medios por actor

| Flujo | Emisor → Receptor | Modalidad | Medio primario | Medio respaldo | Confirmación de recepción | Registro |
| --- | --- | --- | --- | --- | --- | --- |
| **F1** Aviso de alerta | Nodo Central → CDE | Punto a punto + grupal | Alerthor + grupo WhatsApp CDE | Llamada celular a integrantes | ACK o lectura dentro de 15 min | Libro de guardia del Nodo + Ficha del Alerta |
| **F2** Recomendación técnica | SHST / CDE → Rector | Punto a punto | Correo institucional + llamada | WhatsApp punto a punto | Respuesta explícita | Acta o minuta del CDE |
| **F3** Decisión | Rector → Nodo Central y Vocería | Punto a punto | Llamada + correo institucional | WhatsApp punto a punto | Respuesta explícita | Registro de decisión |
| **F4** Novedad operativa a áreas | Nodo Central / Vocería → Decanos, Directores, Escuelas, Mayordomías | Grupal + masiva | Alerthor + grupos WhatsApp/Telegram por público | SMS masivo | Acuse o respuesta del responsable de área | Registro de Difusión y libro del Nodo |
| **F5** Reporte de estado | Mayordomías, Escuelas, Brigadas → Nodo Central | Punto a punto | WhatsApp o llamada al Nodo Central | RACUNS CH1 / CH3 | Acuse del Nodo | Libro de guardia (cada 30 min en Naranja/Rojo) |
| **F6** Estado de comunicaciones | Telecomunicaciones → Nodo Central y CDE | Punto a punto + grupal | Grupo WhatsApp técnico + llamada | RACUNS CH1 | Respuesta explícita | Registro técnico de Telecomunicaciones |
| **F7** Coordinación externa | UNS ↔ Defensa Civil / COE | Punto a punto | Telefonía de guardia + correo institucional | RACUNS CH4 | Respuesta explícita | Libro de guardia del Nodo |
| **F8** Difusión masiva a la comunidad | Vocería → comunidad y medios | Masiva | Se rige por el **Documento C** | Se rige por el Documento C | Según Documento C | Registro de Difusión (Documento C) |

### 4.4. Reglas de operación de los medios primarios

1. **Padrón oficial vigente.** El **SHST** y **Telecomunicaciones** administran las plataformas y los **padrones** de contacto; cada área es responsable de informar sus altas, bajas y cambios dentro de las 48 horas. El padrón se verifica y depura con frecuencia trimestral y antes de cada simulacro integral.
2. **Mensaje oficial único.** Solo tienen validez los mensajes originados en el Nodo Central o en la Vocería. Los grupos oficiales reenvían el texto oficial sin agregados ni interpretación propia (coherente con Documento C, Sección 10).
3. **Confirmación de recepción y escalamiento.** Todo mensaje crítico requiere confirmación (acuse, lectura o respuesta). Sin confirmación dentro de los **15 minutos**, se escala al medio de respaldo (llamada celular) y, de persistir la falta de confirmación, al enlace radial RACUNS del destinatario.
4. **Trazabilidad.** Toda emisión crítica y su confirmación se registran (fecha, hora, medio, destinatarios, operador), conforme al principio de seguridad y trazabilidad y a los registros del Documento A y del Documento C.
5. **Protección de datos personales.** Los padrones y los datos de contacto se tratan conforme a la Ley N° 25.326 y se utilizan exclusivamente para emergencias, simulacros y pruebas.
6. **Disciplina de grupos.** Cada grupo oficial tiene administrador designado; se prohíben cadenas, contenido ajeno a la emergencia y decisiones por grupo: los grupos coordinan, no deciden.
7. **Orden de uso ante degradación parcial.** Caída de datos/internet: priorizar SMS y llamadas. Congestión de voz conmutada: llamadas breves con protocolo predefinido y confirmación por SMS.
8. **Interoperabilidad externa.** Los flujos con Defensa Civil, Municipio y otras instituciones usan los medios oficiales convenidos y, como respaldo, el enlace CH4 de RACUNS.

### 4.5. Degradación y traspaso a RACUNS

1. **Degradación parcial:** falla de uno o más medios primarios sin caída general. Se aplica el orden de uso de 4.4 (7) y el Nodo Central registra medios afectados y flujos reasignados.
2. **Estado de Comunicaciones Degradadas:** caída o inutilización de los medios convencionales (telefonía celular, internet y/o energía de red), verificada por el Nodo Central y declarada por el CDE conforme a 5.3. RACUNS pasa a ser medio principal de coordinación; los medios primarios quedan relegados a uso oportunista cuando recuperen servicio.
3. **Traspaso:** declarada la degradación, el Nodo Central notifica el cambio de medio principal a todos los actores por RACUNS y por todo medio primario aún operativo, asentando hora y medios en el libro de guardia.
4. **Retorno:** verificada la estabilidad de los medios primarios, Telecomunicaciones ejecuta pruebas de servicio, notifica el retorno por ambos sistemas y registra el cierre del período de degradación; RACUNS retoma su rol alternativo.

### 4.6. Evolución, sistema propio y adopción de nuevos medios

1. **Sistema propio (en desarrollo):** alcance objetivo: padrón multi-público propio; emisión multicanal (notificación push, SMS, correo y voz); registro de entregas y confirmaciones; propiedad local de datos y padrones; interfaces documentadas. Su desarrollo e implementación constituyen un **objetivo a mediano plazo**. Su entrada en operación requiere prueba exitosa en al menos un simulacro integral y un ciclo de operación en paralelo con Alerthor.
2. **Evitación de cautividad:** exportación periódica de padrones y registros; cláusulas de portabilidad y APIs documentadas en los contratos con terceros.
3. **Criterios de adopción de futuros medios:** (a) redundancia con medios existentes; (b) trazabilidad y registro; (c) accesibilidad; (d) protección de datos personales; (e) operación probada en al menos un simulacro; (f) administración y costo sostenibles; (g) sin dependencia de proveedor único.
4. **Incorporación:** todo medio nuevo se incorpora mediante actualización de esta sección (inventario y flujos), prueba conforme a la Sección 7 y comunicación formal a los actores del proceso.

---

## 5. RACUNS – RED ALTERNATIVA DE COMUNICACIONES DE LA UNS

### 5.1. Definición, propósito y alcance

Red autónoma de comunicaciones basada en tecnología VHF, destinada a asegurar la conectividad institucional y operativa ante interrupciones de los servicios convencionales de telecomunicaciones y energía.

- **Propósito principal:** comunicación interna entre dependencias universitarias.
- **Propósito secundario:** integración con instituciones externas mediante convenios firmados por el Rectorado, poniendo la red a disposición de la comunidad en emergencias mayores.
- **Alcance:** Campus Palihue, Colón 80, Complejo Alem, Escuelas Medias, Anexo Radio y predios de interés.

### 5.2. Fundamento local (antecedentes)

Temporal e inundación del **07/03/2025**, tornado del **17/12/2023** y apagón del **16/06/2019**: interrupciones simultáneas de energía, telefonía celular e internet. Durante 2025 la UNS colaboró con Defensa Civil mediante el monitoreo del arroyo Napostá Grande (Unidad Remota de Telemetría Puente Canessa) y el Complejo Alem como centro de acopio de donaciones. Experiencia piloto validada en la **Feria Gastronómica del Sudoeste Bonaerense 2025** (20.000 asistentes, colapso de telefonía celular, operación efectiva de handies VHF por operadores sin experiencia previa).

### 5.3. Criterio de activación

RACUNS se activa como medio principal de coordinación cuando el Nodo Central verifique la caída o inutilización de los medios convencionales (telefonía celular, internet y/o energía de red) y el CDE declare el **Estado de Comunicaciones Degradadas**. La verificación y la declaración quedarán asentadas en el libro de guardia.

### 5.4. Infraestructura

| Nodo / Equipamiento | Emplazamiento | Rol operativo |
| --- | --- | --- |
| **Repetidor principal VHF (50 W)** | Complejo Alem, edificio BBYF (torre metálica de 10 m con pararrayos y puesta a tierra; altura relativa 28 m) | Troncal CH1; antena omnidireccional de alto rendimiento, duplexor y gabinete protegido con ventilación y protección contra sobretensiones |
| **BASE CENTRAL** | Mayordomía San Juan 670 (24 hs) | Control troncal, libro de guardia, despacho y **Sala de Crisis primaria** |
| **BASE RECTORADO** | Colón 80 | Nodo de comando de autoridades y punto de enlace institucional |
| **BASE PALIHUE** | Edificio Central del Campus Palihue | Supervisión del predio abierto y accesos |
| **BASE LH** | Laboratorio de Hidráulica, Departamento de Ingeniería | Nodo técnico y respaldo del troncal (5.8) |
| **ANEXO RADIO (Campus Radio)** | Edificio Anexo de la Radio AM UNS | Radiobase fija bibanda integrada al troncal; cadena de transmisión AM con respaldo energético; **Sala de Crisis alternativa**; nodo de la Capa 4 de difusión masiva; portador del nodo Starlink **S2** (5.10) |
| **Radiobases bibanda (proyectadas)** | Nodos Colón 80, Escuelas Medias y Campus Palihue | Expansión de cobertura sujeta a pruebas de campo (7.1) |
| **Radiobase móvil** | Unidad vehicular designada | Equipo bibanda + kit Starlink **S3** (5.10); repetidor temporal ante caída del troncal (5.8) |
| **Nodo Meshtastic Palihue** | Campus Palihue | Nodo único de malla LoRa, autónomo solar (Capa 5) |
| **Flota de handies** | 12 unidades bibanda operativas | Canales pregrabados con responsable por sector, rol o responsabilidad |

### 5.5. Plan de canales

| Canal | Modo | Uso operativo y disciplina |
| --- | --- | --- |
| **CH1** | Repetidor Alem (semidúplex) | Troncal de Mando y Emergencia: exclusivo directivas del CDE, novedades de Bases y reportes críticos. Escucha permanente en Naranja/Rojo. Prohibido el tráfico secundario |
| **CH2** | Simplex operativo | Coordinación logística y cuadrillas: mantenimiento edilicio, choferes, maniobras de generadores y grupos técnicos |
| **CH3** | Simplex local | Coordinación interna de predio: mayordomos, brigadistas y personal de seguridad dentro del campus |
| **CH4** | Enlace | Interoperabilidad con el COE de Defensa Civil Bahía Blanca |
| **Simplex de contingencia** | Simplex pregrabado | Frecuencia de contingencia ante caída del repetidor (5.8) |
| **Memorias adicionales** | Simplex | Frecuencias pregrabadas por grupos operativos (mantenimiento, SHST, eléctricos, autoridades, brigadistas, logística) |

> **Régimen del Anexo Técnico de Radiocomunicaciones:** los valores de frecuencias, canales, códigos y subtonos constituyen el **Anexo Técnico de Radiocomunicaciones**, documento de carácter **RESTRINGIDO**: no se publica en repositorios abiertos ni se difunde fuera de los destinatarios del punto 1.2. La versión pública de este Documento B omite dichos valores; cada equipo se entrega programado por Telecomunicaciones contra acta de entrega.

### 5.6. Asignación de la flota de handies (12 unidades)

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

### 5.7. Metodología bibanda y subcapas de retransmisión

1. **Canal principal VHF:** enlace por línea de vista, libre de interferencia por obstáculos (árboles, edificios de hormigón), para troncal y enlaces entre nodos.
2. **Canal secundario UHF:** conectividad en espacios cerrados o por rebotes, donde VHF no alcanza.
3. **Subcapa de retransmisión:** todo mensaje recibido por UHF en un nodo que no alcance punto a punto su destino será retransmitido por el operador del nodo en VHF hacia el siguiente nodo; en tránsito entre nodos, si VHF no fuera posible, se intentará UHF por proximidad.
4. Los handies permanecerán en escucha del canal troncal e interactuarán con el sistema según su posición lo favorezca.

### 5.8. Procedimiento de degradación del troncal y caída del repetidor

| Paso | Acción |
| --- | --- |
| **Detección** | La BASE CENTRAL advierte la caída del repetidor por ausencia de retorno en CH1 o por reporte de dos o más estaciones sin acceso al troncal |
| **Migración inmediata** | Todas las estaciones y handies migran a la frecuencia simplex de contingencia pregrabada (Anexo Técnico restringido), que pasa a operar como canal troncal provisional de mando y emergencia |
| **Repetidor temporal** | Si la caída se prolonga más allá de 30 minutos y existe disponibilidad, la radiobase móvil se despliega y asume el rol de repetidor temporal; hasta su puesta en servicio, la BASE LH y la BASE ANEXO RADIO sostienen el control del troncal provisional por turnos definidos por Telecomunicaciones |
| **Restitución** | Verificada la recuperación del repetidor principal, Telecomunicaciones ordena el regreso a CH1 y asienta el evento, la duración y las estaciones afectadas en el Libro de Prueba Radial (Anexo A.2) |
| **Prueba** | El procedimiento completo se ejercita con frecuencia trimestral (7.2), incluyendo migración, repetidor temporal y restitución |

### 5.9. Arquitectura en capas (redundancia funcional)

| Capa | Tecnología | Rol | Estado | Fortalezas / límites |
| --- | --- | --- | --- | --- |
| **1 – Troncal** | VHF repetidora (Alem, 50 W) + bases fijas (SJ670, Colón 80, Palihue, LH, Anexo Radio) | Mando y emergencia (CH1) | Operativa | Línea de vista, cobertura urbana; ante caída del repetidor opera 5.8 |
| **2 – Proximidad** | UHF simplex / rebotes | Interior de edificios, sombra radioeléctrica | Operativa | Penetra hormigón; menor alcance |
| **3 – Datos** | Starlink en tres modalidades: **S1** respaldo fijo, **S2** nodo Anexo Radio, **S3** kit móvil (5.10) | Internet de contingencia; réplica de servidores Alem↔Palihue; emisión de comunicados web; enlace alternativo AM–FM | Operativa | Satelital, independiente; requiere apuntamiento y energía; conmutación manual en S1 |
| **4 – Difusión masiva** | Radio AM UNS (Anexo Radio) + FM UTN-FRBB (convenio) | Comunicados a la comunidad cuando cae todo lo digital | Operativa (AM) / convenio en curso (FM) | Alcance masivo; unidireccional |
| **5 – Malla** | Meshtastic / LoRa – nodo único en Campus Palihue, autónomo solar | Mensajería de texto sin infraestructura; último recurso de brigadas y puestos de terreno | Operativa (nodo único) | Autónoma, bajo consumo, ubicación estratégica; sin voz; cobertura limitada al nodo |

> **Nota de accesibilidad:** los criterios de formatos accesibles (sonoro, visual de alto contraste, textual simple) de los mensajes y alarmas se rigen por el Documento C; este documento provee el soporte técnico de megafonía, alarmas en predios y emisión radial.

> **Nota de continuidad (Capa 3):** los objetivos de recuperación (RTO/RPO) del enlace de respaldo S1 y del Centro de Datos serán definidos por la Dirección General de Telecomunicaciones dentro de los **60 días hábiles** posteriores a la aprobación de este documento, con alcance limitado a **servidores y su infraestructura informática**. Hasta dicha definición rige como criterio mínimo: réplica diaria de servicios críticos y enlace satelital de contingencia disponible y probado.

### 5.10. Enlace satelital de contingencia (Starlink): tres modalidades

#### S1 – Respaldo fijo (Dirección General de Telecomunicaciones)
- **Función:** enlace de respaldo entre los **servidores del Complejo Alem** y su **respaldo en Campus Palihue** ante degradación o caída del enlace de fibra óptica actual.
- **Alcance:** exclusivamente **servidores y su infraestructura informática**; no transporta tráfico administrativo ordinario.
- **Conmutación MANUAL:** ante degradación de la fibra, la conmutación al enlace S1 es **manual** y se ejecuta conforme al siguiente procedimiento:
  1. **Detección:** monitoreo del Centro de Datos / Telecomunicaciones advierte degradación o caída del enlace de fibra.
  2. **Decisión:** la Dirección General de Telecomunicaciones (o el responsable designado) dispone la conmutación al enlace S1.
  3. **Ejecución:** conmutación manual de los servicios de réplica y respaldo al enlace S1 y verificación de la replicación Alem↔Palihue.
  4. **Registro:** asiento en libro de guardia con fecha, hora, causa, operador y servicios conmutados.
  5. **Retorno:** restitución manual a la fibra una vez verificada su estabilidad, con registro.
- **Prueba:** simulacro trimestral de conmutación manual con medición de tiempos (7.2).

#### S2 – Nodo de Radio AM (Anexo Radio)
- **Función:** nodo Starlink en el Anexo Radio para **transmisión de novedades a la comunidad** (soporte de emisión de la Capa 4) y como **enlace alternativo para la interconexión con la FM de la UTN-FRBB**.
- **Dominio y destino:** la **Vocería Institucional o el CDE** definen su destino **fijo o itinerante** según necesidad operativa.
- **Operación:** lo operan los **técnicos designados por la Vocería**, en coordinación con Telecomunicaciones para contrato, cuenta y ciberseguridad.
- **Prueba:** prueba trimestral de emisión vía S2 y del enlace alternativo con la FM (7.2).

#### S3 – Kit móvil en vehículo (radiobase móvil)
- **Función:** asistencia en campo: **Sala de Crisis alternativa, tienda de campaña en territorio**, consulta de radares meteorológicos y emisión de comunicados web.
- **Operadores:** mínimo dos operadores entrenados por turno potencial (Telecomunicaciones o LH); tiempo objetivo de puesta en servicio menor a 30 minutos.
- **Rol radial:** ante caída del repetidor principal asume el rol de repetidor temporal (5.8).

#### Disposiciones comunes a S1, S2 y S3
- **Titularidad y contrato:** la cuenta, el contrato de servicio y el equipamiento son administrados por la Dirección General de Telecomunicaciones, con responsable titular y suplente designados.
- **Ciberseguridad básica:** red de contingencia segregada de la red institucional; contraseña única y distinta de la de fábrica; firmware actualizado antes de cada prueba; sin exposición de servicios de gestión desde internet; registro de accesos durante la emergencia.
- **Pruebas:** cada modalidad se prueba con frecuencia trimestral con registro de resultado y tiempos (Anexo A.3).

### 5.11. Disciplina radial, prueba semanal y capacitación

- **Protocolo de enlace:** identificación con el indicativo del puesto asignado en toda transmisión; mensajes breves, claros y estructurados; confirmación de recepción por repetición (colación).
- **Disciplina de canales:** prioridad absoluta de CH1 para mando y emergencia; el tráfico de trabajo, logístico o rutinario se cursará estrictamente por CH2/CH3 o por las memorias de grupo pregrabadas.
- **Prueba radial semanal:** día y hora definidos por la Dirección de Telecomunicaciones; cada Base (incluidas BASE LH y BASE ANEXO RADIO) y handy reportará ubicación, estado del equipo y nivel de batería. El resultado será asentado en el **Libro de Prueba Radial (Anexo A.2)** y cualquier falla deberá ser reportada a Telecomunicaciones dentro de las 24 horas para su inmediata subsanación.
- **Capacitación para operadores no especializados:** la Dirección de Telecomunicaciones, en articulación con la Jefatura de Higiene y Seguridad (SHST), dictará módulos de instrucción práctica obligatoria destinados a todo el personal asignado a la flota de handies que no posea formación técnica previa en radiocomunicaciones. Contenido mínimo: protocolo básico de enlace, códigos de brevedad, disciplina de escucha (pensar antes de transmitir), procedimiento de caída del repetidor (5.8) y procedimientos específicos para reportar emergencias.

### 5.12. Marco regulatorio

- **Licencia ENACOM vigente** para banda VHF (expediente CNC 11660/1998). Telecomunicaciones mantendrá el expediente técnico y la documentación de la licencia actualizados y disponibles para auditoría.
- **Uso de UHF:** se realizará en frecuencia fuera de la reservada para uso de radioaficionados. El trámite de regularización ante ENACOM será iniciado por la Dirección General de Telecomunicaciones dentro de los **60 días hábiles** posteriores a la aprobación de este documento; su completamiento constituye tarea de mediano plazo con reporte periódico al CDE hasta su cierre.

### 5.13. Redundancia energética por nodo

**Red eléctrica (primaria) → UPS / banco de baterías 24–48 h (secundaria) → grupo electrógeno institucional o paneles solares (terciaria).**

- El **nodo Meshtastic Palihue** posee autonomía energética solar propia e independiente del esquema general.
- El reabastecimiento de combustible y la rotación de baterías para eventos que superen las 48 horas de autonomía constituyen acción a cargo de la **Subsecretaría de Infraestructura y Servicios**.

### 5.14. Mantenimiento del sistema

1. Inspección mensual de antena, conexiones y bajada coaxial.
2. Verificación semestral del banco de baterías y protecciones eléctricas.
3. Actualización de firmware o parámetros del sistema de control.
4. Prueba radial semanal (5.11).
5. Verificación semestral del nodo Meshtastic Palihue (panel solar, baterías y mensajería).

> **Unidad técnica designada:** Laboratorio de Hidráulica del Departamento de Ingeniería, con apoyo de Telecomunicaciones.

### 5.15. Proyecciones del sistema

- **Radioclubes locales:** en Bahía Blanca operan dos radioclubes; la vinculación mediante convenio de colaboración técnica se proyecta como tarea de **largo plazo**, orientada a enlaces HF de contingencia y soporte de operadores habilitados en emergencias de magnitud excepcional. A la fecha de esta versión no existe convenio iniciado.
- **Digitalización:** evaluación de migración parcial o dualidad tecnológica hacia DMR o TETRA si se requirieran trunking, cifrado o gestión avanzada de canales.
- **Expansión de nodos:** radiobases bibanda proyectadas en Colón 80, Escuelas Medias y Campus Palihue, sujetas a resultado de las pruebas de campo (7.1); evaluación de nodos Meshtastic adicionales sujeta a prueba del nodo único existente.
- **Notificaciones masivas:** se registra el servicio **Alerthor (tercero)** y el **proyecto de desarrollo de un sistema propio** de similares características para evitar cautividad tecnológica (objetivo a mediano plazo, ver 4.6).

---

## 6. TOPOLOGÍA DE LA RED

```text
                      [REPETIDOR VHF ALEM – BBYF]
                        (50 W · torre 10 m · 28 m)
                                    │  CH1 semidúplex
       ┌──────────────┬─────────────┼─────────────┬──────────────┐
       ▼              ▼             ▼             ▼              ▼
  [BASE CENTRAL] [BASE RECTORADO] [BASE      [BASE LH]     [RADIOBASES
   SJ670 24 h     Colón 80        PALIHUE]    Lab. Hidr.    BIBANDA
   Sala de Crisis nodo de comando Ed.Central  nodo técnico  PROYECTADAS:
   primaria       de autoridades  + nodo Mesh nodo técnico  Colón 80, Esc.
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
        repetidor temporal ante caída del troncal (5.8)
  [ENLACE S1] ── servidores Alem ↔ respaldo Palihue ·
        conmutación MANUAL ante degradación de fibra (5.10)
  [NODO MESH PALIHUE] ── Capa 5 · único · autónomo solar (5.9)
```
---
## 7. PRUEBAS DE CAMPO Y VALIDACIÓN TÉCNICA

### 7.1. Plan de pruebas de campo

Se ejecutará una prueba de campo integral con radiobases y handies en los nodos **Colón 80, Campus Palihue, Escuelas Preuniversitarias, Anexo Radio y BASE LH**, con la siguiente secuencia:

1. Coordinación previa con mayordomías y responsables de predio; asignación de operadores por nodo.
2. Verificación de energía, puesta a tierra y estado de antenas en cada nodo.
3. Prueba de cobertura por puntos fijos por predio: plantas bajas, subsuelos, terrazas, aulas críticas, estacionamientos y sendas arboladas.
4. Prueba comparativa VHF vs. UHF y validación de la subcapa de retransmisión entre nodos.
5. Prueba de autonomía energética con corte simulado de red en al menos un nodo.
6. Prueba de interoperabilidad CH4 con Defensa Civil, cuando la autoridad municipal esté disponible.
7. Verificación del enlace VHF y del respaldo energético del Anexo Radio, y del rol de la BASE LH como respaldo del troncal.
8. Verificación del nodo Meshtastic Palihue (mensajería y autonomía solar).
9. Registro de resultados en la **Planilla de Prueba de Campo (Anexo A.1)** e informe de sombras radioeléctricas para ajuste de ingeniería.

### 7.2. Pruebas periódicas complementarias

| Prueba | Frecuencia | Responsable |
| --- | --- | --- |
| Prueba radial semanal (5.11) | Semanal | Telecomunicaciones |
| Transmisión conjunta AM UNS – FM UTN-FRBB | Trimestral | Vocería + Telecomunicaciones |
| Conmutación energética de nodos críticos (ATS, UPS, generador móvil) | Semestral | Telecomunicaciones + Infraestructura |
| Procedimiento de caída del repetidor (5.8) | Trimestral | Telecomunicaciones |
| Despliegue y apuntamiento Starlink S3 (5.10) | Trimestral | Telecomunicaciones |
| **Conmutación MANUAL del enlace S1 fibra→Starlink (5.10)** | Trimestral | Telecomunicaciones |
| **Emisión vía Starlink S2 y enlace alternativo con la FM (5.10)** | Trimestral | Vocería + Telecomunicaciones |
| Verificación del nodo Meshtastic Palihue (5.14) | Semestral | Telecomunicaciones + LH |
| Simulacro integral con activación completa de RACUNS y Nodo Central | Anual | Comité + Telecomunicaciones |

---

## 8. INDICADORES TÉCNICOS Y MEJORA CONTINUA

| Indicador | Meta |
| --- | --- |
| Cumplimiento de prueba radial semanal | 100 % |
| Fallas radiales reportadas subsanadas dentro de las 24 h | ≥ 95 % |
| Cobertura sin sombras radioeléctricas en áreas críticas de cada predio | 100 % |
| Autonomía energética de nodos ante corte de red | ≥ 24 h |
| Pruebas trimestrales AM/FM ejecutadas | 100 % |
| Pruebas trimestrales de caída del repetidor ejecutadas | 100 % |
| Pruebas trimestrales de despliegue Starlink S3 ejecutadas | 100 % |
| Simulacros trimestrales de conmutación manual S1 ejecutados | 100 % |
| Pruebas trimestrales de emisión S2 y enlace alternativo FM ejecutadas | 100 % |
| Nodo Meshtastic Palihue operativo en verificación semestral | 100 % |
| Checklist de mantenimiento preventivo sin observaciones abiertas | 100 % |

- Todo desvío se registrará y tratará conforme al ciclo **PDCA** del Documento A (Sección de Mejora Continua). El registro de comunicaciones críticas y las revisiones post-incidente se rigen por el Documento A.
- Los resultados de pruebas y mantenimientos alimentarán la revisión anual del presente documento mediante control de versiones.
- Las modificaciones de frecuencias, canales o emplazamientos requerirán aprobación de la Dirección de Telecomunicaciones y actualización del **Anexo Técnico de Radiocomunicaciones (restringido)**.

---

## ANEXO A – PLANILLAS TÉCNICAS DE REGISTRO

### A.1. Planilla de Prueba de Campo (plantilla)

| Ítem | Nodo / predio | Punto de prueba | Canal / modalidad (CH1 / CH2 / CH3 / UHF) | Resultado de señal (1–5) | Sombra radioeléctrica (S/N) | Batería | Observaciones |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |

### A.2. Libro de Prueba Radial Semanal (plantilla)

| Fecha | Hora | Estación (Base / handy ID) | Operador | Estado del equipo | Nivel de batería | Novedades / fallas | Reporte a Telecomunicaciones (S/N y hora) |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |

### A.3. Checklist de Mantenimiento Preventivo (plantilla)

| Sistema | Tarea | Frecuencia | Responsable | Fecha | Resultado | Observaciones |
| --- | --- | --- | --- | --- | --- | --- |
| Pluviales y bombas de achique | Limpieza de sumideros; prueba de bombas | Semestral / pre-temporada | Infraestructura |  |  |  |
| Cubiertas y desagües | Inspección y sellado | Anual / pre-temporada | Infraestructura |  |  |  |
| Arbolado | Poda preventiva de ejemplares añejos | Semestral | Infraestructura |  |  |  |
| Grupos electrógenos (ATS) | Prueba bajo carga | Trimestral | Telecomunicaciones / Infraestructura |  |  |  |
| UPS y bancos de baterías | Verificación de autonomía y protecciones | Semestral | Telecomunicaciones |  |  |  |
| Repetidor VHF Alem | Inspección de antena, coaxial y gabinete | Mensual | LH / Telecomunicaciones |  |  |  |
| Bases y handies (incl. BASE LH y Anexo Radio) | Prueba radial y estado de equipos | Semanal | Telecomunicaciones |  |  |  |
| Starlink S1 (respaldo fijo) | Simulacro de conmutación manual fibra→Starlink | Trimestral | Telecomunicaciones |  |  |  |
| Starlink S2 (nodo Anexo Radio) | Prueba de emisión y enlace alternativo con FM | Trimestral | Vocería / Telecomunicaciones |  |  |  |
| Starlink S3 (kit vehicular) | Despliegue y apuntamiento | Trimestral | Telecomunicaciones |  |  |  |
| Nodo Meshtastic Palihue | Panel solar, baterías y mensajería | Semestral | Telecomunicaciones / LH |  |  |  |
| Megáfonos de mayordomías | Prueba de sirena y carga de batería | Trimestral | Mayordomías |  |  |  |
| Red de Gas (Calderas / Comedor) | Prueba de corte de válvulas maestras y electroválvulas | Semestral | Dirección de Mantenimiento |
| Ascensores (SJ670, Alem) | Verificación de llaves de rescate, intercomunicadores y UPS de nivelación | Trimestral | Dirección de Mantenimiento |
| Ciberseguridad y Backups | Prueba de restauración de backups críticos y segregación de red de emergencia | Trimestral | Dirección de Gestión y Seguridad de la Información |
| Freezers Críticos (-80°C) | Verificación de conexión a UPS / prioridad en grupo electrógeno | Semestral | Mantenimiento + SHST |
| Flota Institucional | Revisión de botiquines, linternas y protocolo de choferes en vehículos | Semestral | Subsecretaría de Infraestructura |
| Evaluación Estructural | Inspección de cubiertas, mampostería y anclajes en patrimonio histórico | Anual (pre-temporada) | Dirección General de Construcciones |
