# ANEXO OPERATIVO 07-B – ANEXO TÉCNICO DE INFRAESTRUCTURA Y COMUNICACIONES (RACUNS)

## DOCUMENTO B – TÉCNICO

**Revisión 0 – Versión 1 (Consolidado Institucional 2026)**
**Universidad Nacional del Sur – Bahía Blanca**

## Control de Versiones del Documento

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Segregación del PECl-UNS Rev 0 V4: contenido técnico de infraestructura, energía y radiocomunicaciones (RACUNS) |

*El presente documento integra el contenido técnico y de ingeniería del protocolo. Los aspectos operativos de decisión y custodia se rigen por el Documento A (Protocolo Operativo); los aspectos de difusión, vocería y mensajes a la comunidad se rigen por el Documento C (Manual de Comunicación Pública).*

## 1. OBJETO Y ALCANCE TÉCNICO

### 1.1. Objeto

Definir la ingeniería, la infraestructura, los procedimientos técnicos y el mantenimiento de los sistemas de soporte del Protocolo de Emergencias Climáticas de la UNS: infraestructura crítica y respaldo energético, red alternativa de radiocomunicaciones (RACUNS), capas complementarias de comunicación y planes de prueba y validación técnica.

### 1.2. Alcance y destinatarios

Este documento es de uso obligatorio para: Dirección General de Telecomunicaciones, Subsecretaría de Infraestructura y Servicios, Laboratorio de Hidráulica del Departamento de Ingeniería (LH), mayordomías de todos los predios, Seguridad Patrimonial y brigadas técnicas. Predios comprendidos: Campus Altos de Palihue, Complejo Alem, San Juan 670, 12 de Octubre, Colón 80, Centro Histórico Rondeau 29, Casa de la Cultura, Escuelas Preuniversitarias (11 de Abril y Agraria) y predios de interés.

### 1.3. Documentos relacionados

1. DOCUMENTO A – PROTOCOLO OPERATIVO DE EMERGENCIAS METEOROLÓGICAS (PECl-UNS).
2. DOCUMENTO C – MANUAL DE COMUNICACIÓN PÚBLICA Y VOCERÍA.
3. DOCUMENTO INSTITUCIONAL "RACUNS – RED ALTERNATIVA DE COMUNICACIONES DE LA UNIVERSIDAD NACIONAL DEL SUR" (Noviembre 2025).
4. SMN – SAT MÓDULO "UMBRALES PARA LOS ALERTAS" (2.ª edición, julio 2024).
5. LICENCIA ENACOM VHF UNS (expediente CNC 11660/1998).
6. ANEXOS OPERATIVOS 01, 03 y 05 del Plan Director de Emergencias.

## 2. UMBRALES METEOROLÓGICOS DE REFERENCIA TÉCNICA

*Fuente: SMN, Módulo "Umbrales para los Alertas", 2.ª edición 2024 (umbrales de Patagonia según Anaya y otros, 2020). Estos valores constituyen la referencia técnica de disparo de las acciones de infraestructura; la decisión institucional se rige por el Documento A.*

| Fenómeno | Amarillo | Naranja | Rojo |
| --- | --- | --- | --- |
| **Lluvias / Tormentas** | 15 mm en 12 h ó 30 mm en 24 h | 30 mm en 12 h ó 60 mm en 24 h | 60 mm en 12 h ó 90 mm en 24 h |
| **Viento (sostenido / ráfagas)** | 55 km/h / 65 km/h | 75 km/h / 90 km/h | 90 km/h / 110 km/h |
| **Nevadas** | En zonas bajas donde el fenómeno es raro, su ocurrencia con acumulación constituye, a priori, nivel amarillo | — | — |

**Notas técnicas:** para amarillo y naranja se considera acumulado en 12 h (sin descartar lluvias intensas en períodos más cortos); para rojo, 24 h. Los umbrales son dinámicos y públicos; Telecomunicaciones y LH verificarán periódicamente su vigencia en el sitio del SMN y actualizarán este cuadro mediante control de versiones.

