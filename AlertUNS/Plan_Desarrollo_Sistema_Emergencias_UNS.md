# PLAN DE DESARROLLO: Sistema de Gestión de Emergencias UNS
## App tipo BomberBOT adaptada a la Universidad Nacional del Sur

**Elaborado por:** Comité de Dirección de Emergencia

**Fecha:** 30 de septiembre de 2026

**Basado en:** BomberBOT + Protocolos PECl-UNS (Documentos A, B, AT-01, AT-02)

---

## 1. ANÁLISIS DEL PROYECTO

### 1.1. Características principales a implementar

**Funcionalidades críticas (basadas en BomberBOT y protocolos UNS):**

| Módulo | Descripción | Prioridad |
|--------|-------------|-----------|
| **Sistema de Alertas Críticas** | Notificaciones que suenan, vibran y hablan incluso con app cerrada/en silencio | 🔴 Alta |
| **Gestión de Niveles SMN** | Verde, Amarillo, Naranja, Rojo, ACP, Violeta | 🔴 Alta |
| **Respuestas Rápidas** | "En camino", "Retrasado", "No disponible", "Recibido" | 🔴 Alta |
| **Panel de Administración Web** | Dashboard, gestión de personal, estadísticas | 🔴 Alta |
| **Comunicación Interna** | Mensajería segregada por roles/departamentos | 🟡 Media |
| **Checklists Digitales** | Mantenimiento preventivo, infraestructura, comunicaciones | 🟡 Media |
| **Gestión de Custodia Escolar** | Registro de retiro de menores (Escuelas Preuniversitarias) | 🟡 Media |
| **Monitoreo en Tiempo Real** | Estado del personal, ubicación, disponibilidad | 🟡 Media |
| **Funcionalidad Offline** | Sincronización cuando hay conexión | 🟡 Media |
| **Integración con RACUNS** | Interfaz con sistema de radiocomunicaciones | 🟢 Baja |

### 1.2. Actores del sistema

- **Administrador CDE** (Comité de Dirección de Emergencia)
- **Oficina de Recepción de Avisos de Emergencia** (ORAE)
- **Mayordomos de Edificios**
- **Directores/Decanos**
- **Docentes y Nodocentes**
- **Estudiantes**
- **Familias** (Escuelas Preuniversitarias)
- **Personal de Mantenimiento**
- **Telecomunicaciones**

---

## 2. ARQUITECTURA TÉCNICA RECOMENDADA

### 2.1. Stack Tecnológico sugerido

| Componente | Tecnología |
|------------|------------|
| **App Móvil** | **React Native** o **Flutter** |
| **Backend API** | **Laravel (PHP)** o **Node.js + Express** |
| **Panel Web** | **React.js** o **Vue.js** | 
| **Notificaciones** | **Firebase Cloud Messaging (FCM)** + **APNs** | 
| **Tiempo Real** | **WebSockets** (Laravel Reverb / Socket.io) | 
| **Almacenamiento** | **AWS S3** o similar | 
| **Autenticación** | **JWT + OAuth2** | 

### 2.2. Diagrama de Arquitectura
```text
┌──────────────────────────────────────────────────────────────────┐
│                             CLIENTES                             │
│ ┌──────────────┐      ┌──────────────┐      ┌──────────────────┐ │
│ │ App Android  │      │   App iOS    │      │ Panel Web Admin  │ │
│ │  (React N.)  │      │  (React N.)  │      │   (React/Vue)    │ │
│ └──────┬───────┘      └──────┬───────┘      └────────┬─────────┘ │
└────────┼─────────────────────┼───────────────────────┼───────────┘
         │                     │                       │
         └─────────────────────┼───────────────────────┘
                               │
                               ▼
                ┌──────────────────────────────┐
                │    API REST + WebSockets     │
                │    (Laravel 11 + Reverb)     │
                └──────────────┬───────────────┘
                               │
         ┌─────────────────────┼───────────────────────┐
         │                     │                       │
 ┌───────▼────────┐    ┌───────▼────────┐      ┌───────▼───────┐
 │     MySQL      │    │     Redis      │      │ Firebase FCM  │
 │  (Base Datos)  │    │  (Cache/Queue) │      │    + APNs     │
 └────────────────┘    └────────────────┘      └───────────────┘
                               ▲
                               │
                ┌──────────────┴───────────────┐
                │  Scraping SMN (Python Cron)  │
                │  Integra RACUNS / Alerthor   │
                └──────────────────────────────┘
```

### 2.3. Flujo de Alerta Crítica

```text
┌───────────┐      ┌─────────────────────┐      ┌───────────────┐
│  SMN SAT  ├─────►│ Scraping Cron 5 min ├─────►│ Laravel Queue │
└───────────┘      └─────────────────────┘      └───────┬───────┘
                                                        │
         ┌───────────────────┬──────────────────────────┼──────────────────────────┐
         │                   │                          │                          │
 ┌───────▼───────┐   ┌───────▼───────┐          ┌───────▼───────┐          ┌───────▼───────┐
 │ Firebase FCM  │   │   WebSocket   │          │  SMS Gateway  │          │  Alerthor CH1 │
 │ priority:high │   │(Actualización │          │  (Personal    │          │   (RACUNS en  │
 └───────┬───────┘   │ en t. real)   │          │   crítico)    │          │  Naranja/Rojo)│
         │           └───────┬───────┘          └───────┬───────┘          └───────────────┘
         ▼                   ▼                          ▼
 ┌───────────────┐   ┌───────────────┐          ┌───────────────┐
 │   App móvil   │   │   Panel Web   │          │   Respaldo    │
 │(Alarma + voz  │   │     Admin     │          │               │
 │ + vibración)  │   │               │          │               │
 └───────────────┘   └───────────────┘          └───────────────┘
```

---

## 3. PLAN DE TRABAJO DETALLADO

### FASE 1: PLANIFICACIÓN Y DISEÑO (4-6 semanas)

#### Semana 1-2: Análisis y Diseño
- [ ] Reuniones con stakeholders (CDE, DCI, Telecomunicaciones, SHST, Infraestructura)
- [ ] Definición detallada de requisitos funcionales y no funcionales
- [ ] Mapeo de protocolos UNS a casos de uso de la app
- [ ] Diseño de wireframes y prototipos (Figma/Adobe XD)
- [ ] Arquitectura de base de datos detallada (Ver Anexo 3)
- [ ] Diseño de API (endpoints, autenticación, roles)
- [ ] Diseño de cascada de mensajes (DCI → Decanos → Mayordomías)

#### Semana 3-4: Diseño Técnico
- [ ] Diagrama de flujo de emergencias (Anexo A del Documento A)
- [ ] Diseño del sistema de notificaciones críticas (Android + iOS)
- [ ] Definición de 14 roles y permisos (CDE, DCI, Mayordomo, etc.)
- [ ] Plan de seguridad y cifrado (Ley 25.326 de Protección de Datos)
- [ ] Plan de pruebas (incluye pruebas radiales semanales AT-02)
- [ ] Diseño de plantillas M1-M8 (Anexo C del Documento C)

#### Semana 5-6: Configuración de Entorno
- [ ] Configuración de servidores de desarrollo (tu hosting)
- [ ] Setup de Firebase (FCM, Analytics, Crashlytics)
- [ ] Configuración de CI/CD (GitHub Actions o GitLab CI)
- [ ] Repositorios Git (monorepo o múltiples)
- [ ] Ambientes: dev, staging, producción
- [ ] Setup de Laravel con Reverb para WebSockets

**Entregable:** Documentación técnica completa + prototipos funcionales

---

### FASE 2: DESARROLLO DEL BACKEND (8-10 semanas)

#### Semana 7-10: Core Backend (Laravel 11)

