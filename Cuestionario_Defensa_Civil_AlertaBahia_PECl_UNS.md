# Cuestionario para la reunión con la Dirección de Defensa Civil de Bahía Blanca

**Ref: PECl-UNS Rev 0 V4**
** ** 
**Marco operativo: Ley 27.287 (SINAGIR) · ISO 22320 (gestión de emergencias) · ISO 22301 (continuidad operativa)**
**Septiembre de 2026 — Reunión de articulación interinstitucional previa a la revisión del protocolo**

---

## 1. Contexto y propósito del cuestionario

El Municipio de Bahía Blanca presentó el 8 de septiembre de 2026 la plataforma **Alerta Bahía** (bahia.gob.ar/alertabahia y botón homónimo en la aplicación MiBahía), que centraliza pronósticos y alertas vigentes, cuatro cámaras en tiempo real sobre el canal Maldonado y el arroyo Napostá, los protocolos de Defensa Civil, un mapa interactivo de **Puntos Seguros de Encuentro y Centros de Evacuados** para Bahía Blanca, Cabildo, General Daniel Cerri e Ingeniero White, y las novedades de obras y mantenimiento del sistema pluvial (1.683 bocas de tormenta relevadas, 33 km de canales a cielo abierto y 64 km de ductos cerrados). La plataforma se declara de funcionamiento permanente —no solo con alerta activa—, se integra con el canal municipal de WhatsApp (82.277 usuarios) e Instagram (más de 20.000 seguidores), y se inscribe en un plan integral de contingencias con **división territorial de la ciudad en ocho sectores**, mapeos comunitarios y capacitaciones en escuelas y centros de evacuados.

La presentación de Alerta Bahía llega a este comité en un momento oportuno, durante el proceso de revisión del PECl-UNS. Con el propósito de acercar el documento a la capacidad real de respuesta de la primera hora de la emergencia, redactamos una serie de **preguntas organizadas en bloques** para las autoridades del municipio. Recorren, en orden, la arquitectura técnica de la plataforma, la interoperabilidad radial y el enlace permanente, los puntos seguros, los centros de evacuados y la sectorización territorial, el plan municipal y el marco SINAGIR, el ciclo de vida del alerta, y la preparación conjunta con capacitación y mejora continua.

---

## 2. Bloque A — Plataforma Alerta Bahía: arquitectura técnica e integración institucional

### P1. Ingesta y trazabilidad de la información meteorológica

¿La incorporación de productos del SMN a Alerta Bahía (alertas, advertencias, ACP, SAT–Temperaturas Extremas) es automática desde las fuentes oficiales o pasa por curación humana del COE antes de publicarse? ¿Qué latencia media registran entre la emisión del SMN y la publicación en la plataforma, y cómo garantizan la trazabilidad del estado?

### P2. Observación meteorológica propia del municipio

¿El municipio cuenta con una estación meteorológica propia, además de la información del SMN que centraliza Alerta Bahía? De ser así, ¿los datos en tiempo real (temperatura, viento, humedad, precipitación) están disponibles para instituciones públicas como la UNS mediante API, webhook u otro mecanismo de integración técnica?

### P3. Interfaz institucional de datos (API)

¿Existe o está previsto un servicio de datos documentado (API pública, feeds GeoJSON/RSS, webhooks, o al menos un canal de suscripción) que permita a instituciones como la UNS consumir en forma automática el estado de alertas, los niveles por zona y el estado de las cámaras? ¿Con qué acuerdos de nivel de servicio (disponibilidad, límites de consulta, soporte) y a partir de qué convenio de adhesión?

### P4. Continuidad operativa de la propia plataforma

¿Sobre qué infraestructura se aloja Alerta Bahía (datacenter propio, nube comercial provincial o nacional)? ¿Cuál es su comportamiento previsto ante la caída simultánea de energía y telecomunicaciones? ¿La plataforma tiene definidos un RTO/RPO, existe réplica en sitio alterno, y si hay una versión de solo texto accesible por canales de bajo ancho de banda (SMS, página estática espejo) que siga operando cuando las redes comerciales caen?

