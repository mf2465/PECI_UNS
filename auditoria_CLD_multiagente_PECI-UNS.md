# AUDITORÍA EXPERTA MULTI-AGENTE DEL PECl-UNS
## Rev 0 – Versión 4 (Consolidado Institucional 2026)

**Comité de Auditoría Externa Internacional** — simulación multi-agente bajo marco SINAGIR (Ley 27.287), ISO 22320 (Gestión de Emergencias) e ISO 22301 (Continuidad Operativa)
**Línea base contrastada:** `auditoria_version4.md` (24 hallazgos V-01 a V-24, 7 situaciones no contempladas S-01 a S-07, 5 actores omitidos A-01 a A-05)
**Metodología:** simulación cronológica de 7 escenarios de estrés (E1–E7) con 10 agentes en primera persona, análisis de fricciones inter-agente, verificación de redundancias tecnológicas y validación de plazos de decisión contra los cortes 22:00/10:00/16:00.

---

## SECCIÓN I – RESUMEN EJECUTIVO

**Calificación global: 6,8 / 10**

La auditoría previa calificó el protocolo en 7,5/10 sobre la base de una lectura documental. La simulación multi-agente sostiene la mayor parte de ese diagnóstico —el PECI-UNS es, en su arquitectura documental, uno de los protocolos universitarios más completos de la región en materia de umbrales SMN, ventanas de decisión y doctrina de confinamiento— pero **revisa a la baja la fortaleza que la auditoría previa atribuyó a la "arquitectura de comunicaciones redundante" (RACUNS)**. Puesta a prueba en el Escenario E4 (Rojo + colapso de redes), la redundancia es sustancialmente conceptual: la Capa 3 (Meshtastic/LoRa) figura como "a incorporar" y la Capa 1 (troncal VHF) depende de un **repetidor físico único** en el Complejo Alem sin sitio alterno. Esto degrada, en la práctica, el nivel real de resiliencia de todo el sistema de mando y control durante el escenario que el propio protocolo define como el más exigente.

A esto se suman siete hallazgos nuevos, no identificados por la auditoría documental previa, que solo emergen al simular la interacción entre agentes con criterios institucionales en conflicto (Sección III), y una contradicción interna no detectada previamente entre las Secciones 4.7 y 5 del documento respecto del fenómeno Zonda.

El protocolo **no es descartable ni requiere reescritura**: su columna vertebral (glosario unificado SMN, umbrales regionales, ventanas horarias, doctrina de resguardo, custodia escolar) es sólida y debe conservarse. Lo que la simulación expone es que varias de sus redundancias "de papel" no están aún desplegadas físicamente, y que la gobernanza de nombres propios (suplentes, handies por sede, corte de tránsito) sigue incompleta.

---

## SECCIÓN II – PUNTOS FUERTES VALIDADOS

1. **Ventanas horarias de decisión (22:00 / 10:00 / 16:00 — Sección 7.1).** Validado en E2: aun con una alerta Naranja emitida a las 21:30 (30 minutos antes del corte), el mecanismo obligó al CDE a producir un dictamen y al Rector a resolver antes de las 22:00, evitando la improvisación. Es una de las mejores prácticas del documento y de las pocas normativas universitarias argentinas que fija plazos duros y no discrecionales.

2. **Doctrina de Resguardo vs. Evacuación (Sección 7.8).** Validada en E3 y E4: frente a la tentación de A7 (Decano con laboratorio crítico) de evacuar personal hacia el exterior durante ráfagas extremas, la doctrina escrita le dio a A1 (Rector) y A2 (SHST) un argumento normativo firme para sostener el confinamiento, evitando el error clásico de exponer personas en la vía pública durante el pico del fenómeno.

3. **Ficha del Alerta y regla de lectura obligatoria de la línea de tiempo (Sección 7.3).** Validada en los siete escenarios: obliga al operador del Nodo Central (A3) a leer el detalle zonal y no solo el color del mapa, lo que en E6 (niebla + ola de calor simultáneas) evitó que se tratara como un evento único cuando en realidad eran dos productos SAT distintos con lógicas de decisión diferentes.