## 3. VULNERABILIDADES POR PREDIO E INFRAESTRUCTURA CRÍTICA

### 3.1. Mapeo de vulnerabilidades y directivas técnicas de prevención

| Predio / Sede | Vulnerabilidades críticas | Directiva técnica específica |
| --- | --- | --- |
| Campus Altos de Palihue | Exposición a campo abierto frente a vientos SO/NO; arbolado de gran porte sobre sendas y estacionamientos; cubiertas livianas; riesgo de aislamiento vehicular por anegamiento de accesos | Poda preventiva semestral; clausura anticipada de sendas arboladas en Naranja/Rojo; confinamiento en pabellones centrales de hormigón; resguardo vehicular fuera de la proyección del arbolado |
| Complejo Alem / San Juan / 12 de Octubre | Edificaciones de gran altura (San Juan 670, 7 pisos); grandes superficies vidriadas; riesgo de anegamiento en subsuelos, depósitos y salas de calderas; alta densidad poblacional | Revisión permanente de bombas de achique y sumideros; bajada obligatoria de cortinas metálicas y cierre de ventanales; confinamiento en pasillos internos y plantas bajas; desconexión preventiva de ascensores en Rojo |
| Sede Rectorado (Colón 80), Centro Histórico Rondeau 29 y Casa de la Cultura | Patrimonio histórico; cubiertas y aberturas tradicionales; Sala de Crisis institucional y archivos históricos | Inspección y sellado de cubiertas y desagües pluviales; activación de la Base Fija VHF de comando; protección preventiva de archivos |
| Escuelas Preuniversitarias (11 de Abril, Agraria, etc.) | Población de menores; dependencia de transporte público y retiro de tutores; talleres y galpones en la Escuela Agraria | Aplicación del Protocolo de Custodia (Documento A); enlace radial directo vía handy VHF con Base Central |

### 3.2. Infraestructura crítica y respaldo energético / tecnológico

1. **Centro de Datos (Telecomunicaciones):** servidores institucionales con Grupo Electrógeno exclusivo de 100 kVA con Panel de Transferencia Automático (ATS) y bancos de UPS para transición de carga.
2. **Generador Móvil de Respaldo (100 kVA):** emplazado habitualmente en proximidades de San Juan 670, sobre plataforma móvil, para soporte de infraestructura crítica con desconexión prolongada.
3. **Adecuación energética de la Mayordomía San Juan 670:** UPS dedicada (1 a 2 kVA) para Base VHF, telefonía y cargadores; acometida exterior con tablero de transferencia manual para acople rápido del generador móvil.
4. **Respaldo DC en sitio del repetidor VHF (Complejo Alem – BBYF):** fuente con cargador flotante y banco de baterías de ciclo profundo (12 V AGM/Gel 100 Ah), autonomía de 24 a 48 horas.
5. **Laboratorios con sustancias químicas y materiales biológicos:** protocolos específicos ante cortes prolongados de energía (conservación, disponibilidad de N líquido), a cargo de cada unidad académica con asistencia del SHST.

### 3.3. Mantenimiento preventivo de infraestructura

1. Plan anual de inspección y poda preventiva de arbolado (Palihue y predios preuniversitarios) previo a la temporada primavera-verano.
2. Mantenimiento programado de sistemas pluviales y cubiertas: limpieza de canaletas y sumideros.
3. Pruebas bajo carga de grupos electrógenos (ATS) y motobombas de achique, con registro.
4. Verificación semestral de UPS, bancos de baterías y tableros de transferencia.
5. El cumplimiento se registrará en el Checklist de Mantenimiento Preventivo (Anexo A.3).

## 4. RACUNS – RED ALTERNATIVA DE COMUNICACIONES DE LA UNS

### 4.1. Definición, propósito y alcance

