# Auditoría Experta Multi-Agente del Protocolo de Emergencias Climáticas

**PECl-UNS · Revisión 0 – Versión 4 (Consolidado Institucional 2026) · Universidad Nacional del Sur**

- **Marco normativo:** Ley 27.287 (SINAGIR) · ISO 22320 · ISO 22301
- **Método:** Simulación de 10 agentes institucionales (A1 a A10) en 7 escenarios de estrés cronológicos (E1 a E7)
- **Línea base:** `auditoria_version4.md` — calificación documental previa 7,5/10
- **Dictamen del comité:** 12 hallazgos nuevos (NV-01 a NV-12) y 6 contradicciones internas (C-1 a C-6)
- **Calificación global bajo simulación:** **6,3 / 10**
- **Emisión:** Comité de Auditoría Externa Internacional · Bahía Blanca · Septiembre de 2026

---

## Índice

- [SECCIÓN I — RESUMEN EJECUTIVO]
  - [1.1. Objeto, método y alcance de la auditoría]
  - [1.2. Calificación global]
  - [1.3. Los cuatro hallazgos que explican la nota]
- [SECCIÓN II — PUNTOS FUERTES VALIDADOS]
  - [F-1. Ventanas horarias de decisión 22:00 / 10:00 / 16:00 (protocolo, 7.1)]
  - [F-2. Doctrina de confinamiento seguro interno frente a evacuación (protocolo, 7.8 y 7.5)]
  - [F-3. Protocolo de custodia y retiro autorizado en escuelas (protocolo, 8, Anexo F y C.3)]
  - [F-4. Arquitectura RACUNS en capas con disciplina de canales (protocolo, 12.5, 12.8 y 12.9)]
  - [F-5. Biblioteca de mensajes pre-estructurados M1 a M5 (protocolo, 11.5)]
  - [F-6. Monitoreo dual con ficha del alerta y regla de lectura del detalle (protocolo, 7.2, 7.3, 9.2 y Anexo B)]
  - [F-7. Ciclo de mejora continua PDCA con informe de 72 horas (protocolo, 15, Anexos D y E)]
- [SECCIÓN III — VULNERABILIDADES CRÍTICAS DETECTADAS]
  - [3.1. Hallazgos nuevos de la simulación multi-agente (NV-01 a NV-12)]
  - [3.2. Confirmaciones de la auditoría previa con evidencia nueva de simulación]
  - [3.3. Contradicciones internas del documento]
- [SECCIÓN IV — SITUACIONES NO CONTEMPLADAS]
- [SECCIÓN V — MATRIZ DE CALIFICACIÓN POR DOMINIO]
- [SECCIÓN VI — NARRATIVA DEL PEOR ESCENARIO]
  - [E4. Tormenta roja con colapso simultáneo de redes: reconstrucción minuto a minuto]
- [SECCIÓN VII — RECOMENDACIONES PRIORITARIAS]
- [ANEXO A — REGISTROS DE SIMULACIÓN (E1 a E7)]
  - [E1. Escenario Amarillo Preventivo: vientos de 60 km/h, alerta emitida a las 05:30]
  - [E2. Escenario Naranja con decisión anticipada: alerta emitida a las 21:30]
  - [E3. Escenario Naranja durante cursada: alerta a las 14:15, impacto a las 15:00]
  - [E4. Escenario Rojo extremo con colapso de redes: tormenta a las 13:30]
  - [E5. Escenario ACP durante evento masivo: Feria Gastronómica en Palihue]
  - [E6. Escenario Advertencia violeta y Temperaturas Extremas simultáneas: lunes 06:00]
  - [E7. Escenario crítico con víctima: árbol sobre estudiante en Palihue]
- [ANEXO B — Tabla maestra de fricciones entre agentes]
- [ANEXO C — Cumplimiento de las ventanas de decisión 22:00 / 10:00 / 16:00]

---

## SECCIÓN I — RESUMEN EJECUTIVO

### 1.1. Objeto, método y alcance de la auditoría

El presente informe somete el Protocolo de Emergencias Climáticas de la Universidad Nacional del Sur (PECl-UNS, Revisión 0 – Versión 4, Consolidado Institucional 2026) a una auditoría de ejecutabilidad mediante simulación dinámica. A diferencia de la revisión documental estática que produjo la línea base (auditoria_version4.md, 24 vulnerabilidades, calificación 7,5/10), esta intervención opera como Comité de Auditoría Externa Internacional bajo el marco de la Ley 27.287 (SINAGIR), ISO 22320 e ISO 22301, y aplica un método de estrés con diez agentes institucionales simulados (A1 a A10) que interactúan en primera persona sobre siete escenarios cronológicos de severidad creciente (E1 a E7). El propósito no es relevar el texto del protocolo, sino ejecutarlo: ponerlo a correr contra el reloj, contra las jerarquías reales y contra las caídas simultáneas de los sistemas que él mismo declara como fundamento (Sección 12.2 del protocolo: temporal del 07/03/2025, tornado del 17/12/2023 y apagón del 16/06/2019).

Cada escenario se resolvió con narrativa minuto a minuto, tabla de fricciones entre agentes, verificación del comportamiento de las capas de comunicación y validación del cumplimiento de las ventanas de decisión 22:00 / 10:00 / 16:00. Los registros completos obran en el Anexo A; la reconstrucción literaria del peor escenario (E4) se desarrolla en la Sección VI. Los hallazgos nuevos se identifican con prefijo NV- y no repiten los V-xx de la auditoría previa salvo cuando se aporta evidencia de simulación adicional, caso en el cual se cita expresamente el identificador original.

### 1.2. Calificación global

**Calificación global del PECl-UNS Rev 0 V4 bajo simulación multi-agente: 6,3 / 10.**

La auditoría previa otorgó 7,5/10 sobre la base de la calidad documental. Ese puntaje es consistente con lo que el protocolo dice; el que otorga este comité mide lo que el protocolo puede hacer. La diferencia (1,2 puntos) no proviene de nuevos errores de redacción, sino de la puesta en ejecución: el documento describe una arquitectura de anticipación notable (ventanas horarias, doctrina de confinamiento, RACUNS en cinco capas, plantillas M1-M5) cuya cadena de disparo presenta cuatro puntos únicos de falla que la revisión estática no podía advertir. El bucle de activación de RACUNS (NV-01), la dependencia total del monitoreo de la conectividad a internet (NV-02), la vocería como cuello de botella sin guardia 24/7 (NV-03) y la ausencia de autoridad de mando inicial delegada (NV-04) configuran un patrón sistémico: un protocolo de excelencia normativa cuya primera hora de emergencia depende, en los hechos, de la improvisación virtuosa de tres o cuatro personas.

Dicho patrón quedó demostrado de manera repeatible: en tres de los siete escenarios (E2, E3, E4) la respuesta institucional correcta se produjo por decisiones tomadas fuera del procedimiento escrito — el SHST ordenando confinamiento sin resolución del CDE, Base Central declarando el Estado de Comunicaciones Degradadas ad-referéndam, un director escolar inventando la ventana de retiro diferido. El protocolo funcionó porque había gente buena desobedeciendo su letra con buen criterio. Esa es la definición operativa de un sistema frágil, y la razón de una nota que castiga la ejecutabilidad sin desmerecer el diseño.

**Tabla 1 — Síntesis cuantitativa de la auditoría**

| **Indicador**                                         | **Resultado de la simulación**                           |
|-------------------------------------------------------|----------------------------------------------------------|
| **Escenarios ejecutados**                             | 7 (E1 a E7), en secuencia cronológica                    |
| **Agentes simulados**                                 | 10 (A1 a A10), con cruces de fricción documentados       |
| **Hallazgos nuevos (NV-01 a NV-12)**                  | 12: 2 críticos, 6 altos, 4 medios                        |
| **Hallazgos previos confirmados con evidencia nueva** | 6 (V-01, V-02, V-03, V-04, V-06, V-12)                   |
| **Contradicciones internas detectadas**               | 6, con número de sección (ver 3.3)                       |
| **Cumplimiento de cortes 22/10/16**                   | Decisión: 4/5 casos en término; difusión: 1/5 en término |
| **Capas RACUNS que reemplazaron a redes caídas**      | E4: Capa 1 (VHF) sostuvo 6 h; Capa 4 nunca se activó     |
| **Calificación global**                               | **6,3 / 10 (previa documental: 7,5)**                    |

### 1.3. Los cuatro hallazgos que explican la nota

Primero, el bucle de activación: RACUNS debe activarse cuando el CDE declara el Estado de Comunicaciones Degradadas (protocolo, 12.3), pero cinco de los diez miembros del CDE no tienen handy asignado en la flota de doce unidades (12.6), de modo que el único órgano habilitado a declarar el estado que activa la red alternativa es, en gran parte, inalcanzable por esa misma red. En E4 el Estado se declaró a las 13:45 por acto improvisado del SHST y de Base Central, ratificado casi dos horas después. Segundo, el monitoreo sin vía de respaldo: las tres fuentes del SAT previstas para el Nodo Central (9.3: web, aplicación y correo del SMN) comparten un único modo de falla, la conectividad a internet; en E4 el protocolo perdió, simultáneamente, el fenómeno que administraba y la red que lo administraba, y el cese del alerta llegó por un oficial de Defensa Civil que leyó el parte por radio (CH4).

Tercero, la difusión con titular único y sin guardia: el principio de voz oficial única (11.1) concentra la emisión en la Dirección de Comunicación Institucional sin esquema de suplencia nocturna, sin handy asignado y sin plantillas pre-aprobadas de publicación automática; la latencia medida entre decisión y difusión fue de 11 minutos en E2, 8 en E3, 30 en E6 y 2 horas 40 en el preventivo de E1, suficiente para que miles de personas ya estuvieran en tránsito. Cuarto, el vacío de comando en la primera media hora: para un alerta naranja que estalla durante la cursada (E3, 45 minutos de margen), el protocolo ordena el confinamiento prioritario (7.4.B) pero no dice quién lo ordena; lo hizo el SHST por iniciativa propia, con el Rector localizable recién por teléfono. Estos cuatro puntos, y no las 24 vulnerabilidades de la línea base, son el argumento de la calificación, porque todos ellos tienen capacidad de producir la parálisis de la primera hora, que es la única hora que importa en un evento severo.

## SECCIÓN II — PUNTOS FUERTES VALIDADOS

Los siete elementos que siguen no son fortalezas de papel: cada uno fue sometido a estrés en al menos un escenario y resistió, total o parcialmente, en condiciones adversas. Para cada uno se consigna la evidencia de simulación que valida su efectividad, con la salvedad de que ninguna fortaleza individual compensa los puntos únicos de falla descritos en la Sección III.

### F-1. Ventanas horarias de decisión 22:00 / 10:00 / 16:00 (protocolo, 7.1)

La regla de oro de suspensión anticipada operó como anillo de encarrilamiento en todos los escenarios con decisión obligatoria. En E2, con el alerta naranja emitido a las 21:30 — apenas 30 minutos antes del corte — la cadena completa ficha, notificación, dictamen y decisión del Rector cerró a las 21:58: dos minutos de holgura. En E6, la decisión por calor extremo para el turno mañana se adoptó a las 22:05 del domingo. La predecibilidad de los cortes también protegió a las escuelas preuniversitarias, cuyas familias recibieron la novedad con margen para organizar la jornada. El defecto detectado no es de la regla sino de la cadena P5-P6: la difusión excedió el corte en 11 a 30 minutos (NV-03 y Anexo C), pero la decisión misma, que es el paso irreversible jurídica y operativamente, se adoptó siempre dentro de término cuando hubo alerta con antelación razonable.

### F-2. Doctrina de confinamiento seguro interno frente a evacuación (protocolo, 7.8 y 7.5)

En E3, E4 y E5 la doctrina evitó exponer personas a ráfagas de 90 a 122 km/h y a granizo. La evidencia más contundente proviene de E4: a las 16:20 un panel vidriado del pabellón 3 de Palihue estalló hacia el interior durante una ráfaga de 122 km/h y no produjo ni un herido, porque el aula estaba desalojada en cumplimiento del confinamiento temprano ordenado a las 13:45, que alejó a las personas de los ventanales. En E5, veinte mil asistentes fueron migrados de carpas a pabellones de hormigón siguiendo la directiva específica de Palihue (6.2), con solo dos contusiones leves en el movimiento. La doctrina demuestra alineación con la práctica internacional (retención ante tornados y granizo) y fue correctamente comprendida por los agentes operativos sin necesidad de consulta al texto, señal de que su lógica es intuitiva para personal no especializado.

