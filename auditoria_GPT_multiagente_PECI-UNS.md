# Informe de Auditoría Multidimensional y Simulación Multiagente
## PECl-UNS Rev. 0 — Versión 4

**Tipo de documento:** Auditoría externa mediante simulación multiagente  
**Documento auditado:** `PECI_UNS - Rev 0 Versión 4.md`  
**Auditoría precedente:** `auditoria_version4.md`  
**Metodología:** análisis documental + simulación de estrés multiagente  
**Fecha:** septiembre de 2026  
**Resultado global:** **6,9/10**  
**Nivel de madurez:** **Avanzado documental / Intermedio operativo**

---

# I. Resumen ejecutivo

La presente auditoría realiza una evaluación multidimensional del **Plan de Emergencias Climáticas de la Universidad Nacional del Sur (PECl-UNS), Rev. 0 — Versión 4**, tomando como línea de base la auditoría precedente contenida en `auditoria_version4.md` y sometiendo posteriormente el protocolo a una simulación de estrés mediante diez agentes institucionales con responsabilidades, necesidades y perspectivas diferentes.

La evaluación no se limita a verificar la existencia formal de procedimientos. El objetivo principal es determinar si el PECl-UNS puede sostener una respuesta institucional coordinada cuando simultáneamente aparecen restricciones de comunicaciones, interrupciones energéticas, pérdida parcial de infraestructura, presión de la comunidad, presencia de personas con movilidad reducida, actividades académicas críticas y requerimientos externos de información.

La conclusión general es que el PECl-UNS Rev. 0 V4 constituye una **base institucional sólida y conceptualmente superior a un procedimiento reactivo convencional**, particularmente por incorporar anticipación, ventanas temporales de decisión, niveles de alerta, confinamiento, evacuación, custodia escolar, monitoreo centralizado, comunicaciones redundantes, registro documental y ciclo PDCA.

Sin embargo, la simulación demuestra que existe una diferencia significativa entre disponer de un procedimiento escrito y disponer de un **sistema de comando institucional operacionalmente cerrado**.

El principal problema no reside en la ausencia absoluta de procedimientos, sino en la existencia de **bucles operativos incompletos**.

El protocolo contempla:

> detectar → validar → analizar → recomendar → decidir → comunicar → ejecutar → custodiar → recuperar → mejorar

pero, bajo condiciones de máxima presión, debería evolucionar hacia:

> **detectar → validar → decidir → comunicar → confirmar recepción → ejecutar → informar → reevaluar → transferir el mando → recuperar → mejorar**

La simulación identificó diez hallazgos nuevos derivados específicamente de la interacción entre los diez agentes y los escenarios de estrés. Entre ellos se destacan:

- ausencia de una autoridad delegada automática ante falta de respuesta del nivel decisorio;
- dependencia circular entre la declaración de comunicaciones degradadas y la disponibilidad del Centro de Decisiones;
- falta de independencia real entre algunas capas de comunicación;
- ausencia de un mecanismo institucional general de confirmación de recepción;
- inexistencia de un procedimiento formal de transferencia de comando;
- falta de una estructura ICS/SCI explícita;
- ausencia de priorización formal de recursos durante incidentes concurrentes;
- inexistencia de un BIA con RTO/RPO para servicios críticos;
- falta de una secuencia formal de transición energética para RACUNS;
- confusión potencial entre mensaje enviado y mensaje efectivamente recibido, comprendido y ejecutado.

Por ello, la valoración global obtenida es:

# **6,9 / 10**

El PECl-UNS se considera:

> **APTO COMO BASE INSTITUCIONAL, PERO NO RECOMENDABLE PARA SU APROBACIÓN DEFINITIVA SIN CERRAR LAS VULNERABILIDADES CRÍTICAS IDENTIFICADAS.**

Las prioridades inmediatas son:

1. formalizar la delegación de autoridad;
2. transformar P1–P10 en una estructura de comando tipo ICS/SCI;
3. establecer criterios objetivos para activar comunicaciones degradadas;
4. diferenciar claramente capacidades RACUNS operativas, condicionales y proyectadas;
5. incorporar un procedimiento de transferencia de comando y sitio alternativo;
6. implementar confirmación de recepción de comunicaciones críticas;
7. establecer BIA/RTO/RPO para servicios esenciales;
8. formalizar el procedimiento de recuperación posterior a una alerta.

---

# II. Siete fortalezas principales

## 1. Confinamiento como doctrina de protección

El protocolo presenta una definición particularmente sólida del confinamiento ante amenazas externas, evitando convertir automáticamente una emergencia meteorológica en una evacuación.

