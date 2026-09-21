# AT-01 – EMERGENCIAS CLIMÁTICAS – PREVENCIÓN DE INFRAESTRUCTURA EDILICIA Y SERVICIOS ESENCIALES

**Universidad Nacional del Sur – Bahía Blanca**
**Revisión 0 – Versión 2 – Consolidado 2026**

## CONTROL DE VERSIONES

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Borrador inicial de segregación (estructura de 5 piezas definida por SHST: A, B, AT-01, AT-02, PE) |
| 0 | 2 | 09/2026 | Enriquecimiento íntegro desde PECI_UNS Rev 0 Versión 7_B (secciones 3.3.1 a 3.3.4): matriz de responsabilidades por Dirección, protocolos preventivos y de emergencia, protección de patrimonio y laboratorios, delimitación con AT-02, PE y Documento B |

## NOTA DE ARQUITECTURA DOCUMENTAL Y SEGREGACIÓN

Este anexo regula la **prevención, el mantenimiento, la disponibilidad y la verificación de la infraestructura edilicia y los servicios esenciales** que sostienen la operación institucional durante emergencias climáticas.

- **Documento A (Operativo):** Decide niveles de alerta, custodia y ventanas horarias.
- **Documento B (Soporte Técnico):** Define la arquitectura y capacidades de comunicaciones.
- **AT-01 (este documento):** Previene y mantiene edificios y servicios esenciales (energía edilicia, gas, pluviales, cubiertas, arbolado, ascensores, patrimonio).
- **AT-02:** Previene y mantiene los sistemas de comunicaciones (RACUNS, Starlink, Meshtastic, fuentes de nodos, UPS de telecomunicaciones).
- **PE (Procedimientos Específicos):** Encuadra técnicamente los riesgos específicos por sector (ciberseguridad, laboratorios químicos/biológicos, archivos, flota en tránsito).

**Delimitación técnica con AT-02:** los grupos electrógenos edilicios, los paneles de transferencia automática (ATS), las UPS asociadas a servicios esenciales y las motobombas de achique corresponden a este anexo; las UPS, bancos DC y fuentes switching de los nodos de comunicaciones corresponden al AT-02. Las pruebas bajo carga trimestrales de los ATS y grupos electrógenos se ejecutan de manera conjunta entre ambos anexos.

**Delimitación con PE:** los protocolos específicos de ciberseguridad y segregación de redes (PE-01), conservación de muestras, reactivos y freezers críticos (PE-02), protección de archivos y patrimonio documental (PE-03), y actuación de flota en tránsito (PE-04) se rigen por sus respectivos PE; este anexo provee únicamente el soporte edilicio y de servicios esenciales necesario para su ejecución.

## 1. OBJETO

Establecer los criterios de prevención, mantenimiento, disponibilidad y verificación de la infraestructura edilicia y de los servicios esenciales necesarios para reducir la vulnerabilidad de los predios de la UNS frente a emergencias meteorológicas, garantizando la integridad física de las personas, la continuidad de los servicios críticos y la preservación del patrimonio institucional.

## 2. ALCANCE

### 2.1. Alcance territorial

Aplica a los predios alcanzados por el PECl-UNS, entre otros: Campus Altos de Palihue; Complejo Alem; San Juan 670; 12 de Octubre; Colón 80; Rondeau 29; Casa de la Cultura; Escuelas Preuniversitarias (11 de Abril y Agraria); Anexo de la Radio AM UNS; demás predios que sean incorporados al PECl-UNS.

### 2.2. Sistemas y elementos comprendidos

- Cubiertas y aberturas;
- Desagües pluviales, canaletas, bajadas y sumideros;
- Bombas de achique fijas y móviles;
- Arbolado de gran porte y espacio público asociado;
- Instalaciones eléctricas de respaldo (grupos electrógenos, ATS, UPS y bancos de baterías edilicias);
- Instalaciones de gas (válvulas maestras, electroválvulas, redes de calderas y cocinas);
- Ascensores (maniobra preventiva, rescate, UPS de nivelación);
- Accesos, subsuelos y sectores susceptibles de anegamiento;
- Infraestructura crítica edilicia (salas de máquinas, depósitos estratégicos, reservas de agua);
- Estructura, mampostería, anclajes y herrajes en edificios de patrimonio histórico.