### F-3. Protocolo de custodia y retiro autorizado en escuelas (protocolo, 8, Anexo F y C.3)

El circuito de verificación DNI contra listado, asiento en el Registro de Retiro Autorizado y reporte de nómina a Base Central funcionó completo en E3: 320 alumnos de 11 de Abril confinados en gimnasio, 47 en custodia extendida al final del día por corte de transporte, registro firmado sin observaciones y reportes periódicos por H-08. La custodia extendida (8.4) con provisión de agua y resguardo también se activó sin fricción interna. La fortaleza tiene un borde: la fricción con padres que exigían retiro durante el pico de ráfagas (E3 y E4) fue resuelta por decisión de los directores fuera del texto (NV-10), lo que no invalida el protocolo pero demuestra que su letra está incompleta en el punto más sensible, que es justamente el que enfrenta la mayor presión de familias.

### F-4. Arquitectura RACUNS en capas con disciplina de canales (protocolo, 12.5, 12.8 y 12.9)

Cuando en E4 cayeron simultáneamente la energía, la telefonía celular y el acceso a internet, la Capa 1 (troncal VHF por repetidor Alem con banco de baterías de 24 a 48 horas) sostuvo la totalidad de la coordinación durante más de seis horas: llamados generales, reportes de novedades cada 30 minutos, enlace con el COE de Defensa Civil por CH4 y despacho de recursos. El comportamiento bajo carga fue destacable: cuando el tráfico logístico del evento de E5 saturó CH1, la imposición de la disciplina de canales por la Dirección de Telecomunicaciones (12.9.2) degradó el tráfico a CH2 y restituyó la exclusividad de mando en menos de un minuto. La experiencia operativa previa (Feria Gastronómica 2025, antecedente recogido en 12.2) se tradujo en reglas escritas que los operadores respetaron bajo estrés.

### F-5. Biblioteca de mensajes pre-estructurados M1 a M5 (protocolo, 11.5)

Las plantillas redujeron el tiempo de redacción a minutos en los momentos de mayor presión: en E2 el comunicado de suspensión salió del plantilla M2 en siete minutos desde la decisión, con estructura, lenguaje claro y una única acción por mensaje. En E5, el mensaje M3 se adaptó para el confinamiento masivo con una sola modificación de alcance. La ventaja no es solo de velocidad: bajo estrés, la plantilla impide los dos errores clásicos de la comunicación de emergencia, el mensaje con múltiples acciones contradictorias y el silencio mientras se redacta. El defecto asociado (ausencia de plantilla para naranja durante cursada, que no es ACP) se registra en el Anexo A, escenario E3.

### F-6. Monitoreo dual con ficha del alerta y regla de lectura del detalle (protocolo, 7.2, 7.3, 9.2 y Anexo B)

La rutina estructurada de lecturas (06:00, 10:00, 16:00, 18:00, 19:00, 22:00 y extraordinarias) y la obligación de leer la línea de tiempo completa antes de decidir (4.6 y 7.3) demostraron valor exactamente donde se las buscaba: en E6, con advertencia violeta por niebla y alerta rojo por calor simultáneos, el operador pudo reconstruir el cuadro completo de productos vigentes porque el protocolo le exige leer el detalle y no el color del mapa. La ficha del alerta (Anexo B) generó además trazabilidad auditable: cada simulación dejó registro de recepción, fuente, fenómeno, nivel, vigencia, turnos intersectados y notificados, exactamente lo que exige la revisión posterior bajo ISO 22320. Esta fortaleza, no obstante, colapsa en E4 por la dependencia de internet (NV-02): la rutina es buena, pero el medio no es autónomo.

### F-7. Ciclo de mejora continua PDCA con informe de 72 horas (protocolo, 15, Anexos D y E)

El propio diseño de indicadores del protocolo permitió que esta auditoría midiera su incumplimiento: el indicador de tiempo decisión-difusión (15.3) es el que reveló el patrón de latencia post-corte en E2, E3 y E6, y el informe de 72 horas fue correctamente encargado al cierre de E4 con las tres brechas principales identificadas por los propios agentes. Esa capacidad de autodiagnóstico es una fortaleza real y poco frecuente: el protocolo no solo prescribe la respuesta, sino que instrumenta el aprendizaje posterior. La limitación es de alcance, no de arquitectura: ningún indicador mide hoy el tiempo de convocatoria del CDE, el estado de carga de la flota bajo corte prolongado ni la cobertura de canales efectivos por emisora, huecos que las recomendaciones R-01 a R-10 de la Sección VII incorporan al tablero.

## SECCIÓN III — VULNERABILIDADES CRÍTICAS DETECTADAS

### 3.1. Hallazgos nuevos de la simulación multi-agente (NV-01 a NV-12)

Los doce hallazgos que siguen son exclusivos de la simulación dinámica: no constan en la auditoría previa porque solo se manifiestan cuando el protocolo se ejecuta contra reloj y contra caídas combinadas de sistemas. La severidad se asignó por combinación de probabilidad de ocurrencia (los disparadores son los escenarios que el propio protocolo declara verosímiles, 12.2) y de consecuencia sobre la vida, la primera hora de respuesta o la continuidad institucional.

**Tabla 2 — Hallazgos nuevos de la auditoría multi-agente**

| **ID**    | **Hallazgo (con sección del protocolo)**                                                                                                                                                                                                            | **Agente afectado** | **Escenario de colapso** | **Severidad**  | **Recomendación concreta**                                                                                                                              |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|--------------------------|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| **NV-01** | Bucle de activación de RACUNS: 5 de 10 miembros del CDE sin handy (12.6); el órgano que debe declarar el Estado de Comunicaciones Degradadas (12.3) es inalcanzable por la única red viva                                                           | A1, A5, A3          | E4 (13:33-15:30)         | **CRÍTICA**    | Asignar 5 handies al CDE (Rectorado, Vocería, Planificación, Académica, Sanidad) y regla de quórum de 3 para la declaración, con ratificación por acta  |
| **NV-02** | Monitoreo sin vía offline: web, app y correo del SMN (9.3) comparten la conectividad a internet como único modo de falla; en colapso el Nodo pierde la fuente de alertas                                                                            | A3                  | E4 (13:31 en adelante)   | **CRÍTICA**    | Enlace satelital bidireccional en Base Central + boletín SMN por CH4 convenido con Defensa Civil + receptor de radiodifusión de monitoreo               |
| **NV-03** | Vocería como cuello de botella 24/7: voz oficial única (11.1) sin guardia nocturna, sin handy, sin suplencia operativa y sin plantillas de publicación automática; latencia P5-P6 de 11 a 160 minutos                                               | A5, A3              | E1, E2, E6               | **ALTA**       | Guardia de vocería rotativa + plantillas M1-M5 firmadas en blanco con publicación automática por el Nodo + suplente designado por resolución            |
| **NV-04** | Sin autoridad de mando inicial (Incident Commander) para naranja durante cursada: 7.4.B ordena confinamiento prioritario pero no asigna quién lo ordena; asimétrico con ACP (7.5)                                                                   | A3, A2              | E3 (14:15-14:22)         | **ALTA**       | Resolución de delegación de autoridad: SHST y Base Central ordenan confinamiento preventivo de oficio, con ratificación posterior del CDE               |
| **NV-05** | Canal obligatorio inexistente: la matriz de difusión exige FM UTN-FRBB en Naranja/Rojo (11.6) pero el convenio está en curso (11.3); la Capa 5 queda reducida a AM UNS sin respaldo energético protocolar                                           | A5, A4              | E2, E4                   | **ALTA**       | Firmar convenio + emisora FM alternativa de respaldo + grupo electrógeno propio para Radio AM UNS (extiende V-02)                                       |
| **NV-06** | Recursos críticos diferidos a resolución de emergencia: la radiobase móvil y el kit Starlink (Capa 4) serán designados por resolución del CDE (12.4) durante la propia emergencia                                                                   | A4                  | E4 (14:10)               | **ALTA**       | Designación permanente previa por resolución: vehículo, chofer, kit, procedimiento de despliegue y apuntamiento bajo llave                              |
| **NV-07** | Sin censo de ocupación ni rendición de cuentas (accountability ICS): bajo confinamiento nadie sabe cuántas personas hay por edificio; el registro existe solo para retiros escolares (Anexo F)                                                      | A6, A8, A9          | E5, E4, E7               | **ALTA**       | Censo digital por aula y pabellón con reporte agregado por CH1 cada 30 minutos, extendiendo la rutina de novedades de 9.2.2                             |
| **NV-08** | Reanudación sin verificación técnica previa (all-clear): P9 (Anexo A) pasa del cese SMN a la resolución de reanudación sin inspección de daños residuales                                                                                           | A2, A6              | E7 (15:35 en adelante)   | **ALTA**       | Checklist de inspección post-evento firmado por SHST e Infraestructura como condición previa obligatoria de P9                                          |
| **NV-09** | Fenómenos simultáneos sin regla de combinación: niebla (7.6: demorar traslados) y calor rojo (7.7: virtualidad) generan directivas contradictorias para el mismo turno                                                                              | A1, A6, A8          | E6 (domingo 22:00)       | **MEDIA-ALTA** | Matriz de decisión combinada por pares de fenómenos con criterio de prevalencia: vida, continuidad, patrimonio                                          |
| **NV-10** | Retiro autorizado sin ventana diferida: 8.3 no condiciona el egreso escolar al pico del evento; los directores improvisaron la denegación durante ráfagas, exponiéndose jurídicamente                                                               | A8                  | E3 (14:45), E4 (15:00)   | **MEDIA-ALTA** | Cláusula de ventana de retiro diferido en la Sección 8 y en el Anexo F: egresos escalonados entre pulsos de ráfaga por acceso cubierto                  |
| **NV-11** | Autonomía energética de la flota VHF: solo San Juan 670 tiene cargadores sobre UPS (6.3); en eventos de más de 6 horas los handies H-07, H-08 y H-09 agotan batería sin dónde recargar                                                              | A6, A8              | E4 (15:00-20:30)         | **MEDIA**      | Kit de carga dual (vehículo y solar) por predio con baterías de repuesto en cada mayordomía                                                             |
| **NV-12** | Interfaz sanitaria externa incompleta: sin activación protocolar del sistema público de emergencias (107/SAME), sin criterio de traslado institucional, sin guion familiar y sin preservación de escena no fatal (S-04 cubre solo la víctima fatal) | A2, A7, A5          | E7 (15:17-16:40)         | **ALTA**       | Anexo de emergencia médica: cadena 107 - Medicina del Trabajo - traslado, guion de contacto familiar y preservación de escena para eventos con víctimas |

*Los agentes se identifican según la nomenclatura del comité: A1 Rector, A2 SHST, A3 Operador Nodo Central, A4 Telecomunicaciones, A5 Vocero, A6 Mayordomo, A7 Decano con laboratorio, A8 Director de escuela preuniversitaria, A9 Enlace Defensa Civil, A10 Estudiante con movilidad reducida.*

### 3.2. Confirmaciones de la auditoría previa con evidencia nueva de simulación

Se confirman seis hallazgos de la línea base, ahora con evidencia de ejecución que en varios casos agrava su severidad. V-01 (suplencias no nombradas): en E4 el Rector fue inalcanzable entre las 13:33 y las 15:30, y ninguna suplencia designada pudo sustituirlo; el CDE de hecho se constituyó con seis de diez miembros y un externo. V-02 (convenio UTN-FRBB en curso): en E2 y E4 el canal FM de la matriz de difusión simplemente no existía y la Capa 5 quedó reducida a la AM universitaria, que además operó sin respaldo energético normado. V-03 (transición sin capacitación): en E1 el operador de Seguridad Patrimonial dudó de la clasificación del umbral (ráfagas de 60 km/h contra el valor naranja de 65) y demoró la validación; en E4 el mismo perfil debió operar la Base VHF de comando. V-04 (flota insuficiente): E4 y E5 mostraron decanatos, comedor, residencias y biblioteca sin radio; la reserva H-12 terminó afectada al enlace del COE. V-06 (eventos masivos): E5 evidenció además la ausencia de mando unificado con el productor del evento. V-12 (accesibilidad): E4 transformó el hallazgo en bloqueo material, con un estudiante en silla de ruedas retenido en tercer piso por desconexión de ascensores sin equipamiento de bajada asistida.