Esta diferenciación resulta especialmente importante cuando el desplazamiento hacia el exterior puede aumentar la exposición de las personas.

La distinción entre:

- amenaza externa;
- emergencia estructural;
- incendio;
- inundación severa;
- amenaza química o ambiental;
- alerta climática;
- condiciones extremas;

permite seleccionar medidas diferentes según el mecanismo de daño.

La simulación confirmó que esta es una de las partes más robustas del PECl-UNS.

---

## 2. Ventanas temporales de decisión

La existencia de ventanas de decisión asociadas a los turnos académicos constituye una fortaleza significativa.

El protocolo establece:

- turno mañana: decisión hasta las **22:00 del día anterior**;
- turno tarde: decisión hasta las **10:00**;
- turno noche: decisión hasta las **16:00**.

Esto permite pasar de una respuesta exclusivamente reactiva a una estrategia anticipatoria.

El problema detectado no está en la existencia de las ventanas, sino en la gestión de escenarios que evolucionan rápidamente después del cierre de una ventana.

---

## 3. Formulario de alerta y trazabilidad

El **Formulario de Alerta — Anexo B** proporciona una estructura útil para registrar:

- producto;
- fenómeno;
- nivel;
- zona;
- vigencia;
- rangos;
- productos simultáneos;
- acción recomendada;
- notificaciones.

Esto genera una trazabilidad mínima que puede ser utilizada posteriormente durante la auditoría postevento.

El mecanismo es compatible con la evolución hacia un sistema formal de gestión de incidentes.

---

## 4. Cadena P1–P10

La secuencia:

**P1 Monitorizar → P2 Validar → P3 Analizar → P4 Recomendar → P5 Decidir → P6 Comunicar → P7 Ejecutar → P8 Custodiar → P9 Recuperar → P10 Mejorar**

constituye probablemente el elemento con mayor potencial de evolución del documento.

La estructura ya contiene, implícitamente, varias funciones propias de un sistema de comando de incidentes.

La principal recomendación es no reemplazarla, sino **formalizarla y ampliarla** mediante una estructura institucional tipo ICS/SCI.

---

## 5. Arquitectura RACUNS

La incorporación de RACUNS representa una fortaleza considerable.

El protocolo contempla:

- VHF;
- canales diferenciados;
- repetidor;
- comunicación con Defensa Civil;
- UPS;
- alimentación alternativa;
- monitoreo;
- registro;
- canales internos;
- canales externos.

La existencia de una infraestructura de comunicaciones independiente de Internet constituye una capacidad crítica frente a escenarios de pérdida simultánea de energía, telefonía celular e Internet.

No obstante, debe distinguirse con precisión entre:

- capacidad existente y operativa;
- capacidad condicionada;
- capacidad en proceso de incorporación;
- capacidad proyectada.

---

## 6. Procedimiento específico para establecimientos educativos

La sección de custodia escolar presenta un nivel de detalle superior al resto del protocolo.

Se contemplan:

- identificación del responsable;
- autorización de retiro;
- verificación mediante DNI;
- registro de personas autorizadas;
- rutas seguras;
- comunicación a la Base Central;
- permanencia extendida cuando el contexto impide la salida segura.

La simulación, sin embargo, detectó la necesidad de agregar una capa específica para **concentraciones masivas de familiares y gestión de accesos externos**.

---

## 7. Comunicación institucional unificada

La definición de una voz oficial única, canales redundantes y mensajes estructurados constituye otra fortaleza importante.

El protocolo contempla:

- mensajes institucionales;
- canales redundantes;
- lenguaje claro;
- pictogramas;
- accesibilidad;
- comunicación externa.

La principal debilidad no es la falta de canales, sino la ausencia de una metodología institucional universal para verificar:

> **enviado → recibido → comprendido → ejecutado**

---

# III. Vulnerabilidades críticas