## 3. VULNERABILIDADES POR PREDIO

### 3.1. Mapeo de vulnerabilidades y directivas técnicas de prevención

| Predio / Sede | Vulnerabilidades críticas | Directiva técnica específica |
| --- | --- | --- |
| Campus Altos de Palihue | Exposición a campo abierto frente a vientos SO/NO; arbolado de gran porte sobre sendas y estacionamientos; cubiertas livianas; riesgo de aislamiento vehicular por anegamiento de accesos | Poda preventiva semestral; clausura anticipada de sendas arboladas en Naranja/Rojo; confinamiento en pabellones centrales de hormigón; resguardo vehicular fuera de la proyección del arbolado |
| Complejo Alem / San Juan 670 / 12 de Octubre | Edificaciones de gran altura (San Juan 670, 7 pisos); grandes superficies vidriadas; riesgo de anegamiento en subsuelos, depósitos y salas de calderas; alta densidad poblacional | Revisión permanente de bombas de achique y sumideros; bajada obligatoria de cortinas metálicas y cierre de ventanales; confinamiento en pasillos internos y plantas bajas; desconexión preventiva de ascensores en Rojo |
| Sede Rectorado (Colón 80), Rondeau 29 y Casa de la Cultura | Patrimonio histórico; cubiertas y aberturas tradicionales; archivos históricos | Inspección y sellado de cubiertas y desagües pluviales; protección preventiva de archivos; nodo de comando BASE RECTORADO con respaldo energético |
| Escuelas Preuniversitarias (11 de Abril, Agraria, etc.) | Población de menores; dependencia de transporte público y retiro de tutores; talleres y galpones en la Escuela Agraria | Aplicación del Protocolo de Custodia (Documento A); enlace radial directo vía handy VHF con Base Central |
| Edificio Anexo Radio AM UNS | Cadena de transmisión AM y nodo de comunicaciones; Sala de Crisis alternativa | Respaldo energético verificado; inclusión en prueba radial semanal y en pruebas de campo |

### 3.2. Identificación sectorial adicional

Cada mayordomía deberá mantener actualizado un **registro de sectores vulnerables internos** (subsuelos críticos, salas de calderas, depósitos de insumos, archivos, laboratorios con materiales sensibles), reportando a la Subsecretaría de Infraestructura y Servicios cualquier novedad que requiera intervención preventiva.

## 4. MATRIZ DE RESPONSABILIDADES TÉCNICAS POR DIRECCIÓN

| Dirección / Servicio UNS | Riesgo Crítico Asociado | Directiva Técnica Principal |
| --- | --- | --- |
| Dirección de Mantenimiento | Corte de gas, anegamientos, arbolado, flota vehicular, ascensores | Ejecución de cortes preventivos, limpieza de sumideros, balizamiento de zonas de exclusión, protocolo de choferes y rescate en ascensores |
| Dirección General de Construcciones Universitarias | Daño estructural, colapso de cubiertas, patrimonio histórico | Inspección de techos, protección de archivos y emisión del "Certificado de Aptitud de Ocupación" post-evento |
| Servicios de Seguridad e Higiene en el Trabajo (SHST) | Riesgo químico/biológico, EPP, primeros auxilos, auditoría de laboratorios | Supervisión de protocolos de laboratorios críticos, coordinación de brigadas y contención de residuos peligrosos |
| Dirección de Gestión y Seguridad de la Información | Ciberataques, pérdida de datos, vulnerabilidad de servidores | Verificación de backups externos, segregación de redes de emergencia y ciberseguridad en modo contingencia (PE-01) |
| Dirección General de Sistemas de Información | Caída de servicios digitales, Moodle, web institucional | Conmutación a servidores de respaldo y priorización de tráfico informático crítico (PE-01) |
| Dirección General de Telecomunicaciones | Caída de fibra óptica, redes de datos, RACUNS | Conmutación manual a Starlink S1, soporte a Sistemas de Información y mantenimiento de RACUNS (AT-02) |
| Subsecretaría de Infraestructura y Servicios | Coordinación general edilicia, reservas estratégicas, provisión de recursos | Articulación entre direcciones, provisión de insumos (agua potable, cobertores, tarimas, combustible) y gestión de reservas estratégicas |

