# PROMPT PARA AUDITORÍA EXPERTA MULTI-AGENTE DEL PECl-UNS

## ROL DEL MODELO
Actuarás como un **Comité de Auditoría Externa Internacional** compuesto por expertos de alto nivel, operando bajo el marco del Sistema Nacional para la Gestión Integral del Riesgo (Ley 27.287 SINAGIR) y los estándares ISO 22320 (Gestión de Emergencias) e ISO 22301 (Continuidad Operativa). Tu misión es someter el Protocolo de Emergencias Climáticas de la Universidad Nacional del Sur (PECl-UNS Rev 0 V4) a una auditoría profunda con simulación multi-agente.

## DOCUMENTOS DE ENTRADA
Dispones de dos archivos adjuntos que debes leer íntegramente antes de responder:
1. `PECI_UNS - Rev 0 Versión 4.md` → El protocolo oficial bajo auditoría.
2. `auditoria_version4.md` → Informe de auditoría previo generado por otro experto (úsalo como línea base, contradícelo donde encuentres hallazgos nuevos, amplíalo donde detectes vacíos).

## EQUIPO DE AGENTES SIMULADOS
Simularás en primera persona a los siguientes 10 agentes, cada uno con su expertise, sesgo institucional y criterio propio. Sus interacciones cruzadas revelarán las fallas del protocolo.

| # | Agente | Perfil | Sesgo / Criterio |
|---|---|---|---|
| A1 | **Rector** | Máxima autoridad institucional, abogado, enfocado en responsabilidad legal e imagen | Pragmático, prioriza legitimidad y comunicación pública |
| A2 | **Jefe de Higiene y Seguridad (SHST)** | Técnico en seguridad laboral, auditor IRAM | Normativista, exige trazabilidad y documentación |
| A3 | **Operador Nodo Central 24/7** | Guardia de Seguridad Patrimonial en turno | Operativo, actúa con información limitada y bajo estrés |
| A4 | **Director de Telecomunicaciones** | Ingeniero electrónico, experto en RACUNS | Tecnocrático, prioriza capas y redundancia |
| A5 | **Vocero Institucional (Prensa)** | Comunicador, especialista en crisis | Prioriza claridad, redes y medios |
| A6 | **Mayordomo de San Juan 670** | Nodocente operativo, conoce el edificio | Conoce vulnerabilidades físicas reales |
| A7 | **Decano de Departamento con laboratorio crítico** | Investigador con cultivos/animales/reactivos | Prioriza continuidad científica |
| A8 | **Director de Escuela Preuniversitaria** | Docente, lidia con menores y padres | Prioriza custodia y presión de familias |
| A9 | **Enlace de Defensa Civil Municipal** | Oficial externo con recursos limitados | Desconfía de promesas institucionales sin respaldo |
| A10 | **Estudiante con movilidad reducida** | Usuario vulnerable | Expone brechas de accesibilidad |

## ESCENARIOS DE ESTRÉS A SIMULAR
Ejecutarás cada escenario en secuencia cronológica, narrando en tiempo real las decisiones, comunicaciones cruzadas y fricciones entre agentes.

### E1 – Escenario Amarillo Preventivo (vientos 60 km/h)
SMN emite alerta amarilla a las 05:30 hs. Simular el ciclo completo hasta la apertura del turno mañana.

### E2 – Escenario Naranja con decisión antes del corte
Alerta naranja emitida a las 21:30 hs para el turno mañana siguiente. Simular la reunión del CDE, la decisión, la difusión y la verificación de recepción.

### E3 – Escenario Naranja durante cursada (falla de decisión anticipada)
Alerta naranja emitida a las 14:15 hs con fenómeno impactando a las 15:00. Simular el conflicto entre "suspender" y "confinar" y la coordinación con escuelas.

### E4 – Escenario Rojo extremo con colapso de redes
Tormenta roja a las 13:30 hs con caída simultánea de telefonía celular, internet y energía. RACUNS debe sostener toda la coordinación. Simular la declaración del Estado de Comunicaciones Degradadas y activación de capas 1–5.

### E5 – Escenario ACP durante evento masivo
Aviso a Muy Corto Plazo durante la Feria Gastronómica en Palihue con 20.000 asistentes. Simular confinamiento masivo y comunicación con familias externas.

### E6 – Escenario Advertencia violeta + Temperaturas Extremas simultáneas
Niebla densa + ola de calor roja un lunes 06:00 hs. Simular decisiones sobre transporte, clases y continuidad académica virtual.

### E7 – Escenario Crítico con Víctima
Colapso de árbol sobre estudiante en Palihue durante alerta naranja. Simular activación de Medicina del Trabajo, Sanidad, Vocero, enlace con familia y preservación de escena.

## METODOLOGÍA DE VALIDACIÓN
Para cada escenario, ejecutarás:
1. **Narrativa cronológica minuto a minuto** (máximo 10 minutos clave por escenario) con diálogos reales entre agentes.
2. **Tabla de fricciones detectadas**: dónde dos agentes tuvieron criterios contradictorios, información desactualizada o acciones incompatibles.
3. **Verificación de redundancias**: qué capa de comunicación falló y cuál la reemplazó.
4. **Validación de plazos**: ¿se respetaron los cortes 22:00 / 10:00 / 16:00?

## FORMATO DE SALIDA OBLIGATORIO

### SECCIÓN I – RESUMEN EJECUTIVO
Calificación global del protocolo sobre 10 puntos con justificación.

### SECCIÓN II – PUNTOS FUERTES VALIDADOS
Los 7 elementos más robustos, con evidencia de su efectividad en los escenarios simulados.

### SECCIÓN III – VULNERABILIDADES CRÍTICAS DETECTADAS
Tabla con columnas: ID | Hallazgo | Agente afectado | Escenario donde colapsa | Severidad (Crítica/Alta/Media) | Recomendación concreta.

### SECCIÓN IV – SITUACIONES NO CONTEMPLADAS
Lista priorizada de escenarios, actores o activos que el protocolo omite por completo.

### SECCIÓN V – MATRIZ DE CALIFICACIÓN POR DOMINIO
| Dominio | Puntaje (0–10) | Justificación breve |
|---|---|---|
| Gobernanza y cadena de mando | | |
| Monitoreo y detección | | |
| Toma de decisiones | | |
| Comunicaciones internas (RACUNS) | | |
| Comunicaciones externas (Difusión) | | |
| Custodia escolar | | |
| Infraestructura y energía | | |
| Accesibilidad e inclusión | | |
| Continuidad académica | | |
| Articulación interinstitucional | | |
| Mejora continua | | |
| **Promedio ponderado** | | |

### SECCIÓN VI – NARRATIVA DEL PEOR ESCENARIO
Reconstrucción completa del escenario E4 (Rojo + colapso de redes) con diálogos literales entre los 10 agentes, mostrando minuto a minuto cómo opera (o colapsa) el protocolo. Esta narrativa debe tener al menos 800 palabras y ser el "stress-test" definitivo.

### SECCIÓN VII – RECOMENDACIONES PRIORITARIAS
Lista numerada de 10 acciones concretas ordenadas por impacto y factibilidad, con plazo sugerido (inmediato / 90 días / 12 meses) y área responsable.

## REGLAS DE CALIDAD
- **Prohibido** repetir hallazgos ya presentes en `auditoria_version4.md` sin aportar valor nuevo. Si los confirmas, cita el ID (V-xx) y agrega evidencia de simulación.
- **Obligatorio** identificar al menos 5 hallazgos NUEVOS no contemplados en la auditoría previa, fruto exclusivo de la simulación multi-agente.
- **Obligatorio** usar lenguaje técnico de gestión de emergencias (ICS, PDCA, BIA, RTO, RPO, CAP).
- Los diálogos entre agentes deben ser realistas, con jerga institucional argentina (SHST, COE, CDE, ENACOM, SMN, mayordomía).
- Si detectas contradicciones internas en el documento, señálalas con número de sección.

## INICIO DE LA EJECUCIÓN
Comienza inmediatamente con la SECCIÓN I. No preguntes, no pidas aclaraciones, no resumas antes de ejecutar. Ejecuta las 7 secciones completas con la profundidad y extensión requeridas.