**Módulo 1: Autenticación y Usuarios**
- [ ] Sistema de registro/login con roles UNS
- [ ] Gestión de roles y permisos (14 tipos de usuario)
- [ ] Perfiles de usuario (con foto, departamento, teléfono alternativo, suplente)
- [ ] Integración opcional con LDAP/SSO de la UNS
- [ ] Gestión de sesiones y tokens JWT
- [ ] Registro de suplentes por cada rol CDE (Sección 9.1)

**Módulo 2: Sistema de Alertas SMN**
- [ ] Scraping automático del SAT SMN (web + app + línea de tiempo)
- [ ] Parser de niveles: Verde/Amarillo/Naranja/Rojo/ACP/Violeta
- [ ] Lectura obligatoria de línea de tiempo (72 horas en 4 rangos de 6h)
- [ ] Detección de alertas simultáneas (no son excluyentes)
- [ ] Motor de decisiones basado en ventanas horarias (22:00, 10:00, 16:00)
- [ ] Umbrales Patagonia (Anaya 2020) - Tabla Sección 5
- [ ] Gestión de ACP (Aviso a Muy Corto Plazo, vigencia 1-3 horas)
- [ ] SAT-Temperaturas Extremas (sin línea de tiempo)
- [ ] Ficha del Alerta digital (Anexo B del Documento A)
- [ ] Historial de alertas y eventos simultáneos

**Módulo 3: Notificaciones Críticas**
- [ ] Integración FCM (Android) con priority: high
- [ ] Integración APNs (iOS) con Critical Alerts
- [ ] Sistema de notificaciones de alta prioridad
- [ ] Alarma con sonido + vibración + voz (TTS)
- [ ] Override de modo silencio (permisos especiales)
- [ ] Sistema de confirmación de recepción (4 tipos de respuesta)
- [ ] Redundancia: mínimo 3 canales simultáneos (Sección 10 Doc A)
- [ ] Cola de notificaciones con Laravel Queue

**Módulo 4: Gestión de Emergencias**
- [ ] Creación de emergencias (manual y automática desde SMN)
- [ ] Tipos: puntual, general, climática, mayor, sanitaria, esperable
- [ ] Call-outs selectivos (por departamento, edificio, rol)
- [ ] Sistema de respuestas rápidas (4 tipos)
- [ ] Monitoreo en tiempo real vía WebSockets
- [ ] Cancelación de emergencias (M6 - Cese Verde)
- [ ] Gestión de ACP: cese inmediato + confinamiento interno
- [ ] Escucha permanente Alerthor CH1 en Naranja/Rojo
- [ ] Confinamiento vs Evacuación (Sección 7.7)

#### Semana 11-14: Módulos Complementarios

**Módulo 5: Checklists Digitales**
- [ ] Editor de checklists jerárquico: unidad → contenedor → ítem
- [ ] Checklist AT-01 Mantenimiento Preventivo Infraestructura (Sección 12)
- [ ] Checklist AT-02 Mantenimiento Comunicaciones (Sección 7)
- [ ] Funcionalidad offline (sync automático)
- [ ] Análisis con IA (detección de anomalías)
- [ ] Exportación a PDF
- [ ] Historial y estadísticas
- [ ] Registro de pruebas radiales semanales
- [ ] Registro de pruebas trimestrales Starlink S1/S2/S3
- [ ] Registro de pruebas Meshtastic Palihue semestrales

**Módulo 6: Comunicación Interna (Documento C)**
- [ ] Editor de mensajes con plantillas M1-M8
- [ ] Cascada de mensajes institucional
- [ ] Anuncios urgentes vs normales
- [ ] Chat grupal por emergencia
- [ ] Confirmación de recepción por cada nivel
- [ ] Gestión de rumores (M7)
- [ ] Partes prolongados (M8) con horarios de actualización
- [ ] Versiones accesibles: sonora (TTS), visual (alto contraste), textual
- [ ] Registro de difusión (Anexo B del Documento C)

**Módulo 7: Gestión de Custodia Escolar (Anexo C Doc A)**
- [ ] Registro de retiro autorizado con campos:
    - Fecha y hora
    - Nombre alumno
    - Nombre adulto autorizado
    - DNI adulto
    - Vínculo
    - Firma digital
    - Observaciones
- [ ] Verificación contra listado de adultos autorizados
- [ ] Reportes a Oficina de Recepción de Avisos
- [ ] Custodia extendida (corte de transporte)
- [ ] M5 - Plantilla de mensaje a familias
- [ ] Prohibición de retiro individual sin tutor acreditado

**Módulo 8: Panel de Administración**
- [ ] Dashboard principal con estado actual
- [ ] Gestión de personal y suplentes
- [ ] Estadísticas y reportes (tiempos de respuesta, cobertura)
- [ ] Gestión de edificios y sectores vulnerables
- [ ] Mapa de vulnerabilidades por predio (Sección 3.1 AT-01)
- [ ] Logs de auditoría
- [ ] Sala de Crisis: SJ670 / Anexo Radio UNS
- [ ] Indicadores AT-02 (Sección 9):
    - % pruebas radiales semanales (100%)
    - % fallas subsanadas en 24h (≥95%)
    - % cobertura áreas críticas (100%)
    - Autonomía nodos (≥24h)

**Entregable:** API funcional con documentación (Swagger/OpenAPI)

---

### FASE 3: DESARROLLO DE APP MÓVIL (10-12 semanas)

#### Semana 15-26: App Android/iOS (React Native)

**Sprint 1: Setup y Autenticación**
- [ ] Setup de React Native con Expo
- [ ] Pantallas de login/registro
- [ ] Selección de rol (14 tipos)
- [ ] Código de invitación UNS (6 dígitos)
- [ ] Configuración de perfil (con suplente)
- [ ] Login con LDAP UNS (opcional)

**Sprint 2: Dashboard y Navegación**
- [ ] Dashboard principal con nivel SMN actual
- [ ] Navegación por módulos (bottom tabs)
- [ ] Banner de alerta activa
- [ ] Indicador de conexión (online/offline)
- [ ] Estado de Alerthor CH1

**Sprint 3: Sistema de Alertas (CRÍTICO - Anexo técnico)**
- [ ] Recepción de alertas FCM en background
- [ ] Alarma crítica (sonido + vibración + voz TTS)
- [ ] Pantalla full-screen con detalles SMN
- [ ] Lectura de línea de tiempo y detalle zonal
- [ ] Eventos simultáneos visibles
- [ ] Botones de respuesta rápida (4 tipos)
- [ ] Permisos especiales (batería, notificaciones críticas)
- [ ] Funcionamiento con app cerrada
- [ ] Soporte para 6 niveles SMN
- [ ] Diferenciación por tipo de emergencia

**Sprint 4: Respuestas y Monitoreo**
- [ ] Sistema de respuestas (En camino / Retrasado / No disponible / Recibido)
- [ ] Estado en tiempo real del personal (WebSocket)
- [ ] Mapa de ubicación (opcional, con privacidad)
- [ ] Notificaciones de cancelación (M6)
- [ ] Confirmación de recepción con timestamp

**Sprint 5: Checklists**
- [ ] Visualización de checklists asignados (AT-01, AT-02)
- [ ] Formulario de inspección con ítems jerárquicos
- [ ] Modo offline con SQLite local
- [ ] Sincronización automática al recuperar conexión
- [ ] Historial personal
- [ ] Fotos y evidencias
- [ ] Firma digital

**Sprint 6: Mensajería y Comunicación**
- [ ] Chat interno por departamentos
- [ ] Mensajes M1-M8 (plantillas)
- [ ] Mensajes urgentes vs normales
- [ ] Historial de comunicaciones
- [ ] Notificaciones segregadas por rol
- [ ] Versión sonora (TTS) de mensajes críticos

