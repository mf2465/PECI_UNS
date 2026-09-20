AT-02 – EMERGENCIAS CLIMÁTICAS – PREVENCIÓN Y DISPONIBILIDAD DE LOS SISTEMAS DE COMUNICACIONES
Universidad Nacional del Sur – Bahía Blanca - Revisión 0 – Versión 3 – Consolidado 2026

1. OBJETO
Establecer las condiciones técnicas necesarias para asegurar la disponibilidad, confiabilidad, autonomía y capacidad de recuperación de los sistemas de comunicaciones utilizados como soporte del PECl-UNS.
La arquitectura técnica de dichos sistemas se define en el Documento B (Anexo Operativo 07-B – Soporte Técnico); el presente anexo regula su prevención, mantenimiento, pruebas y disponibilidad.
El documento no establece los contenidos de comunicación pública, vocería o difusión a la comunidad, que corresponden al Anexo Operativo 1 – Plan de Comunicaciones de la Emergencia, ni las decisiones operativas de alerta, que corresponden al Anexo Operativo 7A.

2. ALCANCE
Comprende, entre otros:
RACUNS (VHF / UHF);
bases fijas: BASE CENTRAL (SJ670), BASE RECTORADO (Colón 80), BASE PALIHUE, BASE LH y BASE ANEXO RADIO;
nodos fijos bibanda proyectados (Colón 80, Escuelas Medias y Campus Palihue);
equipos portátiles: flota de 12 unidades asignadas más 6 unidades de refuerzo en incorporación;
Starlink en modalidades S1, S2 y S3;
radiobase móvil (repetidor temporal);
Meshtastic / LoRa (nodo Palihue);
sistemas de alimentación asociados: fuentes switching 13.8 V 30 A, UPS dedicadas, bancos DC y baterías de nodos;
cableado coaxial, antenas, conectores y reserva estratégica;
agenda técnica de contactos;
pruebas y mantenimiento.
Aplica a los sectores responsables de la infraestructura de comunicaciones, telecomunicaciones y soporte técnico vinculados con los predios alcanzados por el PECl-UNS. Los sectores técnicos deberán mantener actualizada la información correspondiente a los sistemas bajo su responsabilidad.

3. DOCUMENTOS RELACIONADOS
Plan Director de Emergencias de la UNS (PDE).
Anexo Operativo 7A – Protocolo Operativo de Actuación ante Emergencias Meteorológicas.
Anexo Operativo 1 – Plan de Comunicaciones de la Emergencia (Pública y Vocería).
Documento B – Anexo Operativo 07-B (Soporte Técnico / Arquitectura de Comunicaciones).
AT-01 – Prevención de Infraestructura Edilicia y Servicios Esenciales.
PE – Procedimientos Específicos ante Emergencias.
Anexo Técnico de Radiocomunicaciones (carácter restringido).
Ley Nacional N.º 27.287 – SINAGIR.
Sistema de Alerta Temprana del Servicio Meteorológico Nacional.
POT-RACUNS – Plan de Telecomunicaciones Operacionales.

4. CRITERIOS TÉCNICOS Y PRINCIPIO DE REDUNDANCIA
Ninguna comunicación crítica deberá depender exclusivamente de:
un único medio;
un único proveedor;
una única infraestructura;
un único nodo.
La arquitectura deberá permitir migrar a medios alternativos cuando se produzca degradación, conforme a la Regla Objetiva de los 2 de 3 Pilares y al procedimiento de Estado de Comunicaciones Degradadas (ECD) definidos en el Documento B.
**Disponibilidad:** toda capacidad crítica deberá estar operativa o ser restituible dentro de plazos definidos y verificados mediante pruebas.
**Autonomía:** los nodos críticos deberán sostener operación independiente de la red eléctrica y de las redes comerciales mediante UPS, bancos de baterías, grupo electrógeno o paneles solares.
**Trazabilidad:** toda prueba, falla, intervención y restitución deberá registrarse en las planillas del Anexo A.
**Mantenimiento preventivo:** las tareas periódicas son ineludibles y constituyen condición de disponibilidad del sistema.
**Validación mediante pruebas:** toda capacidad deberá probarse periódicamente y después de cada cambio relevante de equipamiento o emplazamiento.
La continuidad técnica deberá procurar que una falla de un componente no implique automáticamente la pérdida de una capacidad crítica.