Red autónoma de comunicaciones basada en tecnología VHF, destinada a asegurar la conectividad institucional y operativa ante interrupciones de los servicios convencionales de telecomunicaciones y energía. Propósito principal: comunicación interna entre dependencias universitarias; de manera secundaria, integración con instituciones externas mediante convenios firmados por el Rectorado, poniendo la red a disposición de la comunidad en emergencias mayores. Alcance: Campus Palihue, Colón 80, Complejo Alem, Escuelas Medias y predios de interés.

### 4.2. Fundamento local (antecedentes)

Temporal e inundación del 07/03/2025, tornado del 17/12/2023 y apagón del 16/06/2019: interrupciones simultáneas de energía, telefonía celular e internet. Durante 2025 la UNS colaboró con Defensa Civil mediante el monitoreo del arroyo Napostá Grande (Unidad Remota de Telemetría Puente Canessa) y el Complejo Alem como centro de acopio de donaciones. Experiencia piloto validada en la Feria Gastronómica del Sudoeste Bonaerense 2025 (20.000 asistentes, colapso de telefonía celular, operación efectiva de handies VHF por operadores sin experiencia previa).

### 4.3. Criterio de activación

RACUNS se activa como medio principal de coordinación cuando el Nodo Central verifique la caída o inutilización de los medios convencionales (telefonía celular, internet y/o energía de red) y el CDE declare el **Estado de Comunicaciones Degradadas**. La verificación y la declaración quedarán asentadas en el libro de guardia.

### 4.4. Infraestructura

1. **Repetidor principal VHF (50 W):** Complejo Alem, edificio BBYF, sobre torre metálica existente de 10 m con pararrayos y puesta a tierra (altura relativa 28 m); antena omnidireccional de alto rendimiento, duplexor y gabinete protegido con ventilación y protección contra sobretensiones.
2. **BASE CENTRAL:** Mayordomía San Juan 670 (24 hs) – control troncal, libro de guardia y despacho.
3. **BASE RECTORADO:** Colón 80 (Sala de Crisis) – comando de autoridades.
4. **BASE PALIHUE:** Edificio Central del Campus Palihue – supervisión del predio abierto y accesos.
5. **Radiobases bibanda (proyectadas):** nodos Colón 80, Escuelas Medias y Campus Palihue.
6. **Radiobase móvil:** unidad vehicular con equipo bibanda y kit de conectividad satelital (Starlink); el área proveedora del vehículo y el personal afectado serán designados por resolución del CDE.
7. **Flota de handies:** 12 unidades bibanda operativas con canales pregrabados, cada una con responsable por sector, rol o responsabilidad.

### 4.5. Plan de canales

| Canal | Modo | Uso operativo y disciplina |
| --- | --- | --- |
| CH1 | Repetidor Alem (semidúplex) | Troncal de Mando y Emergencia: exclusivo directivas del CDE, novedades de Bases y reportes críticos. Escucha permanente en Naranja/Rojo. Prohibido el tráfico secundario |
| CH2 | Simplex operativo | Coordinación logística y cuadrillas: mantenimiento edilicio, choferes, maniobras de generadores y grupos técnicos |
| CH3 | Simplex local | Coordinación interna de predio: mayordomos, brigadistas y personal de seguridad dentro del campus |
| CH4 | Enlace | Interoperabilidad con el COE de Defensa Civil Bahía Blanca |
| Memorias adicionales | Simplex | Frecuencias pregrabadas por grupos operativos (mantenimiento, SHST, eléctricos, autoridades, brigadistas, logística), definidas por la Dirección de Telecomunicaciones en el Anexo Técnico de Radiocomunicaciones |

### 4.6. Asignación de la flota de handies (12 unidades)

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

### 4.7. Metodología bibanda y subcapas de retransmisión