**Sprint 7: Custodia Escolar**
- [ ] Vista para personal docente/directivo
- [ ] Formulario de retiro con validación de DNI
- [ ] Búsqueda en listado de adultos autorizados
- [ ] Firma digital en pantalla
- [ ] Reportes automáticos a Oficina de Recepción
- [ ] Plantilla M5 para familias

**Sprint 8: Modo de Emergencia y Configuración**
- [ ] Modo emergencia (contactos rápidos, rutas seguras)
- [ ] Mapa de zonas seguras de confinamiento por predio
- [ ] Configuración de notificaciones
- [ ] Datos personales y suplente
- [ ] Historial de actividad
- [ ] Soporte y ayuda
- [ ] Módulo Moodle de autoprotección (enlace)

**Entregable:** App móvil funcional para Android e iOS

---

### FASE 4: DESARROLLO WEB - PANEL DE ADMINISTRACIÓN (6-8 semanas)

#### Semana 27-34: Panel Web (React + Laravel Blade)

**Módulo 1: Dashboard**
- [ ] Vista general del estado SMN actual
- [ ] Alertas activas con nivel y vigencia
- [ ] Personal disponible en tiempo real
- [ ] Estadísticas rápidas
- [ ] Estado de RACUNS y comunicaciones (AT-02)
- [ ] Estado de infraestructura crítica (AT-01)

**Módulo 2: Gestión de Emergencias**
- [ ] Creación manual de emergencias
- [ ] Monitoreo en tiempo real (mapa + lista)
- [ ] Historial de emergencias
- [ ] Exportación de reportes
- [ ] Cancelación de emergencias (M6)
- [ ] Ficha del Alerta digital (Anexo B)
- [ ] Motor de ventanas horarias (22:00, 10:00, 16:00)
- [ ] Integración con SMN (scraping automático)
- [ ] Gestión de ACP (confinamiento inmediato)

**Módulo 3: Gestión de Personal**
- [ ] CRUD de usuarios con 14 roles
- [ ] Asignación de suplentes por cada rol CDE
- [ ] Gestión de departamentos y edificios
- [ ] Importación masiva (CSV/Excel)
- [ ] Desactivación de cuentas
- [ ] Roles CDE completos (Sección 9.1):
    - Rectorado (Daniel Vega / Andrea S. Castellano)
    - Secretaría General de Planificación
    - DCI (Marcelo Tedesco - Vocería)
    - Servicios Técnicos (Walter R. Cravero)
    - Infraestructura (Gonzalo J. Gilardi)
    - Bienestar Universitario (Ana Paula Murray)
    - Secretaría Académica (Mariano E. Garrido)
    - SHST (Guillermo E. Dominella)
    - Medicina del Trabajo (Jorge Ignacio Frizza)
    - Dirección de Sanidad (Walter Villalba)

**Módulo 4: Gestión de Edificios (AT-01)**
- [ ] Mapeo de predios UNS:
    - Campus Palihue (pabellones centrales de hormigón)
    - Complejo Alem / SJ670 (7 pisos, cortinas metálicas)
    - Colón 80 / Rondeau 29 / Casa de la Cultura (patrimonio)
    - Escuelas Preuniversitarias
    - Anexo Radio AM UNS
- [ ] Asignación de mayordomos
- [ ] Zonas de confinamiento por predio
- [ ] Vulnerabilidades por predio (Sección 3.1)
- [ ] Sectores vulnerables internos
- [ ] Checklists por edificio

**Módulo 5: Checklists y Mantenimiento**
- [ ] Editor visual de checklists
- [ ] Asignación de tareas
- [ ] Análisis de resultados
- [ ] Detección de anomalías (IA)
- [ ] Reportes en PDF
- [ ] Checklist AT-01 (Sección 12):
    - Pluviales y bombas de achique
    - Cubiertas y desagües
    - Arbolado
    - Grupos electrógenos (ATS)
    - UPS y bancos de baterías
    - Red de gas
    - Ascensores
    - Freezers críticos
    - Flota institucional
    - Evaluación estructural
    - Reserva de agua
- [ ] Checklist AT-02:
    - Prueba radial semanal
    - Caída de repetidor
    - Starlink S1/S2/S3
    - Meshtastic Palihue
    - Conmutación energética

**Módulo 6: Comunicaciones (Documento C)**
- [ ] Gestión de mensajes con plantillas M1-M8
- [ ] Editor de mensajes con formato
- [ ] Historial de comunicaciones
- [ ] Estadísticas de recepción
- [ ] Gestión de rumores (M7)
- [ ] Partes prolongados (M8)
- [ ] Registro de difusión (Anexo B Doc C)
- [ ] Capas de difusión:
    - Capa 1: digital (web, Moodle, correo, redes)
    - Capa 2: radial (AM UNS → FM UTN-FRBB dúplex)
    - Capa 3: predios (megafonía, pantallas, alarmas)
    - Capa 4: telefonía (SMS masivo)
    - Capa 5: presencial (mayordomías, brigadas)

**Módulo 7: Reportes y Estadísticas**
- [ ] Dashboard de métricas
- [ ] Reportes por período
- [ ] Tiempos de respuesta
- [ ] Análisis de efectividad
- [ ] Exportación de datos
- [ ] Informe post-activación (≤72 horas)
- [ ] Indicadores AT-02 (Sección 9):
    - % pruebas radiales (100%)
    - % fallas subsanadas 24h (≥95%)
    - % cobertura crítica (100%)
    - Autonomía nodos (≥24h)

**Módulo 8: Configuración**
- [ ] Parámetros del sistema
- [ ] Integración con SMN (cron scraping)
- [ ] Gestión de notificaciones
- [ ] Backups y logs
- [ ] Permisos globales
- [ ] Ventanas horarias configurables
- [ ] Umbrales SMN actualizables
- [ ] Control de versiones del protocolo (PDCA)

**Entregable:** Panel web funcional y responsivo

---

### FASE 5: INTEGRACIÓN Y PRUEBAS (6-8 semanas)

#### Semana 35-42: Pruebas Integrales

**Pruebas Funcionales**
- [ ] Pruebas unitarias (PHPUnit / Laravel)
- [ ] Pruebas de integración
- [ ] Pruebas E2E (Cypress / Detox)
- [ ] Pruebas de carga (10,000+ usuarios simultáneos)
- [ ] Pruebas de seguridad (OWASP Top 10)

**Pruebas Específicas**
- [ ] Pruebas de notificaciones críticas (diferentes dispositivos/fabricantes)
- [ ] Pruebas de modo offline (SQLite sync)
- [ ] Pruebas de concurrencia (WebSockets)
- [ ] Pruebas de recuperación ante fallos
- [ ] Pruebas de compatibilidad (Android 8+, iOS 13+)
- [ ] Pruebas de cascada de mensajes (M1-M8)
- [ ] Pruebas de ventanas horarias (22:00, 10:00, 16:00)
- [ ] Pruebas de custodia escolar (DNI validation)
- [ ] Pruebas de checklists AT-01 y AT-02
- [ ] Pruebas de scraping SMN (72 horas, eventos simultáneos)
- [ ] Pruebas de ACP (vigencia 1-3 horas)

**Pruebas con Usuarios**
- [ ] Pruebas con CDE
- [ ] Pruebas con mayordomos
- [ ] Pruebas con docentes
- [ ] Pruebas con personal de mantenimiento
- [ ] Pruebas con estudiantes (beta cerrada)
- [ ] Pruebas con Telecomunicaciones (RACUNS)
- [ ] Pruebas con Escuelas Preuniversitarias
- [ ] Simulacros trimestrales de mesa
- [ ] Simulacro integral anual

#### Semana 43-44: Correcciones y Optimización
- [ ] Corrección de bugs
- [ ] Optimización de performance
- [ ] Mejoras de UX/UI basadas en feedback
- [ ] Documentación de usuario
- [ ] Manuales de capacitación
- [ ] Módulo Moodle de autoprotección