4. **Protocolo de custodia escolar con verificación de DNI y Registro de Retiro (Sección 8, Anexo F).** Validado en E3 y E7: le dio a A8 (Director de Escuela Preuniversitaria) una herramienta concreta para resistir la presión de familias que exigían el retiro de menores durante el confinamiento, algo que en la simulación resultó ser el punto de mayor fricción emocional pero de resolución más clara gracias al procedimiento escrito.

5. **Biblioteca de mensajes pre-estructurados M1–M5 (Sección 11.5).** Validada en E1, E2 y E3: permitió a A5 (Vocero) emitir comunicados en minutos, sin redactar bajo presión, manteniendo el formato de lenguaje claro exigido por 11.4. Fue el único subsistema que funcionó sin fricciones en las tres primeras simulaciones.

6. **Concepto de arquitectura en capas de RACUNS (Sección 12.8).** Aun con el hallazgo crítico de punto único de falla (Sección III, N-01), el diseño conceptual de degradar de VHF a UHF, de UHF a difusión masiva AM/FM y de digital a presencial dio a los agentes técnicos (A4) un marco de decisión claro sobre "qué capa probar primero" en E4, en lugar de improvisar.

7. **Antecedente real de la Feria Gastronómica del Sudoeste Bonaerense 2025 (Sección 12.2).** Validado como evidencia empírica (no solo teórica) en E5: demuestra que operadores sin experiencia previa en radiocomunicaciones lograron sostener coordinación con handies VHF bajo colapso real de telefonía celular con 20.000 asistentes, lo cual respalda la viabilidad de la Sección 12.9 (capacitación de operadores no especializados).

---

## SECCIÓN III – VULNERABILIDADES CRÍTICAS DETECTADAS

### III.1. Hallazgos nuevos y confirmados con nueva evidencia de simulación