| ID | Hallazgo | Agente afectado | Escenario | Severidad | Recomendación |
|---|---|---|---|---|---|
| **N-01** | No existe un tiempo máximo de espera ni autoridad delegada automática cuando el decisor principal no responde. | Rector / CDE / SHST | E4 | **Crítica** | Crear matriz de delegación con suplentes, autoridad temporal y SLA de decisión. |
| **N-02** | La activación de comunicaciones degradadas depende del CDE, que puede ser precisamente uno de los elementos incomunicados. | Operador 24/7 / Telecom | E4 | **Crítica** | Definir criterios objetivos para activar provisionalmente comunicaciones degradadas. |
| **N-03** | Algunas capas de comunicación consideradas redundantes dependen de la misma infraestructura de Internet. | Telecom / Vocería | E4 | **Alta** | Clasificar canales por independencia física y lógica. |
| **N-04** | No existe un mecanismo general de ACK para comunicaciones críticas. | Todos | E3/E4 | **Alta** | Implementar confirmación de recepción, comprensión y ejecución. |
| **N-05** | No existe una transferencia de comando formal ante pérdida simultánea de Colón 80 y San Juan 670. | Rector / SHST / Telecom | E4 | **Crítica** | Crear sitio alternativo y procedimiento de transferencia de comando. |
| **N-06** | P1–P10 no se encuentra formalizado como estructura ICS/SCI con funciones, suplentes y cadena de mando. | Todos | E4 | **Alta** | Formalizar Comando, Operaciones, Planificación, Logística, Administración, Seguridad y Información Pública. |
| **N-07** | No existe una metodología explícita para priorizar recursos cuando existen incidentes concurrentes. | CDE / Infraestructura | E4 | **Alta** | Definir prioridades institucionales y criterios de asignación de recursos. |
| **N-08** | No existe BIA institucional con RTO/RPO para servicios críticos. | Laboratorios / Sistemas / Infraestructura | E4 | **Alta** | Ejecutar análisis de impacto y definir RTO/RPO por servicio crítico. |
| **N-09** | La continuidad energética de RACUNS requiere una secuencia operativa explícita de UPS → generación → cargas prioritarias. | Telecom / Infraestructura | E4 | **Alta** | Incorporar procedimiento de transferencia, prueba y load-shedding. |
| **N-10** | La comunicación enviada no equivale necesariamente a comunicación recibida y comprendida. | Todos | E4 | **Alta** | Incorporar ciclo formal de confirmación. |

## Hallazgos previamente identificados y confirmados por la simulación

| ID | Vulnerabilidad previa | Resultado de la simulación |
|---|---|---|
| **V-01** | Falta de identificación nominal suficiente de centros alternativos del CDE. | **Confirmada** |
| **V-02** | Acuerdo de comunicaciones AM/FM con UTN-FRBB pendiente. | **Confirmada** |
| **V-04** | Disponibilidad limitada de radios portátiles. | **Confirmada** |
| **V-06** | Falta de protocolo específico para eventos masivos. | **Confirmada y agravada** |
| **V-11** | UHF sujeto a regularización administrativa/regulatoria. | **Confirmada** |
| **V-12** | Asistencia a personas con discapacidad o movilidad reducida insuficientemente operacionalizada. | **Confirmada y agravada** |
| **V-15** | Continuidad académica definida de manera genérica. | **Confirmada** |
| **V-16** | Comunicación externa de crisis incompleta. | **Confirmada** |
| **V-19** | Ausencia de protocolo específico de gas. | **Confirmada** |
| **V-21** | Falta de procedimiento específico de rescate de personas atrapadas en ascensores. | **Confirmada** |

---

# IV. Situaciones omitidas o insuficientemente desarrolladas

La simulación multiagente permitió detectar situaciones que no están suficientemente desarrolladas en el protocolo.

## S-08 — CDE incompleto o sin quórum

Debe contemplarse expresamente qué ocurre cuando no se consigue reunir al conjunto de autoridades necesario para tomar una decisión.

El sistema necesita una **autoridad mínima de continuidad**.

---

## S-09 — Pérdida simultánea de Colón 80 y San Juan 670

La pérdida de los dos nodos institucionales principales constituye un escenario de alto impacto.

Debe existir:

- sitio alternativo;
- responsable alternativo;
- medios de comunicación;
- documentación mínima;
- energía;
- radio;
- capacidad de asumir el comando.

---

## S-10 — Información meteorológica contradictoria

Debe contemplarse una situación en la que:

- SMN informa una condición;
- observaciones locales indican otra;
- Defensa Civil comunica una evolución diferente.

Debe definirse quién valida la información y bajo qué criterio se modifica la respuesta.

---

## S-11 — Escalada rápida

Ejemplo:

**Amarillo → Naranja → ACP → Rojo**

en un período inferior a una ventana formal de decisión.

El protocolo necesita un mecanismo de escalada extraordinaria que no dependa de esperar la siguiente ventana horaria.

---

## S-12 — Cese de alerta sin condiciones de reapertura

La finalización de una alerta meteorológica no implica necesariamente que:

- las instalaciones estén seguras;
- haya energía;
- existan comunicaciones;
- las vías de acceso estén liberadas;
- no existan daños estructurales.

Debe separarse:

> **fin de alerta meteorológica**

de:

> **autorización institucional de reapertura**.

---

## S-13 — Falla física del Nodo Central

Debe definirse qué ocurre si San Juan 670 queda:

- inundado;
- sin energía;
- inaccesible;
- evacuado;
- afectado por incendio;
- sin personal.

---

## S-14 — Saturación de CH1

La utilización de CH1 como canal de comando puede generar saturación durante un incidente con múltiples edificios.

Debe establecerse:

- disciplina de radio;
- prioridad de mensajes;
- mensajes de emergencia;
- control del tráfico;
- posibilidad de migración a otro canal.

---

## S-15 — Rumor o información falsa

La pérdida de Internet puede favorecer la aparición de mensajes no oficiales.

Debe existir un procedimiento específico para:

- detectar;
- desmentir;
- emitir información oficial;
- identificar la fuente válida.

---

## S-16 — Emergencia durante cambio de turno

Debe definirse la transferencia formal de:

- responsabilidades;
- estado del incidente;
- recursos;
- comunicaciones;
- pendientes;
- decisiones tomadas.

---

## S-17 — Mantenimiento crítico durante una emergencia

Debe contemplarse qué ocurre cuando personal externo o interno está trabajando en:

- tableros;
- cubiertas;
- ascensores;
- instalaciones eléctricas;
- laboratorios;
- sistemas de climatización;
- infraestructura hidráulica.

---

## S-18 — Contratistas y proveedores externos

Debe existir un mecanismo de:

- identificación;
- localización;
- contabilización;
- evacuación;
- contacto;
- rendición de personal externo.

---

# V. Matriz de evaluación por dominios

| Dominio | Puntaje /10 | Evaluación |
|---|---:|---|
| Gobernanza y cadena de mando | **6,5** | Buena estructura conceptual, pero falta delegación automática y transferencia formal. |
| Monitoreo y detección | **8,0** | Uno de los componentes más desarrollados. |
| Toma de decisiones | **6,5** | Buenas ventanas temporales, pero insuficiente gestión de escalada rápida y ausencia del decisor. |
| Comunicaciones internas RACUNS | **7,5** | Arquitectura sólida, aunque existen capacidades condicionadas y falta ACK. |
| Comunicaciones externas | **6,5** | Existe voz institucional, pero falta mayor redundancia independiente y procedimiento de rumor/crisis. |
| Custodia escolar | **8,0** | Procedimiento detallado y operativo. |
| Infraestructura y energía | **7,0** | Buena previsión, pero insuficiente priorización de cargas y continuidad formal. |
| Accesibilidad e inclusión | **5,5** | Principios presentes, operacionalización insuficiente. |
| Continuidad académica | **5,5** | Falta BIA, RTO/RPO y priorización por servicios. |
| Articulación interinstitucional | **6,5** | Defensa Civil está contemplada, pero faltan SITREP, criterios de transferencia y responsabilidades formales. |
| Mejora continua | **8,0** | PDCA, informes postevento y ejercicios constituyen una base fuerte. |

## Resultado ponderado

# **6,9 / 10**

La puntuación refleja un protocolo documentalmente avanzado, pero que todavía presenta vulnerabilidades importantes cuando se somete a un escenario de estrés sistémico.

---

# VI. Simulación E4 — Escenario de máxima exigencia

## 1. Descripción del escenario

Se selecciona E4 como escenario de máxima exigencia por combinar simultáneamente:

- alerta meteorológica severa;
- actividad académica en curso;
- interrupción de energía;
- pérdida de Internet;
- degradación de telefonía celular;
- presión de familiares;
- afectación de un laboratorio crítico;
- requerimiento de información por Defensa Civil;
- presencia de una persona con movilidad reducida;
- necesidad de comunicación institucional externa;
- circulación de rumores;
- incertidumbre respecto de la recuperación.

Los diez agentes son:

1. **A1 — Rector**
2. **A2 — Responsable SHST**
3. **A3 — Operador del Nodo Central 24/7**
4. **A4 — Director de Telecomunicaciones**
5. **A5 — Vocero institucional**
6. **A6 — Responsable/caretaker de San Juan 670**
7. **A7 — Decano con laboratorio crítico**
8. **A8 — Director de establecimiento preuniversitario**
9. **A9 — Enlace con Defensa Civil**
10. **A10 — Estudiante con movilidad reducida**

---

## 2. 13:30 — Inicio del incidente

El SMN emite una actualización que eleva el escenario a alerta roja.

El Nodo Central recibe la información.

**A3 — Operador:**

> “Base Central a todos los puestos. Confirmo alerta rojo. Repito: alerta rojo. Se inicia protocolo de emergencia.”