**Entregable:** Sistema completo y probado

---

### FASE 6: DESPLIEGUE Y LANZAMIENTO (4-6 semanas)

#### Semana 45-47: Preparación para Producción
- [ ] Configuración de servidores de producción (tu hosting)
- [ ] Migración de datos
- [ ] Certificados SSL y seguridad
- [ ] Backup y disaster recovery
- [ ] Monitoreo y alertas (Grafana/Prometheus)
- [ ] Configuración de Redis para colas
- [ ] Setup de Laravel Reverb

#### Semana 48-49: Publicación
- [ ] Publicación en Google Play Store
- [ ] Publicación en Apple App Store (con aprobación Critical Alerts)
- [ ] Despliegue de panel web
- [ ] Configuración de dominios
- [ ] DNS y CDN (Cloudflare)
- [ ] Configuración de Firebase en producción

#### Semana 50-51: Capacitación y Rollout
- [ ] Capacitación a administradores (CDE)
- [ ] Capacitación a mayordomos
- [ ] Capacitación a personal de seguridad
- [ ] Capacitación a Telecomunicaciones
- [ ] Capacitación a DCI (Vocería)
- [ ] Material de capacitación (videos, manuales)
- [ ] Módulo Moodle de autoprotección
- [ ] Soporte técnico inicial
- [ ] Prueba trimestral de difusión masiva

**Entregable:** Sistema en producción y operativo

---

### FASE 7: SOPORTE Y MEJORA CONTINUA (Ongoing)

- [ ] Monitoreo 24/7
- [ ] Soporte técnico nivel 1 y 2
- [ ] Actualizaciones de seguridad
- [ ] Nuevas funcionalidades (roadmap)
- [ ] Mejora continua basada en feedback (ciclo PDCA)
- [ ] Reportes mensuales de uso
- [ ] Revisión anual del protocolo
- [ ] Informe post-activación ≤72 horas
- [ ] Control de versiones del software
- [ ] Interpretación divergente: consulta a Base Central SJ670 / SHST

---

## 4. RECURSOS NECESARIOS

### 4.1. Recursos Humanos

| Rol | Cantidad | Dedicación | Descripción |
|-----|----------|-------------|-------------|
| **Project Manager** | 1 | Part-time | Coordinación general, cronograma, stakeholders |
| **Desarrollador Backend Senior (Laravel)** | 1 | Full-time | API, BD, scraping SMN, colas |
| **Desarrollador Frontend Web** | 1 | Full-time | Panel de administración React |
| **Desarrollador Móvil** | 1-2 | Full-time | Apps Android/iOS (React Native) |
| **Diseñador UX/UI** | 1 | Part-time | Interfaces, pictogramas ISO 7010:2019 |
| **QA Engineer** | 1 | Part-time | Pruebas, automatización |
| **DevOps** | 1 | Part-time | Infraestructura, CI/CD |
| **Especialista en Seguridad** | 1 | Consultoría | Auditorías, Ley 25.326 |
| **Scraping Developer (Python)** | 1 | Part-time | Integración SMN |

**Nota:** Tu rol podría ser Project Manager + Backend Developer Laravel, aprovechando tus conocimientos.

### 4.2. Recursos Tecnológicos

