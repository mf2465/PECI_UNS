# AT-02 – EMERGENCIAS CLIMÁTICAS – PREVENCIÓN Y DISPONIBILIDAD DE LOS SISTEMAS DE COMUNICACIONES

**Universidad Nacional del Sur – Bahía Blanca**
**Revisión 0 – Versión 2 – Consolidado 2026**

## CONTROL DE VERSIONES

| Rev. | Versión | Fecha | Motivo del Cambio |
| --- | --- | --- | --- |
| 0 | 1 | 09/2026 | Borrador inicial de segregación (estructura de 5 piezas definida por SHST: A, B, AT-01, AT-02, PE) |
| 0 | 2 | 09/2026 | Enriquecimiento desde Documento B (Rev 0 Versión 7) y expediente de adquisición Fase 2: nodos fijos bibanda (Colón 80, Escuelas Medias, Palihue), radiobase móvil, reserva estratégica de antena, fuentes 13.8 V 30 A y cableado con relevamiento; alineación de pruebas, indicadores, registros y coordinación con AT-01 y PE |

Nota de segregación: este anexo regula la prevención, el mantenimiento, la disponibilidad y la verificación de los sistemas de comunicaciones. La arquitectura técnica y los criterios de degradación se definen en el Documento B (Anexo Operativo 07-B); la infraestructura edilicia y los servicios esenciales (energía de respaldo edilicia, bombeo, gas, ascensores) corresponden al AT-01; los riesgos específicos por sector se rigen por los Procedimientos Específicos (PE).

## 1. OBJETO

Establecer las condiciones técnicas necesarias para asegurar la disponibilidad, confiabilidad, autonomía y capacidad de recuperación de los sistemas de comunicaciones utilizados como soporte del PECl-UNS.

La arquitectura técnica de dichos sistemas se define en el Documento B (Anexo Operativo 07-B – Soporte Técnico); el presente anexo regula su prevención, mantenimiento, pruebas y disponibilidad.

## 2. ALCANCE

Comprende, entre otros:

- RACUNS (VHF / UHF);
- bases fijas: BASE CENTRAL (SJ670), BASE RECTORADO (Colón 80), BASE PALIHUE, BASE LH y BASE ANEXO RADIO;
- nodos fijos bibanda nuevos (Colón 80, Escuelas Medias y Campus Palihue – Agronomía), en adquisición y puesta en servicio;
- equipos portátiles: flota de 12 unidades asignadas más 6 unidades de refuerzo en incorporación;
- Starlink en modalidades S1, S2 y S3;
- radiobase móvil (repetidor temporal);
- Meshtastic / LoRa (nodo Palihue);
- sistemas de alimentación de comunicaciones: fuentes switching 13.8 V 30 A, UPS dedicadas, bancos DC y baterías de nodos;
- cableado coaxial, antenas, conectores y reserva estratégica (antena colineal de troncal);
- agenda técnica de contactos;
- pruebas y mantenimiento.

## 3. PRINCIPIO DE REDUNDANCIA

Ninguna comunicación crítica deberá depender exclusivamente de:

- un único medio;
- un único proveedor;
- una única infraestructura;
- un único nodo.

La arquitectura deberá permitir migrar a medios alternativos cuando se produzca degradación, conforme al procedimiento de degradación y traspaso del Documento B.

## 4. MANTENIMIENTO DE RACUNS

### 4.1. Repetidor VHF (Complejo Alem – BBYF)

Verificar:

- antena;
- coaxial;
- gabinete;
- alimentación;
- puesta a tierra;
- protección contra sobretensiones;
- respaldo DC.

El repetidor principal se encuentra definido técnicamente con 50 W y respaldo de 24–48 horas. Se aplicará inspección mensual de antena, conexiones y bajada coaxial, y verificación semestral del banco de baterías y protecciones eléctricas, con registro en el checklist de mantenimiento preventivo.

### 4.2. Bases fijas y nodos nuevos

Realizar:

- prueba radial semanal;
- verificación de batería;
- inspección física;
- identificación de fallas;
- registro;
- comunicación de novedades a Telecomunicaciones.

Para los nodos bibanda nuevos, al cierre de cada instalación: verificación de ROE, programación conforme al Anexo Técnico Restringido, prueba de cobertura según el plan de pruebas de campo del Documento B e incorporación inmediata a la prueba radial semanal.

### 4.3. Equipos portátiles

- Prueba semanal integrada a la prueba radial;
- verificación de baterías y cargadores;
- inspección física;
- control de asignación por acta;
- reserva H-12 disponible y verificada.

### 4.4. Energía y alimentación

Esquema por nodo: red eléctrica (primaria) → UPS / banco de baterías 24–48 h (secundaria) → grupo electrógeno institucional o paneles solares (terciaria).

- **Fuentes switching 13.8 V 30 A de las bases fijas:** verificación semestral de tensión de salida, ventilación (cooler) y protecciones (cortocircuito, sobrecarga, sobretemperatura y sobretensión).
- **Nodo Meshtastic Palihue:** autonomía solar propia, independiente del esquema general.
- **Reabastecimiento de combustible y rotación de baterías** para eventos superiores a 48 h: Subsecretaría de Infraestructura y Servicios, en coordinación con el AT-01.
- **Delimitación con AT-01:** los grupos electrógenos edilicios y ATS corresponden al AT-01; las UPS, bancos DC y fuentes de los nodos de comunicaciones corresponden a este anexo; las pruebas bajo carga trimestrales se ejecutan de manera conjunta.

### 4.5. Cableado, antenas y reserva estratégica