1. **Canal principal VHF:** enlace por línea de vista, libre de interferencia por obstáculos (árboles, edificios de hormigón), para troncal y enlaces entre nodos.
2. **Canal secundario UHF:** conectividad en espacios cerrados o por rebotes, donde VHF no alcanza.
3. **Subcapa de retransmisión:** todo mensaje recibido por UHF en un nodo que no alcance punto a punto su destino será retransmitido por el operador del nodo en VHF hacia el siguiente nodo; en tránsito entre nodos, si VHF no fuera posible, se intentará UHF por proximidad.
4. Los handies permanecerán en escucha del canal troncal e interactuarán con el sistema según su posición lo favorezca.

### 4.8. Arquitectura en capas (redundancia funcional)

| Capa | Tecnología | Rol | Fortalezas / límites |
| --- | --- | --- | --- |
| 1 – Troncal | VHF repetidora (Alem, 50 W) + bases fijas | Mando y emergencia (CH1) | Línea de vista, cobertura urbana; cae si cae el repetidor |
| 2 – Proximidad | UHF simplex / rebotes | Interior de edificios, sombra radioeléctrica | Penetra hormigón; menor alcance |
| 3 – Malla | Meshtastic / LoRa (a incorporar) | Mensajería de texto sin infraestructura | Autónoma, bajo consumo; sin voz |
| 4 – Datos | Starlink móvil en camioneta | Internet de contingencia; réplica Alem↔Palihue; emisión de comunicados web | Satelital, independiente; requiere apuntamiento y energía |
| 5 – Difusión masiva | Radio AM UNS + FM UTN-FRBB (convenio) | Comunicados a la comunidad cuando cae todo lo digital | Alcance masivo; unidireccional |

### 4.9. Disciplina radial, prueba semanal y capacitación

1. **Protocolo de enlace:** identificación con el indicativo del puesto asignado en toda transmisión; mensajes breves, claros y estructurados; confirmación de recepción por repetición (colación).
2. **Disciplina de canales:** prioridad absoluta de CH1 para mando y emergencia; el tráfico de trabajo, logístico o rutinario se cursará estrictamente por CH2/CH3 o por las memorias de grupo pregrabadas.
3. **Prueba radial semanal:** día y hora definidos por la Dirección de Telecomunicaciones; cada Base y handy reportará ubicación, estado del equipo y nivel de batería. El resultado será asentado en el Libro de Prueba Radial (Anexo A.2) y cualquier falla deberá ser reportada a Telecomunicaciones dentro de las 24 horas para su inmediata subsanación.
4. **Capacitación para operadores no especializados:** la Dirección de Telecomunicaciones, en articulación con la Jefatura de Higiene y Seguridad (SHST), dictará módulos de instrucción práctica obligatoria destinados a todo el personal asignado a la flota de handies que no posea formación técnica previa en radiocomunicaciones. Contenido mínimo: protocolo básico de enlace, códigos de brevedad, disciplina de escucha (pensar antes de transmitir) y procedimientos específicos para reportar emergencias.

### 4.10. Marco regulatorio

Licencia ENACOM vigente para banda VHF (expediente CNC 11660/1998). El uso de UHF se realizará en frecuencia fuera de la reservada para uso de radioaficionados, sujeto a regularización y verificación ante ENACOM como tarea de mediano plazo. Telecomunicaciones mantendrá el expediente técnico y la documentación de la licencia actualizados y disponibles para auditoría.

### 4.11. Redundancia energética por nodo

Red eléctrica (primaria) → UPS / banco de baterías 24–48 h (secundaria) → grupo electrógeno institucional o paneles solares (terciaria).

### 4.12. Mantenimiento del sistema

1. Inspección mensual de antena, conexiones y bajada coaxial.
2. Verificación semestral del banco de baterías y protecciones eléctricas.
3. Actualización de firmware o parámetros del sistema de control.
4. Prueba radial semanal (4.9).
5. Unidad técnica designada: Laboratorio de Hidráulica del Departamento de Ingeniería, con apoyo de Telecomunicaciones.