### 3.3. Contradicciones internas del documento

La simulación expuso contradicciones entre secciones del propio protocolo que la lectura lineal no revela. Se listan con su numeración para su tratamiento en la próxima revisión de versión.

**Tabla 3 — Contradicciones internas detectadas**

| **N.º** | **Contradicción**                                                                                                                           | **Secciones en conflicto** | **Efecto en simulación**                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|--------------------------------------------------------------------------------|
| C-1     | La matriz de difusión exige la FM UTN-FRBB como canal mínimo obligatorio, pero el convenio que la habilita está en curso de establecimiento | 11.6 vs 11.3               | E2 y E4: canal omitido; Capa 5 reducida a AM UNS                               |
| C-2     | El Estado de Comunicaciones Degradadas lo declara el CDE, pero cinco de sus diez integrantes no integran la flota de handies                | 12.3 vs 12.6 y 10.1        | E4: declaración ad-referéndam improvisada a las 13:45                          |
| C-3     | El confinamiento durante cursada se activa sin ordenante explícito, mientras la evacuación exige orden del CDE                              | 7.4.B vs 7.8               | E3: orden de confinamiento por iniciativa del SHST, sin respaldo escrito       |
| C-4     | El nivel Rojo promete asistencia a personas con necesidades especiales a la vez que desconecta ascensores sin medios alternos               | 7.4.C vs 6.2               | E4: usuario de silla de ruedas retenido en tercer piso sin silla de evacuación |
| C-5     | Las tres fuentes del SAT dependen de internet, pese a que el fundamento del protocolo es el antecedente de caída simultánea de redes        | 9.3 vs 12.2                | E4: Nodo sin fuente de alertas durante 4,5 horas                               |
| C-6     | El respaldo web de la Capa 1 es el enlace Starlink de RACUNS, cuya dotación recién será designada por resolución del CDE                    | 11.2 vs 12.4               | E4: Capa 4 sin activación efectiva en 6 horas de evento                        |

El patrón de las seis contradicciones es homogéneo: el protocolo enuncia capacidades cuya existencia formal depende de condiciones aún no cumplidas (convenios sin firma, designaciones sin resolución, fuentes sin respaldo). Bajo el principio de trazabilidad de ISO 22320, una capacidad documentada pero no instrumentada es un riesgo mayor que una capacidad omitida, porque el operador confía en ella y no planifica su ausencia. La revisión V5 debería resolver las seis con resoluciones y anexos ejecutables antes de la aprobación por Rectorado.

## SECCIÓN IV — SITUACIONES NO CONTEMPLADAS

La lista siguiente prioriza vacíos del protocolo verificados en simulación, distintos de los hallazgos NV. La prioridad combina probabilidad del disparador (todos tienen antecedente regional verificable) y magnitud del daño si ocurren sin procedimiento. Se indica entre paréntesis cuando el vacío extiende una situación S-xx ya anotada por la auditoría previa; en esos casos el aporte nuevo es la evidencia de ejecución y la delimitación operativa del hueco.

1.  **Prioridad 1**— Víctima con lesiones graves durante alerta activa y SAME saturado: el protocolo no define la cadena 107, el criterio de traslado institucional ni la preservación de escena no fatal (extiende S-04, que cubre solo la víctima fatal). En E7 el traslado se decidió en 20 minutos sin cobertura legal documental.

2.  **Prioridad 2**— Falla del propio repetidor RACUNS (impacto de rayo o daño de torre en el BBYF): la Capa 1 cae si cae el repetidor (lo admite 12.8) y no existe procedimiento de degradación a simplex puro ni protocolo de relevo del nodo. La autonomía de 24 a 48 horas de baterías tampoco contempla eventos de más de dos días.

3.  **Prioridad 3**— Alerta emitido menos de 60 minutos antes del corte: la ventana E2 demostró que el circuito P2 a P6 completo consume entre 28 y 41 minutos; no existe procedimiento de decisión abreviada (quórum reducido, voto anticipado por plantilla) para alertas de emisión tardía.

4.  **Prioridad 4**— Flujo entrante de consultas de familias de asistentes externos a eventos masivos: toda la arquitectura de difusión (11.2) es unidireccional; en E5, con telefonía colapsada, miles de familias no tenían canal de entrada y el único dato disponible era la señal radial en loop.

5.  **Prioridad 5**— Censo de ocupantes por edificio bajo confinamiento: sin censo no hay rendición de cuentas ICS, no hay priorización de evacuación y no hay respuesta para el COE municipal (E4 y E5).

6.  **Prioridad 6**— Eventos de más de 8 horas con recarga de flota VHF bajo corte eléctrico: solo la mayordomía de San Juan 670 tiene cargadores respaldados por UPS (6.3); los handies de escuelas y Palihue entran en zona de agotamiento.

7.  **Prioridad 7**— Reanudación con daños residuales (árboles inestables, vidrios, subsuelos anegados): P9 no exige verificación técnica previa; en E7 el resto del fuso caído quedó inclinado sobre la senda mientras el alerta ya había cesado.

8.  **Prioridad 8**— Matriz de prioridad de carga del generador móvil único de 100 kVA: laboratorios críticos, comunicaciones y mayordomía compiten sin regla de arbitraje (E4, 14:25); tampoco hay BIA que fije RTO y RPO de los servicios digitales (SIU, Moodle, Data Center), por lo cual la priorización no puede fundarse en nada objetivo.

9.  **Prioridad 9**— Estudiante con movilidad reducida en edificio alto con ascensores desconectados: contradicción C-4 sin salida material (extiende V-12); la evacuación asistida manual de un adulto en silla de ruedas desde tercer piso es inviable bajo ráfagas extremas.

10. **Prioridad 10**— Cierre anticipado del turno noche en curso al emitirse un alerta nocturno (21:30 en E2): las ventanas de 7.1 regulan la suspensión anticipada de turnos futuros, no la liberación anticipada del turno en desarrollo.

11. **Prioridad 11**— Rumores virales durante eventos con víctimas (E7, 15:25): sin monitoreo de redes ni vocería de crisis en caliente, la primera narrativa pública del incidente fue una leyenda con fotografía.

12. **Prioridad 12**— Integración del personal del evento masivo (productor, seguridad privada, catering) al mando institucional: en E5 el personal de megafonía respondía a un empleador ajeno a la UNS (extiende V-06); falta el concepto de mando unificado ICS con contrato y anexo operativo.

Ninguna de las doce situaciones requiere tecnología nueva ni presupuesto mayor: ocho se resuelven con resoluciones, cláusulas y plantillas; tres con equipamiento menor (sillas de evacuación, kits de carga, receptor satelital) y una con convenio. Lo que ninguna admite es su resolución durante el evento, que es lo que la simulación probó: cada una de ellas fue resuelta en caliente por improviso, con el costo de tiempo y de exposición jurídica que el detalle del Anexo A registra.

## SECCIÓN V — MATRIZ DE CALIFICACIÓN POR DOMINIO

La matriz pondera once dominios según su contribución al resultado de la primera hora de emergencia. Los pesos reflejan la doctrina ISO 22320: gobernanza, decisión y comunicaciones concentran casi la mitad del tablero porque determinan si el resto del sistema llega a activarse. El promedio ponderado resultante es 6,3/10 y coincide con la calificación global de la Sección I por construcción metodológica: el tablero se calificó dominio a dominio con la evidencia de los Anexos A a C y luego se promedió, sin ajuste posterior.

**Tabla 4 — Calificación por dominio (ponderada)**

| **Dominio**                        | **Peso**  | **Puntaje (0-10)** | **Justificación breve**                                                                                                                 |
|------------------------------------|-----------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Gobernanza y cadena de mando       | 15 %      | 5,5                | Bucle de activación NV-01, suplencias sin nombrar (V-01), CDE de hecho con 6/10 en E4; PDCA y roles titulares bien definidos            |
| Monitoreo y detección              | 10 %      | 6,0                | Rutina 7.2 y ficha Anexo B excelentes; fuentes 100 % dependientes de internet (NV-02) y operador de transición sin capacitación (V-03)  |
| Toma de decisiones                 | 12 %      | 6,0                | Ventanas 22/10/16 validadas (F-1); sin autoridad de mando inicial (NV-04) ni decisión abreviada para alertas tardías                    |
| Comunicaciones internas (RACUNS)   | 12 %      | 7,0                | Capa 1 sostuvo 6 h en E4 (F-4); 5 miembros del CDE fuera de la red, Capa 4 sin designación (NV-06), UHF sin regularizar (V-11)          |
| Comunicaciones externas (Difusión) | 10 %      | 6,0                | Plantillas M1-M5 (F-5) y multicapa; vocería sin guardia 24/7 (NV-03), canal FM inexistente (NV-05), sin canal de entrada para familias  |
| Custodia escolar                   | 8 %       | 7,5                | Protocolo 8 robusto y validado en E3 (F-3); fricción de retiro durante pico sin regla (NV-10)                                           |
| Infraestructura y energía          | 8 %       | 7,0                | Triple redundancia por nodo y ATS del Data Center; recarga de flota limitada (NV-11) y prioridad del generador móvil sin matriz         |
| Accesibilidad e inclusión          | 5 %       | 4,0                | Registro de movilidad reducida sin protocolo de asistencia (V-12); contradicción C-4 con bloqueo material en E4                         |
| Continuidad académica              | 5 %       | 5,0                | Virtualidad asincrónica prevista (7.7) sin plan de virtualidad, sin BIA ni RTO/RPO (V-15); escuelas sin criterio térmico propio (NV-09) |
| Articulación interinstitucional    | 8 %       | 6,5                | CH4 con el COE operó en E4 y E5; convenios clave sin firmar (V-02), mando unificado ausente en eventos masivos (V-06)                   |
| Mejora continua                    | 7 %       | 7,5                | PDCA, indicadores e informe de 72 h (F-7); faltan indicadores de convocatoria, censo y cobertura real de canales                        |
| **Promedio ponderado**             | **100 %** | **6,3**            | **Calificación global coincidente con la Sección I; diseño ≈ 8,5, ejecutabilidad ≈ 4,5**                                                |

La lectura de la matriz identifica tres franjas. La franja alta (7,0 y más: custodia, mejora continua, RACUNS, infraestructura) agrupa los dominios donde el protocolo invirtió diseño específico y evidencia de campo previa. La franja media (6,0 a 6,5: monitoreo, decisión, difusión, articulación) contiene los dominios con arquitectura correcta y cadena de disparo frágil. La franja baja (accesibilidad 4,0, continuidad académica 5,0, gobernanza 5,5) agrupa los dominios donde la simulación encontró bloqueos materiales o vacíos normativos completos. La diferencia entre 6,3 y el 7,5 de la línea base se explica casi por completo en la franja media: es el costo, medido, de depender de personas en lugar de procedimientos para encender el sistema.

## SECCIÓN VI — NARRATIVA DEL PEOR ESCENARIO

### E4. Tormenta roja con colapso simultáneo de redes: reconstrucción minuto a minuto

Contexto: lunes de primavera. Desde el mediodía el SMN mantiene alerta naranja por tormentas; los tres predios principales operan con cursada plena del turno tarde. La cifra de personas dentro de los predios se estima en unos 3.800 estudiantes y 400 trabajadores; la palabra estima es parte del hallazgo, porque nadie la sabe con certeza. La narrativa que sigue reconstruye, con diálogos literales entre los diez agentes del comité, cómo opera y dónde casi colapsa el protocolo cuando ocurre exactamente lo que su Sección 12.2 declara como fundamento: la caída simultánea de energía, telefonía celular e internet.