### P5. Canales de salida y alcance de la difusión municipal

El canal municipal de WhatsApp concentra 82.277 usuarios y las campañas institucionales en escuelas y jardines ya están en marcha. ¿Las emisiones de alerta a la comunidad contemplan destinatarios institucionales prioritarios (universidades, hospitales, escuelas de gestión estatal), o sólo el padrón general de vecinos? ¿Existe mecanismo para que la UNS retransmita sus comunicados oficiales — por ejemplo, la suspensión del turno — a través de los canales de Alerta Bahía?

---

## 3. Bloque B — Interoperabilidad radial y enlace permanente

### P6. Homologación radial del enlace CH4

El PECl-UNS define el canal CH4 como "interoperabilidad con el COE de Defensa Civil Bahía Blanca", pero esa interoperabilidad no está homologada del otro lado: ¿qué infraestructura radial opera el COE (bandas VHF/UHF, modos, tonos de silenciamiento CTCSS/DCS, estaciones base, repetidoras propias), y si sería posible acordar un enlace con la UNS directo por radio en caso de comunicaciones comerciales y digitales degradadas? En caso afirmativo, ¿aceptarían incorporar la prueba radial semanal del protocolo como verificación conjunta con reporte recíproco de recepción?

### P7. Notificación proactiva del COE a las instituciones

Ante la emisión de un ACP o de un alerta rojo con impacto inminente, ¿el COE realiza aviso telefónico/radial proactivo a instituciones críticas del distrito (hospitales, universidades, escuelas), o el modelo es que cada institución consulte por sus medios? ¿Existe un padrón formal de enlaces institucionales 24/7 con personal permanente con suplente y horario de guardia verificado?

---

## 4. Bloque C — Puntos seguros, centros de evacuados y sectorización territorial

### P8. Habilitación y capacidad de los Puntos Seguros y Centros de Evacuados

El mapa interactivo publica Puntos Seguros de Encuentro y Centros de Evacuados para las cuatro localidades. ¿Cuáles son los criterios de habilitación de cada sitio (estructura, accesibilidad, sanitarios, respaldo energético), su capacidad nominal en personas, su dotación de personal y los servicios que garantizan? ¿Qué instrumento — convenio marco, acta de afectación, verificación técnica previa — se requiere para que las instalaciones que el PECl-UNS ofrece como gimnasios, comedores o aulas magnas sean efectivamente incorporadas al sistema municipal como centros de acopio o albergue?

### P9. Los ocho sectores territoriales y los predios de la UNS

La ciudad se dividirá en ocho sectores con reuniones de vecinos e instituciones para difundir puntos de encuentro, puntos seguros y puntos de abastecimiento. ¿A qué sector pertenece cada predio universitario (complejo Alem y Altos de Palihue, San Juan 670, Campus Palihue, Escuelas Medias 11 de Abril, Escuela de Agricultura y Ganadería)? ¿Puede la UNS participar formalmente de las reuniones de su sector?

---

## 5. Bloque D — Plan municipal, marco SINAGIR y forma documental

### P10. Documento del plan integral de contingencias

¿Este plan director para la emergencia, existe como documento formal compartible con las instituciones del distrito, y bajo qué estructura se organiza (amenazas, fases SINAGIR, funciones ICS, anexos)? ¿Qué forma y contenidos esperan formalmente del protocolo institucional de una universidad nacional inserta en el distrito — padrones de personal, planos de predios, fichas de enlace, formatos de parte — y existe un registro municipal donde el PECl-UNS debería inscribirse para ser interlocutor válido?

### P11. Criterios de activación del COE y mando unificado

¿Cuáles son los umbrales y criterios con que el COE municipal se activa (adoptan los niveles SMN, o agregan disparadores propios por anegamiento, viento o temperatura), y en qué niveles de activación se convoca a las instituciones de los padrones? 