El operador registra el evento y comienza la activación de la cadena P1–P10.

**A2 — SHST:**

> “Recibido. Inicio evaluación de condiciones internas y aplicación de medidas de protección.”

**A4 — Telecom:**

> “RACUNS operativo. CH1 para comando, CH2 logística, CH3 operación local, CH4 enlace externo.”

**A1 — Rector:**

> “Necesito informe inmediato de situación y propuesta de suspensión total.”

La primera observación de auditoría aparece inmediatamente: el protocolo define qué debe ocurrir, pero no establece con precisión el tiempo máximo para la decisión ni qué ocurre si el Rector no puede responder.

---

## 3. 13:35 — Caída de servicios

Una falla de infraestructura provoca pérdida de energía en parte de los edificios.

Simultáneamente comienzan problemas de conectividad.

**A4 — Telecom:**

> “Confirmo degradación de Internet. La red móvil está inestable.”

**A3 — Operador:**

> “RACUNS permanece disponible.”

**A6 — San Juan 670:**

> “Base Central tiene UPS. Necesito saber cuánto tiempo tenemos antes de entrar en alimentación alternativa.”

**A4 — Telecom:**

> “Estoy verificando la transferencia.”

La infraestructura de comunicaciones demuestra resiliencia.

Pero aparece una nueva vulnerabilidad: la continuidad radioeléctrica no está acompañada todavía por una matriz formal de cargas críticas.

---

## 4. 13:37 — Presión en la escuela

Los familiares comienzan a acercarse a la institución.

**A8 — Director escolar:**

> “Los padres están preguntando si sus hijos salen.”

**A2 — SHST:**

> “No se autoriza ninguna salida individual mientras esté vigente la condición de riesgo.”

**A8:**

> “Necesito un mensaje institucional para comunicarlo.”

**A5 — Vocero:**

> “Lo preparo. Pero Internet está degradado.”

**A4:**

> “Puedo transmitirlo por radio a los responsables.”

Se evidencia que el procedimiento escolar es más preciso que el procedimiento de comunicación general.

---

## 5. 13:40 — Laboratorio crítico

El Decano informa que el laboratorio ha perdido energía.

**A7 — Decano:**

> “Tenemos corte de energía. Necesito confirmar cuánto tiempo tenemos para preservar los cultivos.”

**A2:**

> “¿Tenés protocolo interno de continuidad?”

**A7:**

> “Sí, pero necesito saber si la energía alternativa será asignada al laboratorio.”

**A6:**

> “¿Qué carga es prioritaria?”

**A4:**

> “Ese es justamente el problema. El protocolo no establece una tabla institucional de prioridad de cargas.”

La simulación descubre aquí N-07 y N-08:

- no existe priorización formal de recursos concurrentes;
- no existe BIA/RTO/RPO suficientemente operacionalizado.

---

## 6. 13:44 — Defensa Civil solicita SITREP

**A9 — Defensa Civil:**

> “COE a UNS, ¿me reciben?”

**A3:**

> “UNS recibe.”

**A9:**

> “Necesito SITREP.”

El operador busca el formato.

**A3:**

> “Estoy consolidando información.”

**A9:**

> “Necesito estado de personas, daños, comunicaciones, energía y requerimientos.”

**A3:**

> “Entendido.”

La solicitud externa demuestra una necesidad de estructuración del reporte de situación.

El protocolo debería establecer formalmente un **SITREP institucional estándar**, con frecuencia y campos obligatorios.

---

## 7. 13:50 — Prioridad energética

La situación comienza a deteriorarse.

**A6:**

> “Tenemos capacidad limitada de generación.”

**A7:**

> “Necesito mantener el laboratorio.”

**A4:**

> “Necesito mantener el nodo de comunicaciones.”

**A2:**

> “También tenemos que mantener sectores de seguridad.”

**A1:**

> “¿Quién decide qué cargas quedan alimentadas?”

Silencio.

La pregunta pone en evidencia una de las vulnerabilidades más importantes.

No existe una matriz suficientemente precisa de:

- carga crítica;
- prioridad;
- tiempo de autonomía;
- RTO;
- consecuencias de pérdida;
- autoridad para desconectar.

---

## 8. 13:54 — Estudiante con movilidad reducida

El estudiante intenta desplazarse dentro del edificio.

**A10 — Estudiante:**

> “Estoy en el segundo piso. Se cortó la energía. ¿Qué hago?”

**A2:**

> “No bajes por tu cuenta. Permanecé en un sector seguro.”

**A10:**