| ID | Hallazgo | Agente(s) afectado(s) | Escenario donde colapsa | Severidad | Recomendación concreta |
|---|---|---|---|---|---|
| **N-01** *(NUEVO)* | El repetidor VHF de 50 W en Alem (Sección 12.4) es un **punto único de falla (SPOF)** de toda la Capa 1/Troncal (CH1). La Capa 3 (Meshtastic/LoRa), única redundancia real de infraestructura de radio, figura textualmente como "a incorporar" (12.8): hoy no existe. Si el repetidor cae (sobretensión, impacto de rayo pese a pararrayos, o agotamiento de las 24–48 h de autonomía DC), el mando y control troncal se degrada directamente al Anexo presencial (mensajería a pie). | A4 (Telecom.), A3 (Nodo Central), A9 (Def. Civil) | E4 | **Crítica** | Realizar un análisis formal de riesgo de sitio único (BIA de infraestructura) y evaluar un segundo punto de repetición (p. ej. Palihue) o antena de respaldo de despliegue rápido; priorizar el piloto Meshtastic/LoRa del Anexo D como redundancia real, no aspiracional. |
| **N-02** *(NUEVO)* | La flota de handies (Sección 12.6) asigna H-08 a "Escuelas Medias" y H-09 a la Escuela de Agricultura y Ganadería, pero **no asigna handy dedicado al Instituto Inicial y Primario**, pese a que la Sección 2 lo incluye expresamente en el alcance especial y es la población de menor autonomía y mayor dependencia de adultos de todo el sistema. | A8 (Dir. Escuela), A6 (Mayordomo) | E3 | **Alta** | Asignar un handy H-13 dedicado al Instituto Inicial y Primario, con protocolo de custodia diferenciado por edad (ver Sección IV). |
| **N-03** *(NUEVO)* | **Brecha de tránsito matutino**: la decisión del Turno Mañana se toma a las 22:00 del día anterior (7.1), pero el propio protocolo prevé una lectura de "confirmación o ajuste" del SAT recién a las 06:00 (7.2), hora en que el turno ya está formalmente en curso y parte de la comunidad ya se trasladó al predio. No hay procedimiento para una escalada que ocurra en esa ventana de 22:00–06:00 mientras las personas ya están en tránsito. | A3 (Nodo Central), A2 (SHST), A9 (Def. Civil) | E1 | **Alta** | Definir un "corte de tránsito" adicional (p. ej. 05:00) exclusivo para alertas nocturnas extraordinarias, con protocolo de "regreso seguro a domicilio" para quienes ya iniciaron traslado. |
| **N-04** *(NUEVO — contradicción interna)* | **Contradicción entre Secciones 4.7 y 5.** La 4.7 define el fenómeno Zonda como propio de "cordillera, precordillera, puna y llanos desde 38°S hasta Bolivia (Cuyo y NOA)", zona que no incluye Bahía Blanca. Sin embargo, la tabla de la Sección 5, titulada "Umbrales aplicables a la región de Bahía Blanca (Patagonia)", incluye explícitamente niveles Z1–Z4 de viento Zonda. Un operador de guardia sin formación meteorológica formal (Sección 9.4, protocolo de transición) puede aplicar un criterio geográficamente erróneo. | A3 (Nodo Central) | E1 | **Media-Alta** | Eliminar la fila de Zonda de la tabla de la Sección 5, o aclarar expresamente que se incluye solo a efectos de salidas de campo hacia Cuyo/NOA. |
| **N-05** *(NUEVO)* | No existe **BIA (Business Impact Analysis)** ni **RTO/RPO** definidos para el Centro de Datos ni para la Capa 1 digital (web, Moodle, correo), pese a contar con ATS y UPS (6.3, 9.3). El ANEXO OPERATIVO 05 (Plan de Continuidad Operativa y Crítica) existe como documento relacionado pero no está integrado ni referenciado en detalle dentro del PECI. | A4 (Telecom.) | E4 | **Media** | Incorporar un BIA formal de los sistemas digitales críticos, con RTO/RPO explícitos, articulado con el Anexo Operativo 05; evaluar estandarizar la ingesta del SAT vía protocolo **CAP** (Common Alerting Protocol) para automatizar la Ficha del Alerta y reducir el tiempo detección→ficha. |
| **N-06** *(NUEVO)* | **Conflicto de doble rol no previsto**: el personal esencial (operadores del Nodo Central, mayordomos, docentes) reside en la misma ciudad expuesta al evento (antecedente: inundación 07/03/2025) y puede tener su propio hogar o familia en riesgo simultáneo. El protocolo no prevé relevo de emergencia ni preparación familiar previa del personal esencial, un principio estándar en doctrina ICS/FEMA. | A3, A6 | E4 | **Media** | Incorporar un plan de preparación familiar del personal esencial y un protocolo de relevo de emergencia con doble dotación garantizada por turno. |
| **N-07** *(NUEVO — amplía V-06)* | La Capa 1 (digital institucional) se define expresamente para "públicos internos" (11.2); la Capa 2 (radio/TV) es de alcance masivo pero unidireccional y pasivo. **No existe un canal dirigido a público externo no institucional** en eventos masivos (ej. Feria Gastronómica, 20.000 asistentes), más allá de la megafonía in situ. | A5 (Vocero), A9 (Def. Civil) | E5 | **Alta** | Habilitar un canal de emergencia por evento con inscripción rápida vía QR/SMS al ingreso, para alcanzar a asistentes externos sin cuenta institucional. |
| V-11 *(confirmado, severidad elevada)* | El uso de UHF "sujeto a regularización ante ENACOM" (12.10) se puso a prueba en E4: es precisamente durante el colapso de VHF cuando el operador recurre a UHF como Capa 2 de proximidad, es decir, el uso irregular ocurre exactamente en el momento de mayor necesidad y mayor exposición institucional. | A4, A9 | E4 | **Crítica** *(elevada de Alta a Crítica)* | Regularizar ante ENACOM antes de la aprobación formal, o restringir el uso operativo de UHF a frecuencias ya licenciadas hasta obtener la habilitación. |

### III.2. Tabla de fricciones inter-agente detectadas en la simulación