13:28. El celular del operador de guardia vibra con la notificación del SMN: actualización extraordinaria, escalada a rojo por tormentas con ráfagas de hasta 110 km/h y granizo, impacto inmediato. A3, guardia de Seguridad Patrimonial en su segundo año, está solo en la Mayordomía de San Juan 670. Completa la Ficha del Alerta número 143 y dispara la notificación al grupo del CDE mientras sube el volumen de la base radial.

> «Base Central San Juan a todas las bases: SMN escaló a rojo, ráfagas de ciento diez, impacto inmediato. Reporte de novedades, cambio.»

13:31. El fenómeno llega antes que cualquier respuesta. La primera ráfaga de 118 km/h encaja contra la fachada sudoeste del complejo Alem y los tres predios se apagan a la vez: red eléctrica de media tensión caída, antenas celulares sin datos, internet institucional muerto. La UPS de la mayordomía entra en carga sin solución de continuidad: la Base VHF sigue viva. A3 repite el llamado general.

> «H-05, Alem: cortina metálica de San Juan 672 golpeando, el subsuelo empieza a anegar, motobomba en marcha.»
>
> «H-07, Palihue: clausura total de sendas arboladas, confinamiento en pabellones uno a cinco, sin novedades de personas.»

13:33. A3 intenta llamar al jefe del SHST: el celular no da tono. Intenta el WhatsApp institucional: sin conexión. Sube el volumen al máximo y espera: contra lo que teme, la red responde, porque la red no depende de nada de lo que acaba de caer. Es la única cosa del sistema que sigue en pie.

13:37. A2, jefe de Higiene y Seguridad, llega corriendo desde su oficina del complejo Alem, toma el handy H-01 del escritorio del sector y se comunica con Base Central.

> «A2: Operador, ¿tenés el detalle del SAT? ¿Cómo seguís el alerta sin internet?»
>
> «A3: Tengo lo último: rojo, ráfagas ciento diez, hasta las dieciocho. Después, no sé: web, app y correo, las tres caídas. Para mí el alerta terminó cuando terminó la señal.»

Es la primera manifestación del hallazgo NV-02: las tres fuentes de monitoreo del protocolo comparten un único modo de falla, y el Nodo Central acaba de quedar administrando un fenómeno que ya no puede ver.

13:40. Convocatoria del CDE. A2 lo intenta por todos los medios que quedan: línea fija conmutada (caída, es VoIP), celular (sin señal), handy (solo tienen cinco de los diez). El protocolo asigna radios a Higiene y Seguridad, Servicios Técnicos, Infraestructura, Telecomunicaciones, mayordomías, laboratorios, escuelas, medicina y cuadrilla; Rectorado, Vocería, Planificación, Académica y Sanidad quedan fuera de la única red viva. La activación de RACUNS como medio principal exige que el CDE declare el Estado de Comunicaciones Degradadas; el órgano que debe declararlo es, en gran parte, inalcanzable.

> «A2: Anotalo en el libro de guardia: Base Central y SHST declaramos el Estado de Comunicaciones Degradadas ad-referéndam del CDE. Hora trece cuarenta y cinco. RACUNS pasa a medio principal de coordinación. Que quede firmado por mí y por vos.»

13:50. A10, estudiante que se desplaza en silla de ruedas, quedó en el tercer piso de San Juan 670 cuando el protocolo desconectó los ascensores por nivel rojo. Llama por línea interna a la mayordomía. A6, el mayordomo del edificio, contesta entre dos novedades.

> «A6: Estimado, el protocolo desconecta los ascensores con rojo, y en este edificio no tenemos silla de evacuación. Quedate en el pasillo central, lejos de los ventanales, y en cuanto cedan las ráfagas te bajo entre cuatro personas.»
>
> «A10: ¿Y si hay que evacuar ahora?»
>
> «A6: Si hay que evacuar ahora, la calle es más peligrosa que el pasillo. Pero no te voy a mentir: para bajarte necesito cuatro hombres y diez minutos que hoy no tengo.»

La vulnerabilidad V-12 deja de ser una observación de papel: la evacuación asistida de un adulto en silla de ruedas desde un tercer piso, sin equipamiento, bajo ráfagas de 110 km/h, es materialmente imposible. El protocolo promete asistencia a personas con necesidades especiales y desconecta, en el mismo nivel de alerta, el único medio vertical del edificio.

14:00. A9, oficial de enlace de Defensa Civil, ingresa por CH4 desde el COE municipal.

> «A9: COE Bahía Blanca a Base UNS: tenemos catorce incidentes simultáneos en la ciudad. Necesito dos datos: ¿cuánta gente tienen adentro y están en condiciones de alojar? El intendente quiere el Alem como centro de acopio.»
>
> «A3: Le paso novedades por predio, pabellones confinados y subsuelo anegado. Un censo exacto no lo tengo: el registro de ocupación que existe es el de las escuelas, el Anexo F, y es de retiros.»
>
> «A9: Anotado: UNS, ocupación estimada, sin censo. Es lo mismo que me pasan todos. Segunda pregunta: ¿me garantizan el Alem con luz y sanitarios cuando lleguen los camiones?»

La primera pregunta del sistema externo es la rendición de cuentas que el protocolo no instrumenta (NV-07); la segunda es la promesa que la Sección 13 le hace al municipio sin procedimiento que la respalde.

14:10. A4, director de Telecomunicaciones, reporta por H-04 desde el Data Center.

> «A4: ATS funcionó, servidores arriba, el Data Center tiene su propio grupo de cien kVA. El problema es el Starlink: la camioneta y el kit están asignados por resolución del CDE, y no hay CDE reunido para resolver nada. Necesito esa designación ahora o la Capa cuatro no existe.»
>
> «A2: Designación verbal de emergencia: el móvil de cuadrilla H-11 queda afectado al kit Starlink, con su chofer a cargo. Se ratifica por acta en cuanto haya quórum. Y el apuntamiento lo hacen cuando pare el granizo: afuera caen piedras de golf.»

14:25. A7, decano del departamento con laboratorio crítico, irrumpe por CH2 con la voz cortada por la estática del equipo: pierde el nitrógeno líquido de los tanques de respaldo y catorce años de cultivos si no recupera energía en tres horas. A6 replica por CH1: San Juan necesita el acople del generador para la Base y los cargadores. A4 zanja el empate técnico: el generador móvil es único, el Data Center tiene el suyo. El protocolo no define matriz de prioridad de carga: la única unidad móvil de 100 kVA tiene tres demandantes simultáneos y ninguna regla de arbitraje.

> «A2: Prioridad uno, comunicaciones: la Base ya tiene UPS, se sostiene sola. Prioridad dos, el laboratorio del nitrógeno. El generador va al pabellón de A7 dos horas y después a San Juan. A7, pasame por escrito por CH2 lo que perdés si no llega, para el acta.»

14:40. A5, el Vocero, recién se entera. Sin handy, sin señal, en su casa del barrio, enciende la radio de la cocina y escucha la AM universitaria. Conduce hasta la emisora bajo granizo y encuentra al operador de turno en penumbra.

> «A5: ¿Tenemos grupo electrógeno propio acá?»
>
> «Locutor: Tenemos una UPS de veinte minutos. Si la red no vuelve, quedamos fuera del aire ya.»
>
> «A5: Pasá el comunicado M2 en loop mientras haya aire, anotá mi número como línea de guardia de prensa y si corta la UPS avisá por el handy del conductor, que es el único que tiene radio en el edificio.»

La Capa 5 de difusión masiva, la última del diseño, resulta ser una emisora sin respaldo energético normado: el protocolo prevé receptores a pilas para la comunidad, pero ningún generador para la propia radio. La voz oficial de la UNS queda colgada de una UPS de veinte minutos.

15:00. H-08, Escuelas Medias 11 de Abril, reporta por CH1.

> «H-08: Base, trescientos veinte chicos en el gimnasio, luz de emergencia activa. Los padres están empezando a llegar y necesito pauta: ¿entrego o retengo?»
>
> «A8: El protocolo permite el retiro con DNI, y con eso estoy cubierto. Pero mandar chicos a la calle con este granizo es una locura. Necesito autorización para demorar la entrega.»
>
> «A2: Ventana de retiro diferido: egresos de a dos, por el acceso cubierto, entre pulsos de ráfaga. Alguien tome nota de esto para la revisión del protocolo, porque lo estamos inventando ahora.»

15:30. A1, el Rector, entra empapado a la Sala de Crisis alternativa de San Juan 670. Se enteró por la radio AM de su auto cuarenta minutos atrás y no pudo avisar que venía: nadie tenía cómo ubicarlo y él no tenía con qué ubicar a nadie. Su primera intervención es un acta.

> «A1: Llegué tarde y lo asumo, y quiero que quede registrado para la revisión. Lo primero: ratifico por acta todo lo actuado ad-referéndam por Seguridad e Higiene y por la Base Central desde las trece cuarenta y cinco. Lo segundo: parte de víctimas por CH1 cada treinta minutos, al Vocero en la radio ya, y control de daños con Infraestructura apenas ceda el viento.»

15:45. El CDE de hecho queda constituido: Rector, SHST, Servicios Técnicos, Telecomunicaciones, Infraestructura y el operador de Base Central, con enlace permanente del COE por CH4. Quórum: seis de diez, más un externo. Con ese órgano se administrará el evento completo.

16:00. Vence el corte del turno noche. El CDE resuelve la suspensión con difusión limitada a los medios vivos: AM, megafonía de mayordomías y cadena de handies. Para los miles de estudiantes que no escuchan radio y ya estaban camino a la universidad, la suspensión no existe todavía: la encontrarán en la puerta. A5, al aire, lee el M2 adaptado cada media hora, mientras la UPS aguanta.

16:20. Pico del evento: ráfaga de 122 km/h. Un panel vidriado del pabellón 3 de Palihue estalla hacia adentro. El aula está vacía porque el confinamiento temprano la desalojó a las 13:45: la doctrina de resguardo del punto 7.8 acaba de evitar la primera víctima. H-07 reporta dos árboles caídos en sendas 1 y 4, sin personas afectadas.

17:40. El granizo cede. 18:05. A9 vuelve al CH4.

> «A9: COE a Base UNS: el SMN cesó el rojo, sigue amarillo hasta las veintiuna. Lo paso por acá porque ustedes no tienen internet, ¿no?»
>
> «A3: Correcto. Anotado: cese informado por Defensa Civil a las dieciocho cero cinco. Gracias, jefe.»

El cese del alerta le llegó al Nodo Central por el canal humanamente más simple del sistema: un oficial leyéndole el parte por radio. La detección del fin del evento que el protocolo administró durante cinco horas dependió de la cortesía del municipio.

18:20. Discusión de reanudación. A2 se planta.

> «A2: No reanudamos nada sin inspección: dos árboles caídos, vidrios en el pabellón tres y sesenta centímetros de agua en los subsuelos de Alem. Mañana a las seis, inspección con luz y checklist firmado por Infraestructura; recién después resolvemos el turno mañana.»
>
> «A1: El turno mañana ya está suspendido desde anoche por el naranja, así que no hay apuro. Lo confirmo por AM con el M5 modificado y quedamos con guardia de inspección a las seis. Quiero el informe de las setenta y dos horas con lo que faltó, no con lo que funcionó.»

19:30. H-10, Medicina del Trabajo, emite el parte final: tres atendidos, dos contusiones menores y un corte por vidrio atendido en el puesto. Sin víctimas de gravedad. El azar ayudó: el panel estallado cayó sobre un aula vaciada por una orden que no estaba en el procedimiento. 20:30. Acta de cierre. A2 cierra el libro de guardia de Base Central con una frase que este comité adopta como síntesis del dictamen.

> «A2: El protocolo aguantó porque hubo gente que improvisó bien. Lo que no puede ser es que la próxima vez dependamos de la misma suerte: radios para todo el CDE, una emisora con generador propio y una inspección obligatoria antes de reanudar. Escribilo en el informe de las setenta y dos horas, que para eso existe.»

Tres días después, el informe elevado por el SHST registra exactamente esas tres brechas. Este comité las reconoce como NV-01, NV-05 y NV-08, y agrega las que el propio informe no pudo ver: que el monitoreo cayó con la red (NV-02), que la voz oficial estuvo veinte minutos de colgar del aire (NV-03) y que durante 117 minutos la institución no tuvo autoridad formal en funciones (NV-01, V-01). El peor escenario no demostró que el protocolo sea malo: demostró que es bueno en la segunda hora y huérfano en la primera.

## SECCIÓN VII — RECOMENDACIONES PRIORITARIAS

Las diez acciones que siguen componen el Plan de Acción Correctiva (CAP) de esta auditoría. Fueron ordenadas por impacto sobre la primera hora de emergencia y factibilidad institucional, y cada una cierra al menos un hallazgo NV o una contradicción C identificada en la Sección III. El criterio de secuencia es deliberado: las cinco primeras son instrumentables por resolución interna sin presupuesto relevante y desbloquean la cadena de disparo completa del protocolo; las cinco restantes requieren compras, convenios o desarrollo organizacional de mediano plazo. El plazo inmediato significa antes de la próxima temporada severa de primavera-verano.

**Tabla 5 — Plan de Acción Correctiva priorizado**

| **N.º**  | **Acción concreta**                                                                                                                                                                                                                                                                                                              | **Cierra**           | **Impacto / factibilidad** | **Plazo**               | **Área responsable**                                 |
|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|----------------------------|-------------------------|------------------------------------------------------|
| **R-01** | Romper el bucle de activación: asignar cinco handies a los miembros del CDE sin radio (Rectorado, Vocería, Planificación, Académica, Sanidad) y establecer por resolución el quórum de tres (SHST + Base Central + cualquier miembro alcanzable) para declarar el Estado de Comunicaciones Degradadas, con ratificación por acta | NV-01, V-01, C-2     | Alto / Alta                | **Inmediato**           | Rectorado + Telecomunicaciones                       |
| **R-02** | Delegación de autoridad de mando inicial: resolución que habilite al SHST y a Base Central a ordenar de oficio el confinamiento preventivo ante naranja durante cursada y a adoptar la decisión abreviada nocturna para alertas emitidos cerca del corte, con ratificación posterior del CDE                                     | NV-04, NV-03         | Alto / Alta                | **Inmediato**           | Rectorado (resolución) + SHST                        |
| **R-03** | Verificación técnica obligatoria antes de la reanudación: checklist de inspección post-evento (arbolado, vidrios, cubiertas, subsuelos, ascensores, energías) firmado por SHST e Infraestructura como condición previa no dispensable del proceso P9                                                                             | NV-08                | Alto / Alta                | **Inmediato**           | SHST + Subsecretaría de Infraestructura              |
| **R-04** | Difusión desatendida pre-aprobada: plantillas M1 a M5 firmadas en blanco por Vocería y Rectorado, con publicación automática por el Nodo Central (web, SMS y redes) al momento de la resolución, más guardia rotativa de vocería con suplencia designada                                                                         | NV-03, NV-05 parcial | Alto / Alta                | **Inmediato a 90 días** | Comunicación Institucional + SHST                    |
| **R-05** | Fuente de monitoreo autónoma: enlace satelital bidireccional en Base Central, convenio simple con Defensa Civil para lectura del SAT por CH4 y receptor de radiodifusión de monitoreo en el libro de guardia                                                                                                                     | NV-02, C-5           | Alto / Media               | 90 días                 | Telecomunicaciones                                   |
| **R-06** | Censo de ocupación y rendición de cuentas ICS: censo digital por aula y pabellón con reporte agregado por CH1 cada treinta minutos durante confinamiento, extendiendo la rutina de novedades existente; cartilla de zonas seguras por edificio con censo en papel de respaldo                                                    | NV-07                | Medio-alto / Alta          | 90 días                 | Decanatos y Direcciones + SHST                       |
| **R-07** | Ventana de retiro diferido y listados vivos: cláusula en la Sección 8 y en el Anexo F que condicione el egreso escolar a la fase del evento (retiro solo entre pulsos, por acceso cubierto y de forma escalonada) y proceso semestral de actualización de los listados de adultos autorizados                                    | NV-10                | Medio-alto / Alta          | 90 días                 | Secretaría General Académica + Direcciones escolares |
| **R-08** | Resiliencia de la Capa 5: grupo electrógeno propio para Radio AM UNS con autonomía mínima de 12 horas, convenio de dúplex firmado con UTN-FRBB y convenio de respaldo con una FM comercial o comunitaria local                                                                                                                   | NV-05, C-1, V-02     | Alto / Media               | 90 días                 | Comunicación Institucional + Telecom. + Rectorado    |
| **R-09** | Kit de accesibilidad de evacuación: sillas de evacuación en edificios de altura (prioridad San Juan 670), escort capacitado por edificio para el registro de movilidad reducida, simulacros específicos y cláusula que reconcilie 7.4.C con 6.2                                                                                  | V-12, C-4            | Alto / Media               | 90 días a 12 meses      | Bienestar Universitario + Infraestructura            |
| **R-10** | Anexo de eventos masivos con mando unificado: procedimiento para eventos de más de 200 personas con integración ICS del organizador (productor, seguridad privada, catering), megafonía protocolar, censo de asistencia por sector y canal radial de consultas para familias externas                                            | NV-07, V-06          | Alto / Media               | 12 meses                | Secretaría de Extensión + SHST + Comunicación        |

Complementariamente a las diez acciones del CAP, se recomienda incorporar al tablero de indicadores de la Sección 15 tres mediciones que esta auditoría necesitó y no existían: tiempo de convocatoria del CDE desde la notificación (objetivo: quórum en 15 minutos), latencia decisión-difusión por canal (objetivo: igual o menor a 5 minutos para digital automático) y censo de cobertura radial efectiva (porcentaje de predios con recepción verificada en la prueba trimestral de difusión). Sin esas tres métricas, la próxima revisión anual no podrá distinguir si las correcciones aplicaron o solo se documentaron.

La secuencia completa del CAP es ejecutable en un ciclo presupuestario con recursos menores: las acciones inmediatas son resoluciones y procedimientos, las de 90 días son compras de equipamiento menor y convenios simples, y solo R-10 exige desarrollo organizacional de un año. Si la UNS ejecuta R-01 a R-04 antes de la próxima temporada severa, la calificación de este comité pasaría de 6,3 a un rango de 7,8 a 8,1 sin tocar una sola línea del resto del protocolo: el cuello de botella del sistema no está en su doctrina, está en su interruptor.

## ANEXO A — REGISTROS DE SIMULACIÓN (E1 a E7)

Los registros que siguen documentan la ejecución cronológica de los siete escenarios, con su tabla de fricciones entre agentes, la verificación de redundancias de comunicación y la validación de plazos. La reconstrucción extendida y con diálogos literales del escenario E4 obra en la Sección VI; aquí se consigna su ficha de resultados. Las horas son locales de Bahía Blanca.

### E1. Escenario Amarillo Preventivo: vientos de 60 km/h, alerta emitida a las 05:30

Escenario de línea de base: el SMN emite alerta amarillo por vientos (ráfagas previstas de 60 km/h, umbral regional amarillo de 65) en actualización extraordinaria previa al turno mañana. No hay decisión de suspensión exigible; el ciclo completo de detección, validación y difusión preventiva debe cerrar antes de la apertura del turno.

**Tabla A.1 — Línea de tiempo E1**

| **Hora** | **Suceso y decisiones**                                                                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 05:30    | El SMN emite el alerta amarillo por vientos. El turno mañana aún no inicia y el operador de guardia de la transición (9.4) recibe la notificación automática de la app en el celular designado.      |
| 05:32    | El operador lee el detalle de la zona y completa la Ficha del Alerta F-089. Duda de clasificación: consulta si ráfagas de 60 km/h exceden el umbral; el operador no tiene formación técnica (V-03).  |
| 06:00    | Lectura rutinaria del SAT (7.2). Llamada a la guardia del SHST (operador B): se confirma nivel amarillo sin intersección de corte; actividades en aulas normales y suspensión de exteriores (7.4.A). |
| 06:10    | Notificación al CDE por WhatsApp institucional. Por nivel amarillo no se exige respuesta de sus integrantes.                                                                                         |
| 06:40    | El Vocero responde al mensaje y comunica que llega a la oficina a las 08:00. No existe guardia de vocería ni plantilla de publicación automática nocturna (NV-03).                                   |
| 07:15    | Mayordomía de Palihue ejecuta la prealerta (7.4.A): clausura de sendas arboladas con cinta, verificación de baterías VHF y despeje preventivo de sumideros.                                          |
| 07:30    | Docentes de educación física inician práctica al aire libre en Palihue: ninguna comunicación llegó al sector (el M1 sigue sin publicarse).                                                           |
| 08:10    | Se publica el M1 por web, Moodle, correo y redes (matriz 11.6: una emisión más recordatorio en cada corte). Retardo total: 2 horas 40 minutos desde la detección.                                    |
| 08:25    | Un preceptor alerta al docente de educación física por WhatsApp y suspende la práctica. Ráfagas máximas registradas: 62 km/h a las 09:40, sin incidentes.                                            |
| 10:00    | Corte del turno tarde sin productos que intersecten: normalidad. Cierre del registro en el libro de guardia con la trazabilidad completa de la ficha.                                                |

**Tabla A.2 — Fricciones detectadas en E1**

| **Agentes en tensión** | **Fricción**                                                                                               | **Resolución improvisada**                                            | **Ref.**       |
|------------------------|------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|----------------|
| A3 - A2                | Interpretación del umbral (60 km/h de ráfagas) por personal de guardia sin capacitación en lectura del SAT | Validación telefónica con la guardia del SHST, 28 minutos de consulta | V-03           |
| A3 - A5                | Difusión preventiva nocturna sin vocería de guardia: el mensaje M1 quedó 2 horas 40 minutos en espera      | Publicación al inicio del horario administrativo                      | NV-03          |
| A6 - docentes          | Clausura física de sendas sin comunicación directa a los responsables de actividades al aire libre         | Alerta informal de un preceptor por WhatsApp                          | NV-07 (conexo) |

**Tabla A.3 — Verificación de redundancias en E1**

| **Capa / componente**                  | **Comportamiento**                         | **Reemplazo / efecto**                                          |
|----------------------------------------|--------------------------------------------|-----------------------------------------------------------------|
| Capas 1 y 4 (digital, telefonía)       | Operativas sin falla                       | No se requirió reemplazo                                        |
| Proceso P2 a P6 (cadena humana)        | Falla de latencia en el mensaje preventivo | Sin reemplazo: el vacío quedó expuesto durante el turno         |
| Canal directo a actividades exteriores | Inexistente                                | Alerta informal de un preceptor: dependencia de la buena suerte |

Validación de plazos: el nivel amarillo no exige decisión por ventana de corte, por lo que el cumplimiento formal es no aplicable. La difusión preventiva, sin embargo, excedió todo plazo razonable y reveló que el indicador de tiempo decisión-difusión (15.3) solo se mide para suspensiones: los mensajes preventivos no tienen objetivo temporal alguno, hueco de tablero que se corrige en la Sección VII.

### E2. Escenario Naranja con decisión anticipada: alerta emitida a las 21:30

El SMN emite a las 21:30 una actualización extraordinaria con alerta naranja por vientos del sudoeste de 75 a 90 km/h, para el rango de la mañana siguiente (06:00 a 12:00). El corte de decisión del turno mañana es a las 22:00: el sistema dispone de 30 minutos para ejecutar la cadena completa P2 a P6, y el turno noche está todavía en desarrollo hasta las 22:00.

**Tabla A.4 — Línea de tiempo E2**

| **Hora** | **Suceso y decisiones**                                                                                                                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 21:30    | Emisión del alerta naranja (vientos SO 75-90 km/h, rango mañana de 06:00 a 12:00 del día siguiente, vigencia 24 horas).                                                                                                                              |
| 21:33    | Ficha F-090 completada; notificación al CDE por WhatsApp institucional y llamado directo a la guardia del SHST (9.2.4).                                                                                                                              |
| 21:37    | Relevo de respuestas: contestan seis de diez miembros del CDE. El Rector responde por teléfono a las 21:41; los cuatro restantes no responden antes del cierre del ciclo.                                                                            |
| 21:45    | El SHST solicita la apertura del detalle: la línea de tiempo confirma intersección plena con el turno mañana. Dictamen técnico en audio de dos minutos por el grupo: suspender (P4).                                                                 |
| 21:52    | Fricción de decisión: el Rector plantea esperar a las 06:00 y reevaluar para evitar suspensión por dudas; el SHST sostiene la regla de oro de 7.1: decidir antes del corte o perder el margen de protección de la comunidad en tránsito.             |
| 21:58    | Decisión del Rector: suspensión del turno mañana (P5). Faltan dos minutos para el corte de las 22:00.                                                                                                                                                |
| 22:00    | Vence el corte con la resolución adoptada y sin comunicado público: la difusión apenas comienza (P6).                                                                                                                                                |
| 22:04    | El Vocero, despertado por el llamado, redacta desde la plantilla M2 y publica web, redes y correo. El SMS masivo sale a las 22:11.                                                                                                                   |
| 22:20    | Canal FM UTN-FRBB de la matriz 11.6: omitido; el convenio sigue en curso de establecimiento (11.3, NV-05).                                                                                                                                           |
| 22:45    | Confirmación de recepción de escuelas: el director de 11 de Abril responde desde su celular personal 25 minutos después del llamado; la Escuela Agraria recién a las 23:05, con la directiva en su domicilio y el handy H-09 en poder del mayordomo. |
| 23:10    | La AM universitaria difunde el comunicado en su boletín nocturno. El turno noche finalizó a las 22:00 sin novedades.                                                                                                                                 |
| 07:30    | Impacto real: ráfagas de 82 km/h entre las 07:30 y las 09:00, dentro de lo previsto, sobre predios sin estudiantes. Resultado de la decisión: correcto.                                                                                              |

**Tabla A.5 — Fricciones detectadas en E2**

| **Agentes en tensión** | **Fricción**                                                                                                                                  | **Resolución improvisada**                                                       | **Ref.**       |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|----------------|
| A1 - A2                | Suspensión anticipada contra espera de confirmación: criterio de imagen y presión de familias frente al criterio normativo de la regla de oro | Decisión a las 21:58, dos minutos antes del corte                                | NV-04          |
| A3 - CDE               | Quórum parcial (6/10) en la ventana de 30 minutos; sin regla de quórum válido para decidir                                                    | Dictamen del SHST y decisión del Rector con los alcanzables                      | NV-01, V-01    |
| A5 - A3                | Latencia de redacción y publicación nocturna sin guardia de vocería                                                                           | M2 a los 4 minutos de redacción, publicación completa a los 13 minutos del corte | NV-03          |
| A8 - A1                | Directivos escolares reclamando difusión temprana a familias y confirmación de recepción formal                                               | Confirmación telefónica individual, con demoras de hasta 40 minutos              | NV-07 (conexo) |

**Tabla A.6 — Verificación de redundancias en E2**

| **Capa / componente**           | **Comportamiento**                                              | **Reemplazo / efecto**                                                                |
|---------------------------------|-----------------------------------------------------------------|---------------------------------------------------------------------------------------|
| Capa 1 (digital institucional)  | Operativa                                                       | Web, redes y correo difundieron en minutos; el SMS llegó 19 minutos después del corte |
| Capa 2 (radial FM del convenio) | Ausente por convenio no firmado                                 | Capa 2 reducida a la AM universitaria (NV-05)                                         |
| Capa 5 (RACUNS)                 | Sin activación (redes comerciales operativas)                   | Escucha permanente de CH1 activada por 7.4.B                                          |
| Confirmación de recepción       | Parcial: solo escuelas, con dependencia de celulares personales | Sin reemplazo protocolar: hueco de verificación (11.7)                                |

Validación de plazos: decisión adoptada a las 21:58, dentro del corte de las 22:00; difusión iniciada a las 22:04 y completa a las 22:11, once minutos fuera de término. El incumplimiento es marginal pero sistemático (se repite en E3 y E6): la cadena humana P5 a P6 consume entre 13 y 35 minutos, por lo que todo alerta emitido con menos de una hora de antelación al corte compromete la vigencia de la regla de oro. Este patrón fundamenta la acción R-02 y R-04 del plan correctivo.

### E3. Escenario Naranja durante cursada: alerta a las 14:15, impacto a las 15:00

El SMN emite a las 14:15 una actualización extraordinaria con alerta naranja por tormentas severas (ráfagas de 90 km/h y granizo) desde las 15:00, en pleno desarrollo del turno tarde. El corte de las 10:00 ya venció: el protocolo entra en el régimen de fenómeno durante actividades, donde la prioridad cambia de suspensión a resguardo en sede (7.1, regla de oro). La ventana útil entre detección e impacto es de 45 minutos.

**Tabla A.7 — Línea de tiempo E3**

| **Hora** | **Suceso y decisiones**                                                                                                                                                                                                                          |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 14:15    | Emisión del alerta naranja por tormentas con ráfagas de 90 km/h y granizo desde las 15:00, rango tarde.                                                                                                                                          |
| 14:18    | Ficha F-091; notificación al CDE y a la guardia del SHST (9.2.4).                                                                                                                                                                                |
| 14:20    | Consulta del operador: define si corresponde suspender o confinar con el turno en desarrollo y el corte ya vencido. 7.4.B prescribe el confinamiento prioritario, sin ordenante explícito (C-3).                                                 |
| 14:22    | El SHST asume la orden por WhatsApp institucional y por CH1: confinamiento preventivo inmediato en todos los predios, alejado de ventanales. La orden se ejecuta sin resolución del Rector ni CDE reunido: 7 minutos desde la detección (NV-04). |
| 14:25    | Escuelas: H-08 confirma custodia; 320 alumnos de 11 de Abril confinados en el gimnasio con luz natural y agua.                                                                                                                                   |
| 14:30    | Estudiante con movilidad reducida en aula de planta alta de Palihue: no hay personal asignado para el desplazamiento al sector interno (V-12); dos compañeros lo asisten por iniciativa del docente.                                             |
| 14:45    | Llegada de padres a las escuelas en aumento. Una madre exige retirar a su hija; la directora deniega el egreso mientras duren las ráfagas: la cláusula no existe en 8.3 y la directiva queda jurídicamente expuesta (NV-10).                     |
| 15:00    | Impacto: ráfagas de 95 km/h y granizo de 2 cm durante 35 minutos.                                                                                                                                                                                |
| 15:05    | H-07 reporta por CH1 árbol caído sobre la senda 2 de Palihue sin víctimas; se cordona el sector con vallas.                                                                                                                                      |
| 15:40    | CDE virtual reunido con quórum de cinco miembros más el SHST; se evalúa el turno noche (ventana de corte 16:00).                                                                                                                                 |
| 15:52    | Decisión: suspensión del turno noche; difusión M2 a las 16:08 por canales digitales y AM.                                                                                                                                                        |
| 17:30    | El SMN desescala a amarillo. 17:50: el CDE descarta reanudación (turno noche ya suspendido) y programa el M5 para el turno mañana siguiente.                                                                                                     |
| 18:20    | Retiro escalonado en escuelas: 47 alumnos quedan en custodia extendida por corte de transporte urbano (8.4), con registro del Anexo F completo y reporte final de nómina a Base Central.                                                         |

**Tabla A.8 — Fricciones detectadas en E3**

| **Agentes en tensión** | **Fricción**                                                                                                   | **Resolución improvisada**                                                     | **Ref.**       |
|------------------------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|----------------|
| A3 - A2                | Autoridad para ordenar el confinamiento sin CDE reunido en ventana de 45 minutos                               | Orden directa del SHST por WhatsApp y CH1, ratificada verbalmente después      | NV-04, C-3     |
| A8 - familias          | Derecho de retiro contra doctrina de confinamiento durante el pico del evento                                  | Denegación y egresos diferidos de a dos por la directora, sin respaldo escrito | NV-10          |
| A2 - A5                | Ausencia de plantilla para naranja durante cursada (M3 es específico de ACP): el mensaje se adaptó manualmente | Adaptación del M3 con cambio de fuente del aviso                               | NV-03 (conexo) |
| A10 - docentes         | Asistencia a estudiante con movilidad reducida en evacuación de sector sin personal designado                  | Acompañamiento por dos compañeros de curso                                     | V-12, C-4      |

**Tabla A.9 — Verificación de redundancias en E3**

| **Capa / componente**         | **Comportamiento**                                | **Reemplazo / efecto**                                               |
|-------------------------------|---------------------------------------------------|----------------------------------------------------------------------|
| Capa 3 (megafonía de predios) | Operativa y primera en llegar al público interno  | Primó sobre WhatsApp institucional, que registró demoras sectoriales |
| Capa 1 (digital)              | Operativa                                         | Difusión de suspensión del turno noche a los 8 minutos del corte     |
| Capa 5 (RACUNS)               | CH1 en escucha permanente desde las 14:22 (7.4.B) | Sin falla; reportes de novedades cada 30 minutos cumplidos           |
| Telefonía celular             | Operativa                                         | Coexistió con VHF sin conflicto de canal                             |

Validación de plazos: la orden de confinamiento fue efectiva 7 minutos después de la detección (excelente en resultado, irregular en autoridad). Para el corte de las 16:00 del turno noche: decisión a las 15:52 (en término) y difusión a las 16:08 (8 minutos fuera). El escenario demuestra que el régimen durante cursada funciona solo si alguien decide asumir la orden: el protocolo prescribe la acción sin asignar el disparador.

### E4. Escenario Rojo extremo con colapso de redes: tormenta a las 13:30

Ficha de resultados del escenario cuya reconstrucción completa, con diálogos literales, obra en la Sección VI. Tormenta roja con ráfagas de hasta 122 km/h y granizo, caída simultánea de energía, telefonía celular e internet a las 13:31, con turno tarde en plena cursada. El protocolo debía sostener la coordinación completa por RACUNS y declarar el Estado de Comunicaciones Degradadas (12.3).

**Tabla A.10 — Hitos principales de E4**

| **Hora** | **Hito**                                                                                                                           |
|----------|------------------------------------------------------------------------------------------------------------------------------------|
| 13:28    | Escalada a rojo; ficha F-143 y notificación al CDE con datos aún vivos.                                                            |
| 13:31    | Caída simultánea de energía, celular e internet. UPS de mayordomía sostiene la Base VHF.                                           |
| 13:45    | Estado de Comunicaciones Degradadas declarado ad-referéndam por SHST y Base Central: el CDE no puede reunirse (5 de 10 sin handy). |
| 14:10    | Capa 4 (Starlink) sin designación de vehículo y dotación (12.4): no llegará a activarse en todo el evento.                         |
| 15:30    | El Rector arriba a la Sala de Crisis alternativa informado por la radio AM de su automóvil; ratifica por acta lo actuado.          |
| 16:00    | Corte del turno noche: suspensión resuelta por CDE de hecho (6/10) y difundida solo por AM, megafonía y cadena de handies.         |
| 16:20    | Ráfaga de 122 km/h: estallido de panel vidriado en aula desalojada por confinamiento temprano; sin heridos.                        |
| 18:05    | Cese del rojo informado por Defensa Civil por CH4: el Nodo carece de fuente propia de monitoreo.                                   |
| 20:30    | Acta de cierre; informe de 72 horas encargado con las brechas principales identificadas por los propios agentes.                   |

**Tabla A.11 — Fricciones detectadas en E4**

| **Agentes en tensión** | **Fricción**                                                                                                     | **Resolución improvisada**                                                         | **Ref.**            |
|------------------------|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|---------------------|
| A3 - CDE               | Convocatoria imposible del órgano de declaración del Estado de Comunicaciones Degradadas                         | Declaración ad-referéndam de SHST y Base Central, ratificada 117 minutos después   | NV-01, V-01, C-2    |
| A4 - A7 - A6           | Generador móvil único con tres demandantes (laboratorio crítico, Base VHF, mayordomía) y sin matriz de prioridad | Arbitraje verbal del SHST con prioridad comunicaciones - laboratorio - edilicio    | NV-06, Sección IV.8 |
| A8 - familias          | Entrega de menores bajo granizo: el retiro autorizado no prevé fase de evento                                    | Ventana de retiro diferido: egresos de a dos por acceso cubierto entre pulsos      | NV-10               |
| A10 - protocolo        | Ascensores desconectados por nivel rojo sin medio de evacuación asistida del registro de movilidad reducida      | Retención en pasillo central del tercer piso con promesa de bajada manual al ceder | V-12, C-4           |
| A5 - Capa 5            | La emisora AM no tiene grupo electrógeno normado: la voz oficial a 20 minutos de quedar fuera del aire           | Comunicado M2 en loop y línea de guardia de prensa con el número del conductor     | NV-05               |
| A9 - A3                | El COE exige censo de ocupación para dimensionar la ayuda y la logística del centro de acopio                    | Reporte por predios con ocupación estimada, sin censo                              | NV-07               |

**Tabla A.12 — Verificación de redundancias en E4**

| **Capa / componente**                | **Comportamiento**                                                   | **Reemplazo / efecto**                                                                  |
|--------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| Capa 1 (VHF troncal, repetidor Alem) | Operativa durante 6 horas sobre banco de baterías                    | Sostuvo la totalidad del mando, los reportes y el enlace CH4                            |
| Capa 2 (UHF de proximidad)           | Operativa con restricciones de alcance                               | Cobertura interior de edificios sin interferir CH1                                      |
| Capa 3 (LoRa / Meshtastic)           | No incorporada todavía (12.8)                                        | Sin efecto: dependencia total de voz                                                    |
| Capa 4 (Starlink móvil)              | No activada: designación pendiente de resolución del CDE (12.4)      | Sin reemplazo: sin emisión web ni lectura del SAT durante todo el evento (NV-02, NV-06) |
| Capa 5 (AM UNS / FM convenio)        | AM al aire con UPS de 20 minutos; FM ausente por convenio no firmado | Voz oficial sosténida en condición precaria; sin canal de entrada para familias (NV-05) |
| Fuentes del SAT (web, app, correo)   | Caídas a las 13:31                                                   | Cese del alerta recibido por CH4 de Defensa Civil a las 18:05                           |

Validación de plazos: corte de las 16:00 del turno noche resuelto por el CDE de hecho en torno a esa hora y difundido a las 16:15 solo por los canales vivos. El incumplimiento formal de difusión es aquí estructural y no marginal: sin canal digital ni SMS (colapsados) y sin FM del convenio (inexistente), la mitad de la comunidad objetivo no tuvo forma protocolar de enterarse antes de trasladarse. La validación de la vigencia del ACP y del cese del alerta, por su parte, dependió íntegramente del enlace externo CH4.

### E5. Escenario ACP durante evento masivo: Feria Gastronómica en Palihue

El SMN emite a las 15:40 un Aviso a Muy Corto Plazo (ACP) por tormenta severa con ráfagas destructivas y granizo, vigencia de 2 horas (hasta 17:40), con el polígono cubriendo el Campus Palihue, donde la Feria Gastronómica del Sudoeste Bonaerense reúne veinte mil asistentes y más de ciento veinte stands operados en gran parte por personal externo a la UNS. El protocolo aplicable es el punto 7.5: cese inmediato y confinamiento seguro interno, sin evacuación externa mientras el ACP permanezca activo.

**Tabla A.13 — Línea de tiempo E5**

| **Hora** | **Suceso y decisiones**                                                                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 15:40    | Emisión del ACP por tormenta severa, vigencia 2 horas, polígono con Palihue. La app del SMN notifica al Nodo Central.                                                                                |
| 15:43    | Ficha F-092; notificación al CDE y al SHST. El punto 7.5 ordena cese inmediato de actividades y confinamiento en todos los predios.                                                                  |
| 15:46    | Base Palihue y H-07 coordinan con el productor del evento: fricción de mando sobre la megafonía y el personal de seguridad privada, que responden a un empleador externo (V-06, NV-07).              |
| 15:50    | Inicio de lluvia intensa. Migración masiva hacia los pabellones centrales de hormigón según la directiva de 6.2 para Palihue. Tres carpas gastronómicas pierden cobertura por anclaje insuficiente.  |
| 16:05    | Colapso de la telefonía celular por congestión masiva (antecedente idéntico del piloto 2025, 12.2). Miles de asistentes intentan comunicarse; las familias externas quedan sin canal de entrada.     |
| 16:10    | CH1 congestionado con tráfico logístico del evento; Telecomunicaciones impone la disciplina de 12.9.2: todo tráfico de proveedores a CH2, CH1 exclusivo de mando. Restitución en menos de un minuto. |
| 16:20    | H-10 atiende dos contusiones leves durante la migración. Defensa Civil solicita por CH4 censo de asistentes por sector: no existe (NV-07).                                                           |
| 17:40    | Vence la vigencia del ACP sin nuevos pulsos de radar; llovizna residual.                                                                                                                             |
| 17:50    | El CDE evalúa la reanudación (7.5.3): se suspende el resto de la jornada de la feria; salida escalonada por sectores con megafonía y cadena de handies.                                              |
| 18:20    | Desalojo completo del predio. Cierre: dos asistencias médicas menores, tres carpas destruidas, un vehículo dañado por rama.                                                                          |

**Tabla A.14 — Fricciones detectadas en E5**

| **Agentes en tensión**              | **Fricción**                                                                                                       | **Resolución improvisada**                                    | **Ref.**         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|------------------|
| Productor del evento - Base Palihue | Mando unificado ausente: megafonía y seguridad privada operan bajo contrato externo sin integración ICS con la UNS | Coordinación ad hoc por H-07 y el delegado del productor      | V-06, NV-07      |
| A9 - A6                             | El COE exige censo de asistentes por sector para dimensionar recursos; nadie lo tiene                              | Estimación visual por sectores y reporte a las 16:25          | NV-07            |
| A4 - CH1                            | Congestión de la troncal con tráfico de proveedores del evento                                                     | Imposición de disciplina de canales: degradación a CH2        | F-4 (validación) |
| A5 - familias externas              | Veinte mil asistentes sin teléfono y sus familias sin canal de información entrante                                | Sin resolución: la arquitectura de difusión es unidireccional | Sección IV.4     |

**Tabla A.15 — Verificación de redundancias en E5**

| **Capa / componente**          | **Comportamiento**                                             | **Reemplazo / efecto**                                                                |
|--------------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------|
| Telefonía celular (Capa 4 y 1) | Colapsada por congestión masiva a las 16:05                    | VHF y megafonía del evento asumieron la coordinación completa, como en el piloto 2025 |
| Capa 1 (VHF troncal)           | Operativa con congestión inicial                               | Disciplina de canales de 12.9.2 la restituyó en menos de un minuto                    |
| Capa 2 (radial masiva)         | Sin convocatoria (SMS parcialmente operativo)                  | AM sin uso en el evento; difusión interna suficiente por megafonía                    |
| Megafonía del evento           | Operativa, pero operada por personal externo sin protocolo UNS | Guion improvisado desde Base Palihue; sin registro de alcance efectivo                |

Validación de plazos: el régimen ACP no está sujeto a las ventanas 22/10/16; la obligación temporal es la inmediatez del cese y del confinamiento (7.5.1), cumplida en 6 minutos, y la evaluación de reanudación al vencer la vigencia (7.5.3), cumplida 10 minutos después del vencimiento. El escenario valida la doctrina ACP del protocolo y, al mismo tiempo, expone que el mando sobre veinte mil personas se ejerció sin censo, sin integración del personal externo y sin canal para las familias: exactamente el perfil del evento en que la UNS ya tuvo experiencia real.

### E6. Escenario Advertencia violeta y Temperaturas Extremas simultáneas: lunes 06:00

Domingo 18:10: el SMN emite advertencia violeta por niebla densa para la madrugada y mañana del lunes. Domingo 19:05: el SAT de Temperaturas Extremas emite nivel rojo por calor extremo para el lunes (máximas previstas de 38 a 40 grados). El lunes es día de clases de los tres turnos. Las directivas de ambos productos se aplican sobre el mismo turno mañana con recomendaciones que tensionan entre sí: la niebla demora traslados (7.6) y el calor rojo orienta a la suspensión presencial con virtualidad asincrónica (7.7).

**Tabla A.16 — Línea de tiempo E6**

| **Hora**   | **Suceso y decisiones**                                                                                                                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dom. 18:10 | Advertencia violeta por niebla densa para lunes de madrugada y mañana (ciclo de actualización de advertencias: 06:00 y 18:00).                                                                                                                 |
| Dom. 19:05 | SAT de Temperaturas Extremas: nivel rojo por calor extremo para el lunes (ciclo propio de actualización: 19:00).                                                                                                                               |
| Dom. 22:00 | Corte de decisión del turno mañana. El CDE evalúa con información parcial: la niebla del lunes no estaba confirmada a las 22:00 del domingo porque el próximo ciclo de la advertencia es a las 06:00 (desincronización de ciclos, NV-09).      |
| Dom. 22:05 | Dictamen del SHST: por calor rojo, suspensión presencial con adaptación a virtualidad asincrónica (7.7); la niebla no es causal autónoma de suspensión (7.6: solo demora traslados y suspende salidas de campo).                               |
| Dom. 22:30 | Difusión del M2 (30 minutos después del corte: patrón de latencia NV-03). Fricción de interpretación en escuelas: 7.7 habla de actividades sin distinguir nivel preuniversitario; las direcciones extienden la suspensión por criterio propio. |
| Lun. 05:50 | Niebla efectiva con visibilidad inferior a 50 metros en los accesos; transporte urbano con demoras de 20 a 40 minutos. Sin actividad presencial que proteger, el efecto se concentra en el personal esencial y las residencias.                |
| Lun. 06:00 | Residentes de las residencias universitarias caminan al comedor sin protocolo de traslado interno (V-07).                                                                                                                                      |
| Lun. 09:30 | Temperatura de 36 grados; cuatro pabellones de Palihue sin climatización (vulnerabilidad 6.1). Sin exposición de personas por la suspensión.                                                                                                   |
| Lun. 10:00 | Corte del turno tarde: el CDE mantiene la suspensión presencial por calor y habilita virtualidad asincrónica.                                                                                                                                  |
| Lun. 12:00 | Pico de tráfico en Moodle; los servidores del Data Center resisten sobre ATS y generador propio (6.3). La continuidad digital opera, aunque sin RTO ni RPO normados que permitan declarar cumplimiento objetivo.                               |
| Lun. 16:00 | Corte del turno noche: suspensión presencial mantenida; actividades virtuales sincrónicas autorizadas desde las 19:00 con fricción de pautas docentes (V-15: sin plan de virtualidad).                                                         |
| Lun. 18:40 | Cese de la advertencia; M5 difundido para el martes con recomendaciones por calor residual.                                                                                                                                                    |

**Tabla A.17 — Fricciones detectadas en E6**

| **Agentes en tensión** | **Fricción**                                                                                                                                                 | **Resolución improvisada**                                                          | **Ref.**      |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|---------------|
| A3 - ciclos del SMN    | El corte 22:00 exige decidir con información de niebla aún no actualizada (próximo ciclo 06:00): decisión con datos parciales                                | Dictamen fundado solo en el calor y monitoreo extraordinario a las 06:00            | NV-09         |
| A1 - A8                | Suspensión por calor en escuelas preuniversitarias: 7.7 no distingue nivel ni edad; los directores extienden la medida por criterio propio frente a familias | Extensión discrecional uniforme de la suspensión                                    | NV-09         |
| A1 - A7                | Prioridad de climatización de laboratorios con cultivos sensibles por encima de 30 grados frente al cierre general del predio                                | Excepción autorizada para el pabellón del laboratorio con registro de acceso mínimo | V-08 (conexo) |
| A1 - docentes          | Virtualidad sincrónica autorizada sin pauta de plataforma, horarios ni evaluación                                                                            | Cada cátedra resolvió por su cuenta la modalidad del turno noche                    | V-15          |

**Tabla A.18 — Verificación de redundancias en E6**

| **Capa / componente**                    | **Comportamiento**                              | **Reemplazo / efecto**                                                       |
|------------------------------------------|-------------------------------------------------|------------------------------------------------------------------------------|
| Capas 1 a 4 (todas)                      | Operativas sin falla                            | El riesgo del escenario fue de decisión, no de canal                         |
| Monitoreo (ciclos 18:00 / 19:00 / 06:00) | Fuente viva pero desincronizada del corte 22:00 | Lectura extraordinaria a las 06:00 como paliativo, sin corrección del diseño |
| Data Center sobre ATS                    | Operativo bajo pico de tráfico                  | Continuidad digital real, aunque sin RTO/RPO que la declare auditable        |

Validación de plazos: corte de las 22:00 del domingo con decisión a las 22:05 (en término) y difusión a las 22:30 (30 minutos fuera, patrón NV-03). Los cortes de las 10:00 y 16:00 del lunes se cumplieron en decisión y difusión. El escenario valida la regla de lectura del detalle para productos simultáneos (4.6 y 7.3) y expone la ausencia de regla de combinación de fenómenos con directivas contradictorias, que en un caso menos benigno podría forzar la exposición de personas al traslado en niebla para cumplir una presencialidad que el calor prohíbe.

### E7. Escenario crítico con víctima: árbol sobre estudiante en Palihue

Alerta naranja activo por tormentas (ráfagas de 95 km/h, granizo intermitente) con confinamiento vigente en todos los predios. A las 15:12, una ráfaga derriba un fresno de gran porte sobre un estudiante que cruzaba la senda peatonal 2 del Campus Palihue, clausurada de forma parcial con cinta desde las 14:40. El estudiante queda consciente, con lesión visible en una pierna. Redes de comunicación operativas (el escenario no incluye colapso).

**Tabla A.19 — Línea de tiempo E7**

| **Hora** | **Suceso y decisiones**                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 15:12    | La ráfaga derriba el fresno sobre el estudiante en la senda 2. Testigos llaman al 107 y reportan por H-07 a Base Central: árbol caído sobre alumno, consciente, lesión visible, se solicita asistencia médica urgente.                            |
| 15:14    | Notificación a Medicina del Trabajo (H-10) y al SHST (H-01). Base Central asienta novedad crítica y abre el registro de incidente.                                                                                                                |
| 15:17    | El SAME municipal informa saturación por el evento climático (12 incidentes simultáneos en la ciudad): ambulancia con demora estimada de 40 minutos. No existe criterio protocolar de traslado institucional (NV-12).                             |
| 15:20    | SHST y enfermero de Medicina del Trabajo acceden caminando desde el pabellón 1. Control primario: fractura expuesta. Se decide mover al estudiante al interior del pabellón por refugio ante granizo (doctrina 7.8), con inmovilización precaria. |
| 15:25    | Rumores virales: fotografías del árbol caído con leyenda de gravedad extrema circulan en redes sin control institucional. El Vocero recién difunde una nota a las 15:40; sin protocolo de monitoreo de crisis (V-16).                             |
| 15:30    | Contacto con la familia a cargo de Bienestar Universitario sin guion ni protocolo (S-04, A-01). El Rector instruye contención, datos verificados y cero especulación.                                                                             |
| 15:35    | Preservación de escena: el mayordomo cordona el sector con vallas; el resto del fuso permanece inclinado con riesgo de segunda caída sobre la senda. No existe evaluación arboréa de urgencia (NV-08 conexo).                                     |
| 16:00    | La ambulancia no llegó (42 minutos). El SHST resuelve el traslado en el móvil de cuadrilla H-11 con el enfermero a bordo: decisión sin cobertura documental, con exposición jurídica institucional.                                               |
| 16:40    | Ingreso hospitalario del estudiante; pronóstico reservado. Base Central registra el cierre del traslado.                                                                                                                                          |
| 17:05    | Comunicado institucional con estado verificado del estudiante. El SMN mantiene el naranja hasta las 17:30.                                                                                                                                        |
| 18:00    | Informe preliminar del SHST al Rectorado y apertura del expediente de lecciones aprendidas de 72 horas (15.2).                                                                                                                                    |

**Tabla A.20 — Fricciones detectadas en E7**

| **Agentes en tensión** | **Fricción**                                                                                                                                           | **Resolución improvisada**                                        | **Ref.**       |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|----------------|
| A2 - A9/SAME           | Saturación del sistema médico externo: la ambulancia prometida en 40 minutos no llega, y el protocolo no define qué hace la institución mientras tanto | Traslado propio en H-11 con enfermero, sin respaldo documental    | NV-12          |
| A2 - A1                | Decisión de traslado con responsabilidad legal no cubierta: mover una fractura expuesta sin ambulancia                                                 | Autoridad asumida por el SHST y registrada en el libro de guardia | NV-12, NV-04   |
| A5 - A1                | Comunicación de crisis con rumor viral activo: la primera narrativa pública no fue institucional                                                       | Nota oficial a los 28 minutos, sin monitoreo previo de redes      | V-16           |
| A6 - A2                | Señalética de clausura insuficiente (cinta en tramo parcial) pese a la directiva de 6.2 sobre sendas arboladas                                         | Cordón con vallas recién tras el incidente                        | NV-08 (conexo) |

**Tabla A.21 — Verificación de redundancias en E7**

| **Capa / componente**        | **Comportamiento**                        | **Reemplazo / efecto**                                                  |
|------------------------------|-------------------------------------------|-------------------------------------------------------------------------|
| Capa 5 (RACUNS, CH1)         | Operativa                                 | Reporte del incidente, despacho de recursos y seguimiento sin falla     |
| Telefonía celular            | Operativa                                 | Llamada al 107 efectiva; la falla fue de capacidad externa, no de canal |
| Cadena médica externa (SAME) | Saturada por demanda ciudadana simultánea | Reemplazo improvisado por traslado institucional en H-11                |
| Comunicación de crisis       | Sin monitoreo ni sala de prensa           | Sin reemplazo: el rumor corrió 28 minutos sin respuesta oficial         |

Validación de plazos: sin ventanas de corte aplicables al incidente. La métrica crítica que el protocolo no define es el tiempo de respuesta médica: entre la ocurrencia (15:12) y la asistencia calificada en pabellón (15:20) transcurrieron 8 minutos, y entre el incidente y el ingreso hospitalario, 88 minutos, de los cuales 42 correspondieron a la espera de una ambulanza que no llegó. Un objetivo de tiempo sanitario (equivalente sanitario del RTO) es requisito mínimo de un plan con población a cargo y obra incorporado en la acción R-10 complementaria.

## ANEXO B — Tabla maestra de fricciones entre agentes

La tabla consolida las doce fricciones de mayor densidad institucional de los siete escenarios, con su resolución y el estado normativo del punto en el protocolo. Se lee como mapa de las zonas donde el documento calla y la organización habla: cada fila sin norma de respaldo es una decisión que la próxima emergencia tomará sin red.

**Tabla B.1 — Fricciones consolidadas por escenario**

| **Agentes**              | **Naturaleza de la fricción**                       | **Esc.**   | **Resolución en la simulación**                            | **Norma vigente**   |
|--------------------------|-----------------------------------------------------|------------|------------------------------------------------------------|---------------------|
| A1 - A2                  | Suspensión anticipada contra espera de confirmación | E2         | Decisión 2 minutos antes del corte por regla de oro        | Cubierta (7.1)      |
| A3 - A2                  | Autoridad de orden de confinamiento sin CDE         | E3, E4     | Orden del SHST por iniciativa, ratificación verbal         | Vacío (C-3)         |
| A5 - A3                  | Latencia de vocería sin guardia 24/7                | E1, E2, E6 | Publicación entre 11 y 160 minutos de la decisión          | Vacío (NV-03)       |
| A1/A5 - red              | Miembros del CDE inalcanzables por RACUNS           | E4         | CDE de hecho 6/10 y ratificación por acta                  | Vacío (NV-01)       |
| A4 - A7 - A6             | Arbitraje del generador móvil único                 | E4         | Prioridad verbal: comunicaciones, laboratorio, edilicio    | Vacío               |
| A8 - familias            | Retiro de menores durante pico de ráfagas           | E3, E4     | Ventana de retiro diferido improvisada                     | Vacío (NV-10)       |
| A6/A8 - A9               | Censo de ocupación exigido por el COE               | E4, E5     | Ocupación estimada, sin censo                              | Vacío (NV-07)       |
| Productor - Base Palihue | Mando sobre megafonía y personal externo            | E5         | Coordinación ad hoc sin integración ICS                    | Vacío (V-06)        |
| A2 - SAME                | Saturación sanitaria externa y traslado propio      | E7         | Móvil de cuadrilla con enfermero, sin cobertura documental | Vacío (NV-12)       |
| A10 - protocolo          | Ascensores cortados sin evacuación asistida         | E4         | Retención en tercer piso con promesa de bajada manual      | Contradicción (C-4) |
| A1 - A8                  | Calor extremo en escuelas sin criterio de nivel     | E6         | Extensión discrecional de la suspensión                    | Ambiguo (7.7)       |
| A3 - ciclos SMN          | Corte 22:00 con advertencia sin actualizar          | E6         | Decisión con información parcial y relectura 06:00         | Vacío (NV-09)       |

El patrón consolidado es concluyente: de las doce fricciones mayores, solo una (la de E2) tenía norma completa de respaldo en el momento del conflicto. Las once restantes se resolvieron por autoridad asumida, criterio personal o costumbre. En términos de ISO 22320, el protocolo tiene doctrina y tiene difusión, pero carece de la capa intermedia que convierte el criterio en decisión legítima: reglas de delegación, quórum y arbitraje escritas antes del evento. Esa capa es exactamente el objeto de las acciones R-01, R-02 y R-07 del plan correctivo, y su ausencia es la razón estructural por la que la ejecutabilidad del documento vale menos que su diseño.

## ANEXO C — Cumplimiento de las ventanas de decisión 22:00 / 10:00 / 16:00

La tabla resume la validación de plazos de los siete escenarios sobre las tres ventanas de decisión del punto 7.1, separando la adopción de la decisión (P5) de su difusión completa (P6), porque la regla de oro exige ambas antes del corte. El resultado cuantitativo: cinco decisiones exigibles, cuatro en término; cinco difusiones exigibles, una en término.

**Tabla C.1 — Plazos por escenario**

| **Escenario** | **Ventana evaluada**              | **Decisión (P5)**      | **Difusión completa (P6)**     | **Cumplimiento**                                |
|---------------|-----------------------------------|------------------------|--------------------------------|-------------------------------------------------|
| E1            | No exigible (amarillo)            | No aplica              | 08:10 (2 h 40 desde detección) | Sin plazo normado: difusión preventiva tardía   |
| E2            | Corte 22:00 (turno mañana)        | 21:58                  | 22:11                          | **Marginal: decisión sí, difusión no (11 min)** |
| E3            | Corte 16:00 (turno noche)         | 15:52                  | 16:08                          | **Marginal: decisión sí, difusión no (8 min)**  |
| E3            | Confinamiento (fenómeno en curso) | 14:22 (efectiva)       | 14:25 (megafonía)              | Eficaz pero irregular: orden sin norma (NV-04)  |
| E4            | Corte 16:00 (turno noche)         | ≈ 16:05 (CDE de hecho) | 16:15 (solo canales vivos)     | **Incumplimiento estructural de difusión**      |
| E5            | Régimen ACP (sin cortes)          | 17:50 (post vigencia)  | 17:50                          | Cumplido                                        |
| E6            | Corte 22:00 (turno mañana)        | 22:05                  | 22:30                          | **Marginal: decisión sí, difusión no (30 min)** |
| E6            | Cortes 10:00 y 16:00 (lunes)      | En término             | En término                     | Cumplido                                        |
| E7            | Sin ventana aplicable             | No aplica              | No aplica                      | Tiempo sanitario sin objetivo normado (NV-12)   |

La conclusión del anexo es la estadística que funda dos acciones correctivas: la cadena P2 a P6 completa consume entre 28 y 41 minutos con personal nocturno disponible, por lo que todo alerta naranja o rojo emitido con menos de una hora de antelación al corte compromete la difusión (R-02: decisión abreviada; R-04: difusión automática). El caso E4 agrega la variable estructural: con las redes digitales caídas y el canal FM inexistente, no hay difusión completa posible en el horizonte de una hora, cualquiera sea la diligencia del equipo. La ventana de decisión del protocolo es tan buena como el canal más lento que la deba ejecutar.