5. MANTENIMIENTO DE RACUNS
5.1. Repetidor principal VHF (Complejo Alem – BBYF)
Verificar:
antena;
coaxial;
gabinete;
alimentación;
puesta a tierra;
protección contra sobretensiones;
respaldo DC.
El repetidor principal se encuentra definido técnicamente con 50 W y respaldo de 24 a 48 horas. Se aplicará inspección mensual de antena, conexiones y bajada coaxial, y verificación semestral del banco de baterías y protecciones eléctricas. Unidad técnica designada: Laboratorio de Hidráulica (LH), con apoyo de Telecomunicaciones.
5.2. Bases fijas y nodos
Realizar:
prueba radial semanal;
verificación de batería;
inspección física;
identificación de fallas;
registro;
comunicación de novedades a Telecomunicaciones dentro de las 24 horas.
Para los nodos bibanda nuevos, al cierre de cada instalación: verificación de ROE, programación conforme al Anexo Técnico de Radiocomunicaciones (restringido), prueba de cobertura e incorporación inmediata a la prueba radial semanal.
5.3. Equipos portátiles
Prueba semanal integrada a la prueba radial; verificación de baterías y cargadores; inspección física; control de asignación por acta de entrega; reserva H-12 disponible y verificada.
5.4. Fuentes, alimentación y respaldo energético
Esquema por nodo: red eléctrica (primaria) → UPS / banco de baterías 24–48 h (secundaria) → grupo electrógeno institucional o paneles solares (terciaria), conforme al Documento B.
Fuentes switching 13.8 V 30 A de las bases fijas: verificación semestral de tensión de salida, ventilación (cooler) y protecciones contra cortocircuito, sobrecarga, sobretemperatura y sobretensión.
El nodo Meshtastic Palihue posee autonomía solar propia, independiente del esquema general.
El reabastecimiento de combustible y la rotación de baterías para eventos superiores a 48 horas constituyen acción de la Subsecretaría de Infraestructura y Servicios, en coordinación con el AT-01.
**Delimitación con AT-01:** los grupos electrógenos edilicios y los ATS corresponden al AT-01; las UPS, bancos DC y fuentes de los nodos de comunicaciones corresponden a este anexo; las pruebas bajo carga trimestrales se ejecutan de manera conjunta.
5.5. Cableado, antenas y reserva estratégica
Inspección anual de bajadas coaxiales, fijaciones y herrajes; tras eventos severos (ráfagas superiores a 90 km/h o actividad eléctrica): verificación visual y de ROE antes de la restitución al servicio.
Reserva estratégica: antena colineal de troncal (fibra de vidrio 3x 5/8) y conectores PL-259 en stock verificado, con control de integridad semestral.
El rollo de 100 m de cable RG213U (100 % cobre) es administrado por Telecomunicaciones para fraccionamiento en bajadas de antena; el metraje adicional se adquiere conforme al relevamiento in situ (valor de referencia: $ 9.000 por metro).

6. STARLINK
6.1. S1 – Respaldo fijo
Destinado al respaldo de infraestructura informática crítica entre el Complejo Alem y su respaldo en Campus Palihue.
La red de contingencia deberá mantenerse segregada de red institucional y utilizar credenciales diferenciadas y controles de acceso.
Conmutación manual con secuencia detección → decisión → ejecución → registro → retorno; simulacro trimestral con medición de tiempos.
6.2. S2 – Anexo Radio
Destinado al soporte de emisión de la Radio AM y al enlace alternativo con la FM de la UTN-FRBB.
Prueba trimestral de emisión y del enlace alternativo, en conjunto con la Vocería.
6.3. S3 – Móvil
Destinado a:
operaciones de campo;
asistencia a sectores afectados;
Sala de Crisis alternativa.
El objetivo de puesta en servicio establecido es inferior a 30 minutos; prueba trimestral de despliegue y apuntamiento.
6.4. Disposiciones comunes a S1, S2 y S3
Titularidad y contrato a cargo de la Dirección General de Telecomunicaciones, con responsable titular y suplente designados.
Ciberseguridad básica: red de contingencia segregada; contraseña única y distinta de la de fábrica; firmware actualizado antes de cada prueba; sin exposición de servicios de gestión desde internet; registro de accesos durante la emergencia.
Cada modalidad se prueba con frecuencia trimestral, con registro de resultado y tiempos en el Anexo A.