---

## 6. Bloque E — Ciclo de vida del alerta: cese, verificación y voz pública

### P12. Cese del alerta y notificación formal de fin de evento

¿Quién emite oficialmente el cese o la degradación del alerta a nivel distrital, por qué canales llega esa notificación a las instituciones y en qué plazo máximo desde la publicación del SMN? ¿Existe lista formal de notificación post-evento con confirmación de recepción? ¿El plan municipal exige inspección previa a la reanudación de actividades en edificios públicos afectados, y aceptarían extender esa pauta a los predios universitarios con verificación conjunta de Infraestructura?

### P13. Coordinación de vocerías en nivel rojo

El protocolo PECl-UNS dispone que en nivel rojo la difusión es "exclusiva por parte del Rectorado en coordinación con Defensa Civil y autoridades locales". ¿Existe una pauta municipal de jerarquía de vocerías para el distrito — quién habla primero, qué se espera que digan las instituciones, cómo se evita la contradicción entre municipio, provincia y universidad? ¿Hay mecanismo de coordinación de mensajes en tiempo real (grupo de crisis de comunicaciones, pool de medios, boletín conjunto) al que la Vocería universitaria pueda sumarse durante el evento?

### P14. Emisoras de emergencia y respaldo energético radial

¿El municipio mantiene convenios con emisoras AM/FM locales para la difusión de emergencias, y exige o promueve respaldo energético autónomo en las que ofician de canal oficial? ¿Qué expectativa tienen sobre el potencial convenio dúplex AM-UNS / FM-UTN-FRBB?

---

## 7. Bloque F — Preparación conjunta, capacitación y mejora continua

### P15. Simulacros y ejercicios conjuntos

¿El plan anual de Defensa Civil contempla ejercicios con participación de instituciones críticas, y en qué fecha se programan frente a la temporada de alertas (noviembre–abril)? ¿Aceptarían que el simulacro integral anual universitario sea observado por un evaluador del COE con informe de observaciones, y estarían dispuestos a coejercitar un escenario de colapso de redes, con activación de RACUNS y enlace CH4 real — al menos una vez por temporada?

### P16. Formación como requisito de la participación conjunta

Para la participación de las instituciones en ejercicios y operativos conjuntos — simulacros, activaciones del COE, apoyo en centros de evacuados —, ¿el municipio exige como requisito que los integrantes de los comités de emergencia y de las brigadas cuenten con formación en Sistema de Comando de Incidentes (SCI) o en los protocolos del SINAGIR (Ley 27.287)? En caso afirmativo, ¿el propio municipio dicta esa capacitación o mantiene un registro de cursos homologados al que la UNS pueda recurrir para formar a su Comité de Dirección de Emergencia (CDE) y a sus brigadas de primera intervención?

### P17. Programas educativos extensibles a las escuelas preuniversitarias

Las actividades de prevención en jardines y escuelas (lúdicas para nivel inicial, charlas de Defensa Civil para secundarios) ¿son extensibles a las Escuelas Medias de la UNS (11 de Abril/Alem) y a la Escuela de Agricultura y Ganadería, con contenido específico sobre el retiro autorizado y la custodia extendida? ¿Qué materiales didácticos estandarizados tienen disponibles, y pueden compartirse para adaptarlos a la población universitaria menor de edad?

### P18. Indicadores post-evento y retroalimentación institucional

¿Qué métricas registra sistemáticamente el COE tras cada activación (tiempo emisión SMN→activación, tiempo activación→notificación, evacuados por centro, cobertura de canales, incidentes) y con qué formato se conservan? ¿Estarían dispuestos a compartir esos indicadores con las instituciones articuladas para alimentar el ciclo PDCA del PECl-UNS (informe de 72 horas, indicadores de difusión y convocatoria), y existe interés en constituir un mecanismo formal de retroalimentación post-evento entre municipio y universidad?