## 5. TOPOLOGÍA DE LA RED

```
                     [REPETIDOR VHF ALEM – BBYF]
                      (50 W · torre 10 m · 28 m)
                                  │  CH1 semidúplex
      ┌───────────────┬───────────┼───────────┬────────────────┐
      ▼               ▼           ▼           ▼                ▼
 [BASE CENTRAL] [BASE RECTORADO] [BASE    [RADIOBASES      [RADIOBASE
  SJ670 24 hs     Colón 80       PALIHUE]  BIBANDA          MÓVIL]
  (Op. A + Op.B)  (Sala Crisis)  Ed.Central PROYECTADAS:    camioneta
      │               │           │          Colón 80,      + Starlink
      │               │           │          Esc. Medias,   (Capa 4)
      │               │           │          Palihue]
      └───────────────┴───────────┼───────────┴────────────────┘
                                  │  CH2 / CH3 simplex
                                  │  UHF proximidad / subcapa de retransmisión
                      [FLOTA 12 HANDIES  H-01 … H-12]
                                  │  CH4 enlace
                      [COE DEFENSA CIVIL BAHÍA BLANCA]
```

## 6. PRUEBAS DE CAMPO Y VALIDACIÓN TÉCNICA

### 6.1. Plan de pruebas de campo

Se ejecutará una prueba de campo integral con radiobases y handies en los nodos Colón 80, Campus Palihue y Escuelas Preuniversitarias, con la siguiente secuencia:

1. Coordinación previa con mayordomías y responsables de predio; asignación de operadores por nodo.
2. Verificación de energía, puesta a tierra y estado de antenas en cada nodo.
3. Prueba de cobertura por puntos fijos por predio: plantas bajas, subsuelos, terrazas, aulas críticas, estacionamientos y sendas arboladas.
4. Prueba comparativa VHF vs. UHF y validación de la subcapa de retransmisión entre nodos.
5. Prueba de autonomía energética con corte simulado de red en al menos un nodo.
6. Prueba de interoperabilidad CH4 con Defensa Civil, cuando la autoridad municipal esté disponible.
7. Registro de resultados en la Planilla de Prueba de Campo (Anexo A.1) e informe de sombras radioeléctricas para ajuste de ingeniería.

### 6.2. Pruebas periódicas complementarias

1. Prueba radial semanal (4.9) con registro en Anexo A.2.
2. Prueba trimestral de transmisión conjunta AM UNS – FM UTN-FRBB, coordinada con la Vocería (Documento C).
3. Prueba semestral de conmutación energética de nodos críticos (ATS, UPS, generador móvil).
4. Simulacro integral anual con activación completa de RACUNS y Nodo Central.

## 7. INDICADORES TÉCNICOS Y MEJORA CONTINUA

| Indicador | Meta |
| --- | --- |
| Cumplimiento de prueba radial semanal | 100 % |
| Fallas radiales reportadas subsanadas dentro de las 24 h | ≥ 95 % |
| Cobertura sin sombras radioeléctricas en áreas críticas de cada predio | 100 % |
| Autonomía energética de nodos ante corte de red | ≥ 24 h |
| Pruebas trimestrales AM/FM ejecutadas | 100 % |
| Checklist de mantenimiento preventivo sin observaciones abiertas | 100 % |

1. Todo desvío se registrará y tratará conforme al ciclo PDCA del Documento A (Sección de Mejora Continua).
2. Los resultados de pruebas y mantenimientos alimentarán la revisión anual del presente documento mediante control de versiones.
3. Las modificaciones de frecuencias, canales o emplazamientos requerirán aprobación de la Dirección de Telecomunicaciones y actualización del Anexo Técnico de Radiocomunicaciones.

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
| Bases y handies | Prueba radial y estado de equipos | Semanal | Telecomunicaciones |  |  |  |
| Megáfonos de mayordomías | Prueba de sirena y carga de batería | Trimestral | Mayordomías |  |  |  |