7. MESHTASTIC / LORA
El nodo Palihue constituye un sistema de mensajería de último recurso para operaciones en terreno.
Verificar:
alimentación solar;
autonomía;
funcionamiento;
cobertura;
integridad del nodo.
La verificación se realizará semestralmente, con registro en el Checklist de Mantenimiento Preventivo de Comunicaciones (Anexo A.1).

8. PRUEBAS
Se establece como régimen mínimo de pruebas y simulacros de los sistemas de comunicaciones el siguiente cuadro. Los procedimientos de ejecución y los registros se rigen por este anexo y por el Documento B.
| Sistema | Frecuencia | Responsable |
| --- | --- | --- |
| Prueba radial semanal (bases, nodos y portátiles) | Semanal | Telecomunicaciones |
| Caída de repetidor y migración a simplex de contingencia | Trimestral | Telecomunicaciones |
| Starlink S1 – conmutación manual fibra→Starlink | Trimestral | Telecomunicaciones |
| Starlink S2 – emisión y enlace alternativo FM | Trimestral | Telecomunicaciones + Vocería |
| Starlink S3 – despliegue y apuntamiento | Trimestral | Telecomunicaciones |
| Meshtastic Palihue | Semestral | Telecomunicaciones + LH |
| Fuentes y respaldo energético (UPS, bancos, fuentes 13.8 V) | Semestral | Telecomunicaciones |
| Prueba integral de campo | Según programa | Telecomunicaciones + predios |
| Simulacro de declaración de ECD con Regla de los 2 de 3 Pilares y Triangulación | Trimestral | Telecomunicaciones + Nodo Central |
Los valores e indicadores ya establecidos se consolidan en la Sección 10.

9. AGENDA INTERNA DE CONTACTO OPERATIVO
Telecomunicaciones mantendrá una agenda restringida con:
área;
función;
nombre;
teléfono;
correo;
enlaces externos relevantes.
La verificación se realizará durante la prueba radial semanal y la actualización deberá efectuarse ante cambios de personal o función dentro de las 24 horas. La plantilla y su régimen de distribución restringida se rigen por el Anexo A.2.

10. INDICADORES
| Indicador | Meta |
| --- | --- |
| Cumplimiento de pruebas radiales semanales | 100 % |
| Fallas radiales subsanadas dentro de las 24 h | ≥ 95 % |
| Cobertura sin sombras radioeléctricas en áreas críticas | 100 % |
| Autonomía energética de nodos ante corte de red | ≥ 24 h |
| Pruebas programadas (trimestrales y semestrales) ejecutadas | 100 % |
| Declaraciones de ECD con triangulación documentada | 100 % |
| Agenda interna de contacto actualizada | 100 % |
| Checklist de mantenimiento sin observaciones abiertas | 100 % |

11. REGISTROS Y MEJORA CONTINUA
Registros: Libro de Prueba Radial, Checklist de Mantenimiento Preventivo de Comunicaciones (Anexo A.1), registros de conmutación y despliegue Starlink, y actas de entrega de equipos.
Todo desvío se registrará y tratará conforme al ciclo PDCA del Documento A / Anexo Operativo 7A (Sección de Mejora Continua).
Las revisiones post-incidente se documentarán en el informe de activación de 72 horas, con análisis técnico de comunicaciones.
Los resultados de pruebas y mantenimientos alimentarán los indicadores de la Sección 10 y la revisión anual del presente anexo mediante control de versiones.