| Escenario | Agente 1 | Agente 2 | Fricción |
|---|---|---|---|
| E2 | A1 Rector | A2 SHST | Alerta a las 21:30 deja 30 minutos: SHST exige Ficha completa y cruce de turnos (P3) antes de recomendar; Rector presiona por una resolución inmediata para no incumplir el corte de 22:00. |
| E3 | A7 Decano (lab. crítico) | A1 Rector | El confinamiento decretado a las 14:15 impide a A7 trasladar cultivos/animales al exterior; tensión entre continuidad científica (BIA de laboratorio) y doctrina de resguardo (7.8). |
| E4 | A4 Telecom. | A9 Enlace Def. Civil | Con CH1 caído por sobretensión en el repetidor, A9 exige enlace CH4 inmediato con el COE municipal; A4 debe reencaminar por UHF sin cobertura formal, generando ventana de silencio de radio. |
| E5 | A5 Vocero | A9 Enlace Def. Civil | El Vocero difunde por redes institucionales, pero los 20.000 asistentes externos de la Feria no siguen esas cuentas; Defensa Civil reclama desconocer el protocolo interno de confinamiento del predio. |
| E6 | A8 Dir. Escuela | A1 Rector | Niebla y ola de calor simultáneas sin umbral objetivo de demora de inicio de turnos (7.6 es cualitativa); el Director exige un criterio numérico que el Rector no tiene para decidir. |
| E7 | A5 Vocero | A1 Rector | Tensión entre transparencia informativa inmediata y la reserva legal de datos de la víctima hasta notificación formal a la familia y a la autoridad judicial. |

### III.3. Verificación de redundancias (foco en E4)

- **Capa 1 (Digital) + energía comercial:** caen simultáneamente. La Capa 4 (Starlink móvil) debía reemplazarla, pero el vehículo no estaba pre-posicionado (12.4 lo describe como "proyectada"/"a designar por el CDE"), generando más de 40 minutos de demora en su activación real.
- **Capa 5/Troncal VHF (CH1):** cae por sobretensión en el repetidor de Alem pese al pararrayos. Sin Capa 3 (Meshtastic) desplegada, el sistema recae directamente en la Capa 6 (presencial: mensajería a pie de mayordomos y brigadistas), retrocediendo el ICS institucional a un modelo pre-radioeléctrico.
- **Capa 2 (AM/FM):** es la única que se mantiene operativa de punta a punta, al depender de UPS propia independiente de la red comercial — valida parcialmente el diseño, aunque su alcance es unidireccional y no permite retroalimentación desde el terreno.

### III.4. Validación de plazos (cortes 22:00 / 10:00 / 16:00)

| Escenario | Corte aplicable | Hora de alerta SMN | Hora real de decisión simulada | ¿Cumplido? |
|---|---|---|---|---|
| E1 (Amarillo) | No aplica corte de suspensión | 05:30 | Registro 05:35; difusión preventiva 05:50 | Cumplido, con margen amplio |
| E2 (Naranja anticipado) | 22:00 (Turno Mañana) | 21:30 | Decisión del Rector 21:57; difusión 21:59 | Cumplido, **margen de solo 1 minuto** — riesgo estructural del modelo |
| E3 (Naranja durante cursada) | No aplica corte (evento en curso) | 14:15 (impacto 15:00) | Confinamiento decretado 14:22 | Cumplido vía protocolo de confinamiento, no de suspensión |

---

## SECCIÓN IV – SITUACIONES NO CONTEMPLADAS