## 5. MANTENIMIENTO PREVENTIVO DE RUTINA Y ESTACIONAL

Las tareas de preparación previa a la temporada de riesgos (primavera-verano) y de rutina anual son ineludibles y se registran en el Checklist de Mantenimiento Preventivo de Infraestructura (Sección 11).

### 5.1. Arbolado y espacio público

- Inspección y poda preventiva semestral en Campus Palihue y predios preuniversitarios.
- Balizamiento o cierre con cadenas de estacionamientos bajo arbolado de gran porte ante Alerta Naranja.
- Identificación de ejemplares añosos con riesgo de vuelco o desprendimiento de ramas.

### 5.2. Pluviales y cubiertas

- Limpieza periódica de canaletas, bajadas y sumideros.
- Inspección y sellado de cubiertas (especialmente en patrimonio histórico y subsuelos críticos).
- Verificación de desagües pluviales y puntos de ingreso de agua.
- Inspección de anclajes, herrajes y fijaciones en cubiertas livianas.

### 5.3. Sistemas de bombeo

- Verificación periódica de disponibilidad, alimentación, funcionamiento, capacidad de extracción y condiciones de descarga de bombas de achique fijas y móviles.
- Prueba operativa bajo carga antes de cada temporada de riesgos.
- Stock mínimo de combustible para motobombas y repuestos críticos (sellos, impulsores).

### 5.4. Energía de respaldo edilicia

- Pruebas bajo carga trimestrales de grupos electrógenos y paneles de transferencia automática (ATS).
- Verificación semestral de UPS edilicias, bancos de baterías y tableros de transferencia.
- Control de nivel de combustible, estado de bornes, niveles de aceite y refrigerante.
- Rotación de combustible en tanques de larga duración.
- **Pruebas bajo carga conjuntas con AT-02:** los grupos electrógenos que alimentan tanto servicios edilicios como nodos de comunicaciones se prueban trimestralmente con carga simultánea, registrando resultados en ambos anexos.

### 5.5. Gas y redes asociadas

- Inspección semestral de válvulas maestras, electroválvulas y reguladores.
- Prueba operativa de corte preventivo en calderas y cocinas (Comedor Universitario).
- Verificación de ventilaciones y detectores de monóxido de carbono.

### 5.6. Ascensores

- Verificación trimestral de llaves de rescate, intercomunicadores y UPS de nivelación.
- Inspección de estado de cables, poleas y sistemas de freno.
- SLA vigente con empresa externa para maniobras de rescate complejas.

## 6. PROTOCOLOS DE ACTUACIÓN ANTE ALERTA Y EMERGENCIA

### 6.1. Corte preventivo de gas

Ante **Alerta Roja**, Aviso a Muy Corto Plazo (ACP) o sismo, la Dirección de Mantenimiento procederá al corte de las válvulas maestras de gas en calderas y cocinas (Comedor Universitario). La rehabilitación solo se ejecutará tras inspección técnica post-evento y constatación de estanqueidad de la red.

### 6.2. Reserva estratégica de agua

Ante **Alerta Naranja/Roja prolongada**, la Subsecretaría de Infraestructura garantizará el stock de agua potable (mínimo **3 litros/persona/día**) en:

- Nodos de Confinamiento;
- Escuelas Preuniversitarias;
- Residencias universitarias.

El stock se revisará y rotará semestralmente.

### 6.3. Rescate en ascensores

- **En Alerta Roja:** Mantenimiento bajará los ascensores a planta baja y los desconectará preventivamente.
- **Ante corte súbito con personas atrapadas:** Mayordomía usará el intercomunicador para contener a los ocupantes; Mantenimiento ejecutará la maniobra de rescate manual si el personal está habilitado, o activará el SLA de emergencia con la empresa externa.
- **Prohibición:** la maniobra técnica de rescate no será ejecutada por personal no habilitado.

### 6.4. Flota institucional en tránsito

Si un alerta sorprende a vehículos institucionales en la vía pública, los choferes aplicarán el protocolo de **"Detención en lugar seguro"** (lejos de árboles, cables y zonas inundables), confinamiento dentro de la unidad y reporte a Base Central por CH2 o celular. El procedimiento completo se desarrolla en el **PE-04**.