> “¿Quién viene a buscarme?”

El sistema necesita responder con un responsable nominal.

No existe un mecanismo suficientemente explícito de **buddy system**, responsable asignado o equipo de asistencia previamente designado.

**A10:**

> “Necesito saber quién viene.”

La vulnerabilidad V-12 se transforma, en la simulación, en una cuestión operativa concreta.

---

## 9. 13:58 — Confinamiento

La evolución del fenómeno obliga a mantener a las personas en sectores seguros.

**A2:**

> “Confirmo confinamiento. Nadie sale hacia el exterior.”

**A8:**

> “Los alumnos permanecen bajo custodia.”

**A1:**

> “Mantener suspensión.”

**A5:**

> “Necesito emitir la decisión.”

**A4:**

> “Internet continúa degradado.”

**A5:**

> “Entonces necesito canal alternativo.”

La decisión es correcta, pero vuelve a aparecer N-03: varias capas de comunicación dependen de la misma infraestructura física.

---

## 10. 14:02 — Incidente secundario

Se reporta la caída de un árbol y una persona lesionada.

**A3:**

> “Tengo incidente secundario. Persona lesionada.”

**A2:**

> “¿Dónde?”

**A3:**

> “Sector norte.”

**A9:**

> “Defensa Civil puede movilizar recursos.”

**A2:**

> “Solicitamos asistencia.”

Ahora existen dos incidentes simultáneos:

- emergencia climática general;
- accidente con víctima.

El sistema no establece de forma suficientemente explícita cómo se organiza el comando cuando aparece un segundo incidente.

---

## 11. 14:05 — Presión mediática

El Vocero recibe información de que circulan mensajes contradictorios.

**A5:**

> “Hay publicaciones en redes diciendo que la UNS reabre.”

**A1:**

> “No es oficial.”

**A5:**

> “Necesito emitir el desmentido.”

**A4:**

> “La comunicación digital sigue parcialmente caída.”

**A5:**

> “Entonces necesitamos utilizar radio y canales institucionales alternativos.”

La situación demuestra la importancia de separar:

- información meteorológica;
- decisión institucional;
- comunicación pública;
- rumor;
- autorización de reapertura.

---

## 12. 14:10 — Primer SITREP

El operador decide construir manualmente un informe.

**A3:**

> “Voy a consolidar un SITREP.”

**A9:**

> “Necesito hora, situación, personas afectadas, servicios, comunicaciones y requerimientos.”

**A3:**

> “Recibido.”

Se consolida:

- alerta vigente;
- suspensión;
- confinamiento;
- estado energético;
- comunicaciones;
- laboratorio;
- escuela;
- persona con movilidad reducida;
- incidente secundario;
- requerimientos.

El proceso funciona, pero depende de la capacidad individual del operador.

Esto representa un riesgo de dependencia del conocimiento tácito.

---

## 13. 14:15 — SITREP a Defensa Civil

**A3:**

> “SITREP UNS para Defensa Civil. Hora 14:15.”

**A9:**

> “Adelante.”

**A3:**

> “Alerta roja vigente. Actividades suspendidas. Confinamiento activo. Comunicaciones RACUNS operativas. Internet degradado. Energía parcialmente afectada. Laboratorio crítico bajo contingencia. Establecimiento preuniversitario bajo custodia. Persona con movilidad reducida pendiente de asistencia. Se registra incidente secundario con persona lesionada.”

**A9:**

> “Recibido. ¿Requerimientos?”

**A3:**

> “Asistencia para traslado seguro y apoyo ante incidente secundario.”

**A9:**

> “Recibido.”

La interacción confirma la necesidad de formalizar un SITREP estándar y una secuencia de ACK.

---

## 14. 14:30 — Rumor

El Vocero informa nuevamente.

**A5:**

> “Continúan circulando mensajes que dicen que terminó la emergencia.”

**A1:**

> “La alerta todavía no implica reapertura.”

**A2:**

> “Correcto. Necesitamos inspección.”

**A5:**

> “Entonces el mensaje debe decir que el cese meteorológico no implica automáticamente retorno.”

Esta situación identifica una debilidad específica del modelo de recuperación.

---

## 15. 14:45 — Mejora meteorológica

La intensidad del fenómeno comienza a disminuir.

El sistema recibe información que podría interpretarse como finalización de la alerta.

**A3:**

> “La condición meteorológica está mejorando.”

**A1:**

> “No se reabre todavía.”

**A2:**

> “Necesitamos verificar infraestructura, accesos y servicios.”

**A8:**

> “Los padres van a querer retirar a los alumnos.”

**A2:**