1. **Conflicto de doble rol del personal esencial** frente a su propia exposición doméstica al mismo evento (N-06) — no contemplado en absoluto por la auditoría previa.
2. **Plan de resuministro de energía del repetidor Alem** más allá de las 24–48 h de autonomía declaradas (12.11), ante eventos prolongados como el antecedente del 07/03/2025.
3. **Protocolo diferenciado por edad dentro de la custodia escolar**: el Anexo F es un registro único genérico; Nivel Inicial (3–5 años) exige lógicas de contención muy distintas a Secundario (adolescentes con autonomía de desplazamiento), y el protocolo no distingue.
4. **Mecanismo de "opt-in" temporal (QR/SMS) para público externo** de eventos masivos, ampliando el hallazgo V-06 de la auditoría previa con una solución técnica concreta.
5. **Protocolo de desmovilización de RACUNS**: la Sección 12.3 define con precisión el criterio de *activación* del Estado de Comunicaciones Degradadas, pero no define el criterio ni el procedimiento de *desactivación* y retorno de los handies, con riesgo de saturación de canal durante la fase de reanudación (P9).
6. **Preservación de escena y comunicación con la familia ante víctima fatal** (amplía S-04 de la auditoría previa): la simulación de E7 mostró en la práctica la tensión entre A5 (Vocero) y A1 (Rector) descripta en III.2, un choque que la sola enumeración documental de la auditoría previa no había evidenciado.

---

## SECCIÓN V – MATRIZ DE CALIFICACIÓN POR DOMINIO

| Dominio | Puntaje (0–10) | Justificación breve |
|---|---|---|
| Gobernanza y cadena de mando | 6,5 | CDE bien estructurado, pero suplentes sin nombrar (V-01 confirmado, sin cambios desde la auditoría previa) |
| Monitoreo y detección | 8,0 | Doble operador, fuentes redundantes del SAT, Ficha del Alerta robusta |
| Toma de decisiones | 7,0 | Ventanas horarias claras, pero brecha de tránsito matutino (N-03) y márgenes de 1 minuto en alertas tardías (III.4) |
| Comunicaciones internas (RACUNS) | 6,0 | Diseño en capas sólido en el papel; SPOF crítico del repetidor único (N-01) y Capa 3 aún no implementada |
| Comunicaciones externas (Difusión) | 7,0 | Matriz de difusión y plantillas M1–M5 sólidas; convenio UTN-FRBB aún no firmado (V-02) y sin canal para público externo (N-07) |
| Custodia escolar | 6,5 | Procedimiento de retiro con DNI robusto; sin handy dedicado a la escuela con menores más vulnerables (N-02) ni distinción por edad (Sección IV.3) |
| Infraestructura y energía | 7,5 | Buena redundancia energética triple por nodo; sin RTO/RPO definido para sistemas digitales críticos (N-05) |
| Accesibilidad e inclusión | 4,5 | Solo registro de personas con movilidad reducida, sin protocolo de asistencia (V-12 confirmado, crítico) |
| Continuidad académica | 5,5 | "Virtualidad asincrónica" mencionada sin desarrollo operativo (V-15 confirmado) |
| Articulación interinstitucional | 6,5 | Buen enlace con Defensa Civil vía CH4; mayoría de convenios aún no formalizados |
| Mejora continua | 8,0 | Ciclo PDCA, informe post-activación a 72 h e indicadores bien definidos |
| **Promedio ponderado** | **6,7** | Arquitectura documental sólida con brechas operativas y de implementación física detectadas por simulación |

---

## SECCIÓN VI – NARRATIVA DEL PEOR ESCENARIO (E4: Rojo extremo con colapso de redes)

**13:28 hs.** El cielo sobre Bahía Blanca se oscurece con una velocidad que ningún pronóstico de línea de tiempo había anticipado en detalle. En la Mayordomía de San Juan 670, A3 (Operador Nodo Central, turno de Seguridad Patrimonial) mira la pantalla del SAT: "Rojo. Fenómeno tormenta severa, ráfagas destructivas y granizo, zona Bahía Blanca, vigencia inmediata." Completa la Ficha del Alerta en tiempo récord y llama por CH1: "Base Central a CDE, Base Central a CDE. Alerta ROJO confirmada, repito, ROJO, vigencia inmediata, cambio."

**13:31 hs.** A2 (Jefe de SHST) responde desde su handy H-01: "Recibido, Base Central. Activando Comité de Dirección de la Emergencia. Rector, ¿me copia?" A1 (Rector) contesta por WhatsApp institucional, ya que está en una reunión externa: "Copiado. Declaro Rojo. Suspensión total automática, Sección 7.4.C. Autorizo difusión inmediata." A5 (Vocero) dispara el mensaje M2 por los canales digitales.

