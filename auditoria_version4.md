# AUDITORÍA TÉCNICA PROFUNDA
## PECl-UNS Rev 0 – Versión 4 (Consolidado Institucional 2026)

**Auditor:** Análisis experto en gestión de emergencias y continuidad operativa
**Fecha:** Septiembre 2026
**Metodología:** Revisión documental cruzada con estándares ISO 22320, ISO 22301, Ley 27.287 (SINAGIR) y mejores prácticas internacionales

---

## I. PUNTOS FUERTES DEL DOCUMENTO

### 1.1. Fortalezas estructurales
1. **Alineación normativa con SMN oficial:** El glosario unificado (Sección 4) y los umbrales específicos para Patagonia (Sección 5) eliminan ambigüedades interpretativas y anclan el protocolo en datos objetivos verificables.

2. **Ventanas horarias de decisión (22/10/16):** La Sección 7.1 establece criterios temporales predecibles que evitan la improvisación y protegen a la comunidad en tránsito. Esta es una de las mejores prácticas internacionales.

3. **Doctrina de "Confinamiento vs. Evacuación":** La Sección 7.8 define claramente cuándo NO evacuar (ráfagas extremas, granizo), alineándose con protocolos de tornado de EE.UU. y evitando el error común de exponer a las personas en la vía pública.

4. **Protocolo de custodia escolar:** La Sección 8 establece un procedimiento de retiro autorizado con verificación de DNI y registro (Anexo F), cubriendo el mayor riesgo legal y operativo de las escuelas preuniversitarias.

5. **Arquitectura de comunicaciones redundante:** RACUNS (Sección 12) con 5 capas tecnológicas (VHF, UHF, LoRa, Starlink, AM/FM) y redundancia energética triple (red → UPS → generador/solar) es un diseño robusto.

6. **Biblioteca de mensajes pre-estructurados:** Las plantillas M1-M5 (Sección 11.5) permiten comunicación rápida y consistente, reduciendo errores en situaciones de estrés.

7. **Ciclo de mejora continua:** La Sección 15 establece PDCA, indicadores y revisiones anuales, alineado con ISO 22301.

### 1.2. Fortalezas operativas
8. **Procesos P1-P10 bien definidos:** El Anexo A establece una cadena de responsabilidad clara desde el monitoreo hasta la mejora.

9. **Diagramas de flujo operativos:** Los Anexos C.1 y C.2 permiten comprensión rápida incluso bajo estrés.

10. **Capacitación para operadores no especializados:** La Sección 12.9 reconoce que la mayoría del personal no tiene formación en radiocomunicaciones y establece entrenamiento obligatorio.

---

## II. VULNERABILIDADES CRÍTICAS

### 2.1. Vulnerabilidades de gobernanza

**V-01. Suplencias no nombradas (Sección 10.1)**
- **Hallazgo:** La tabla del CDE dice "Suplente interno del área" pero NO nombra a ninguna persona.
- **Riesgo:** En emergencia real, si el titular no está disponible, no hay cadena de mando clara. Puede generar parálisis decisional.
- **Severidad:** **ALTA**
- **Recomendación:** Nombrar explícitamente a cada suplente por resolución rectoral antes de la aprobación del protocolo.

**V-02. Convenio UTN-FRBB "en curso" (Sección 11.3)**
- **Hallazgo:** El convenio de transmisión dúplex AM-FM está "en curso de establecimiento".
- **Riesgo:** Si la UTN no firma, toda la Capa 2 de difusión radial masiva se cae. No hay plan B.
- **Severidad:** **ALTA**
- **Recomendación:** Establecer alternativa con otra emisora FM local (ej. Radio Universidad, radios comunitarias) como respaldo.

**V-03. Protocolo de transición sin capacitación (Sección 9.4)**
- **Hallazgo:** La guardia de Seguridad Patrimonial asume el monitoreo 24/7, pero no se especifica:
  - Capacitación en lectura del SAT
  - Acceso a fuentes (web, app, correo)
  - Criterios de escalamiento
- **Riesgo:** Personal no capacitado puede no detectar alertas críticas o interpretarlas mal.
- **Severidad:** **MEDIA-ALTA**
- **Recomendación:** Incluir módulo de capacitación obligatorio antes de la activación del protocolo de transición.

### 2.2. Vulnerabilidades operativas

**V-04. Flota de handies insuficiente (Sección 12.6)**
- **Hallazgo:** 12 handies para toda la UNS es insuficiente. No hay cobertura para:
  - Decanatos / Direcciones de Departamento (múltiples)
  - Comedor Universitario
  - Residencias Universitarias
  - Biblioteca Central
  - Polideportivo
  - Laboratorios críticos
  - Centro de Datos secundario
- **Riesgo:** Áreas críticas sin comunicación radial directa en emergencia.
- **Severidad:** **ALTA**
- **Recomendación:** Ampliar a mínimo 20 handies, priorizando áreas con alta densidad poblacional o infraestructura crítica.

**V-05. Ausencia de protocolo para actividades de campo**
- **Hallazgo:** Se menciona "suspensión si la zona de destino está bajo alerta" (Sección 7.4.A) pero NO hay:
  - Registro previo obligatorio de salidas de campo
  - Protocolo de comunicación con grupos en terreno
  - Procedimiento de rescate/evacuación de campo
  - Responsable de validar destinos
- **Riesgo:** Grupos de estudiantes y docentes pueden quedar aislados en zonas remotas sin comunicación ni protocolo de rescate.
- **Severidad:** **CRÍTICA**
- **Recomendación:** Crear Anexo específico "Protocolo de Salidas de Campo" con registro obligatorio 48h antes, equipamiento de comunicación (satelital/radial), y procedimiento de emergencia.

**V-06. Falta de protocolo para eventos masivos**
- **Hallazgo:** El alcance menciona "población flotante y asistentes a eventos masivos" pero NO hay protocolo específico para:
  - Eventos culturales (conciertos, obras de teatro)
  - Actos académicos masivos (colaciones, conferencias)
  - Ferias (como la Feria Gastronómica mencionada en RACUNS)
  - Congresos y seminarios
- **Riesgo:** Miles de personas sin protocolo de evacuación/confinamiento específico.
- **Severidad:** **ALTA**
- **Recomendación:** Crear procedimiento estándar para eventos >200 personas, incluyendo evaluación meteorológica 24h antes y plan de contingencia.

**V-07. Residencias universitarias sin protocolo (Sección 6.4)**
- **Hallazgo:** No hay mención de protocolo para estudiantes residentes en:
  - Residencias de Bienestar Universitario
  - Alojamiento de becarios
- **Riesgo:** Estudiantes quedan atrapados sin procedimiento de evacuación o asistencia.
- **Severidad:** **MEDIA**
- **Recomendación:** Incluir protocolo específico para residencias, incluyendo punto de encuentro, provisión de alimentos y comunicación con familias.

**V-08. Laboratorios críticos sin protocolo específico (Sección 6.3)**
- **Hallazgo:** Se mencionan "protocolos específicos ante cortes prolongados de energía" pero NO se definen:
  - Procedimiento para laboratorios con cultivos vivos
  - Protocolo para animales de experimentación
  - Gestión de reactivos sensibles a temperatura
  - Preservación de investigación en curso
- **Riesgo:** Pérdida de investigación valiosa, contaminación ambiental, riesgo biológico.
- **Severidad:** **MEDIA-ALTA**
- **Recomendación:** Crear Anexo "Protocolo de Laboratorios Críticos" con procedimiento de corte de energía, preservación de muestras y gestión de residuos peligrosos.

**V-09. Comedor Universitario sin protocolo (Sección 6.3)**
- **Hallazgo:** Se menciona "Comedor / Buffet" en infraestructura crítica pero NO hay protocolo para:
  - Cierre preventivo
  - Mantenimiento como refugio
  - Provisión de alimentos en emergencia prolongada
- **Riesgo:** Miles de estudiantes sin acceso a alimentos durante emergencias prolongadas.
- **Severidad:** **MEDIA**
- **Recomendación:** Definir si el comedor se mantiene operativo como refugio o se cierra, y establecer stock de emergencia.

**V-10. Transporte institucional sin protocolo**
- **Hallazgo:** No hay procedimiento para:
  - Colectivos propios de la UNS en tránsito
  - Vehículos institucionales al momento del alerta
  - Choferes atrapados en ruta
- **Riesgo:** Personal y estudiantes en vehículos sin protocolo de resguardo.
- **Severidad:** **MEDIA**
- **Recomendación:** Crear procedimiento para transporte institucional, incluyendo puntos de resguardo y comunicación con choferes.

### 2.3. Vulnerabilidades técnicas

**V-11. UHF sin regularización ante ENACOM (Sección 12.10)**
- **Hallazgo:** El uso de UHF está "sujeto a regularización y verificación ante ENACOM".
- **Riesgo:** Uso ilegal de espectro radioeléctrico puede generar sanciones administrativas o penales, incluso en emergencia.
- **Severidad:** **ALTA**
- **Recomendación:** Regularizar ANTES de la aprobación del protocolo. Si no es posible, eliminar UHF del protocolo hasta obtener licencia.

**V-12. Ausencia de protocolo para personas con discapacidad (Sección 6.4)**
- **Hallazgo:** Se menciona "registro de estudiantes con movilidad reducida" pero NO hay:
  - Protocolo de asistencia específica
  - Personal designado y capacitado
  - Equipamiento (sillas de evacuación, rampas portátiles)
  - Señalética accesible (Braille, auditiva)
- **Riesgo:** Personas con discapacidad quedan abandonadas en emergencia.
- **Severidad:** **CRÍTICA**
- **Recomendación:** Crear Anexo "Protocolo de Asistencia a Personas con Discapacidad" con registro, personal asignado, equipamiento y simulacros específicos.

**V-13. Ciberseguridad durante emergencias no abordada**
- **Hallazgo:** No se menciona el riesgo de:
  - Ataques informáticos durante emergencias (cuando el personal está distraído)
  - Caída de servidores por tormentas eléctricas
  - Protocolo de backup en sitio alterno
- **Riesgo:** Pérdida de datos críticos, interrupción de servicios digitales.
- **Severidad:** **MEDIA**
- **Recomendación:** Incluir procedimiento de ciberseguridad en emergencias, incluyendo verificación de backups y protocolo de conmutación.

**V-14. Bibliotecas y archivos sin protocolo de protección**
- **Hallazgo:** Se menciona protección de "archivos históricos" pero NO hay protocolo para:
  - Biblioteca Central (patrimonio bibliográfico)
  - Archivos de departamentos
  - Tesis y publicaciones
- **Riesgo:** Pérdida irreparable de patrimonio bibliográfico ante inundaciones.
- **Severidad:** **MEDIA**
- **Recomendación:** Crear procedimiento de protección de patrimonio bibliográfico, incluyendo elevación de material, cobertores impermeables y digitalización preventiva.

**V-15. Continuidad académica no definida (Sección 7.7)**
- **Hallazgo:** Se menciona "virtualidad asincrónica" pero NO hay:
  - Plan de virtualidad de emergencia
  - Reprogramación de exámenes
  - Extensión del cuatrimestre
  - Capacitación docente
- **Riesgo:** Caos académico post-emergencia, reclamos de estudiantes.
- **Severidad:** **MEDIA-ALTA**
- **Recomendación:** Crear Anexo "Protocolo de Continuidad Académica" con plan de virtualidad, reprogramación y criterios de evaluación.

### 2.4. Vulnerabilidades de comunicación

**V-16. No hay protocolo de comunicación con medios externos**
- **Hallazgo:** Solo se menciona el Vocero Institucional (Sección 11.1) pero NO hay:
  - Sala de prensa
  - Procedimiento de declaraciones
  - Gestión de rumores en redes sociales
  - Protocolo de comunicación con familias de víctimas
- **Riesgo:** Desinformación, pánico, crisis de imagen institucional.
- **Severidad:** **MEDIA**
- **Recomendación:** Crear procedimiento de comunicación de crisis, incluyendo sala de prensa, vocería única, monitoreo de redes y protocolo de comunicación con familias.

**V-17. Ausencia de protocolo para proveedores y contratistas**
- **Hallazgo:** No se menciona qué pasa con el personal externo que está trabajando en la UNS al momento del alerta.
- **Riesgo:** Personal externo sin protocolo de evacuación/confinamiento, responsabilidad legal unclear.
- **Severidad:** **MEDIA**
- **Recomendación:** Incluir en el alcance a proveedores y contratistas, con procedimiento de notificación y evacuación.

### 2.5. Vulnerabilidades logísticas

**V-18. No hay protocolo para cortes de agua**
- **Hallazgo:** Las olas de calor/frío mencionan cortes pero no hay:
  - Reserva de agua potable
  - Puntos de hidratación
  - Protocolo sanitario
- **Riesgo:** Deshidratación masiva, problemas sanitarios.
- **Severidad:** **MEDIA**
- **Recomendación:** Establecer reserva de agua potable (mínimo 3 litros/persona/día) y puntos de hidratación en refugios.

**V-19. Ausencia de protocolo para cortes de gas**
- **Hallazgo:** Las calderas y cocinas del comedor usan gas. No hay procedimiento de corte preventivo.
- **Riesgo:** Explosiones, incendios.
- **Severidad:** **ALTA**
- **Recomendación:** Crear procedimiento de corte preventivo de gas en Alerta Naranja/Roja, con personal capacitado.

**V-20. No hay protocolo para árboles caídos sobre vehículos**
- **Hallazgo:** En Palihue hay estacionamientos bajo árboles. No hay procedimiento para:
  - Vehículos dañados
  - Responsabilidad institucional
  - Remoción de árboles
- **Riesgo:** Reclamos, daños materiales, obstrucción de accesos.
- **Severidad:** **BAJA-MEDIA**
- **Recomendación:** Incluir procedimiento de gestión de árboles caídos, incluyendo contacto con empresa de remoción y protocolo de denuncia de seguros.

**V-21. Ausencia de protocolo para ascensores con personas atrapadas**
- **Hallazgo:** Se menciona "desconexión preventiva" pero NO hay:
  - Procedimiento de rescate de personas atrapadas
  - Personal capacitado
  - Equipamiento de rescate
- **Riesgo:** Personas atrapadas durante horas, pánico.
- **Severidad:** **MEDIA**
- **Recomendación:** Crear procedimiento de rescate en ascensores, con personal capacitado y contacto con empresa de mantenimiento.

### 2.6. Vulnerabilidades post-emergencia

**V-22. Ausencia de análisis psicológico post-evento**
- **Hallazgo:** No se menciona:
  - Contención psicológica post-traumática
  - Seguimiento de afectados
  - Debriefing
- **Riesgo:** Estrés post-traumático no atendido, impacto en salud mental.
- **Severidad:** **MEDIA**
- **Recomendación:** Incluir protocolo de asistencia psicológica post-emergencia, con equipo de profesionales y seguimiento.

**V-23. No hay protocolo para seguros y siniestros**
- **Hallazgo:** No se menciona:
  - Cobertura de seguros institucionales
  - Procedimiento de denuncia de siniestros
  - Documentación requerida
- **Riesgo:** Pérdida de cobertura, demoras en indemnizaciones.
- **Severidad:** **BAJA-MEDIA**
- **Recomendación:** Crear procedimiento de gestión de siniestros, incluyendo contacto con aseguradora, documentación fotográfica y plazos.

**V-24. Ausencia de protocolo para donaciones**
- **Hallazgo:** El Complejo Alem fue centro de acopio. No hay procedimiento formal para:
  - Recepción de donaciones
  - Clasificación y distribución
  - Registro y rendición de cuentas
- **Riesgo:** Caos logístico, acusaciones de mal manejo.
- **Severidad:** **BAJA**
- **Recomendación:** Crear procedimiento de gestión de donaciones, con equipo designado y protocolo de distribución.

---

## III. SITUACIONES NO TENIDAS EN CUENTA

### 3.1. Escenarios no contemplados

**S-01. Emergencias múltiples simultáneas**
- Ejemplo: Alerta Rojo por viento + corte de energía + inundación + accidente de tránsito
- No hay protocolo de priorización de recursos

**S-02. Emergencias en días no laborables**
- Fines de semana, feriados, recesos académicos
- No hay protocolo de activación con personal mínimo

**S-03. Emergencias durante exámenes finales**
- ¿Se reprograman? ¿Se toman igual?
- No hay criterio definido

**S-04. Emergencias con víctimas fatales**
- No hay protocolo de comunicación con familias
- No hay procedimiento de preservación de escena
- No hay coordinación con policía y justicia

**S-05. Emergencias con colapso estructural**
- No hay protocolo de búsqueda y rescate
- No hay coordinación con bomberos
- No hay procedimiento de evaluación de daños

**S-06. Emergencias con contaminación química/biológica**
- No hay protocolo de descontaminación
- No hay equipo de protección personal
- No hay coordinación con autoridades sanitarias

**S-07. Emergencias con rehenes o violencia**
- No hay protocolo de negociación
- No hay coordinación con policía
- No hay procedimiento de evacuación segura

### 3.2. Actores no contemplados

**A-01. Familiares de estudiantes**
- No hay protocolo de comunicación
- No hay punto de encuentro
- No hay procedimiento de información

**A-02. Exalumnos y graduados**
- Pueden estar en la UNS por trámites
- No hay protocolo de asistencia

**A-03. Visitantes internacionales**
- Barrera idiomática
- No hay protocolo de comunicación en otros idiomas

**A-04. Mascotas y animales**
- Escuela Agraria tiene animales
- No hay protocolo de evacuación o cuidado

**A-05. Personas en situación de calle**
- Pueden buscar refugio en la UNS
- No hay protocolo de asistencia

---

## IV. OPORTUNIDADES DE MEJORA

### 4.1. Mejoras tecnológicas

**M-01. App UNS con notificaciones push**
- Implementar sistema de notificaciones geolocalizadas
- Permitir confirmación de recepción
- Incluir botón de pánico

**M-02. Drones para evaluación de daños**
- Evaluar techos, árboles, estructuras
- Reducir riesgo para personal
- Documentar daños para seguros

**M-03. Sistema de geolocalización de personal en campo**
- GPS en handies o teléfonos
- Monitoreo en tiempo real
- Rescate rápido

**M-04. Plataforma de gestión de emergencias**
- Centralizar información
- Registrar decisiones
- Generar informes automáticos

### 4.2. Mejoras organizativas

**M-05. Red de voluntarios capacitados**
- Alumnos avanzados de Medicina, Ingeniería, Psicología
- Apoyo en emergencias
- Créditos académicos

**M-06. Convenios con hoteles**
- Alojamiento de emergencia para estudiantes
- Descuentos institucionales

**M-07. Convenios con supermercados**
- Provisión de alimentos en emergencia
- Stock de emergencia

**M-08. Protocolo de "Familia Segura"**
- Punto de encuentro familiar
- Comunicación con familias
- Reducción de ansiedad

### 4.3. Mejoras de capacitación

**M-09. Simulacros con otras instituciones**
- Defensa Civil, Bomberos, Policía
- Hospitales, otras universidades
- Mejora de coordinación

**M-10. Capacitación en primeros auxilios psicológicos**
- Personal de Salud, Bienestar, docentes
- Contención post-traumática
- Reducción de estrés

**M-11. Capacitación en liderazgo en crisis**
- Directores, decanos, jefes
- Toma de decisiones bajo presión
- Comunicación efectiva

### 4.4. Mejoras de documentación

**M-12. Manual de bolsillo por rol**
- Tarjeta plastificada con procedimientos clave
- Fácil consulta en emergencia
- Incluye contactos críticos

**M-13. Cartografía de zonas seguras**
- Mapas por edificio
- Rutas de evacuación
- Puntos de encuentro

**M-14. Checklist de verificación pre-emergencia**
- Revisión de infraestructura
- Verificación de comunicaciones
- Confirmación de suministros

---

## V. RECOMENDACIONES PRIORITARIAS

### 5.1. Acciones inmediatas (antes de aprobación)

1. **Nombrar suplentes del CDE** (V-01)
2. **Regularizar UHF ante ENACOM** o eliminar del protocolo (V-11)
3. **Crear protocolo de actividades de campo** (V-05)
4. **Crear protocolo de asistencia a personas con discapacidad** (V-12)
5. **Ampliar flota de handies a mínimo 20 unidades** (V-04)

### 5.2. Acciones a corto plazo (0-90 días)

6. **Establecer convenio alternativo de difusión radial** (V-02)
7. **Capacitar a guardia de Seguridad Patrimonial** (V-03)
8. **Crear protocolo de eventos masivos** (V-06)
9. **Crear protocolo de continuidad académica** (V-15)
10. **Crear procedimiento de corte preventivo de gas** (V-19)

### 5.3. Acciones a mediano plazo (3-12 meses)

11. **Crear protocolo de laboratorios críticos** (V-08)
12. **Crear protocolo de residencias universitarias** (V-07)
13. **Crear procedimiento de comunicación de crisis** (V-16)
14. **Implementar app UNS con notificaciones push** (M-01)
15. **Crear red de voluntarios capacitados** (M-05)

---

## VI. CONCLUSIÓN

El PECl-UNS Rev 0 Versión 4 es un documento **sólido y bien estructurado**, con fortalezas significativas en alineación normativa, arquitectura de comunicaciones y procedimientos operativos. Sin embargo, presenta **24 vulnerabilidades identificadas**, de las cuales **6 son críticas o altas** y requieren atención inmediata antes de la aprobación.

Las principales áreas de mejora son:
1. **Gobernanza:** Suplencias no nombradas, convenios pendientes
2. **Operaciones:** Flota de handies insuficiente, protocolos faltantes (campo, eventos masivos, discapacidad)
3. **Técnicas:** Regularización ENACOM, ciberseguridad
4. **Logística:** Cortes de agua/gas, transporte institucional

Con las correcciones prioritarias (Sección V.1), el protocolo alcanzará un nivel de madurez comparable a los mejores estándares internacionales y estará listo para implementación efectiva.

**Calificación global:** 7.5/10
**Potencial con correcciones:** 9.5/10