> “La custodia continúa hasta que exista decisión formal.”

La decisión resulta operacionalmente correcta.

El protocolo debe diferenciar explícitamente:

> **cese de alerta ≠ reapertura institucional**

---

## 16. 15:00 — Recuperación controlada

**A1:**

> “Mantener suspensión hasta completar evaluación.”

**A2:**

> “Se inicia inspección de sectores críticos.”

**A4:**

> “Telecom verifica autonomía y estabilidad.”

**A7:**

> “Laboratorio continúa en contingencia.”

**A8:**

> “Escuela mantiene custodia.”

**A9:**

> “Defensa Civil queda a la espera del próximo SITREP.”

**A5:**

> “Comunicaré que la suspensión continúa.”

**A10:**

> “Ya tengo asistencia.”

**A6:**

> “San Juan 670 mantiene operación.”

**A3:**

> “Registro todo en bitácora.”

El incidente comienza a estabilizarse.

---

## 17. Resultado de E4

La simulación demuestra que RACUNS y el Nodo Central permiten sostener la comunicación incluso ante una degradación importante de los sistemas convencionales.

Sin embargo, el sistema de comando presenta debilidades cuando simultáneamente aparecen:

- ausencia del decisor;
- múltiples incidentes;
- recursos limitados;
- necesidad de priorización;
- pérdida de canales digitales;
- personas con necesidades específicas;
- presión externa;
- necesidad de informes;
- transferencia de responsabilidades.

La conclusión de E4 es:

> **La infraestructura radioeléctrica puede sostener el mando. Lo que todavía falta es que el mando sepa exactamente qué hacer con esa capacidad bajo condiciones de máxima presión.**

---

# VII. Resultados de los escenarios de estrés

| Escenario | Descripción | Resultado |
|---|---|---:|
| **E1** | Alerta amarilla preventiva | **8,5/10** |
| **E2** | Alerta naranja antes del cierre de ventana | **8,0/10** |
| **E3** | Alerta naranja durante clases | **6,0/10** |
| **E4** | Emergencia severa multisistema | **6,0/10** |
| **E5** | ACP durante evento masivo | **5,5/10** |
| **E6** | Alerta violeta + temperatura extrema | **6,5/10** |
| **E7** | Emergencia con víctima | **5,5/10** |

La tendencia es clara:

> **Cuanto más se aproxima el escenario a una emergencia simultánea, dinámica y multisectorial, mayor es la diferencia entre la capacidad documental del protocolo y su capacidad operacional.**

---

# VIII. Diez acciones prioritarias

## 1. Crear matriz formal de delegación de autoridad

**Prioridad:** inmediata  
**Responsable:** Rectorado / Secretaría General

Debe establecerse quién asume la autoridad cuando:

- el Rector no responde;
- un integrante del CDE está incomunicado;
- el responsable titular está ausente;
- el incidente requiere decisión inmediata.

La matriz debe incluir:

- titular;
- suplente;
- autoridad delegada;
- alcance;
- tiempo máximo de espera;
- condiciones de transferencia.

---

## 2. Convertir P1–P10 en estructura ICS/SCI

**Prioridad:** 90 días  
**Responsables:** Rectorado + SHST

Formalizar funciones de:

- Comando;
- Operaciones;
- Planificación;
- Logística;
- Administración/Finanzas;
- Seguridad;
- Información Pública;
- enlace interinstitucional.

Debe existir además un esquema de suplencias y transferencia de mando.

---

## 3. Activación automática de comunicaciones degradadas

**Prioridad:** inmediata  
**Responsables:** Telecom + Nodo Central

Establecer criterios objetivos para activar comunicaciones degradadas sin depender exclusivamente de una decisión del CDE.

Ejemplo:

> pérdida simultánea de Internet + telefonía celular + canal institucional digital durante X minutos → activación automática de RACUNS como sistema primario de emergencia.

---

## 4. Clasificar las capacidades RACUNS

**Prioridad:** inmediata  
**Responsable:** Telecom

Separar documentalmente:

### Operativas
Capacidades disponibles y verificadas.

### Condicionadas
Capacidades que requieren determinada condición técnica o administrativa.

### Proyectadas
Capacidades todavía no incorporadas.

Esto debe aplicarse particularmente a:

- UHF;
- Meshtastic/LoRa;
- Starlink;
- AM/FM UTN-FRBB.

---

## 5. Incorporar anexo para eventos masivos

**Prioridad:** 90 días  
**Responsables:** Rectorado + SHST + Bienestar + Comunicación

Debe contemplar:

- accesos;
- familiares;
- concentración externa;
- control de ingresos;
- menores;
- personas vulnerables;
- movilidad reducida;
- evacuación;
- comunicaciones;
- prensa;
- transporte;
- cierre de perímetro.

---

## 6. Ejecutar BIA institucional

**Prioridad:** 90 días  
**Responsables:** Secretaría General + Servicios Técnicos + áreas críticas

Identificar los servicios esenciales y determinar:

- impacto de interrupción;
- dependencia;
- prioridad;
- RTO;
- RPO;
- autonomía;
- recursos mínimos;
- procedimiento de recuperación.

Debe incluir especialmente:

- laboratorios;
- sistemas informáticos;
- comunicaciones;
- servicios académicos;
- infraestructura crítica;
- seguridad.

---

## 7. Crear SITREP institucional normalizado

**Prioridad:** inmediata  
**Responsables:** SHST + Nodo Central

Establecer un formato obligatorio con:

- hora;
- nivel de alerta;
- situación;
- personas afectadas;
- infraestructura;
- energía;
- comunicaciones;
- incidentes secundarios;
- recursos;
- necesidades;
- decisiones;
- próximos hitos.

---

## 8. Implementar ACK institucional

**Prioridad:** 90 días  
**Responsables:** Comunicación + Telecom

Para comunicaciones críticas implementar:

> **ENVIADO → RECIBIDO → COMPRENDIDO → EJECUTADO → CONFIRMADO**

Debe existir un procedimiento para los puestos que no confirmen recepción.

---

## 9. Crear procedimiento de reapertura

**Prioridad:** inmediata  
**Responsables:** Rectorado + SHST + Infraestructura

La secuencia debe ser:

> **cese de alerta → evaluación técnica → verificación de servicios → evaluación de accesos → decisión de reapertura → comunicación oficial → retorno progresivo**

Nunca debe asumirse que el cese del fenómeno equivale automáticamente a condiciones seguras.

---

## 10. Ejecutar ejercicio integral E4

**Prioridad:** máximo 12 meses; recomendable dentro de 90 días  
**Responsables:** Rectorado + SHST + Telecom + Defensa Civil

El ejercicio debe simular simultáneamente:

- alerta roja;
- corte energético;
- pérdida de Internet;
- pérdida de telefonía;
- utilización de RACUNS;
- incidente secundario;
- víctima;
- persona con movilidad reducida;
- laboratorio crítico;
- establecimiento escolar;
- presión de familiares;
- requerimiento de Defensa Civil;
- rumor público;
- transferencia de mando.

El ejercicio debe concluir con un informe PDCA y actualización del PECl.

---

# IX. Consideraciones sobre BIA, RTO y RPO

La incorporación de conceptos de **Business Impact Analysis (BIA)**, **Recovery Time Objective (RTO)** y **Recovery Point Objective (RPO)** resulta necesaria para pasar de una planificación general de emergencias a una planificación de continuidad institucional.

En una universidad, no todos los servicios tienen la misma criticidad.

Por ejemplo:

| Servicio | Criticidad | RTO | RPO | Observación |
|---|---|---|---|---|
| Comunicaciones de emergencia | Muy alta | Muy corto | N/A | Debe mantenerse durante el incidente. |
| Nodo Central | Muy alta | Muy corto | Mínimo | Requiere energía y comunicaciones alternativas. |
| Laboratorio crítico | Alta | Definir por laboratorio | Definir | Depende del proceso y materiales. |
| Sistemas académicos | Media/alta | Definir | Definir | Requiere evaluación de continuidad. |
| Servicios administrativos | Media | Definir | Definir | Puede admitir mayor interrupción. |
| Servicios no esenciales | Baja | Definir | Definir | Recuperación posterior. |

La tabla anterior es conceptual y **no reemplaza un BIA institucional real**.

---

# X. Evolución recomendada hacia un ICS/SCI institucional

La estructura P1–P10 ya permite construir una arquitectura de comando.

Una posible evolución sería:

```text
                         COMANDO DEL INCIDENTE
                                  |
             +--------------------+--------------------+
             |                    |                    |
        OPERACIONES          PLANIFICACIÓN        INFORMACIÓN
             |                    |                PÚBLICA
             |                    |
       +-----+------+         SITREP / BIA
       |            |         evaluación
    Edificios    Escuela
       |
    SHST / Infraestructura

             +--------------------+--------------------+
             |                                         |
        LOGÍSTICA                              ADMINISTRACIÓN
             |
       RACUNS / Energía
       Transporte / Recursos

                         ENLACE EXTERNO
                              |
                       Defensa Civil