### 6.5. Clausura de sendas y estacionamientos

Ante Alerta Naranja o superior, se balizarán o cerrarán con cadenas los estacionamientos y sendas bajo arbolado de gran porte en Campus Palihue y Escuelas Preuniversitarias.

### 6.6. Protección de vidrios y aberturas

En edificios con grandes superficies vidriadas (San Juan 670, Complejo Alem), se ejecutarán la bajada obligatoria de cortinas metálicas y el cierre de ventanales ante Alerta Naranja o superior.

### 6.7. Confinamiento preventivo

En todos los predios, ante Alerta Naranja/Roja se procederá al confinamiento en:

- **Campus Palihue:** pabellones centrales de hormigón.
- **Edificios de altura (SJ670, Alem):** pasillos internos y plantas bajas, alejados de ventanas.
- **Escuelas Preuniversitarias:** aulas internas designadas, conforme al Protocolo de Custodia (Documento A).

## 7. PROTECCIÓN DE ELEMENTOS CRÍTICOS

### 7.1. Archivos, bibliotecas y patrimonio

- **Protocolo de "Elevación Preventiva":** uso de tarimas y provisión de cobertores de polietileno de emergencia en salas de archivos críticos y Biblioteca Central.
- **Bombas de achique exclusivas** para subsuelos patrimoniales.
- **Inspección anual (pre-temporada)** de cubiertas, mampostería y anclajes en patrimonio histórico a cargo de la Dirección General de Construcciones Universitarias.
- El procedimiento completo se desarrolla en el **PE-03**.

### 7.2. Laboratorios críticos y cadena de frío

- Inventario de **freezers críticos (-80 °C)** conectados a UPS dedicadas o con prioridad de encendido en grupos electrógenos.
- Auditoría del SHST sobre aseguramiento de reactivos ante riesgo de inundación.
- Disponibilidad de nitrógeno líquido y protocolos de conservación ante cortes prolongados de energía.
- El procedimiento completo se desarrolla en el **PE-02**.

### 7.3. Centros de datos y salas de servidores

- Verificación de sistemas de climatización dedicados y UPS asociadas.
- Respaldo energético con grupo electrógeno exclusivo de 100 kVA con ATS en el Centro de Datos de Telecomunicaciones.
- Coordinación con AT-02 para la continuidad de servidores y replicación Alem↔Palihue.

## 8. INFRAESTRUCTURA CRÍTICA EDILICIA

Deberán mantenerse identificados y priorizados los sectores cuya pérdida de funcionamiento pueda comprometer la continuidad institucional, entre ellos:

- Centro de Datos y salas de servidores;
- Laboratorios con materiales sensibles;
- Áreas de servicios esenciales (calderas, bombas, tableros eléctricos principales);
- Sistemas de telecomunicaciones (soporte edilicio provisto por este anexo; equipamiento por AT-02);
- Instalaciones de energía y gas;
- Sistemas de bombeo de achique;
- Nodos de confinamiento designados.

Cada sector crítico contará con **ficha técnica de vulnerabilidad** actualizada, disponible para la Subsecretaría de Infraestructura y el SHST.

## 9. ASCENSORES

Ante condiciones meteorológicas que impliquen riesgo de interrupción eléctrica, se aplicarán las disposiciones técnicas de la Sección 6.3 (maniobra preventiva de bajada a planta baja y desconexión).

En caso de personas atrapadas, la asistencia inicial se realizará mediante los intercomunicadores del ascensor y se solicitará la intervención del servicio técnico correspondiente.

**La maniobra técnica de rescate no será ejecutada por personal no habilitado.**

## 10. FLOTA INSTITUCIONAL

Las condiciones técnicas y de seguridad para vehículos institucionales deberán contemplar:

- Identificación de rutas y sectores vulnerables;
- Lugares seguros de detención;
- Disponibilidad de comunicaciones (handy VHF o celular);
- Reporte de novedades a Base Central.

La actuación concreta del conductor ante una emergencia meteorológica se mantiene en el Documento A y/o en el **PE-04** (Flota institucional en tránsito).

Cada vehículo institucional contará con **revisión semestral** de botiquines, linternas, chalecos reflectivos, protocolo impreso de choferes y elementos de balizamiento.