12. COORDINACIÓN CON OTROS ANEXOS
**AT-01:** energía edilicia, grupos electrógenos, ATS, ascensores e instalaciones de gas; pruebas bajo carga trimestrales conjuntas.
**PE:** los procedimientos específicos se articulan con este anexo (PE-01 integra la segregación de redes y la continuidad de S1; PE-04 integra las comunicaciones de la radiobase móvil y la flota en tránsito).
**Documento B:** fuente de la arquitectura; toda modificación de frecuencias, canales o emplazamientos requiere aprobación de la Dirección de Telecomunicaciones y actualización del Anexo Técnico de Radiocomunicaciones (restringido).
**Documento A / Anexo Operativo 7A:** coordinación operativa, custodia y régimen del Nodo Central 24/7.

ANEXO A – PLANILLAS TÉCNICAS DE REGISTRO
A.1. Checklist de Mantenimiento Preventivo de Comunicaciones (plantilla)
| Sistema | Tarea | Frecuencia | Responsable | Fecha | Resultado | Observaciones |
| --- | --- | --- | --- | --- | --- | --- |
| Repetidor VHF Alem | Inspección de antena, coaxial y gabinete | Mensual | LH / Telecomunicaciones |  |  |  |
| Bases y nodos (incl. BASE LH y Anexo Radio) | Prueba radial y estado de equipos | Semanal | Telecomunicaciones |  |  |  |
| Handies y reserva H-12 | Baterías, cargadores e inspección física | Semanal | Telecomunicaciones |  |  |  |
| UPS y bancos de baterías | Verificación de autonomía y protecciones | Semestral | Telecomunicaciones |  |  |  |
| Fuentes 13.8 V 30 A | Tensión de salida, ventilación y protecciones | Semestral | Telecomunicaciones |  |  |  |
| Starlink S1 | Simulacro de conmutación manual fibra→Starlink | Trimestral | Telecomunicaciones |  |  |  |
| Starlink S2 | Prueba de emisión y enlace alternativo con FM | Trimestral | Telecomunicaciones + Vocería |  |  |  |
| Starlink S3 | Despliegue y apuntamiento | Trimestral | Telecomunicaciones |  |  |  |
| Meshtastic Palihue | Panel solar, baterías y mensajería | Semestral | Telecomunicaciones + LH |  |  |  |
| Cableado, antenas y conectores | Inspección anual y ROE post-evento | Anual / post-evento | Telecomunicaciones |  |  |  |
| Reserva estratégica (antena y conectores) | Control de integridad | Semestral | Telecomunicaciones |  |  |  |
| Agenda interna de contacto | Verificación de roles, teléfonos y enlaces | Semanal (prueba radial) | Telecomunicaciones |  |  |  |
A.2. Agenda Interna de Contacto Operativo (plantilla de distribución restringida)
| Área | Función | Nombre | Teléfono | Correo |
| --- | --- | --- | --- | --- |
| Telecomunicaciones | Coordinador técnico de Comunicaciones |  |  |  |
| Nodo Central SJ670 | Operador de tráfico 24/7 |  |  |  |
| LH / Infraestructura | Soporte técnico y logístico de campo |  |  |  |
| Mayordomías / brigadas | Jefes y coordinadores en campo |  |  |  |
| Defensa Civil BB | Enlace COE (CH4) |  |  |  |
| UTN-FRBB | Enlace convenio FM dúplex |  |  |  |
| Radioclubes locales | Enlace radioaficionados / ENACOM |  |  |  |
Nota de distribución: esta agenda se actualiza dentro de las 24 horas de cada cambio de personal o función y se verifica en cada prueba radial semanal. Su difusión se restringe a los destinatarios del punto 2.
A.3. Registro de Pruebas y Simulacros de Comunicaciones (plantilla)
| Fecha | Prueba / simulacro | Sistemas involucrados | Responsable | Resultado | Observaciones |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |