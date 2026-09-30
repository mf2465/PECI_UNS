
---

## 3. PLAN DE TRABAJO DETALLADO

### FASE 1: PLANIFICACIÓN Y DISEÑO (4-6 semanas)

#### Semana 1-2: Análisis y Diseño
- [ ] Reuniones con stakeholders (CDE, DCI, Telecomunicaciones, Infraestructura)
- [ ] Definición detallada de requisitos funcionales y no funcionales
- [ ] Diseño de wireframes y prototipos (Figma/Adobe XD)
- [ ] Arquitectura de base de datos detallada
- [ ] Diseño de API (endpoints, autenticación, roles)

#### Semana 3-4: Diseño Técnico
- [ ] Diagrama de flujo de emergencias (basado en Anexos 07-A, 07-C)
- [ ] Diseño del sistema de notificaciones críticas
- [ ] Definición de permisos y roles (12+ tipos de usuario)
- [ ] Plan de seguridad y cifrado
- [ ] Plan de pruebas

#### Semana 5-6: Configuración de Entorno
- [ ] Configuración de servidores de desarrollo
- [ ] Setup de Firebase (FCM, Analytics, Crashlytics)
- [ ] Configuración de CI/CD
- [ ] Repositorios Git (monorepo o múltiples)
- [ ] Ambientes: dev, staging, producción

**Entregable:** Documentación técnica completa + prototipos funcionales

---

### FASE 2: DESARROLLO DEL BACKEND (8-10 semanas)

#### Semana 7-10: Core Backend

**Módulo 1: Autenticación y Usuarios**
- [ ] Sistema de registro/login
- [ ] Gestión de roles y permisos
- [ ] Perfiles de usuario (con foto, departamento, teléfono alternativo)
- [ ] Integración con LDAP/SSO de la UNS (opcional)
- [ ] Gestión de sesiones y tokens

**Módulo 2: Sistema de Alertas**
- [ ] Integración con SMN (web scraping o API)
- [ ] Motor de decisiones basado en horarios (22:00, 10:00, 16:00)
- [ ] Gestión de niveles de alerta (Verde/Rojo)
- [ ] Ficha del Alerta (Anexo B del Documento A)
- [ ] Historial de alertas
- [ ] Lectura obligatoria de línea de tiempo y detalle zonal

**Módulo 3: Notificaciones Críticas**
- [ ] Integración FCM/APNs
- [ ] Sistema de notificaciones de alta prioridad
- [ ] Alarma con sonido, vibración y voz
- [ ] Override de modo silencio (permisos especiales)
- [ ] Sistema de confirmación de recepción
- [ ] Redundancia: mínimo 3 canales simultáneos

**Módulo 4: Gestión de Emergencias**
- [ ] Creación de emergencias (manual y automática)
- [ ] Call-outs selectivos (por departamento, edificio, rol)
- [ ] Sistema de respuestas rápidas
- [ ] Monitoreo en tiempo real
- [ ] Cancelación de emergencias
- [ ] Gestión de ACP (Avisos a Muy Corto Plazo)

#### Semana 11-14: Módulos Complementarios

**Módulo 5: Checklists Digitales**
- [ ] Editor de checklists (jerárquico: unidad → contenedor → ítem)
- [ ] Funcionalidad offline (sync automático)
- [ ] Análisis con IA (detección de anomalías)
- [ ] Exportación a PDF
- [ ] Historial y estadísticas
- [ ] Checklist de Mantenimiento Preventivo de Infraestructura (AT-01)
- [ ] Checklist de Mantenimiento de Comunicaciones (AT-02)

**Módulo 6: Comunicación Interna**
- [ ] Mensajería por departamentos
- [ ] Anuncios urgentes vs normales
- [ ] Chat grupal por emergencia
- [ ] Plantillas M1-M8 (Anexo 07-C)
- [ ] Cascada de mensajes institucional (DCI → Decanos → Mayordomías → Estudiantes)
- [ ] Integración con megafonía (opcional)
- [ ] Gestión de rumores (M7)
- [ ] Partes prolongados (M8)

**Módulo 7: Gestión de Custodia Escolar**
- [ ] Registro de retiro autorizado (Anexo C del Documento A)
- [ ] Verificación de DNI contra listado de autorizados
- [ ] Listado de adultos autorizados
- [ ] Reportes a Oficina de Recepción de Avisos
- [ ] Custodia extendida (corte de transporte público)
- [ ] Registro: fecha, hora, alumno, adulto, DNI, vínculo y firma

**Módulo 8: Panel de Administración**
- [ ] Dashboard principal
- [ ] Gestión de personal
- [ ] Estadísticas y reportes
- [ ] Gestión de edificios y sectores
- [ ] Logs de auditoría
- [ ] Vulnerabilidades por predio (AT-01 Sección 3)
- [ ] Sala de Crisis: San Juan 670 / Anexo Campus Radio UNS

**Entregable:** API funcional con documentación (Swagger/OpenAPI)

---

### FASE 3: DESARROLLO DE APP MÓVIL (10-12 semanas)

#### Semana 15-20: App Android/iOS

**Sprint 1: Setup y Autenticación**
- [ ] Setup de React Native/Flutter
- [ ] Pantallas de login/registro
- [ ] Selección de rol
- [ ] Código de invitación (6 dígitos)
- [ ] Configuración de perfil

**Sprint 2: Dashboard y Navegación**
- [ ] Dashboard principal con estado actual
- [ ] Navegación por módulos
- [ ] Sistema de notificaciones en app
- [ ] Banner de alerta activa

**Sprint 3: Sistema de Alertas (CRÍTICO)**
- [ ] Recepción de alertas en background
- [ ] Alarma crítica (sonido + vibración + voz)
- [ ] Pantalla de alerta con detalles SMN
- [ ] Botones de respuesta rápida
- [ ] Permisos especiales (batería, notificaciones críticas)
- [ ] Funcionamiento con app cerrada
- [ ] Soporte para niveles: Verde, Amarillo, Naranja, Rojo, ACP, Violeta
- [ ] Diferenciación por tipo de emergencia (M1-M8)

**Sprint 4: Respuestas y Monitoreo**
- [ ] Sistema de respuestas (En camino / Retrasado / No disponible / Recibido)
- [ ] Estado en tiempo real del personal
- [ ] Mapa de ubicación (opcional)
- [ ] Notificaciones de cancelación
- [ ] Escucha permanente CH1 (Alerthor) en Naranja/Rojo

**Sprint 5: Checklists**
- [ ] Visualización de checklists asignados
- [ ] Formulario de inspección
- [ ] Modo offline
- [ ] Sincronización automática
- [ ] Historial personal

**Sprint 6: Mensajería y Comunicación**
- [ ] Chat interno por departamentos
- [ ] Mensajes urgentes vs normales
- [ ] Historial de comunicaciones
- [ ] Notificaciones segregadas
- [ ] Confirmación de recepción

**Sprint 7: Custodia Escolar**
- [ ] Vista para personal docente/directivo
- [ ] Registro de retiro con verificación DNI
- [ ] Verificación de identidad
- [ ] Reportes automáticos a Oficina de Recepción
- [ ] Comunicación a familias

**Sprint 8: Configuración y Perfil**
- [ ] Configuración de notificaciones
- [ ] Datos personales
- [ ] Historial de actividad
- [ ] Soporte y ayuda
- [ ] Modo de emergencia (contactos, rutas seguras)

**Entregable:** App móvil funcional para Android e iOS

---

### FASE 4: DESARROLLO WEB - PANEL DE ADMINISTRACIÓN (6-8 semanas)

#### Semana 21-26: Panel Web

**Módulo 1: Dashboard**
- [ ] Vista general del estado
- [ ] Alertas activas con nivel SMN
- [ ] Personal disponible en tiempo real
- [ ] Estadísticas rápidas
- [ ] Accesos rápidos
- [ ] Estado de RACUNS y comunicaciones

**Módulo 2: Gestión de Emergencias**
- [ ] Creación manual de emergencias
- [ ] Monitoreo en tiempo real (mapa + lista)
- [ ] Historial de emergencias
- [ ] Exportación de reportes
- [ ] Cancelación de emergencias
- [ ] Ficha del Alerta digital (Anexo B)
- [ ] Motor de ventanas horarias (22:00, 10:00, 16:00)

**Módulo 3: Gestión de Personal**
- [ ] CRUD de usuarios
- [ ] Asignación de roles
- [ ] Gestión de departamentos
- [ ] Importación masiva (CSV/Excel)
- [ ] Desactivación de cuentas
- [ ] Roles CDE con suplentes (Sección 9.1 Doc A)

**Módulo 4: Gestión de Edificios**
- [ ] Mapeo de edificios UNS (Palihue, Alem, SJ670, Colón 80, Escuelas, etc.)
- [ ] Asignación de mayordomos
- [ ] Zonas de confinamiento por predio
- [ ] Vulnerabilidades por predio (AT-01 Sección 3)
- [ ] Checklists por edificio
- [ ] Sectores vulnerables internos

**Módulo 5: Checklists y Mantenimiento**
- [ ] Editor visual de checklists
- [ ] Asignación de tareas
- [ ] Análisis de resultados
- [ ] Detección de anomalías (IA)
- [ ] Reportes en PDF
- [ ] Checklist AT-01 (Infraestructura: pluviales, cubiertas, arbolado, gas, ascensores)
- [ ] Checklist AT-02 (Comunicaciones: prueba radial, Starlink, Meshtastic)

**Módulo 6: Comunicaciones**
- [ ] Gestión de mensajes
- [ ] Plantillas M1-M8 del Anexo 07-C
- [ ] Historial de comunicaciones
- [ ] Estadísticas de recepción
- [ ] Gestión de rumores (M7)
- [ ] Partes prolongados (M8)
- [ ] Registro de difusión

**Módulo 7: Reportes y Estadísticas**
- [ ] Dashboard de métricas
- [ ] Reportes por período
- [ ] Tiempos de respuesta
- [ ] Análisis de efectividad
- [ ] Exportación de datos
- [ ] Informe post-activación (72 horas)
- [ ] Indicadores AT-02 (Sección 9)

**Módulo 8: Configuración**
- [ ] Parámetros del sistema
- [ ] Integración con SMN
- [ ] Gestión de notificaciones
- [ ] Backups y logs
- [ ] Permisos globales
- [ ] Ventanas horarias de decisión configurables
- [ ] Umbrales SMN actualizables

**Entregable:** Panel web funcional y responsivo

---

### FASE 5: INTEGRACIÓN Y PRUEBAS (6-8 semanas)

#### Semana 27-30: Pruebas Integrales

**Pruebas Funcionales**
- [ ] Pruebas unitarias (backend)
- [ ] Pruebas de integración
- [ ] Pruebas E2E (end-to-end)
- [ ] Pruebas de carga (10,000+ usuarios simultáneos)
- [ ] Pruebas de seguridad

**Pruebas Específicas**
- [ ] Pruebas de notificaciones críticas (diferentes dispositivos y fabricantes)
- [ ] Pruebas de modo offline
- [ ] Pruebas de concurrencia
- [ ] Pruebas de recuperación ante fallos
- [ ] Pruebas de compatibilidad (Android 8+, iOS 13+)
- [ ] Pruebas de cascada de mensajes (M1-M8)
- [ ] Pruebas de ventanas horarias (22:00, 10:00, 16:00)
- [ ] Pruebas de custodia escolar
- [ ] Pruebas de checklists AT-01 y AT-02

**Pruebas con Usuarios**
- [ ] Pruebas con CDE
- [ ] Pruebas con mayordomos
- [ ] Pruebas con docentes
- [ ] Pruebas con personal de mantenimiento
- [ ] Pruebas con estudiantes (beta cerrada)
- [ ] Pruebas con Telecomunicaciones (RACUNS)
- [ ] Pruebas con Escuelas Preuniversitarias

#### Semana 31-32: Correcciones y Optimización
- [ ] Corrección de bugs
- [ ] Optimización de performance
- [ ] Mejoras de UX/UI basadas en feedback
- [ ] Documentación de usuario
- [ ] Manuales de capacitación

**Entregable:** Sistema completo y probado

---

### FASE 6: DESPLIEGUE Y LANZAMIENTO (4-6 semanas)

#### Semana 33-35: Preparación para Producción
- [ ] Configuración de servidores de producción
- [ ] Migración de datos
- [ ] Certificados SSL y seguridad
- [ ] Backup y disaster recovery
- [ ] Monitoreo y alertas (Grafana/Prometheus)

#### Semana 36-37: Publicación
- [ ] Publicación en Google Play Store
- [ ] Publicación en Apple App Store
- [ ] Despliegue de panel web
- [ ] Configuración de dominios
- [ ] DNS y CDN

#### Semana 38-39: Capacitación y Rollout
- [ ] Capacitación a administradores (CDE)
- [ ] Capacitación a mayordomos
- [ ] Capacitación a personal de seguridad
- [ ] Capacitación a Telecomunicaciones
- [ ] Material de capacitación (videos, manuales)
- [ ] Módulo Moodle de autoprotección
- [ ] Soporte técnico inicial

**Entregable:** Sistema en producción y operativo

---

### FASE 7: SOPORTE Y MEJORA CONTINUA (Ongoing)

- [ ] Monitoreo 24/7
- [ ] Soporte técnico nivel 1 y 2
- [ ] Actualizaciones de seguridad
- [ ] Nuevas funcionalidades (roadmap)
- [ ] Mejora continua basada en feedback
- [ ] Reportes mensuales de uso
- [ ] Revisión anual del protocolo (ciclo PDCA)
- [ ] Informe post-activación ≤72 horas

---

## 4. RECURSOS NECESARIOS

### 4.1. Recursos Humanos

| Rol | Cantidad | Dedicación | Descripción |
|-----|----------|-------------|-------------|
| **Project Manager** | 1 | Part-time | Coordinación general, cronograma, stakeholders |
| **Desarrollador Backend Senior** | 1 | Full-time | API, base de datos, integraciones |
| **Desarrollador Frontend Web** | 1 | Full-time | Panel de administración |
| **Desarrollador Móvil** | 1-2 | Full-time | Apps Android/iOS (React Native/Flutter) |
| **Diseñador UX/UI** | 1 | Part-time | Interfaces, prototipos, experiencia de usuario |
| **QA Engineer** | 1 | Part-time | Pruebas, calidad, automatización |
| **DevOps** | 1 | Part-time | Infraestructura, CI/CD, despliegues |
| **Especialista en Seguridad** | 1 | Consultoría | Auditorías, cumplimiento, protección de datos |

**Nota:** Tu rol podría ser Project Manager + Desarrollador Backend, aprovechando tus conocimientos.

### 4.2. Recursos Tecnológicos

#### Infraestructura (ya dispones de hosting y BD)
- [ ] **Servidor de producción** (mínimo 4 vCPUs, 8GB RAM, 100GB SSD)
- [ ] **Servidor de staging** (similar a producción)
- [ ] **Base de datos MySQL** (ya disponible)
- [ ] **Redis** para caché y colas
- [ ] **Almacenamiento de archivos** (S3 o similar, ~500GB inicial)
- [ ] **Balanceador de carga** (si hay alta concurrencia)
- [ ] **Certificados SSL** (Let's Encrypt o comercial)
- [ ] **Backup automático** (diario, con retención de 30 días)

#### Servicios de Terceros

| Servicio | Costo Estimado | Uso |
|----------|----------------|-----|
| **Firebase** (FCM, Analytics, Crashlytics) | Gratis (hasta cierto límite) | Notificaciones push, monitoreo |
| **Google Play Console** | USD 25 (único pago) | Publicación Android |
| **Apple Developer Program** | USD 99/año | Publicación iOS |
| **Servicio de SMS** (Twilio, SendGrid) | USD 50-200/mes | Notificaciones SMS de respaldo |
| **Servicio de Email** (SendGrid, Mailgun) | USD 20-50/mes | Notificaciones por email |
| **Mapas** (Google Maps/Mapbox) | Gratis (hasta cierto uso) | Geolocalización |
| **Monitoreo** (Sentry, DataDog) | USD 50-200/mes | Errores, performance |
| **CDN** (Cloudflare) | Gratis/USD 20/mes | Performance, seguridad |

**Costo total estimado:** USD 200-500/mes (servicios) + costos de desarrollo

### 4.3. Recursos Adicionales Específicos

#### Para Notificaciones Críticas (ALTA PRIORIDAD)
- [ ] **Permisos especiales de Android:** Solicitar inclusión en lista blanca de batería
- [ ] **Notificaciones críticas de iOS:** Requiere aprobación especial de Apple
- [ ] **Documentación técnica** sobre bypass de modo silencio
- [ ] **Pruebas con múltiples fabricantes** (Samsung, Xiaomi, Huawei tienen customizaciones agresivas)

#### Para Integración con SMN
- [ ] **API del SMN** (si existe pública) o sistema de web scraping
- [ ] **Parser de alertas** (formato específico del SMN)
- [ ] **Actualización automática** cada cierto intervalo
- [ ] **Fallback manual** cuando no hay conexión
- [ ] **Lectura obligatoria de línea de tiempo y detalle zonal** (Sección 6.3 Doc A)
- [ ] **Soporte para alertas simultáneas** (no excluyentes)

#### Para Modo Offline
- [ ] **Base de datos local** (SQLite/Realm/WatermelonDB)
- [ ] **Sistema de sincronización** con resolución de conflictos
- [ ] **Indicadores visuales** de estado offline/online
- [ ] **Cola de operaciones pendientes**

#### Para Checklists con IA
- [ ] **Servicio de IA** (OpenAI, Google Vision, AWS Rekognition)
- [ ] **Detección de anomalías** en respuestas
- [ ] **Análisis de patrones** históricos
- [ ] **Alertas automáticas** de mantenimiento preventivo

#### Para RACUNS y Comunicaciones Degradadas
- [ ] **Interfaz con RACUNS** (VHF/UHF)
- [ ] **Soporte para Starlink S1/S2/S3**
- [ ] **Meshtastic/LoRa** como último recurso (nodo Palihue)
- [ ] **Prueba radial semanal** integrada al sistema
- [ ] **Agenda interna de contacto operativo** (AT-02 Sección 8)
- [ ] **Principio de redundancia:** ninguna comunicación crítica depende de un único medio

### 4.4. Recursos Legales y Administrativos
- [ ] **Términos y condiciones** de uso
- [ ] **Política de privacidad** (cumplimiento Ley 25.326 de Protección de Datos Personales)
- [ ] **Contratos de confidencialidad** (NDA) con desarrolladores
- [ ] **Registro de software** (Dirección Nacional del Derecho de Autor)
- [ ] **Aprobación del CDE** para uso institucional

---

## 5. CONSIDERACIONES ESPECIALES PARA LA UNS

### 5.1. Cumplimiento de Protocolos

El sistema debe implementar EXACTAMENTE los procedimientos definidos en:

**Anexo 07-A (Operativo):**
- [ ] Ventanas horarias de decisión (22:00, 10:00, 16:00)
- [ ] Ficha del Alerta (Anexo B) - campos obligatorios
- [ ] Niveles SMN con respuestas específicas (Sección 7)
- [ ] Protocolo de custodia escolar (Sección 8)
- [ ] Gestión de ACP (Avisos a Muy Corto Plazo) - Sección 7.5
- [ ] Regla de oro: decisión antes de hora de corte
- [ ] Confinamiento vs Evacuación (Sección 7.7)
- [ ] SAT-Temperaturas Extremas (Sección 7.6)
- [ ] Roles CDE con suplentes (Sección 9.1)
- [ ] Sala de Crisis: San Juan 670 / Anexo Campus Radio UNS
- [ ] Rutina de monitoreo (Sección 6.2)
- [ ] Umbrales regionales Patagonia (Sección 5)

**Anexo 07-C (Comunicación):**
- [ ] Plantillas M1-M8
- [ ] Cascada de mensajes institucional
- [ ] Redundancia de canales (mínimo 3)
- [ ] Lenguaje claro y accesibilidad (ISO 7010:2019)
- [ ] Gestión de rumores
- [ ] Vocería institucional (DCI)
- [ ] Formatos: sonoro, visual, textual
- [ ] Cuadro de Acción Rápida (Sección 7)
- [ ] Partes prolongados con horarios de actualización
- [ ] Comunicación con familias de afectados (reservada)
- [ ] Pruebas trimestrales de difusión masiva

**AT-01 (Infraestructura):**
- [ ] Checklists de mantenimiento preventivo (Sección 12)
- [ ] Vulnerabilidades por predio (Sección 3)
- [ ] Protocolos de corte de gas, ascensores, etc. (Sección 6)
- [ ] Reserva estratégica de agua (3L/persona/día)
- [ ] Matriz de responsabilidades por Dirección (Sección 4)
- [ ] Evaluación post-evento y Certificado de Aptitud de Ocupación
- [ ] Protección de patrimonio, laboratorios y archivos (Sección 7)
- [ ] Mantenimiento estacional pre-temporada (Sección 5)

**AT-02 (Comunicaciones):**
- [ ] Pruebas radiales semanales (Sección 7)
- [ ] Gestión de RACUNS (VHF/UHF)
- [ ] Starlink S1/S2/S3 (Sección 5)
- [ ] Meshtastic/LoRa Palihue (Sección 6)
- [ ] Agenda de contactos (Sección 8)
- [ ] Indicadores de disponibilidad (Sección 9)
- [ ] Principio de redundancia (Sección 3)
- [ ] Fuentes switching 13.8V 30A y UPS dedicadas (Sección 4.4)
- [ ] Reserva estratégica de antena (Sección 4.5)

### 5.2. Integraciones Recomendadas

| Sistema UNS | Tipo de Integración | Prioridad |
|-------------|---------------------|-----------|
| **SMN (Servicio Meteorológico)** | API/Web Scraping | 🔴 Alta |
| **Alerthor** | Coordinación interna CH1 | 🔴 Alta |
| **Moodle** | API para notificaciones académicas | 🟡 Media |
| **Sistema de Gestión de Personal** | Sincronización de usuarios | 🟡 Media |
| **Radio AM UNS** | Interfaz para emisión automática | 🟢 Baja |
| **Sistema de Control de Acceso** | Integración para evacuaciones | 🟢 Baja |
| **Megafonía de Predios** | Activación remota | 🟢 Baja |
| **FM UTN-FRBB** | Enlace dúplex para emergencias | 🟢 Baja |

### 5.3. Escalabilidad y Crecimiento

- [ ] Arquitectura modular para agregar nuevos módulos
- [ ] Soporte para múltiples sedes (Campus Palihue, Alem, Colón 80, Rondeau 29, Casa de la Cultura, Escuelas, Anexo Radio)
- [ ] Capacidad para 10,000+ usuarios simultáneos
- [ ] Sistema de multi-tenancy (para futuras expansiones)
- [ ] Preparado para nuevas categorías de emergencia (sanitaria, puntual, general, mayor)

---

## 6. PRESUPUESTO ESTIMADO

### 6.1. Desarrollo (One-time)

| Concepto | Horas | Costo Estimado (USD) |
|----------|-------|----------------------|
| Planificación y Diseño | 160 | 8,000 - 12,000 |
| Backend | 640 | 32,000 - 48,000 |
| App Móvil | 800 | 40,000 - 60,000 |
| Panel Web | 480 | 24,000 - 36,000 |
| Pruebas y QA | 320 | 16,000 - 24,000 |
| Despliegue | 80 | 4,000 - 6,000 |
| **TOTAL DESARROLLO** | **2,480** | **124,000 - 186,000** |

**Nota:** Estos son costos de mercado. Si lo desarrollas tú + equipo interno, el costo sería principalmente tiempo.

### 6.2. Operación Anual

| Concepto | Costo Anual (USD) |
|----------|-------------------|
| Infraestructura (servidores, BD, storage) | 3,000 - 6,000 |
| Servicios terceros (SMS, email, monitoreo) | 2,400 - 4,800 |
| Apple Developer + Google Play | 124 |
| Soporte y mantenimiento | 12,000 - 24,000 |
| Actualizaciones y mejoras | 6,000 - 12,000 |
| **TOTAL ANUAL** | **23,524 - 46,924** |

---

## 7. CRONOGRAMA GENERAL

| Fase | Duración | Fechas Estimadas |
|------|----------|------------------|
| **Fase 1:** Planificación y Diseño | 6 semanas | Octubre - Noviembre 2026 |
| **Fase 2:** Backend | 10 semanas | Diciembre 2026 - Febrero 2027 |
| **Fase 3:** App Móvil | 12 semanas | Enero - Marzo 2027 |
| **Fase 4:** Panel Web | 8 semanas | Febrero - Abril 2027 |
| **Fase 5:** Pruebas | 8 semanas | Abril - Mayo 2027 |
| **Fase 6:** Despliegue | 6 semanas | Junio - Julio 2027 |
| **Fase 7:** Soporte continuo | Ongoing | Agosto 2027 en adelante |

**Fecha estimada de lanzamiento:** **Julio/Agosto 2027** (antes de la próxima temporada de tormentas primavera-verano)

---

## 8. RECOMENDACIONES FINALES

### 8.1. Para Ti (Miguel)

**Aprovechando tus conocimientos en PHP/MySQL:**
1. **Backend con Laravel:** Es PHP moderno, tiene excelente documentación y comunidades activas
2. **Aprender React Native o Flutter:** Para desarrollo móvil multiplataforma
3. **Considera Antigravity:** Si es tu entorno preferido, úsalo para backend y panel web

**Habilidades a desarrollar/adquirir:**
- [ ] React Native o Flutter (1-2 meses de estudio)
- [ ] Firebase Cloud Messaging (2 semanas)
- [ ] Notificaciones críticas en Android/iOS (1 mes)
- [ ] WebSockets para tiempo real (2 semanas)
- [ ] UX/UI básico para apps móviles (1 mes)

### 8.2. Equipo Sugerido

**Opción A: Equipo Interno (más económico)**
- Tú: Project Manager + Backend Developer
- 1 Desarrollador Móvil (contratado o becario)
- 1 Desarrollador Frontend Web (contratado o becario)
- 1 Diseñador UX/UI (part-time, externo)
- 1 QA (part-time, puede ser estudiante avanzado)

**Opción B: Agencia de Desarrollo (más rápido, más caro)**
- Contratar una agencia especializada en apps móviles
- Tú como Product Owner (definición de requisitos)
- Mayor costo pero menor tiempo

### 8.3. Próximos Pasos Inmediatos

1. **Validación con stakeholders:** Presentar este plan al CDE y obtener aprobación
2. **Formación del equipo:** Definir quiénes participarán
3. **Setup de entorno:** Configurar repositorios, servidores de desarrollo
4. **Kickoff meeting:** Reunión inicial con todo el equipo
5. **Inicio de Fase 1:** Comenzar con diseño y planificación detallada

### 8.4. Riesgos y Mitigación

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Retrasos en aprobación de Apple | Media | Alto | Iniciar proceso temprano, tener app Android primero |
| Problemas con notificaciones críticas | Alta | Alto | Pruebas exhaustivas, múltiples fabricantes |
| Resistencia al cambio del personal | Media | Medio | Capacitación intensiva, champions por área |
| Cambios en protocolos | Baja | Medio | Arquitectura modular, fácil de actualizar |
| Presupuesto insuficiente | Media | Alto | MVP con funcionalidades críticas primero |
| Caída de comunicaciones convencionales | Media | Alto | RACUNS como medio principal; redundancia de canales |

---

## 9. PROPUESTA DE MVP (Producto Mínimo Viable)

Si el presupuesto o tiempo es limitado, recomiendo lanzar primero un **MVP** con las funcionalidades críticas:

### MVP (Fase 1 - 4-5 meses)
1. ✅ Sistema de alertas críticas (sonido + vibración + voz)
2. ✅ Gestión de niveles SMN (Verde a Rojo + ACP + Violeta)
3. ✅ Respuestas rápidas (4 tipos)
4. ✅ Panel básico de administración
5. ✅ Notificaciones push con override de silencio
6. ✅ Gestión de usuarios básica con roles
7. ✅ Dashboard de monitoreo en tiempo real
8. ✅ Ficha del Alerta digital (Anexo B)
9. ✅ Ventanas horarias de decisión automatizadas (22:00, 10:00, 16:00)
10. ✅ Plantillas de mensajes M1-M6

### Funcionalidades Post-MVP (Fase 2)
- Checklists digitales (AT-01 y AT-02)
- Comunicación interna completa con cascada
- Gestión de custodia escolar
- Integración con SMN automática
- Análisis con IA
- Modo offline completo
- Integración RACUNS / Alerthor
- Reportes y estadísticas avanzadas
- Gestión de rumores (M7)
- Partes prolongados (M8)
- Módulo Moodle de autoprotección

---

## 10. CONCLUSIÓN

Este proyecto es **totalmente viable** y se alinea perfectamente con los protocolos de la UNS. La combinación de:
- Tu experiencia técnica en PHP/MySQL
- Los protocolos bien definidos (Anexos 07-A, 07-C, AT-01, AT-02)
- Las tecnologías modernas disponibles (React Native, Firebase, etc.)
- La infraestructura existente (hosting, BD)

...crea las condiciones ideales para desarrollar una solución robusta y efectiva.

**Recomendación final:** Comenzar con el MVP para validar el concepto, obtener feedback real del CDE y usuarios, y luego iterar con las funcionalidades adicionales.

---

## ANEXO 1: Consideraciones Técnicas para Notificaciones Críticas

### Android
- Usar **High Priority FCM messages** con `priority: "high"`
- Solicitar permiso **ACCESS_NOTIFICATION_POLICY** para bypass de DND
- Usar **AlarmManager** con `setExactAndAllowWhileIdle` para alarmas críticas
- Excluir app de **Battery Optimization** (Doze mode)
- Usar **WakeLock** para activar pantalla
- Reproducir audio con **AudioManager.STREAM_ALARM** (volumen máximo)
- Solicitar permiso **SCHEDULE_EXACT_ALARM** (Android 12+)
- Implementar **Foreground Service** para mantener proceso activo

### iOS
- Solicitar aprobación para **Critical Alerts** (requiere documentación de Apple)
- Usar **UNNotificationSound.defaultCriticalSound**
- Configurar **Time Sensitive Notifications** (iOS 15+)
- Solicitar permiso especial en App Store Connect
- Implementar **PushKit** para notificaciones VoIP como fallback

### Web (PWA)
- Usar **Notification API** con `requireInteraction: true`
- Implementar **Service Worker** para notificaciones en background
- Usar **Web Audio API** para reproducción de sonido
- Implementar **Wake Lock API** cuando esté disponible
- Registrar **Push API** subscription para notificaciones del servidor

---

## ANEXO 2: Mapeo de Protocolos a Funcionalidades de la App

| Protocolo UNS | Sección | Funcionalidad en la App |
|---------------|---------|------------------------|
| Doc A - Sección 6 | Ventanas horarias | Motor de decisiones automático (22:00, 10:00, 16:00) |
| Doc A - Sección 7.1 | Nivel Amarillo | Alerta preventiva + suspensión aire libre |
| Doc A - Sección 7.2 | Nivel Naranja | Suspensión turno + confinamiento |
| Doc A - Sección 7.3 | Nivel Rojo | Suspensión total + CDE pleno |
| Doc A - Sección 7.4 | Advertencia violeta | Evaluación transporte |
| Doc A - Sección 7.5 | ACP | Alarma crítica inmediata + confinamiento |
| Doc A - Sección 7.6 | Temperaturas extremas | Virtualidad o medidas protección |
| Doc A - Sección 7.7 | Resguardo vs Evacuación | Lógica de decisión |
| Doc A - Sección 8 | Custodia escolar | Módulo de retiro autorizado con DNI |
| Doc A - Anexo B | Ficha del Alerta | Formulario digital obligatorio |
| Doc A - Anexo C | Registro de retiro | Registro digital con firma |
| Doc C - Sección 4 | Cascada de mensajes | Sistema de difusión en cascada |
| Doc C - Sección 5 | Arquitectura mensajes | Editor con plantillas M1-M8 |
| Doc C - Anexo C | Plantillas M1-M8 | Mensajes predefinidos editables |
| AT-01 - Sección 3 | Vulnerabilidades | Mapa interactivo por predio |
| AT-01 - Sección 5 | Mantenimiento preventivo | Checklists digitales de infraestructura |
| AT-01 - Sección 6 | Protocolos emergencia | Flujos de trabajo automatizados |
| AT-01 - Sección 11 | Evaluación post-evento | Módulo de inspección y certificación |
| AT-01 - Sección 12 | Checklist mantenimiento | Registro sistemático digital |
| AT-02 - Sección 4 | Mantenimiento RACUNS | Checklists de comunicaciones |
| AT-02 - Sección 5 | Starlink | Registro de pruebas S1/S2/S3 |
| AT-02 - Sección 7 | Pruebas | Calendario y seguimiento de pruebas |
| AT-02 - Sección 8 | Agenda contactos | Directorio operativo restringido |
| AT-02 - Sección 9 | Indicadores | Dashboard de KPIs |

---

## ANEXO 3: Estructura de Base de Datos Sugerida (MySQL)