**13:36 hs.** El primer quiebre. A4 (Director de Telecomunicaciones) informa por CH1: "Atención, atención. Se reporta caída de energía comercial en Complejo Alem y San Juan 670. Telefonía celular degradada al 20%. Internet institucional caído." A3 pregunta, con la voz tensa: "¿Y el repetidor?" A4, tras un silencio de casi un minuto que en la sala de la Mayordomía se siente eterno, responde: "El ATS del Data Center conmutó a generador, correcto. Pero el repetidor de Alem no responde. Sospechamos sobretensión pese al pararrayos. CH1 está degradado."

**13:40 hs.** A9 (Enlace de Defensa Civil Municipal) irrumpe por el canal de enlace: "COE Municipal a UNS, COE Municipal a UNS. Necesitamos confirmación de su Estado de Comunicaciones. Tenemos reportes de árboles caídos en Alem y semáforos sin energía en toda la zona." A3 no puede transmitir por CH1 con claridad; intenta CH4 pero la señal también depende parcialmente del mismo repetidor. "Defensa Civil, aquí Base Central, repita último mensaje, tenemos degradación en el troncal." A9, con el tono normativizado de quien desconfía de promesas sin respaldo, contesta: "Eso es exactamente lo que temíamos. Ustedes garantizaron redundancia en el convenio de articulación. ¿Dónde está?"

**13:44 hs.** A1 (Rector), aún fuera de la Sala de Crisis primaria de Colón 80, ordena: "Declaren el Estado de Comunicaciones Degradadas. Formalmente. Que quede asentado en el libro de guardia." A2 (SHST) confirma el asiento y activa el protocolo de la Sección 12.3. Comienza la migración de capas: Capa 1 caída, Capa 5/Troncal degradada. A4 intenta la Capa 2: "Vamos a UHF de proximidad mientras reparamos el troncal." A9 objeta de inmediato: "UHF sin regularización ENACOM no es un canal legal para coordinar con nosotros de forma oficial, aunque en esta situación lo vamos a usar igual, que conste."

**13:49 hs.** En Palihue, A6 (Mayordomo) reporta por handy H-07, ya en UHF: "Base Palihue a Base Central. Tenemos un árbol caído sobre la senda 3, cerca del estacionamiento norte. Ningún vehículo dañado que veamos, pero la senda está bloqueada." A3 anota en el libro de guardia y confirma recepción por colación, tal como exige la disciplina radial de la Sección 12.9.

**13:53 hs.** A8 (Director de Escuela Preuniversitaria), desde el establecimiento de 11 de Abril, transmite por H-08: "Escuela a Base Central. Alumnos en confinamiento en sectores internos, lejos de ventanales. Tenemos cuatro familias en portería exigiendo retiro inmediato." A3 responde citando el protocolo: "Custodia estricta, Sección 8.2. Sin retiro individual sin adulto autorizado y verificación de DNI contra el listado. Manténganse firmes." A8, con la carga emocional del que enfrenta a los padres en persona, insiste: "Entendido, pero decíselo vos a una madre que está golpeando la reja." A2 interviene por radio: "Es la doctrina, no es negociable. Custodia extendida hasta que el CDE autorice el retiro."

**13:58 hs.** A10 (Estudiante con movilidad reducida), en el edificio de San Juan 670, no tiene handy ni canal directo: solo puede escribir por WhatsApp institucional a un compañero, que a su vez avisa a Mayordomía. La brecha de accesibilidad, señalada como crítica en la Sección III, se hace visible en tiempo real: nadie en el protocolo tiene asignada la tarea explícita de verificar su situación, y A6 debe improvisar un desvío de su ronda para asistirla.

**14:02 hs.** A4 confirma un nuevo problema: "El vehículo con el kit Starlink no está desplegado, el CDE nunca resolvió formalmente quién lo conduce en este evento." A1 (Rector), ya en tránsito hacia Colón 80, autoriza por WhatsApp: "Autorizo despliegue inmediato de la unidad móvil, que designe conductor y salga ya." Pasarán más de 40 minutos hasta que el enlace satelital esté operativo, degradando también la Capa 4 en el momento en que más se la necesita.