## 11. EVALUACIÓN POST-EVENTO

Luego de un evento severo (temporal, sismo, inundación, tornado), los sectores afectados deberán ser inspeccionados técnicamente antes de su rehabilitación.

**Ningún edificio podrá ser reocupado** hasta que la Dirección General de Construcciones Universitarias emita el **"Certificado de Aptitud de Ocupación"** o dicte la clausura preventiva, informe que se elevará al CDE.

El procedimiento de evaluación incluye:

- Inspección estructural (cubiertas, mampostería, anclajes);
- Verificación de instalaciones eléctricas, de gas y sanitarias;
- Constatación de estanqueidad de redes;
- Evaluación de accesos y circulaciones;
- Reporte fotográfico y técnico al CDE.

## 12. REGISTROS Y CHECKLIST DE MANTENIMIENTO PREVENTIVO

Se utilizará un **Checklist de Mantenimiento Preventivo de Infraestructura** con registro sistemático. Los resultados alimentan la revisión anual del presente anexo mediante control de versiones.

| Sistema | Tarea | Frecuencia | Responsable | Resultado | Observaciones |
| --- | --- | --- | --- | --- | --- |
| Pluviales y bombas de achique | Limpieza de sumideros; prueba de bombas | Semestral / pre-temporada | Dirección de Mantenimiento | | |
| Cubiertas y desagües | Inspección y sellado | Anual / pre-temporada | Dirección de Mantenimiento | | |
| Arbolado | Poda preventiva de ejemplares añosos | Semestral | Dirección de Mantenimiento | | |
| Grupos electrógenos (ATS) | Prueba bajo carga (conjunta con AT-02) | Trimestral | Infraestructura + Telecomunicaciones | | |
| UPS y bancos de baterías edilicias | Verificación de autonomía y protecciones | Semestral | Dirección de Mantenimiento | | |
| Red de gas (calderas / comedor) | Prueba de corte de válvulas maestras y electroválvulas | Semestral | Dirección de Mantenimiento | | |
| Ascensores (SJ670, Alem) | Verificación de llaves de rescate, intercomunicadores y UPS de nivelación | Trimestral | Dirección de Mantenimiento | | |
| Freezers críticos (-80 °C) | Verificación de conexión a UPS / prioridad en grupo electrógeno | Semestral | Mantenimiento + SHST | | |
| Flota institucional | Revisión de botiquines, linternas y protocolo de choferes en vehículos | Semestral | Subsecretaría de Infraestructura | | |
| Evaluación estructural | Inspección de cubiertas, mampostería y anclajes en patrimonio histórico | Anual (pre-temporada) | Dirección General de Construcciones | | |
| Reserva estratégica de agua | Rotación de stock y verificación de envases | Semestral | Subsecretaría de Infraestructura | | |

Todo desvío se registrará y tratará conforme al ciclo PDCA del Documento A (Sección de Mejora Continua). Las revisiones post-incidente se documentarán en el informe de activación de 72 horas.

## 13. COORDINACIÓN CON OTROS ANEXOS

- **AT-02 (Mantenimiento de Comunicaciones):** delimitación de fronteras en energía (grupos/ATS edilicios vs. UPS/fuentes de nodos); pruebas bajo carga trimestrales conjuntas; soporte edilicio para despliegue de radiobase móvil y repetidor temporal.
- **PE-01 (Ciberseguridad):** soporte edilicio para salas de servidores y Centros de Datos; energía de respaldo para UPS de TI.
- **PE-02 (Laboratorios):** soporte eléctrico para freezers críticos y provisión de grupos electrógenos con prioridad de encendido; coordinación con SHST.
- **PE-03 (Patrimonio):** provisión de tarimas, cobertores y bombas de achique para archivos y bibliotecas; inspección estructural anual.
- **PE-04 (Flota):** provisión de vehículos en condiciones técnicas seguras; definición de lugares seguros de detención dentro de los predios.
- **Documento B (Soporte Técnico):** soporte edilicio para la infraestructura de comunicaciones (torres, gabinetes, salas técnicas, anclajes de antenas).
- **Documento A (Operativo):** referencia para decisiones institucionales de alerta, suspensión y confinamiento; activación de los protocolos de este anexo conforme a los niveles de alerta del Documento A.