- Inspección anual de bajadas coaxiales, fijaciones y herrajes; tras eventos severos (ráfagas >90 km/h o actividad eléctrica): verificación visual y de ROE antes de la restitución al servicio.
- **Reserva estratégica:** antena colineal de troncal (fibra de vidrio 3x 5/8) y conectores PL-259 en stock verificado; control de integridad semestral.
- **Rollo de 100 m de RG213U:** administrado por Telecomunicaciones para fraccionamiento en bajadas de antenas; el metraje adicional se adquiere conforme al relevamiento in situ (valor de referencia $ 9.000 por metro).

## 5. STARLINK

**S1 – Respaldo fijo.** Destinado al respaldo de infraestructura informática crítica. La red de contingencia deberá mantenerse segregada de la red institucional y utilizar credenciales diferenciadas y controles de acceso. Conmutación manual con secuencia detección → decisión → ejecución → registro → retorno; simulacro trimestral con medición de tiempos.

**S2 – Anexo Radio.** Destinado al soporte de emisión y enlace alternativo con la FM UTN-FRBB; prueba trimestral conjunta con Vocería.

**S3 – Móvil.** Destinado a: operaciones de campo; asistencia a sectores afectados; Sala de Crisis alternativa. El objetivo de puesta en servicio establecido es inferior a 30 minutos; prueba trimestral de despliegue y apuntamiento.

**Disposiciones comunes a S1, S2 y S3.** Titularidad y contrato a cargo de Telecomunicaciones, con responsable titular y suplente; ciberseguridad básica (red segregada, contraseña única distinta de la de fábrica, firmware actualizado antes de cada prueba, sin exposición de servicios de gestión desde internet, registro de accesos durante la emergencia); prueba trimestral de cada modalidad con registro de resultado y tiempos.

## 6. MESHTASTIC / LORA

El nodo Palihue constituye un sistema de mensajería de último recurso para operaciones en terreno.

Deberá verificarse:

- alimentación solar;
- autonomía;
- funcionamiento;
- cobertura;
- integridad del nodo.

La verificación se realizará semestralmente.

## 7. PRUEBAS

Se establece como régimen mínimo de validación el siguiente cuadro. Los procedimientos de ejecución, checklists y plantillas de registro corresponden a este anexo; los resultados alimentan los indicadores de la sección 9.

| Prueba | Frecuencia | Responsable |
| --- | --- | --- |
| Prueba radial semanal (bases, nodos nuevos y portátiles) | Semanal | Telecomunicaciones |
| Caída de repetidor y migración | Trimestral | Telecomunicaciones |
| Starlink S1 – conmutación manual | Trimestral | Telecomunicaciones |
| Starlink S2 – emisión y enlace FM | Trimestral | Telecomunicaciones + Vocería |
| Starlink S3 – despliegue y apuntamiento | Trimestral | Telecomunicaciones |
| Meshtastic Palihue | Semestral | Telecomunicaciones + LH |
| Conmutación energética de nodos críticos | Semestral | Telecomunicaciones + Infraestructura (según AT-01) |
| Prueba de campo integral | Según programa | Telecomunicaciones + predios |
| Simulacro de declaración de ECD con Regla de los 2 de 3 Pilares y Triangulación | Trimestral | Telecomunicaciones + Nodo Central |
| Simulacro integral RACUNS / POT-RACUNS / Nodo Central | Anual | Comité + Telecomunicaciones |

## 8. AGENDA INTERNA DE CONTACTO OPERATIVO

Telecomunicaciones mantendrá una agenda restringida con:

- área;
- función;
- nombre;
- teléfono;
- correo;
- enlaces externos relevantes.

La verificación se realizará durante la prueba radial semanal y la actualización deberá efectuarse ante cambios de personal o función dentro de las 24 horas. La plantilla y su régimen de distribución restringida se rigen por el Documento B.

## 9. INDICADORES

Se adoptan como indicadores mínimos:

- 100 % de pruebas radiales semanales;
- ≥ 95 % de fallas radiales subsanadas en 24 h;
- 100 % de cobertura en áreas críticas;
- ≥ 24 h de autonomía energética de nodos;
- 100 % de pruebas programadas (trimestrales y semestrales) ejecutadas;
- 100 % de declaraciones ECD con triangulación documentada;
- 100 % de agenda interna actualizada;
- checklist de mantenimiento sin observaciones abiertas.

## 10. REGISTROS Y MEJORA CONTINUA

- **Registros:** libro de prueba radial, checklist de mantenimiento preventivo de comunicaciones, registros de conmutación y despliegue Starlink, actas de entrega de equipos.
- Todo desvío se registrará y tratará conforme al ciclo PDCA del Documento A; las revisiones post-incidente se documentarán en el informe de activación de 72 horas con análisis técnico de comunicaciones.
- Los resultados alimentan los indicadores del Documento B y la revisión anual del presente anexo mediante control de versiones.

## 11. COORDINACIÓN CON OTROS ANEXOS

- **AT-01:** energía edilicia, grupos electrógenos, ATS, ascensores e instalaciones de gas; pruebas bajo carga trimestrales conjuntas.
- **PE:** los procedimientos específicos se articulan con este anexo (PE-01 integra la segregación de redes y la continuidad de S1; PE-04 integra las comunicaciones de la radiobase móvil y la flota en tránsito).
- **Documento B:** fuente de la arquitectura; toda modificación de frecuencias, canales o emplazamientos requiere aprobación de la Dirección de Telecomunicaciones y actualización del Anexo Técnico de Radiocomunicaciones (restringido).