**14:10 hs.** A7 (Decano con laboratorio crítico) pide autorización para trasladar reactivos sensibles a temperatura fuera del edificio, ante el temor de un corte prolongado. A2 (SHST) cita la Sección 7.8: "Doctrina de resguardo. No se evacúa al exterior con ráfagas extremas en curso. Aseguren lo que puedan puertas adentro." La fricción queda registrada, sin resolución completamente satisfactoria para A7.

**14:18 hs.** La única capa que sigue funcionando de punta a punta es la radial: la Radio AM de la UNS, con UPS propia, continúa emitiendo el comunicado M2 cada 30 minutos como exige la matriz de difusión (11.6), aunque unidireccionalmente, sin poder recibir confirmaciones del terreno.

**14:25 hs.** A4 logra restablecer un enlace parcial de VHF mediante un handy portátil elevado en la terraza de San Juan 670, en línea de vista directa con Palihue, mientras el repetidor de Alem permanece fuera de servicio. Es una solución de emergencia, no un procedimiento documentado: la simulación confirma que, sin Capa 3 (malla Meshtastic) desplegada, la resiliencia real del sistema depende de la improvisación técnica de A4 y no del diseño escrito. A9 (Defensa Civil) cierra el bloque con una frase que resume el stress-test: "El plan en el papel es de diez. Lo que acabamos de ver es un siete, y solo porque tuvieron gente capaz improvisando en la terraza."

---

## SECCIÓN VII – RECOMENDACIONES PRIORITARIAS

1. **[Inmediato]** Nombrar explícitamente por resolución rectoral a los suplentes de cada rol del CDE. — *Rectorado / Secretaría General* (confirma V-01).
2. **[Inmediato]** Elaborar un plan de contingencia formal ante la caída del repetidor único de Alem (sitio alterno o antena de respaldo de despliegue rápido). — *Dirección de Telecomunicaciones* (N-01).
3. **[Inmediato]** Asignar un handy dedicado (H-13) al Instituto Inicial y Primario. — *Escuelas Preuniversitarias / Telecomunicaciones* (N-02).
4. **[Inmediato]** Regularizar el uso de UHF ante ENACOM o restringir su uso operativo hasta contar con la licencia. — *Dirección de Telecomunicaciones* (confirma y eleva V-11).
5. **[90 días]** Definir un "corte de tránsito" adicional (p. ej. 05:00) para alertas nocturnas extraordinarias previas al inicio del Turno Mañana. — *Comisión de Plan de Emergencia / SHST* (N-03).
6. **[90 días]** Corregir la contradicción entre las Secciones 4.7 y 5 respecto del fenómeno Zonda. — *Comisión de Plan de Emergencia* (N-04).
7. **[90 días]** Crear el Anexo "Protocolo de Asistencia a Personas con Discapacidad", con personal designado y equipamiento. — *Secretaría de Bienestar Universitario* (confirma V-12, severidad crítica).
8. **[90 días]** Pre-posicionar el vehículo con kit Starlink y definir un protocolo de despliegue en menos de 15 minutos tras declararse el Estado de Comunicaciones Degradadas. — *Subsecretaría de Infraestructura y Servicios* (refuerza Capa 4).
9. **[12 meses]** Incorporar de forma efectiva la Capa 3 (Meshtastic/LoRa), hoy solo proyectada, como redundancia real del troncal VHF. — *Dirección de Telecomunicaciones* (N-01).
10. **[12 meses]** Desarrollar un BIA formal con RTO/RPO explícitos para el Centro de Datos y la Capa 1 digital, articulado con el Anexo Operativo 05, evaluando la estandarización de la ingesta del SAT vía protocolo CAP. — *Secretaría General de Servicios Técnicos y Transformación Digital* (N-05).

---

*Fin del informe. Documento generado a partir de la lectura íntegra de `PECI_UNS - Rev 0 Versión 4.md` y `auditoria_version4.md`.*