#### Infraestructura (ya dispones de hosting y BD)
- [ ] **Servidor de producción** (mínimo 4 vCPUs, 8GB RAM, 100GB SSD)
- [ ] **Servidor de staging** (similar a producción)
- [ ] **Base de datos MySQL** (ya disponible)
- [ ] **Redis** para caché y colas
- [ ] **Almacenamiento de archivos** (S3 o local, ~500GB inicial)
- [ ] **Balanceador de carga** (si hay alta concurrencia)
- [ ] **Certificados SSL** (Let's Encrypt o comercial)
- [ ] **Backup automático** (diario, con retención de 30 días)
- [ ] **UPS y respaldo energético** (coordinado con AT-01)

#### Servicios de Terceros

| Servicio | Costo Estimado | Uso |
|----------|----------------|-----|
| **Firebase** (FCM, Analytics, Crashlytics) | Gratis (hasta límite) | Notificaciones push, monitoreo |
| **Google Play Console** | USD 25 (único) | Publicación Android |
| **Apple Developer Program** | USD 99/año | Publicación iOS + Critical Alerts |
| **Servicio de SMS** (Twilio) | USD 50-200/mes | Notificaciones SMS respaldo |
| **Servicio de Email** (SendGrid) | USD 20-50/mes | Notificaciones email |
| **Mapas** (Google Maps/Mapbox) | Gratis (hasta límite) | Geolocalización |
| **Monitoreo** (Sentry) | USD 50-200/mes | Errores, performance |
| **CDN** (Cloudflare) | Gratis/USD 20/mes | Performance, seguridad |
| **TTS** (Google Cloud TTS) | USD 0-50/mes | Voz en alertas |

**Costo total estimado:** USD 200-500/mes (servicios)

### 4.3. Recursos Adicionales Específicos

#### Para Notificaciones Críticas (ALTA PRIORIDAD)
- [ ] **Permisos especiales de Android:** Solicitud de inclusión en lista blanca de batería
- [ ] **Notificaciones críticas de iOS:** Aprobación especial de Apple (requiere documentación)
- [ ] **Documentación técnica** sobre bypass de modo silencio
- [ ] **Pruebas con múltiples fabricantes** (Samsung, Xiaomi, Huawei tienen customizaciones agresivas)
- [ ] **Foreground Service** para mantener proceso activo en Android
- [ ] **PushKit VoIP** como fallback en iOS

#### Para Integración con SMN
- [ ] **Web scraping** del sitio oficial SMN
- [ ] **Parser de alertas** (formato específico SMN)
- [ ] **Actualización automática** cada 5 minutos (cron job)
- [ ] **Fallback manual** cuando no hay conexión
- [ ] **Lectura obligatoria de línea de tiempo y detalle zonal** (Sección 6.3 Doc A)
- [ ] **Soporte para alertas simultáneas** (no son excluyentes)
- [ ] **Umbrales Patagonia** (Anaya 2020)

#### Para Modo Offline
- [ ] **SQLite local** (WatermelonDB o Realm)
- [ ] **Sistema de sincronización** con resolución de conflictos
- [ ] **Indicadores visuales** de estado offline/online
- [ ] **Cola de operaciones pendientes**
- [ ] **Firma digital offline** (canvas)

#### Para Checklists con IA
- [ ] **Servicio de IA** (OpenAI / Google Vision)
- [ ] **Detección de anomalías** en respuestas
- [ ] **Análisis de patrones** históricos
- [ ] **Alertas automáticas** de mantenimiento preventivo

#### Para RACUNS y Comunicaciones Degradadas
- [ ] **Interfaz con Alerthor** (CH1 escucha permanente)
- [ ] **Soporte para RACUNS** (VHF/UHF)
- [ ] **Soporte para Starlink S1/S2/S3**
- [ ] **Meshtastic/LoRa** nodo Palihue
- [ ] **Prueba radial semanal** integrada al sistema
- [ ] **Agenda interna de contacto operativo** (AT-02 Sección 8)

### 4.4. Recursos Legales y Administrativos
- [ ] **Términos y condiciones** de uso
- [ ] **Política de privacidad** (Ley 25.326 de Protección de Datos Personales)
- [ ] **Contratos de confidencialidad** (NDA) con desarrolladores
- [ ] **Registro de software** (Dirección Nacional del Derecho de Autor)
- [ ] **Aprobación del CDE** para uso institucional
- [ ] **Cumplimiento ISO 22320** (gestión de emergencias)
- [ ] **Cumplimiento ISO 22301** (continuidad operativa)
- [ ] **Cumplimiento ISO 7010:2019** (símbolos de seguridad)
- [ ] **Cumplimiento Ley 27.287** (SINAGIR)

---

## 5. CONSIDERACIONES ESPECIALES PARA LA UNS

### 5.1. Cumplimiento de Protocolos

El sistema debe implementar EXACTAMENTE los procedimientos definidos en:

**Anexo 07-A (Operativo):**
- [ ] Ventanas horarias de decisión (22:00, 10:00, 16:00)
- [ ] Ficha del Alerta (Anexo B) - todos los campos obligatorios
- [ ] Niveles SMN con respuestas específicas (Sección 7)
- [ ] Protocolo de custodia escolar (Sección 8)
- [ ] Gestión de ACP (Sección 7.5, vigencia 1-3 horas)
- [ ] Regla de oro: decisión antes de hora de corte
- [ ] Confinamiento vs Evacuación (Sección 7.7)
- [ ] SAT-Temperaturas Extremas (Sección 7.6)
- [ ] Roles CDE con suplentes (Sección 9.1)
- [ ] Sala de Crisis: SJ670 primaria / Anexo Radio alternativa
- [ ] Rutina de monitoreo 06:00, 10:00, 16:00, 18:00, 19:00, 22:00
- [ ] Umbrales Patagonia (Sección 5)
- [ ] Alertas simultáneas no excluyentes (Sección 4.3)
- [ ] Lectura obligatoria de línea de tiempo (Sección 6.3)

**Anexo 07-C (Comunicación):**
- [ ] Plantillas M1-M8 completas
- [ ] Cascada de mensajes institucional
- [ ] Redundancia: mínimo 3 canales
- [ ] Lenguaje claro y accesibilidad (ISO 7010:2019)
- [ ] Gestión de rumores (M7)
- [ ] Vocería institucional (DCI)
- [ ] Formatos: sonoro, visual, textual
- [ ] Cuadro de Acción Rápida (Sección 7)
- [ ] Partes prolongados con horarios de actualización (M8)
- [ ] Comunicación con familias (reservada)
- [ ] Pruebas trimestrales de difusión masiva
- [ ] Capas de difusión (Anexo B)

**AT-01 (Infraestructura):**
- [ ] Checklists de mantenimiento preventivo (Sección 12)
- [ ] Vulnerabilidades por predio (Sección 3.1)
- [ ] Protocolos de corte de gas, ascensores (Sección 6)
- [ ] Reserva estratégica de agua (3L/persona/día)
- [ ] Matriz de responsabilidades por Dirección (Sección 4)
- [ ] Evaluación post-evento y Certificado de Aptitud de Ocupación
- [ ] Protección de patrimonio, laboratorios y archivos (Sección 7)
- [ ] Mantenimiento estacional pre-temporada (Sección 5)
- [ ] Ascensores: maniobra preventiva y rescate (Sección 9)
- [ ] Flota institucional en tránsito (Sección 10)

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
- [ ] Repetidor VHF Alem (50W, 24-48h respaldo)

### 5.2. Integraciones Recomendadas

| Sistema UNS | Tipo de Integración | Prioridad |
|-------------|---------------------|-----------|
| **SMN (Servicio Meteorológico)** | Web Scraping + API | 🔴 Alta |
| **Alerthor** | Coordinación CH1 | 🔴 Alta |
| **Moodle UNS** | API para notificaciones académicas | 🟡 Media |
| **Sistema de Gestión de Personal** | Sincronización usuarios | 🟡 Media |
| **LDAP UNS** | Autenticación única | 🟡 Media |
| **Radio AM UNS** | Interfaz para emisión automática | 🟢 Baja |
| **FM UTN-FRBB** | Enlace dúplex | 🟢 Baja |
| **Sistema de Control de Acceso** | Integración evacuaciones | 🟢 Baja |
| **Megafonía de Predios** | Activación remota | 🟢 Baja |

### 5.3. Escalabilidad y Crecimiento

- [ ] Arquitectura modular para agregar nuevos módulos
- [ ] Soporte para 11+ sedes UNS
- [ ] Capacidad para 10,000+ usuarios simultáneos
- [ ] Sistema multi-tenancy (futuras expansiones)
- [ ] Preparado para nuevas categorías de emergencia
- [ ] Preparado para nuevos Procedimientos Específicos (PE)

---

## 6. PRESUPUESTO ESTIMADO

### 6.1. Desarrollo (One-time)

| Concepto | Horas | Costo Estimado (USD) |
|----------|-------|----------------------|
| Planificación y Diseño | 160 | 8,000 - 12,000 |
| Backend Laravel | 640 | 32,000 - 48,000 |
| App Móvil React Native | 800 | 40,000 - 60,000 |
| Panel Web React | 480 | 24,000 - 36,000 |
| Scraping SMN | 80 | 4,000 - 6,000 |
| Pruebas y QA | 320 | 16,000 - 24,000 |
| Despliegue | 80 | 4,000 - 6,000 |
| **TOTAL DESARROLLO** | **2,560** | **128,000 - 192,000** |

**Nota:** Si lo desarrollas tú + equipo interno UNS, el costo sería principalmente tiempo de trabajo.

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
| **Fase 2:** Backend Laravel | 10 semanas | Diciembre 2026 - Febrero 2027 |
| **Fase 3:** App Móvil | 12 semanas | Enero - Marzo 2027 |
| **Fase 4:** Panel Web | 8 semanas | Febrero - Abril 2027 |
| **Fase 5:** Pruebas | 8 semanas | Abril - Mayo 2027 |
| **Fase 6:** Despliegue | 6 semanas | Junio - Julio 2027 |
| **Fase 7:** Soporte continuo | Ongoing | Agosto 2027 en adelante |

**Fecha estimada de lanzamiento:** **Julio/Agosto 2027** (antes de la próxima temporada primavera-verano)

---

## 8. RECOMENDACIONES FINALES

### 8.1. Para Ti (Miguel)

**Aprovechando tus conocimientos en PHP/MySQL y Antigravity:**
1. **Backend con Laravel 11:** PHP moderno, excelente documentación, ideal para APIs REST
2. **Aprender React Native:** Desarrollo móvil multiplataforma con JavaScript
3. **Usa Antigravity** para backend Laravel y panel web (tu entorno favorito)
4. **Laravel Reverb** para WebSockets (tiempo real)
5. **Laravel Queue** para notificaciones masivas

**Habilidades a desarrollar/adquirir:**
- [ ] React Native (1-2 meses de estudio)
- [ ] Firebase Cloud Messaging (2 semanas)
- [ ] Notificaciones críticas en Android/iOS (1 mes)
- [ ] WebSockets con Laravel Reverb (2 semanas)
- [ ] UX/UI básico para apps móviles (1 mes)
- [ ] Web scraping con Python (2 semanas)

### 8.2. Equipo Sugerido

**Opción A: Equipo Interno UNS (más económico)**
- Tú: Project Manager + Backend Developer Laravel
- 1 Desarrollador Móvil React Native (contratado o becario DCI)
- 1 Desarrollador Frontend Web (contratado o becario)
- 1 Diseñador UX/UI (part-time, DCI)
- 1 QA (part-time, estudiante avanzado DCI)
- 1 Scraping Developer Python (part-time, Telecomunicaciones)

**Opción B: Agencia de Desarrollo (más rápido, más caro)**
- Contratar agencia especializada en apps móviles
- Tú como Product Owner (definición de requisitos)
- Mayor costo pero menor tiempo

### 8.3. Próximos Pasos Inmediatos

1. **Validación con stakeholders:** Presentar este plan al CDE y obtener aprobación
2. **Formación del equipo:** Definir quiénes participarán
3. **Setup de entorno:** Configurar repositorios Git, servidores de desarrollo
4. **Kickoff meeting:** Reunión inicial con todo el equipo
5. **Inicio de Fase 1:** Comenzar con diseño y planificación detallada
6. **Solicitud Critical Alerts iOS:** Iniciar trámite con Apple (proceso largo)

### 8.4. Riesgos y Mitigación

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Retrasos en aprobación Critical Alerts iOS | Alta | Alto | Iniciar trámite ya; app Android primero |
| Problemas con notificaciones críticas | Alta | Alto | Pruebas exhaustivas en múltiples fabricantes |
| Resistencia al cambio del personal | Media | Medio | Capacitación intensiva, champions por área |
| Cambios en protocolos UNS | Baja | Medio | Arquitectura modular, fácil de actualizar |
| Presupuesto insuficiente | Media | Alto | MVP con funcionalidades críticas primero |
| Caída de comunicaciones convencionales | Media | Alto | RACUNS como medio principal; redundancia |
| Cambios en SMN (scraping) | Media | Medio | API oficial si se libera; múltiples fuentes |
| Problemas con fabricantes Android (Xiaomi, Huawei) | Alta | Alto | Guía de configuración por fabricante |

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
9. ✅ Ventanas horarias de decisión automatizadas
10. ✅ Plantillas M1-M6 (las principales)
11. ✅ Scraping SMN automático
12. ✅ Soporte para eventos simultáneos

### Funcionalidades Post-MVP (Fase 2)
- Checklists digitales (AT-01 y AT-02)
- Comunicación interna completa con cascada
- Gestión de custodia escolar (Anexo C)
- Análisis con IA
- Modo offline completo
- Integración RACUNS / Alerthor
- Reportes y estadísticas avanzadas
- Gestión de rumores (M7)
- Partes prolongados (M8)
- Módulo Moodle de autoprotección
- Integración LDAP UNS
- Integración con Moodle

---

## 10. CONCLUSIÓN

Este proyecto es **totalmente viable** y se alinea perfectamente con los protocolos PECl-UNS 2026. La combinación de:

- Tu experiencia técnica en PHP/MySQL y Antigravity
- Los protocolos bien definidos (Documentos A, C, AT-01, AT-02)
- Las tecnologías modernas disponibles (React Native, Laravel 11, Firebase)
- La infraestructura existente (hosting, BD MySQL UNS)

...crea las condiciones ideales para desarrollar una solución robusta y efectiva para la UNS.

**Recomendación final:** Comenzar con el MVP para validar el concepto antes de la próxima temporada de tormentas primavera-verano (Octubre 2027), obtener feedback real del CDE y usuarios, y luego iterar con las funcionalidades adicionales.

---

## ANEXO 1: Consideraciones Técnicas para Notificaciones Críticas

### Android
- Usar **High Priority FCM messages** con `priority: "high"` y `sound: "default"`
- Solicitar permiso **ACCESS_NOTIFICATION_POLICY** para bypass de DND
- Usar **AlarmManager** con `setExactAndAllowWhileIdle` para alarmas críticas
- Excluir app de **Battery Optimization** (Doze mode) - guía por fabricante
- Usar **WakeLock** para activar pantalla
- Reproducir audio con **AudioManager.STREAM_ALARM** (volumen máximo)
- Solicitar permiso **SCHEDULE_EXACT_ALARM** (Android 12+)
- Implementar **Foreground Service** para mantener proceso activo
- Usar **fullScreenIntent** para pantalla completa
- Configuraciones específicas por fabricante:
  - **Xiaomi:** Autostart + Battery saver
  - **Huawei:** Battery optimization + Launch manager
  - **Samsung:** Battery optimization + Sleeping apps
  - **Oppo/Realme:** Auto-launch + Battery optimization

### iOS
- Solicitar aprobación para **Critical Alerts** (requiere documentación de emergencia)
- Usar **UNNotificationSound.defaultCriticalSound** con volumen crítico
- Configurar **Time Sensitive Notifications** (iOS 15+)
- Solicitar permiso especial en App Store Connect
- Implementar **PushKit** para notificaciones VoIP como fallback
- Usar **UNUserNotificationCenter** con `interruptionLevel: .critical`
- Configuración de **Notification Service Extension** para personalización

### Web (PWA)
- Usar **Notification API** con `requireInteraction: true`
- Implementar **Service Worker** para notificaciones en background
- Usar **Web Audio API** para reproducción de sonido
- Implementar **Wake Lock API** cuando esté disponible
- Registrar **Push API** subscription para notificaciones del servidor
- Manejar **visibilitychange** para alertas cuando la pestaña está activa

---

## ANEXO 2: Mapeo de Protocolos a Funcionalidades de la App

| Protocolo UNS | Sección | Funcionalidad en la App |
|---------------|---------|------------------------|
| Doc A - Sección 4.1 | Niveles SMN | 6 niveles con colores y acciones |
| Doc A - Sección 4.2 | Línea de tiempo | Visualización 72h en 4 rangos |
| Doc A - Sección 4.3 | Eventos simultáneos | Listado de alertas activas |
| Doc A - Sección 5 | Umbrales Patagonia | Tabla de umbrales por fenómeno |
| Doc A - Sección 6.1 | Ventanas horarias | Motor automático 22/10/16 hs |
| Doc A - Sección 6.2 | Rutina monitoreo | Cron jobs cada hora |
| Doc A - Sección 6.3 | Ficha del Alerta | Formulario digital Anexo B |
| Doc A - Sección 7.1 | Nivel Amarillo | M1 - Preventivo |
| Doc A - Sección 7.2 | Nivel Naranja | M2 - Suspensión |
| Doc A - Sección 7.3 | Nivel Rojo | M4 - Confinamiento |
| Doc A - Sección 7.4 | Advertencia violeta | Evaluación transporte |
| Doc A - Sección 7.5 | ACP | Alarma crítica inmediata |
| Doc A - Sección 7.6 | Temperaturas | Virtualidad o protección |
| Doc A - Sección 7.7 | Resguardo vs Evacuación | Lógica decisión |
| Doc A - Sección 8 | Custodia escolar | Módulo retiro con DNI |
| Doc A - Anexo B | Ficha del Alerta | Plantilla digital |
| Doc A - Anexo C | Registro retiro | Formulario digital con firma |
| Doc C - Sección 5 | Cascada mensajes | Sistema difusión en cascada |
| Doc C - Sección 6 | Arquitectura mensajes | Editor M1-M8 |
| Doc C - Anexo C | Plantillas M1-M8 | Mensajes predefinidos |
| Doc C - Anexo B | Diagrama difusión | Capas 1-5 |
| AT-01 - Sección 3.1 | Vulnerabilidades | Mapa interactivo por predio |
| AT-01 - Sección 5 | Mantenimiento preventivo | Checklists digitales |
| AT-01 - Sección 6 | Protocolos emergencia | Flujos trabajo automatizados |
| AT-01 - Sección 11 | Evaluación post-evento | Módulo inspección |
| AT-01 - Sección 12 | Checklist mantenimiento | Registro sistemático |
| AT-02 - Sección 4 | Mantenimiento RACUNS | Checklists comunicaciones |
| AT-02 - Sección 5 | Starlink | Registro pruebas S1/S2/S3 |
| AT-02 - Sección 7 | Pruebas | Calendario seguimiento |
| AT-02 - Sección 8 | Agenda contactos | Directorio operativo |
| AT-02 - Sección 9 | Indicadores | Dashboard KPIs |

---

## ANEXO 3: Estructura de Base de Datos Sugerida (MySQL)


```sql
-- ============================================
-- TABLAS PRINCIPALES DEL SISTEMA UNS
-- ============================================

-- Usuarios y roles
CREATE TABLE usuarios (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    apellido VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE,
    telefono VARCHAR(20) NOT NULL,
    telefono_alternativo VARCHAR(20),
    dni VARCHAR(20) UNIQUE,
    rol ENUM(
        'admin_cde',
        'recepcion_avisos',
        'shst',
        'dci',
        'telecomunicaciones',
        'mayordomo',
        'decano',
        'director_admin',
        'infraestructura',
        'mantenimiento',
        'construcciones',
        'docente',
        'nodocente',
        'estudiante',
        'familia',
        'chofer'
    ) NOT NULL,
    departamento VARCHAR(100),
    edificio_asignado VARCHAR(100),
    suplente_de BIGINT NULL,
    activo BOOLEAN DEFAULT TRUE,
    dispositivo_token VARCHAR(500),
    plataforma ENUM('android', 'ios', 'web'),
    permisos_notificaciones_criticas BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (suplente_de) REFERENCES usuarios(id)
);

-- Predios UNS
CREATE TABLE predios (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    direccion VARCHAR(200),
    tipo ENUM(
        'campus', 'complejo', 'sede', 'escuela', 'anexo'
    ),
    vulnerabilidades TEXT,
    zonas_confinamiento TEXT,
    sectores_vulnerables TEXT,
    mayordomo_id BIGINT,
    sala_crisis BOOLEAN DEFAULT FALSE,
    base_operativa VARCHAR(50),
    activo BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (mayordomo_id) REFERENCES usuarios(id)
);

-- Alertas SMN
CREATE TABLE alertas_smn (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    ficha_numero VARCHAR(50) UNIQUE,
    fuente ENUM('web_smn', 'app_smn', 'defensa_civil', 'manual'),
    evento ENUM('alerta', 'advertencia', 'acp'),
    fenomeno ENUM(
        'tormenta', 'lluvia', 'viento', 'zonda', 'nevada',
        'temperatura_extrema', 'niebla', 'humo', 'ceniza', 'polvo'
    ),
    nivel ENUM('verde', 'amarillo', 'naranja', 'rojo', 'acp', 'violeta'),
    zona_afectada VARCHAR(200),
    vigencia_desde DATETIME,
    vigencia_hasta DATETIME,
    rangos_diarios VARCHAR(200),
    turnos_intersectados VARCHAR(200),
    umbrales_aplicables TEXT,
    eventos_simultaneos TEXT,
    accion_recomendada TEXT,
    detalle_zonal TEXT,
    linea_tiempo JSON,
    operador_id BIGINT,
    estado ENUM('activa', 'cesada', 'vencida'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (operador_id) REFERENCES usuarios(id)
);

-- Emergencias
CREATE TABLE emergencias (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    alerta_id BIGINT NULL,
    tipo ENUM(
        'puntual', 'general', 'climatica', 'mayor',
        'sanitaria', 'esperable'
    ),
    nivel_smn VARCHAR(20),
    estado ENUM(
        'activa', 'confinamiento', 'evacuacion',
        'cesada', 'reanudada'
    ),
    mensaje_tipo ENUM('M1','M2','M3','M4','M5','M6','M7','M8'),
    edificios_afectados JSON,
    created_by BIGINT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (alerta_id) REFERENCES alertas_smn(id),
    FOREIGN KEY (created_by) REFERENCES usuarios(id)
);

-- Respuestas a emergencias
CREATE TABLE respuestas_emergencia (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    emergencia_id BIGINT,
    usuario_id BIGINT,
    respuesta ENUM('en_camino', 'retrasado', 'no_disponible', 'recibido'),
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    ubicacion_lat DECIMAL(10, 8),
    ubicacion_lng DECIMAL(11, 8),
    FOREIGN KEY (emergencia_id) REFERENCES emergencias(id) ON DELETE CASCADE,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id)
);

-- Checklists (AT-01 y AT-02)
CREATE TABLE checklists (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(200) NOT NULL,
    tipo ENUM('infraestructura', 'comunicaciones', 'general'),
    anexo_ref ENUM('AT-01', 'AT-02', 'general'),
    seccion VARCHAR(50),
    frecuencia ENUM(
        'semanal', 'mensual', 'trimestral', 'semestral',
        'anual', 'pre_temporada', 'post_evento'
    ),
    responsable_rol VARCHAR(100),
    activo BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE checklist_items (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    checklist_id BIGINT,
    descripcion TEXT NOT NULL,
    tipo_respuesta ENUM('ok', 'observacion', 'falla', 'texto', 'numero', 'foto'),
    orden INT,
    obligatorio BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (checklist_id) REFERENCES checklists(id) ON DELETE CASCADE
);

CREATE TABLE checklist_completados (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    checklist_id BIGINT,
    usuario_id BIGINT,
    predio_id BIGINT,
    fecha DATE,
    resultado ENUM('ok', 'observacion', 'falla', 'incompleto'),
    observaciones TEXT,
    offline BOOLEAN DEFAULT FALSE,
    synced_at TIMESTAMP NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (checklist_id) REFERENCES checklists(id),
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id),
    FOREIGN KEY (predio_id) REFERENCES predios(id)
);

CREATE TABLE checklist_respuestas (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    completado_id BIGINT,
    item_id BIGINT,
    respuesta TEXT,
    foto_url VARCHAR(500),
    FOREIGN KEY (completado_id) REFERENCES checklist_completados(id) ON DELETE CASCADE,
    FOREIGN KEY (item_id) REFERENCES checklist_items(id)
);

-- Custodia escolar (Anexo C Doc A)
CREATE TABLE custodia_escolar (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    emergencia_id BIGINT,
    predio_id BIGINT,
    alumno_nombre VARCHAR(100) NOT NULL,
    alumno_dni VARCHAR(20),
    adulto_nombre VARCHAR(100) NOT NULL,
    adulto_dni VARCHAR(20) NOT NULL,
    vinculo VARCHAR(50),
    hora_retiro TIMESTAMP,
    firma_digital TEXT,
    observaciones TEXT,
    reportado_a_oficina BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (emergencia_id) REFERENCES emergencias(id),
    FOREIGN KEY (predio_id) REFERENCES predios(id)
);

CREATE TABLE adultos_autorizados (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    predio_id BIGINT,
    alumno_id VARCHAR(50),
    alumno_nombre VARCHAR(100),
    adulto_nombre VARCHAR(100),
    adulto_dni VARCHAR(20) NOT NULL,
    vinculo VARCHAR(50),
    telefono VARCHAR(20),
    activo BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (predio_id) REFERENCES predios(id)
);

-- Mensajes (M1-M8)
CREATE TABLE mensajes (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    emergencia_id BIGINT NULL,
    remitente_id BIGINT,
    tipo ENUM(
        'M1','M2','M3','M4','M5','M6','M7','M8',
        'interno', 'urgente', 'rutina'
    ),
    asunto VARCHAR(200),
    contenido TEXT NOT NULL,
    contenido_sonoro_url VARCHAR(500),
    contenido_visual_url VARCHAR(500),
    canales JSON,
    estado ENUM('borrador', 'enviado', 'confirmado', 'fallido'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (emergencia_id) REFERENCES emergencias(id),
    FOREIGN KEY (remitente_id) REFERENCES usuarios(id)
);

CREATE TABLE mensaje_destinatarios (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    mensaje_id BIGINT,
    destinatario_id BIGINT,
    recibido_at TIMESTAMP NULL,
    leido_at TIMESTAMP NULL,
    FOREIGN KEY (mensaje_id) REFERENCES mensajes(id) ON DELETE CASCADE,
    FOREIGN KEY (destinatario_id) REFERENCES usuarios(id)
);

-- Indicadores AT-02
CREATE TABLE indicadores_at02 (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    fecha DATE,
    pruebas_radiales_semanal DECIMAL(5,2),
    fallas_subsanadas_24h DECIMAL(5,2),
    cobertura_areas_criticas DECIMAL(5,2),
    autonomia_nodos_horas DECIMAL(5,2),
    pruebas_programadas DECIMAL(5,2),
    declaraciones_ecd DECIMAL(5,2),
    agenda_actualizada BOOLEAN,
    checklist_sin_observaciones BOOLEAN,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Logs de auditoría
CREATE TABLE logs_auditoria (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    usuario_id BIGINT,
    accion VARCHAR(100),
    entidad VARCHAR(50),
    entidad_id BIGINT,
    datos JSON,
    ip_address VARCHAR(45),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id)
);

-- Informes post-activación (72 horas)
CREATE TABLE informes_post_activacion (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    emergencia_id BIGINT,
    tipo_evento ENUM('real', 'simulado'),
    lecciones_aprendidas TEXT,
    acciones_correctivas TEXT,
    analisis_comunicacion TEXT,
    analisis_tecnico TEXT,
    tiempos_emision JSON,
    cobertura_efectiva DECIMAL(5,2),
    rumores_gestionados INT,
    fallas_canales TEXT,
    created_by BIGINT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (emergencia_id) REFERENCES emergencias(id),
    FOREIGN KEY (created_by) REFERENCES usuarios(id)
);

-- Índices para performance
CREATE INDEX idx_usuarios_rol ON usuarios(rol);
CREATE INDEX idx_usuarios_edificio ON usuarios(edificio_asignado);
CREATE INDEX idx_alertas_nivel ON alertas_smn(nivel);
CREATE INDEX idx_alertas_vigencia ON alertas_smn(vigencia_desde, vigencia_hasta);
CREATE INDEX idx_emergencias_estado ON emergencias(estado);
CREATE INDEX idx_emergencias_tipo ON emergencias(tipo);
CREATE INDEX idx_respuestas_emergencia ON respuestas_emergencia(emergencia_id);
CREATE INDEX idx_mensajes_tipo ON mensajes(tipo);
CREATE INDEX idx_custodia_emergencia ON custodia_escolar(emergencia_id);

```
---

## ANEXO 4: Plantillas de Mensajes M1-M8 (Documento C - Anexo C)

### M1 – Preventivo (SMN Amarillo)

**Categoría:** Emergencia climática / Emergencia esperable
**Enfoque comunicacional:** Prevención y preparación
**Medida:** Limitación de actividades al aire libre
**Canales sugeridos:** Correo + Redes + Apps

Debido a (X MOTIVO) se suspenden actividades al aire libre por condiciones 
climáticas a partir de XXX y hasta XXX en todas las instalaciones de la 
Universidad. Las clases y actividades en espacios cerrados continúan 
normalmente. Sugerimos a la comunidad mantenerse informada por los canales 
oficiales de la UNS.

### M2 – Suspensión (SMN Naranja/Rojo)

Debido a (X MOTIVO) se encuentran suspendidas todas actividades presenciales 
en (X SEDE/EDIFICIO) de la UNS. Esta medida incluye clases, consultas, 
prácticos y exámenes. Se solicita a la comunidad no concurrir hasta nuevo 
aviso y se sugiere a los alumnos mantenerse en contacto con sus cátedras a 
través del sistema Moodle. La información oficial se publicará en los medios 
institucionales.

### M3 – Evacuación

A partir de este momento se suspenden todas las actividades presenciales en 
[X SEDE/EDIFICIO]. Les pedimos retirarse de manera ordenada hacia el punto 
de reunión establecido. Mantengan la calma, sigan las indicaciones del 
personal y permanezcan atentos a la información oficial que se difundirá por 
los canales institucionales.

### M4 – Confinamiento (SMN Rojo)

Debido a (X MOTIVO) la Universidad se encuentra en modo de emergencia y se 
ha resuelto el confinamiento del personal y la comunidad estudiantil: todos 
deben permanecer dentro de los edificios de la UNS y no salir al exterior 
hasta recibir nuevas instrucciones oficiales. Mantenga la calma y siga las 
indicaciones del personal.

### M5 – Custodia escolar (Naranja)

Se informa a los padres, madres y adultos responsables de los estudiantes de 
(X ESTABLECIMIENTO) que los alumnos y alumnas se encuentran bajo custodia 
segura en su escuela. El retiro solo se realizará con DNI del adulto 
autorizado. Se informará cualquier cambio por los canales oficiales.

### M6 – Cese (Verde)

La UNS informa el cese de las medidas extraordinarias. Las actividades 
académicas y administrativas se reanudan con normalidad en todos los turnos. 
Gracias por seguir las instrucciones oficiales.

### M7 – Rumor

La Universidad Nacional del Sur confirma que la situación vigente es la 
siguiente: [dato verificado]. Versiones que indiquen lo contrario no son 
oficiales y por lo tanto, son falsas. Invitamos a toda la comunidad a 
mantenerse informada exclusivamente a través de nuestros canales oficiales, 
donde encontrarán datos claros, actualizados y confiables. Gracias por 
acompañar la difusión responsable de la información.

### M8 – Parte prolongado

Parte oficial UNS – Emergencia prolongada:
Servicios disponibles: agua y alimentos en [sector].
Retiro escolar: autorizado en [horario].
Próxima actualización: dentro de 60 minutos.
Mantenga la calma y siga las instrucciones oficiales.

## ANEXO 5: Ficha del Alerta Digital (Anexo B del Documento A)

Campos obligatorios a capturar en la app:

| Campo | Tipo | Descripción |
|-------|------|-------------|
|N.º de ficha / Fecha y hora de recepción |	Auto |	Generado automáticamente |
|Fuente|	Select |	web SMN / app SMN / Defensa Civil / manual |
|Evento |	Select	 |Alerta / Advertencia / ACP |
|Fenómeno	|Select	|tormenta/lluvia/viento/zonda/nevada/temperatura/niebla-humo-ceniza|
|Nivel	| Select |	amarillo / naranja / rojo / violeta |
|Zona afectada	| Text	| Según nomenclatura SMN |
|Vigencia Desde / Hasta |	DateTime |	Rango de vigencia |
|Rangos diarios intersectados	| Multi |	madrugada / mañana / tarde / noche|
|Turnos UNS intersectados	| Multi	|mañana / tarde / noche / escuelas|
|Umbrales aplicables |	Auto |	Sección 5 (Patagonia)|
|Eventos simultáneos en la zona	JSON |	Línea de tiempo | SMN |
|Acción recomendada |	Auto |	Según matriz Sección 7 |
|Operador que completa |	User	| Usuario de Recepción de Avisos |
|Notificados (CDE)	| Multi |	Lista CDE + suplentes|
|Hora / Medios utilizados |	Log	| Timestamp + canales|

---

## ANEXO 6: Checklist de Pruebas de Notificaciones Críticas

** Pruebas Android

- Alarma con app cerrada
- Alarma con app en background
- Alarma con pantalla bloqueada
- Alarma con modo silencio activado
- Alarma con modo No Molestar (DND)
- Voz TTS reproduciendo mensaje
- Vibración en patrón específico
- Wake up de pantalla
- Full screen intent
Pruebas por fabricante:
Samsung (One UI)
Xiaomi (MIUI)
Huawei (EMUI)
Oppo (ColorOS)
Motorola (Stock)
Google Pixel (Stock)

Pruebas iOS
- Critical Alert con app cerrada
- Critical Alert con pantalla bloqueada
- Time Sensitive Notification
- Sonido crítico personalizado
- Voz TTS
- Vibración específica
- Wake up de pantalla

Pruebas Generales
- Notificación recibida en menos de 5 segundos
- Confirmación de recepción registrada
- Respuesta rápida desde notificación
- Funcionamiento offline (cola local)
- Sincronización al recuperar conexión
- Pruebas con 100+ dispositivos simultáneos
- Pruebas de redundancia (3 canales)
