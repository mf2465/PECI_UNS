# PLAN DE DESARROLLO: Sistema de Gestión de Emergencias UNS
## App AlertUNS - adaptada a la Universidad Nacional del Sur -

**Elaborado por:** Comité de Dirección de Emergencia

**Fecha:** 30 de septiembre de 2026

**Basado en:** app BomberBOT + Protocolos PECl-UNS (Documentos A, B, AT-01, AT-02)

---

## 1. ANÁLISIS DEL PROYECTO

### 1.1. Características principales a implementar

**Funcionalidades críticas (basadas en app BomberBOT y protocolos UNS):**

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
- [ ] Diseño de wireframes y prototipos (Figma)
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
- [ ] Configuración de servidores de desarrollo (hosting)
- [ ] Setup de Firebase (FCM, Analytics, Crashlytics)
- [ ] Configuración de CI/CD (GitHub Actions)
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
- [ ] Configuración de servidores de producción (hosting)
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


### 4.2. Recursos Tecnológicos

#### Infraestructura (hosting y BD)
- [ ] **Servidor de producción** (mínimo 4 vCPUs, 8GB RAM, 100GB SSD)
- [ ] **Servidor de staging** (similar a producción)
- [ ] **Base de datos MySQL** (ya disponible)
- [ ] **Redis** para caché y colas
- [ ] **Almacenamiento de archivos** (S3 o local, ~500GB inicial)
- [ ] **Balanceador de carga** (si hay alta concurrencia)
- [ ] **Certificados SSL** (Let's Encrypt o comercial)
- [ ] **Backup automático** (diario, con retención de 30 días)
- [ ] **UPS y respaldo energético** (coordinado con AT-01)


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


| Concepto | Horas | 
|----------|-------|
| Planificación y Diseño | 160 | 
| Backend Laravel | 640 | 
| App Móvil React Native | 800 | |
| Panel Web React | 480 | 
| Scraping SMN | 80 | 
| Pruebas y QA | 320 | 
| Despliegue | 80 | 
| **TOTAL DESARROLLO** | **2,560** | 


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

## PROPUESTA DE MVP (Producto Mínimo Viable)

Con las funcionalidades críticas:

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

**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| X MOTIVO | "alerta amarilla por vientos intensos con ráfagas" |
| XXX (desde) | "las 18:00 hs del día de la fecha" |
| XXX (hasta) | "las 06:00 hs del día siguiente" |

**Acciones asociadas (Documento A, Sección 7.1):**
- Suspender prácticas deportivas, relevamientos de campo, jardinería y trabajos en altura
- Suspender salidas de campo si la zona de destino se encuentra bajo alerta
- Mayordomía / Seguridad / Mantenimiento: prealerta y verificación de generadores, motobombas, baterías VHF y sumideros pluviales

---

### M2 – Suspensión (SMN Naranja/Rojo)

**Categoría:** Emergencia general / Emergencia climática
**Enfoque comunicacional:** Protección inmediata e instrucciones claras
**Medida:** No concurrencia
**Canales sugeridos:** WPP/Telegram, Apps, Correo, Web, Moodle, Redes

Debido a (X MOTIVO) se encuentran suspendidas todas actividades presenciales 
en (X SEDE/EDIFICIO) de la UNS. Esta medida incluye clases, consultas, 
prácticos y exámenes. Se solicita a la comunidad no concurrir hasta nuevo 
aviso y se sugiere a los alumnos mantenerse en contacto con sus cátedras a 
través del sistema Moodle. La información oficial se publicará en los medios 
institucionales.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| X MOTIVO | "alerta naranja por tormentas severas" |
| X SEDE/EDIFICIO | "todas las sedes" / "Campus Altos de Palihue" |

**Acciones asociadas (Documento A, Sección 7.2-7.3):**
- Naranja antes del corte: suspender el turno afectado y difundir antes de la ventana horaria
- Naranja/Rojo: suspensión de toda actividad presencial
- Cierre de accesos y restricción de circulación (Rojo)
- CDE operatividad plena en Sala de Crisis

---

### M3 – Evacuación

**Categoría:** Emergencia general / Emergencia mayor
**Enfoque comunicacional:** Protección inmediata e instrucciones claras
**Medida:** Evacuación
**Canales sugeridos:** Megafonía, plataforma alumnos, redes


A partir de este momento se suspenden todas las actividades presenciales en 
[X SEDE/EDIFICIO]. Les pedimos retirarse de manera ordenada hacia el punto 
de reunión establecido. Mantengan la calma, sigan las indicaciones del 
personal y permanezcan atentos a la información oficial que se difundirá por 
los canales institucionales.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| X SEDE/EDIFICIO | "el edificio San Juan 670" / "el Complejo Alem" |

**Acciones asociadas (Documento A, Sección 7.7):**
- Solo ante peligro estructural inminente, incendio incontrolable o inundación grave destructiva
- Evacuación externa controlada por rutas preestablecidas hacia puntos de encuentro seguros
- Por orden exclusiva del CDE
- **NO se evacúa durante ACP activo** salvo riesgo inminente de colapso estructural

---

### M4 – Confinamiento (SMN Rojo / ACP)

**Categoría:** Emergencia general / Emergencia climática / Emergencia mayor
**Enfoque comunicacional:** Protección inmediata e instrucciones claras
**Medida:** Confinamiento
**Canales sugeridos:** Megafonía, plataforma alumnos, redes, medios externos

Debido a (X MOTIVO) la Universidad se encuentra en modo de emergencia y se 
ha resuelto el confinamiento del personal y la comunidad estudiantil: todos 
deben permanecer dentro de los edificios de la UNS y no salir al exterior 
hasta recibir nuevas instrucciones oficiales. Mantenga la calma y siga las 
indicaciones del personal.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| X MOTIVO | "alerta roja por tormenta severa con ráfagas destructivas" |

**Acciones asociadas (Documento A, Secciones 7.5 y 7.7):**
- ACP vigente (1-3 horas): cese inmediato + confinamiento seguro interno en todos los predios
- NO se evacuará al personal ni a alumnos mientras el ACP permanezca activo
- Zonas de confinamiento:
  - Campus Palihue: pabellones centrales de hormigón
  - SJ670 / Alem: pasillos internos y plantas bajas, alejados de ventanas
  - Escuelas: aulas internas designadas (Protocolo de Custodia)
- Escucha permanente en CH1 (Alerthor) durante Naranja/Rojo

---

### M5 – Custodia escolar (Naranja)

**Categoría:** Emergencia climática
**Enfoque comunicacional:** Prevención, protección y actualización
**Medida:** Custodia de menores
**Canales sugeridos:** Enlaces de Escuelas Preuniversitarias, WPP/Telegram familias, correo


Se informa a los padres, madres y adultos responsables de los estudiantes de 
(X ESTABLECIMIENTO) que los alumnos y alumnas se encuentran bajo custodia 
segura en su escuela. El retiro solo se realizará con DNI del adulto 
autorizado. Se informará cualquier cambio por los canales oficiales.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| X ESTABLECIMIENTO | "la Escuela 11 de Abril" / "la Escuela Agraria" |

**Acciones asociadas (Documento A, Sección 8):**
- Regla de custodia: prohibido retiro individual sin padre/madre/tutor legal acreditado
- Procedimiento de retiro:
  1. Comunicar suspensión/custodia a familias y reportar a Oficina de Recepción
  2. Adulto autorizado se presenta en punto de entrega habilitado
  3. Personal directivo verifica DNI contra listado de autorizados
  4. Registrar: fecha, hora, alumno, adulto, DNI, vínculo y firma
  5. Egreso por ruta segura designada (alejada de ventanas, árboles, estructuras colapsables)
  6. Informar a Oficina de Recepción nómina de retirados y quienes permanecen
- Custodia extendida: si hay corte de transporte, guardia con agua y resguardo

---

### M6 – Cese (Verde)

**Categoría:** Todas
**Enfoque comunicacional:** Reanudación
**Medida:** Cese de medidas extraordinarias
**Canales sugeridos:** Los mismos canales utilizados para la suspensión (Documento C, Sección Comunicación de reanudación)


La UNS informa el cese de las medidas extraordinarias. Las actividades 
académicas y administrativas se reanudan con normalidad en todos los turnos. 
Gracias por seguir las instrucciones oficiales.


**Acciones asociadas:**
- Se difunde por los mismos canales de la suspensión
- Vencida vigencia del ACP: CDE evalúa reanudación o suspensión del resto del turno
- Tras evento severo: ningún edificio se reocupa sin "Certificado de Aptitud de Ocupación" (AT-01, Sección 11)
- Informe post-activación dentro de las 72 horas

---

### M7 – Rumor

**Categoría:** Todas (respuesta a desinformación)
**Enfoque comunicacional:** Veracidad y gestión de rumores
**Canales sugeridos:** Redes sociales oficiales, web institucional


La Universidad Nacional del Sur confirma que la situación vigente es la 
siguiente: [dato verificado]. Versiones que indiquen lo contrario no son 
oficiales y por lo tanto, son falsas. Invitamos a toda la comunidad a 
mantenerse informada exclusivamente a través de nuestros canales oficiales, 
donde encontrarán datos claros, actualizados y confiables. Gracias por 
acompañar la difusión responsable de la información.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| [dato verificado] | "no hay alerta vigente para Bahía Blanca; las actividades continúan con normalidad" |

**Acciones asociadas (Documento C, Principios Rectores):**
- DCI monitorea circulación de rumores
- Evalúa: alcance, potencial de daño, relevancia para seguridad o confianza pública
- Toda respuesta basada en información verificada
- Aportar dato correcto o información disponible

---

### M8 – Parte prolongado

**Categoría:** Emergencia mayor / Confinamiento prolongado
**Enfoque comunicacional:** Protección, coordinación e información sostenida
**Canales sugeridos:** Megafonía de predios (repite puntos clave entre partes), redes, web, radio


Parte oficial UNS – Emergencia prolongada:
Servicios disponibles: agua y alimentos en [sector].
Retiro escolar: autorizado en [horario].
Próxima actualización: dentro de 60 minutos.
Mantenga la calma y siga las instrucciones oficiales.


**Campos editables:**
| Campo | Ejemplo |
|-------|---------|
| [sector] | "pabellón central del Campus Palihue" |
| [horario] | "14:00 hs" |
| 60 minutos | Ajustar según evaluación del CDE |

**Acciones asociadas (Documento C, Comunicación durante confinamiento prolongado):**
- Partes con información de servicios: agua, alimentos, refugios, retiro escolar
- Instrucciones de calma
- Horarios de próxima actualización
- Megafonía de predios repite puntos clave entre partes
- Reserva estratégica de agua: mínimo 3 litros/persona/día (AT-01, Sección 6.2)

---

## ANEXO 5: Ficha del Alerta Digital (Anexo B del Documento A)

> **Uso obligatorio:** Ante toda alerta sobre la zona Bahía Blanca o destino de actividad de campo, el operador de la Oficina de Recepción de Avisos de Emergencia completará esta ficha. Antes de toda decisión, el operador abrirá el detalle de la zona y leerá la línea de tiempo, identificando todos los alertas, advertencias y ACP simultáneos, sin basarse únicamente en el color del mapa (Documento A, Sección 6.3).

### 5.1. Campos obligatorios de la Ficha

| # | Campo | Tipo de dato | Validación | Descripción |
|---|-------|-------------|------------|-------------|
| 1 | N.º de ficha | Auto-generado | Único, secuencial | Formato: UNS-YYYY-NNN |
| 2 | Fecha y hora de recepción | Timestamp | Auto | Al momento de registro en el sistema |
| 3 | Fuente | Select | Obligatorio | web SMN / app SMN / Defensa Civil / manual |
| 4 | Evento | Select | Obligatorio | Alerta / Advertencia / ACP |
| 5 | Fenómeno | Select | Obligatorio | tormenta / lluvia / viento / zonda / nevada / temperatura / niebla-humo-ceniza / polvo |
| 6 | Nivel | Select | Obligatorio | amarillo / naranja / rojo / violeta |
| 7 | Zona afectada | Text | Obligatorio | Según nomenclatura oficial del SMN |
| 8 | Vigencia Desde | DateTime | Obligatorio | Inicio de vigencia del alerta |
| 9 | Vigencia Hasta | DateTime | Obligatorio | Fin de vigencia del alerta |
| 10 | Rangos diarios intersectados | Multi-select | Obligatorio | Madrugada (00-06) / Mañana (06-12) / Tarde (12-18) / Noche (18-00) |
| 11 | Turnos UNS intersectados | Multi-select | Obligatorio | Mañana (06-12) / Tarde (12-18) / Noche (18-22) / Escuelas |
| 12 | Umbrales aplicables a la región | Auto (JSON) | Obligatorio | Carga automática desde Sección 5 del Documento A |
| 13 | Eventos simultáneos en la zona | JSON | Obligatorio | Línea de tiempo del SMN (72h, 4 rangos de 6h) |
| 14 | Acción recomendada según matriz | Auto | Obligatorio | Sección 7 del Documento A (Tabla 7.8) |
| 15 | Operador que completa | User ref | Obligatorio | Usuario autenticado de la Oficina de Recepción |
| 16 | Notificados (CDE) | Multi-user | Obligatorio | Lista CDE con suplentes (Sección 9.1) |
| 17 | Hora de notificación | Timestamp | Auto | Al enviar notificaciones |
| 18 | Medios utilizados | Multi-select | Obligatorio | Alerthor / RACUNS / App / SMS / Email / Teléfono / Megafonía |
| 19 | Observaciones | Text | Opcional | Notas adicionales del operador |
| 20 | Estado | Enum | Auto | activa / cesada / vencida |

### 5.2. Datos de la Línea de Tiempo (SMN)

> **Regla obligatoria (Sección 6.3):** El operador abrirá el detalle de la zona y leerá la línea de tiempo completa antes de decidir. No se debe decidir únicamente por el color del mapa.

| Dato | Tipo | Descripción |
|------|------|-------------|
| Vigencia total | 72 horas | Evolución prevista a 3 días |
| Rango 1 | 00:00 – 06:00 | Madrugada |
| Rango 2 | 06:00 – 12:00 | Mañana |
| Rango 3 | 12:00 – 18:00 | Tarde |
| Rango 4 | 18:00 – 00:00 | Noche |
| Eventos por rango | JSON | Alerta/Advertencia/ACP activo en cada rango |
| Fenómenos simultáneos | JSON | Más de un alerta/advertencia/ACP no son excluyentes |
| Alertas por temperatura | Boolean | SAT-Temperaturas no poseen línea de tiempo |

### 5.3. Umbrales Regionales Patagonia (Sección 5 Documento A)

> Fuente: SMN, Módulo "Umbrales para los Alertas", 2.ª edición 2024 (Anaya y otros, 2020)

| Fenómeno | Amarillo | Naranja | Rojo |
|----------|----------|---------|------|
| Lluvias / Tormentas | 15 mm en 12 h ó 30 mm en 24 h | 30 mm en 12 h ó 60 mm en 24 h | 60 mm en 12 h ó 90 mm en 24 h |
| Viento sostenido | 55 km/h | 75 km/h | 90 km/h |
| Viento ráfagas | 65 km/h | 90 km/h | 110 km/h |
| Nevadas | En zonas bajas donde el fenómeno es raro, con acumulación = amarillo a priori | — | — |

**Notas operativas:**
- Para amarillo y naranja: acumulado en 12 h (sin descartar lluvias intensas en períodos más cortos)
- Para rojo: acumulado en 24 h
- Los umbrales son dinámicos y públicos
- La Oficina de Recepción verificará periódicamente su vigencia en el sitio del SMN

### 5.4. Matriz de Decisión por Nivel (Tabla 7.8 Documento A)

| Situación SMN | Actividades presenciales | Aire libre / campo | Acción clave | Tipo mensaje |
|---------------|--------------------------|--------------------:|--------------|--------------|
| Verde | Normales | Normales | Monitoreo rutinario | Ninguno |
| Amarillo | Normales en aulas | Suspendidas | Difusión preventiva y prealerta | M1 |
| Naranja antes del corte | Suspendidas en turno afectado | Suspendidas | Decidir y difundir antes del corte | M2 |
| Naranja/Rojo o ACP durante cursada | Cese inmediato | Suspendidas | Confinamiento interno; NO evacuar al exterior | M4 |
| Rojo | Suspensión total | Suspendidas | Cierre de accesos; CDE pleno | M4 / M2 |
| Advertencia violeta | Según impacto transporte | Suspendidas salidas/traslados por ruta | Evaluar demora de turnos | M1 adaptado |
| Temperaturas Naranja/Rojo | Virtualidad asincrónica o continuidad protegida | Suspendidas | Medidas de protección y asistencia prioritaria | M2 adaptado |

### 5.5. Ventanas Horarias de Decisión (Sección 6.1 Documento A)

| Turno Académico / Laboral | Horario de Funcionamiento | Horario de Decisión y Difusión Oficial |
|---------------------------|---------------------------|----------------------------------------|
| Turno Mañana | 06:00 a 12:00 hs | **22:00 hs del día anterior** |
| Turno Tarde | 12:00 a 18:00 hs | **10:00 hs del mismo día** |
| Turno Noche | 18:00 a 22:00 hs | **16:00 hs del mismo día** |

**Regla de oro:** Si el SMN emite Alerta Naranja o Roja cuya línea de tiempo se ubica dentro de un turno activo (ACP), la decisión de suspensión deberá adoptarse y difundirse **antes** de la hora de difusión correspondiente. Vencido el horario con el fenómeno en desarrollo, la decisión cambia de "suspensión de actividades" a **"confinamiento en sede"** (Sección 7.7).

### 5.6. Rutina de Monitoreo (Sección 6.2 Documento A)

| Hora | Acción | Registro en app |
|------|--------|-----------------|
| 06:00 | Lectura de actualización rutinaria del SAT; confirmación o ajuste del Turno Mañana | ✅ Check + observaciones |
| 10:00 | Hora de corte del Turno Tarde; verificación línea de tiempo y detalle zonal | ✅ Check + decisión |
| 16:00 | Hora de corte del Turno Noche; verificación línea de tiempo y detalle zonal | ✅ Check + decisión |
| 18:00 | Lectura de actualización rutinaria del SAT | ✅ Check |
| 19:00 | Lectura del SAT-Temperaturas Extremas | ✅ Check |
| 22:00 | Hora de corte del Turno Mañana del día siguiente | ✅ Check + decisión |
| Extraordinaria | Ante toda actualización adicional del SMN, advertencia o ACP recibido | ⚠️ Registro inmediato |

### 5.7. Ficha del Alerta – Formato Digital para la App

```json
{
  "ficha_id": "UNS-2027-0001",
  "fecha_hora_recepcion": "2027-01-15T06:32:00-03:00",
  "fuente": "web_smn",
  "evento": "alerta",
  "fenomeno": "tormenta",
  "nivel": "naranja",
  "zona_afectada": "Bahía Blanca - sudoeste de la provincia de Buenos Aires",
  "vigencia_desde": "2027-01-15T12:00:00-03:00",
  "vigencia_hasta": "2027-01-16T06:00:00-03:00",
  "rangos_diarios": ["tarde", "noche", "madrugada"],
  "turnos_uns_intersectados": ["tarde", "noche"],
  "umbrales_aplicables": {
    "lluvia": "30 mm en 12 h",
    "viento_sostenido": "75 km/h",
    "viento_rafagas": "90 km/h"
  },
  "eventos_simultaneos": [
    {"fenomeno": "tormenta", "nivel": "naranja", "rango": "tarde"},
    {"fenomeno": "viento", "nivel": "amarillo", "rango": "noche"}
  ],
  "linea_tiempo_72h": [
    {"rango": "madrugada_00_06", "eventos": []},
    {"rango": "manana_06_12", "eventos": []},
    {"rango": "tarde_12_18", "eventos": ["tormenta_naranja"]},
    {"rango": "noche_18_00", "eventos": ["tormenta_naranja", "viento_amarillo"]},
    {"rango": "dia2_madrugada", "eventos": ["viento_amarillo"]},
    {"rango": "dia2_manana", "eventos": []},
    {"rango": "dia2_tarde", "eventos": []},
    {"rango": "dia2_noche", "eventos": []}
  ],
  "accion_recomendada": "Suspender turno tarde y noche. Difundir antes de las 10:00 hs.",
  "operador": {"id": 1042, "nombre": "García, Juan"},
  "notificados_cde": [
    {"rol": "Rectorado", "titular": "Daniel Vega", "suplente": "Andrea S. Castellano"},
    {"rol": "SHST", "titular": "Guillermo E. Dominella", "suplente": "—"},
    {"rol": "Infraestructura", "titular": "Gonzalo J. Gilardi", "suplente": "—"}
  ],
  "hora_notificacion": "2027-01-15T06:35:00-03:00",
  "medios_utilizados": ["alherthor_ch1", "app_uns", "sms", "email"],
  "observaciones": "Posible granizo según detalle zonal. Verificar motobombas Alem.",
  "estado": "activa"
}

```
---

## ANEXO 6 RESUMEN: Checklist de Pruebas de Notificaciones Críticas

**Pruebas Android**

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

**Pruebas iOS**
- Critical Alert con app cerrada
- Critical Alert con pantalla bloqueada
- Time Sensitive Notification
- Sonido crítico personalizado
- Voz TTS
- Vibración específica
- Wake up de pantalla

**Pruebas Generales**
- Notificación recibida en menos de 5 segundos
- Confirmación de recepción registrada
- Respuesta rápida desde notificación
- Funcionamiento offline (cola local)
- Sincronización al recuperar conexión
- Pruebas con 100+ dispositivos simultáneos
- Pruebas de redundancia (3 canales)

---

# CHECKLIST DE PRUEBAS DE NOTIFICACIONES CRÍTICAS
## Sistema de Gestión de Emergencias UNS – App tipo BomberBOT

**Responsable:** Equipo QA + Dirección General de Telecomunicaciones UNS
**Frecuencia mínima:** Antes de cada release a producción + prueba trimestral de difusión masiva (Documento C, Sección Pruebas y Simulacros) + simulacros de mesa trimestrales (Documento A, Sección 11)
**Criterio de aceptación:** 100% de pruebas críticas aprobadas antes de cada pase a producción. Cualquier falla crítica bloquea el despliegue.

---

## 6.1. PRUEBAS DE ALARMA EN ANDROID

### 6.1.1. Estados de la app

| # | Prueba | Condición inicial | Resultado esperado | Aprobado |
|---|--------|-------------------|--------------------|:--------:|
| A-01 | Alarma con app completamente cerrada | App cerrada con swipe-away | Alarma suena + vibra + voz TTS | ☐ |
| A-02 | Alarma con app en segundo plano | App minimizada | Alarma suena + vibra + voz TTS | ☐ |
| A-03 | Alarma con app abierta y visible | App en foreground | Alarma + pantalla full-screen | ☐ |
| A-04 | Alarma con pantalla bloqueada | Pantalla apagada con PIN/huella | Despierta pantalla + full-screen intent | ☐ |
| A-05 | Alarma con pantalla apagada | Pantalla negra total | Enciende pantalla + muestra alerta | ☐ |
| A-06 | Alarma con modo silencio | Volumen en silencio | Alarma suena (override) + vibra | ☐ |
| A-07 | Alarma con modo No Molestar (DND) | DND activado | Alarma suena (prioridad crítica bypass DND) | ☐ |
| A-08 | Alarma con modo avión | Sin conexión de red | Recibe al recuperar conexión (cola local) | ☐ |
| A-09 | Alarma con ahorro de batería activo | Modo ahorro de energía | Alarma suena (app en lista blanca de batería) | ☐ |
| A-10 | Alarma con batería crítica (<5%) | Batería muy baja | Alarma suena | ☐ |
| A-11 | Alarma con optimización de batería (Doze) | Doze mode activo | Alarma suena (excluida de Doze) | ☐ |
| A-12 | Alarma tras reinicio del dispositivo | Dispositivo recién encendido | Service restaurado + alarmas activas | ☐ |
| A-13 | Alarma con app recién instalada | Primer uso | Solicita permisos + funciona tras configuración | ☐ |

### 6.1.2. Sonido, vibración y voz

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| A-14 | Volumen al máximo | Suena con AudioManager.STREAM_ALARM al 100% | ☐ |
| A-15 | Volumen al mínimo | Override automático a volumen máximo para alarmas críticas | ☐ |
| A-16 | Vibración en patrón específico | Patrón: 0, 500, 200, 500, 200, 1000 (ms) | ☐ |
| A-17 | Voz TTS reproduciendo mensaje | "Alerta Naranja por tormenta. Confinamiento inmediato." | ☐ |
| A-18 | Voz TTS en español rioplatense | Pronunciación correcta y clara | ☐ |
| A-19 | Sonido diferenciado por nivel | Amarillo: moderado / Naranja: fuerte / Rojo: máximo / ACP: máximo urgente | ☐ |
| A-20 | Sonido en loop hasta respuesta | Repite cada 30 seg hasta respuesta o timeout de 5 min | ☐ |
| A-21 | Cancelación de alarma al responder | Alarma se detiene al tocar cualquier botón de respuesta | ☐ |
| A-22 | Audio con auriculares conectados | Alarma suena por altavoz Y auriculares | ☐ |
| A-23 | Audio con Bluetooth conectado | Alarma suena por altavoz del dispositivo (override BT) | ☐ |

### 6.1.3. Permisos y configuración del sistema

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| A-24 | Permiso de notificaciones (Android 13+) | Solicitado en primer uso con explicación clara | ☐ |
| A-25 | Permiso SCHEDULE_EXACT_ALARM (Android 12+) | Solicitado y otorgado | ☐ |
| A-26 | Permiso ACCESS_NOTIFICATION_POLICY | Solicitado para bypass de DND | ☐ |
| A-27 | Exclusión de Battery Optimization | Guía paso a paso mostrada al usuario | ☐ |
| A-28 | Autostart / Launch manager | Guía específica según fabricante detectado | ☐ |
| A-29 | WakeLock funcional | Pantalla se enciende automáticamente al recibir alarma | ☐ |
| A-30 | FullScreenIntent | Se muestra pantalla completa sobre lock screen | ☐ |
| A-31 | Foreground Service activo | Notificación persistente visible + proceso en memoria | ☐ |
| A-32 | Permiso de ubicación (opcional) | Solicitado para registro de ubicación en respuestas | ☐ |
| A-33 | Permiso de cámara (checklists) | Solicitado solo al usar función de foto | ☐ |

### 6.1.4. Pruebas por fabricante (customizaciones agresivas de Android)

| # | Fabricante / UI | Modelos de prueba | Prueba específica | Aprobado |
|---|-----------------|-------------------|-------------------|:--------:|
| A-34 | Samsung (One UI) | Galaxy A/S series | Autostart + Battery saver + Sleeping apps | ☐ |
| A-35 | Xiaomi (MIUI/HyperOS) | Redmi Note, Mi, POCO | Autostart + Battery saver + Lock apps | ☐ |
| A-36 | Huawei (EMUI/HarmonyOS) | P/Y/Mate series | App launch + Battery optimization | ☐ |
| A-37 | Motorola (Near Stock) | Moto G/Edge | Stock optimization + Moto Display | ☐ |
| A-38 | Oppo (ColorOS) | A/Reno series | Auto-launch + Battery optimization | ☐ |
| A-39 | Google Pixel (Stock) | Pixel 6/7/8/9 | Stock + Doze exclusion + Adaptive Battery | ☐ |
| A-40 | Otros (ZTE, Lenovo, LG) | Modelos comunes UNS | Basic alarm test + notification permissions | ☐ |

### 6.1.5. Pruebas de red y entrega de notificaciones

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| A-41 | FCM high priority con WiFi | Notificación recibida en <5 segundos | ☐ |
| A-42 | FCM high priority con 4G/5G | Notificación recibida en <5 segundos | ☐ |
| A-43 | FCM high priority con 3G | Notificación recibida en <15 segundos | ☐ |
| A-44 | FCM con app en Doze mode | Entrega inmediata (high priority override) | ☐ |
| A-45 | Sin conexión → reconexión | Cola local + sincronización automática | ☐ |
| A-46 | 100 dispositivos simultáneos | Todos reciben en <10 segundos | ☐ |
| A-47 | 1.000 dispositivos simultáneos | Todos reciben en <30 segundos | ☐ |
| A-48 | 5.000 dispositivos simultáneos | Todos reciben en <60 segundos | ☐ |

---

## 6.2. PRUEBAS DE ALARMA EN iOS

### 6.2.1. Estados de la app

| # | Prueba | Condición inicial | Resultado esperado | Aprobado |
|---|--------|-------------------|--------------------|:--------:|
| I-01 | Critical Alert con app cerrada | App cerrada con swipe | Alarma suena + vibra + voz TTS | ☐ |
| I-02 | Critical Alert con app en background | App minimizada | Alarma suena + vibra + voz TTS | ☐ |
| I-03 | Critical Alert con app abierta | App en foreground | Alarma + pantalla full-screen | ☐ |
| I-04 | Critical Alert con pantalla bloqueada | Lock screen activo | Despierta pantalla + muestra alerta | ☐ |
| I-05 | Critical Alert con pantalla apagada | Pantalla negra | Enciende pantalla | ☐ |
| I-06 | Critical Alert con switch silencio | Switch lateral en silencio | **Suena** (Critical Alert override) | ☐ |
| I-07 | Critical Alert con No Molestar / Focus | DND / Focus activado | **Suena** (Time Sensitive bypass) | ☐ |
| I-08 | Critical Alert con modo avión | Sin conexión | Recibe al reconectar (APNs retiene) | ☐ |
| I-09 | Critical Alert con Low Power Mode | Ahorro batería activo | Alarma suena | ☐ |
| I-10 | Critical Alert con Focus personalizado | Modo concentración activo | Alarma suena (Time Sensitive bypass) | ☐ |

### 6.2.2. Sonido, vibración y voz

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| I-11 | Sonido crítico personalizado | defaultCriticalSound con volumen crítico | ☐ |
| I-12 | Voz TTS reproduciendo mensaje | "Alerta Naranja por tormenta. Confinamiento inmediato." | ☐ |
| I-13 | Vibración háptica crítica | Patrón haptic específico para emergencia | ☐ |
| I-14 | Sonido en loop hasta respuesta | Repite hasta respuesta o timeout | ☐ |
| I-15 | Cancelación al responder | Alarma se detiene inmediatamente | ☐ |
| I-16 | Audio con AirPods conectados | Alarma suena por altavoz del iPhone (override) | ☐ |

### 6.2.3. Permisos y aprobación de Apple

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| I-17 | Solicitud permiso notificaciones | Prompt estándar iOS con explicación | ☐ |
| I-18 | Aprobación Critical Alerts (App Store Connect) | Entitlement aprobado por Apple vigente | ☐ |
| I-19 | Entitlement Critical Alerts en Xcode | Configured in Signing & Capabilities | ☐ |
| I-20 | UNNotificationSound.defaultCriticalSound | Sonido crítico funciona en dispositivo real | ☐ |
| I-21 | Time Sensitive Notifications (iOS 15+) | interruptionLevel: .timeSensitive funciona | ☐ |
| I-22 | PushKit VoIP como fallback | Notificación VoIP si APNs estándar falla | ☐ |
| I-23 | Notification Service Extension | Personalización de notificación en background | ☐ |

### 6.2.4. Pruebas de red y entrega

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| I-24 | APNs priority 10 con WiFi | Entrega inmediata (<5 seg) | ☐ |
| I-25 | APNs priority 10 con 4G/5G | Entrega inmediata (<5 seg) | ☐ |
| I-26 | Sin conexión → reconexión | APNs retiene + entrega al reconectar | ☐ |
| I-27 | 100 dispositivos iOS simultáneos | Todos reciben en <10 segundos | ☐ |

---

## 6.3. PRUEBAS EN WEB (PWA / PANEL DE ADMINISTRACIÓN)

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| W-01 | Notification API con requireInteraction | Notificación persiste hasta interacción | ☐ |
| W-02 | Service Worker en background | Notificación con navegador minimizado | ☐ |
| W-03 | Web Audio API | Sonido de alarma se reproduce | ☐ |
| W-04 | Wake Lock API | Pantalla no se apaga durante alerta | ☐ |
| W-05 | Push API subscription | Subscription activa y válida | ☐ |
| W-06 | visibilitychange event | Alerta visible si pestaña activa | ☐ |
| W-07 | Chrome (desktop) | Funciona correctamente | ☐ |
| W-08 | Firefox (desktop) | Funciona correctamente | ☐ |
| W-09 | Safari (desktop) | Funciona correctamente (verificar limitaciones) | ☐ |
| W-10 | Edge (desktop) | Funciona correctamente | ☐ |
| W-11 | Mobile Chrome (Android) | Funciona como PWA instalada | ☐ |
| W-12 | Mobile Safari (iOS) | Derivar a app nativa para alarmas críticas | ☐ |

---

## 6.4. PRUEBAS FUNCIONALES POR NIVEL SMN (Documento A, Sección 7)

| # | Nivel SMN | Prueba | Resultado esperado | Aprobado |
|---|-----------|--------|--------------------|:--------:|
| F-01 | Verde | Alerta verde recibida | Monitoreo rutinario. Sin alarma. Solo registro en log. | ☐ |
| F-02 | Amarillo | Alerta amarilla → M1 | Notificación estándar + sonido moderado + vibración leve | ☐ |
| F-03 | Naranja (antes del corte) | Alerta naranja → M2 | Alarma crítica + voz + vibración. Difusión antes de hora de corte (22:00/10:00/16:00). | ☐ |
| F-04 | Naranja (durante cursada) | Naranja durante actividades | Cese inmediato + confinamiento. Alarma máxima. NO evacuar. | ☐ |
| F-05 | Rojo | Alerta roja → M4 | Alarma máxima + voz + vibración intensa. Cierre de accesos. CDE pleno. | ☐ |
| F-06 | ACP | ACP recibido (vigencia 1-3 h) | Alarma crítica inmediata + full-screen + confinamiento. NO evacuar. | ☐ |
| F-07 | ACP vence | Vigencia del ACP finalizada | CDE evalúa reanudación. Notificación de estado actualizado. | ☐ |
| F-08 | Advertencia violeta | Niebla/humo/polvo/ceniza | Evaluación transporte. Notificación estándar. | ☐ |
| F-09 | SAT-Temperaturas | Naranja/Rojo calor o frío extremo | Notificación al CDE antes de las 22:00 hs. Evaluación. | ☐ |
| F-10 | Eventos simultáneos | Tormenta naranja + viento amarillo | Muestra AMBOS eventos. No se omite ninguno (Sección 4.3). | ☐ |
| F-11 | Cancelación (M6) | Cese de medidas → Verde | Notificación de cese a todos. M6 difundido por mismos canales. | ☐ |
| F-12 | Emergencia imprevista | Fuera de ventanas horarias | Activación en cualquier horario (Documento C, Anexo A). | ☐ |
| F-13 | Línea de tiempo | Lectura de 72h en 4 rangos | App muestra línea de tiempo completa antes de decidir (Sección 6.3). | ☐ |
| F-14 | Ficha del Alerta | Completar Anexo B digital | Todos los campos obligatorios validados. | ☐ |

---

## 6.5. PRUEBAS DE RESPUESTA DEL USUARIO

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| R-01 | Botón "En camino" | Registra respuesta + timestamp + ubicación GPS | ☐ |
| R-02 | Botón "Retrasado" | Registra respuesta + timestamp | ☐ |
| R-03 | Botón "No disponible" | Registra respuesta + timestamp | ☐ |
| R-04 | Botón "Recibido" (confirmación) | Registra confirmación de lectura | ☐ |
| R-05 | Respuesta desde notificación (sin abrir app) | Funciona desde la notificación expandida | ☐ |
| R-06 | Respuesta desde lock screen | Funciona sin desbloquear el dispositivo | ☐ |
| R-07 | Respuesta desde full-screen alert | Funciona en pantalla completa de alarma | ☐ |
| R-08 | Sin respuesta en 5 minutos | Recordatorio automático (re-alarma) | ☐ |
| R-09 | Sin respuesta en 10 minutos | Escalamiento al supervisor/mayordomo | ☐ |
| R-10 | Dashboard en tiempo real (WebSocket) | Estado del personal actualizado en <2 seg | ☐ |
| R-11 | Múltiples respuestas (cambio de estado) | Última respuesta prevalece. Historial registrado. | ☐ |
| R-12 | Respuesta offline → sincronización | Guardada localmente + sincronizada al reconectar | ☐ |
| R-13 | Escucha permanente CH1 (Alerthor) | En Naranja/Rojo, indicación de escucha activa (Documento A, Sección 10) | ☐ |

---

## 6.6. PRUEBAS DE CASCADA DE MENSAJES (Documento C, Sección Cascada)

| # | Capa | Prueba | Resultado esperado | Aprobado |
|---|------|--------|--------------------|:--------:|
| C-01 | Capa 1: digital | Web, Moodle, correo, redes sociales | Todos reciben en <1 minuto | ☐ |
| C-02 | Capa 2: radial | AM UNS → FM UTN-FRBB dúplex | Emisión radial verificada y grabada | ☐ |
| C-03 | Capa 3: predios | Megafonía, pantallas, alarmas en todos los predios | Activación verificada en cada predio | ☐ |
| C-04 | Capa 4: telefonía | SMS masivo a toda la comunidad | SMS recibidos en <2 minutos | ☐ |
| C-05 | Capa 5: presencial | Mayordomías, escuelas, brigadas | Confirmación de recepción presencial | ☐ |
| C-06 | Redundancia | Mínimo 3 canales simultáneos | Verificado en cada emisión (Documento A, Sección 10) | ☐ |
| C-07 | Confirmación de recepción | Registro por nivel de la cascada | Log de quién recibió y cuándo | ☐ |
| C-08 | Registro de difusión | Anexo B del Documento C | Log completo con timestamps por capa | ☐ |
| C-09 | Repetición según matriz | Re-emisión si no hay confirmación | Sistema re-envía automáticamente | ☐ |
| C-10 | Cascada institucional | DCI/Rectorado → Decanos → Mayordomías → Cátedras → Estudiantes | Cada nivel confirma antes de pasar al siguiente | ☐ |
| C-11 | Adaptación sin modificación | Unidades adaptan formato pero NO contenido sustantivo | Verificado que contenido no se altera | ☐ |
| C-12 | Formatos accesibles | Sonora + visual alto contraste + textual simple | Tres formatos generados automáticamente | ☐ |

---

## 6.7. PRUEBAS DE CUSTODIA ESCOLAR (Documento A, Sección 8)

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| E-01 | M5 enviado a familias | Recibido por padres/tutores de la escuela afectada | ☐ |
| E-02 | Registro de retiro con DNI | Sistema valida DNI contra listado de adultos autorizados | ☐ |
| E-03 | DNI no autorizado | Sistema BLOQUEA el retiro y muestra error claro | ☐ |
| E-04 | Registro de retiro con firma digital | Firma capturada en pantalla táctil | ☐ |
| E-05 | Registro completo (Anexo C) | Fecha, hora, alumno, adulto, DNI, vínculo, firma, observaciones | ☐ |
| E-06 | Egreso por ruta segura | Confirmación de salida alejada de ventanas, árboles y estructuras | ☐ |
| E-07 | Reporte a Oficina de Recepción | Nómina de retirados + en custodia enviada automáticamente | ☐ |
| E-08 | Custodia extendida (corte transporte) | Guardia activa + agua + resguardo + comunicación con Base Central | ☐ |
| E-09 | Comunicación con Base Central | Vía handy VHF o teléfono registrado | ☐ |
| E-10 | Prohibición de retiro sin tutor | Sistema impide retiro sin padre/madre/tutor acreditado (Sección 8.1) | ☐ |

---

## 6.8. PRUEBAS DE OFFLINE Y SINCRONIZACIÓN

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| O-01 | Checklist AT-01 completado sin conexión | Guardado en base de datos local | ☐ |
| O-02 | Checklist AT-02 completado sin conexión | Guardado en base de datos local | ☐ |
| O-03 | Respuesta a emergencia registrada sin conexión | Guardada en cola local | ☐ |
| O-04 | Reconexión → sincronización automática | Datos sincronizados sin conflictos ni duplicados | ☐ |
| O-05 | Conflicto de sincronización | Resolución automática (último timestamp) o manual | ☐ |
| O-06 | Indicador visual offline/online | Banner visible en la app indicando estado | ☐ |
| O-07 | Modo avión → completar checklist | Funciona completamente offline | ☐ |
| O-08 | Fotos/evidencias offline | Guardadas localmente + sincronizadas al reconectar | ☐ |
| O-09 | Firma digital offline | Guardada localmente + sincronizada | ☐ |
| O-10 | App cerrada → reconexión | Datos pendientes sincronizados al abrir | ☐ |

---

## 6.9. PRUEBAS DE PERFORMANCE Y CARGA

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| P-01 | 1.000 usuarios simultáneos | Sistema responde en <2 seg | ☐ |
| P-02 | 5.000 usuarios simultáneos | Sistema responde en <5 seg | ☐ |
| P-03 | 10.000 usuarios simultáneos | Sistema responde en <10 seg | ☐ |
| P-04 | 10.000 notificaciones push en 1 minuto | Todas entregadas correctamente | ☐ |
| P-05 | WebSocket con 5.000 conexiones activas | Estado en tiempo real funcional | ☐ |
| P-06 | Base de datos con 100.000 registros | Queries en <500ms | ☐ |
| P-07 | API response time promedio | <200ms | ☐ |
| P-08 | Panel web con 500 usuarios simultáneos | Dashboard funcional y responsivo | ☐ |
| P-09 | Scraping SMN cada 5 minutos | Datos actualizados sin timeout | ☐ |
| P-10 | Generación de informe post-activación (72h) | Generado en <10 segundos | ☐ |

---

## 6.10. PRUEBAS DE SEGURIDAD

| # | Prueba | Resultado esperado | Aprobado |
|---|--------|--------------------|:--------:|
| S-01 | Autenticación JWT | Token válido requerido en cada request | ☐ |
| S-02 | Token expirado | Redirección a login. Sin acceso a datos. | ☐ |
| S-03 | Roles y permisos (14 tipos de usuario) | Usuario no accede a módulos sin permiso | ☐ |
| S-04 | Datos de custodia escolar | Cifrados en tránsito (HTTPS) y en reposo | ☐ |
| S-05 | DNI de adultos autorizados | No expuestos en respuestas API a usuarios sin permiso | ☐ |
| S-06 | Logs de auditoría | Toda acción crítica registrada (usuario, IP, timestamp) | ☐ |
| S-07 | Cumplimiento Ley 25.326 | Datos personales protegidos. Consentimiento registrado. | ☐ |
| S-08 | Inyección SQL | Prevenida con prepared statements / ORM | ☐ |
| S-09 | XSS en panel web | Prevenida con sanitización de inputs | ☐ |
| S-10 | CSRF en formularios | Prevenida con tokens anti-CSRF | ☐ |
| S-11 | Claves de Firebase | Solo en servidor. No expuestas en cliente. | ☐ |
| S-12 | Backup y recuperación | Backup diario funcional. Restauración probada. | ☐ |
| S-13 | Comunicación con familias de afectados | Individual, reservada, verificada (Documento C, Reglas) | ☐ |
| S-14 | Agenda de contacto operativo AT-02 | Acceso restringido. Distribución controlada. | ☐ |

---

## 6.11. SIMULACROS INTEGRADORES (Documento A Sección 11 + Documento C Sección Pruebas)

| # | Simulacro | Frecuencia | Participantes | Criterio de éxito | Aprobado |
|---|-----------|------------|---------------|-------------------|:--------:|
| SIM-01 | Simulacro de mesa: alerta naranja → suspensión de turno | Trimestral | CDE + DCI + Mayordomos + Telecomunicaciones | Decisión en <15 min. Difusión en <30 min. | ☐ |
| SIM-02 | Simulacro de mesa: ACP durante cursada → confinamiento | Trimestral | CDE + Docentes + Seguridad + Mayordomos | Confinamiento en <5 min. Sin evacuación. | ☐ |
| SIM-03 | Simulacro integral: evacuación + custodia escolar | Anual | Todos los actores | Evacuación ordenada. Custodia verificada. | ☐ |
| SIM-04 | Prueba trimestral de difusión masiva (todos los predios) | Trimestral | DCI + Telecomunicaciones + Mayordomos | Verificación de recepción en todos los predios y escuelas | ☐ |
| SIM-05 | Prueba trimestral AM-FM transmisión conjunta | Trimestral | Radio AM UNS + FM UTN-FRBB + Vocería | Transmisión dúplex exitosa | ☐ |
| SIM-06 | Prueba radial semanal integrada | Semanal | Telecomunicaciones | Todas las bases y portátiles responden | ☐ |
| SIM-07 | Simulacro de comunicaciones degradadas (RACUNS) | Trimestral | Telecomunicaciones + CDE | Migración a RACUNS exitosa. ECD documentada. | ☐ |
| SIM-08 | Simulacro post-activación real | Post-evento real | Todos | Informe ≤72 horas con lecciones aprendidas | ☐ |
| SIM-09 | Simulacro de caída de Starlink S1 | Trimestral | Telecomunicaciones + Sistemas | Conmutación manual <30 min. Registro completo. | ☐ |
| SIM-10 | Simulacro de despliegue Starlink S3 (móvil) | Trimestral | Telecomunicaciones | Puesta en servicio <30 min. Apuntamiento correcto. | ☐ |
| SIM-11 | Simulacro de declaración de ECD | Trimestral | Telecomunicaciones + Nodo Central | Regla 2 de 3 Pilares + Triangulación documentada | ☐ |
| SIM-12 | Simulacro integral RACUNS / POT-RACUNS / Nodo Central | Anual | Comité + Telecomunicaciones | Todos los subsistemas operativos | ☐ |

---

## 6.12. CHECKLIST AT-01 INTEGRADO EN LA APP (Sección 12 – Mantenimiento Preventivo de Infraestructura)

| Sistema | Tarea | Frecuencia | Responsable | Resultado | Obs. |
|---------|-------|------------|-------------|:---------:|------|
| Pluviales y bombas de achique | Limpieza de sumideros; prueba de bombas | Semestral / pre-temporada | Dirección de Mantenimiento | ☐ | |
| Cubiertas y desagües | Inspección y sellado | Anual / pre-temporada | Dirección de Mantenimiento | ☐ | |
| Arbolado | Poda preventiva de ejemplares añosos | Semestral | Dirección de Mantenimiento | ☐ | |
| Grupos electrógenos (ATS) | Prueba bajo carga (conjunta con AT-02) | Trimestral | Infraestructura + Telecomunicaciones | ☐ | |
| UPS y bancos de baterías edilicias | Verificación de autonomía y protecciones | Semestral | Dirección de Mantenimiento | ☐ | |
| Red de gas (calderas / comedor) | Prueba de corte de válvulas maestras y electroválvulas | Semestral | Dirección de Mantenimiento | ☐ | |
| Ascensores (SJ670, Alem) | Verificación de llaves de rescate, intercomunicadores y UPS de nivelación | Trimestral | Dirección de Mantenimiento | ☐ | |
| Freezers críticos (-80 °C) | Verificación de conexión a UPS / prioridad en grupo electrógeno | Semestral | Mantenimiento + SHST | ☐ | |
| Flota institucional | Revisión de botiquines, linternas y protocolo de choferes | Semestral | Subsecretaría de Infraestructura | ☐ | |
| Evaluación estructural | Inspección de cubiertas, mampostería y anclajes en patrimonio | Anual (pre-temporada) | Dir. Gral. de Construcciones | ☐ | |
| Reserva estratégica de agua | Rotación de stock y verificación de envases (3L/persona/día) | Semestral | Subsecretaría de Infraestructura | ☐ | |

---

## 6.13. CHECKLIST AT-02 INTEGRADO EN LA APP (Sección 7 – Mantenimiento de Comunicaciones)

| Prueba | Frecuencia | Responsable | Resultado | Obs. |
|--------|------------|-------------|:---------:|------|
| Prueba radial semanal (bases, nodos nuevos y portátiles) | Semanal | Telecomunicaciones | ☐ | |
| Caída de repetidor y migración | Trimestral | Telecomunicaciones | ☐ | |
| Starlink S1 – conmutación manual | Trimestral | Telecomunicaciones | ☐ | |
| Starlink S2 – emisión y enlace FM | Trimestral | Telecomunicaciones + Vocería | ☐ | |
| Starlink S3 – despliegue y apuntamiento | Trimestral | Telecomunicaciones | ☐ | |
| Meshtastic Palihue | Semestral | Telecomunicaciones + LH | ☐ | |
| Conmutación energética de nodos críticos | Semestral | Telecomunicaciones + Infraestructura | ☐ | |
| Prueba de campo integral | Según programa | Telecomunicaciones + predios | ☐ | |
| Simulacro de declaración de ECD (Regla 2 de 3 Pilares + Triangulación) | Trimestral | Telecomunicaciones + Nodo Central | ☐ | |
| Simulacro integral RACUNS / POT-RACUNS / Nodo Central | Anual | Comité + Telecomunicaciones | ☐ | |
| Verificación ROE nodos bibanda nuevos (Colón 80, Escuelas Medias, Palihue) | Al cierre de instalación + semestral | Telecomunicaciones | ☐ | |
| Inspección antena repetidor VHF Alem (50W, respaldo 24-48h) | Mensual | Telecomunicaciones | ☐ | |
| Verificación banco baterías repetidor | Semestral | Telecomunicaciones | ☐ | |
| Fuentes switching 13.8V 30A (tensión, cooler, protecciones) | Semestral | Telecomunicaciones | ☐ | |
| Reserva estratégica de antena (colineal troncal + PL-259) | Semestral | Telecomunicaciones | ☐ | |
| Agenda interna de contacto operativo | Semanal (con prueba radial) | Telecomunicaciones | ☐ | |
| Equipos portátiles (12 asignados + 6 refuerzo + reserva H-12) | Semanal | Telecomunicaciones | ☐ | |

---

## 6.14. INDICADORES DE CUMPLIMIENTO AT-02 (Sección 9)

| Indicador | Meta | Valor obtenido | Cumple |
|-----------|------|:--------------:|:------:|
| % pruebas radiales semanales ejecutadas | 100% | | ☐ |
| % fallas radiales subsanadas en 24 h | ≥ 95% | | ☐ |
| % cobertura en áreas críticas | 100% | | ☐ |
| Autonomía energética de nodos | ≥ 24 h | | ☐ |
| % pruebas programadas (trimestrales y semestrales) ejecutadas | 100% | | ☐ |
| % declaraciones ECD con triangulación documentada | 100% | | ☐ |
| % agenda interna actualizada | 100% | | ☐ |
| Checklist de mantenimiento sin observaciones abiertas | 100% | | ☐ |

---

## 6.15. VERIFICACIÓN DE PREDIOS Y VULNERABILIDADES (AT-01, Sección 3)

| Predio / Sede | Vulnerabilidades críticas a verificar | Confinamiento designado | Verificado |
|---------------|---------------------------------------|-------------------------|:----------:|
| Campus Altos de Palihue | Campo abierto (vientos SO/NO); arbolado gran porte; cubiertas livianas; anegamiento accesos | Pabellones centrales de hormigón | ☐ |
| Complejo Alem / San Juan 670 / 12 de Octubre | Gran altura (SJ670, 7 pisos); superficies vidriadas; anegamiento subsuelos; alta densidad | Pasillos internos y plantas bajas, alejados de ventanas | ☐ |
| Sede Rectorado (Colón 80) / Rondeau 29 / Casa de la Cultura | Patrimonio histórico; cubiertas tradicionales; archivos | BASE RECTORADO con respaldo energético | ☐ |
| Escuelas Preuniversitarias (11 de Abril, Agraria) | Menores; dependencia transporte; talleres/galpones (Agraria) | Aulas internas designadas (Protocolo de Custodia) | ☐ |
| Edificio Anexo Radio AM UNS | Cadena de transmisión AM; nodo de comunicaciones; Sala de Crisis alternativa | Respaldo energético verificado; incluido en prueba radial | ☐ |

---

## 6.16. VERIFICACIÓN DE ROLES CDE Y SUPLENTES (Documento A, Sección 9.1)

| Rol Institucional en Emergencia | Titular | Suplente designado | Verificado |
|--------------------------------|---------|--------------------|:----------:|
| Rectorado (Dirección Superior) | Daniel Vega | Andrea S. Castellano | ☐ |
| Secretaría General de Planificación y Gestión Presupuestaria | Cintia K. Martínez | | ☐ |
| Dirección de Comunicación Institucional (Vocería) | Marcelo Tedesco | | ☐ |
| Secretaría General de Servicios Técnicos y Transformación Digital | Walter R. Cravero | | ☐ |
| Subsecretaría de Infraestructura y Servicios | Gonzalo J. Gilardi | | ☐ |
| Secretaría General de Bienestar Universitario | Ana Paula Murray | | ☐ |
| Secretaría General Académica | Mariano E. Garrido | | ☐ |
| Jefatura de Servicio Higiene, Seguridad y Gestión Ambiental | Guillermo E. Dominella | | ☐ |
| Jefatura de Dpto. de Medicina del Trabajo | Jorge Ignacio Frizza | | ☐ |
| Dirección de Sanidad | Walter Villalba | | ☐ |

**Sala de Crisis primaria:** San Juan 670 – Sala de Consejo de BByF (BASE CENTRAL)
**Sala de Crisis alternativa:** Edificio Anexo Campus Radio UNS

---

## 6.17. REGISTRO DE PRUEBAS – FORMULARIO DE CIERRE

| Campo | Valor |
|-------|-------|
| Fecha de ejecución de pruebas | |
| Versión de app Android | |
| Versión de app iOS | |
| Versión de backend (Laravel) | |
| Versión de panel web | |
| Versión de base de datos (schema) | |
| Responsable QA | |
| Responsable Telecomunicaciones | |
| Responsable Infraestructura | |
| Responsable DCI (Vocería) | |
| Total de pruebas ejecutadas | |
| Pruebas exitosas (✅) | |
| Pruebas fallidas (❌) | |
| Pruebas bloqueadas (⏸️) | |
| Tasa de éxito (%) | |
| Bugs críticos detectados | |
| Bugs menores detectados | |
| Observaciones generales | |
| Acción correctiva (ciclo PDCA – Documento A, Sección 12) | |
| Aprobación para pase a producción | Sí ☐ / No ☐ |
| Firma del responsable | |
| Próxima prueba programada | |

---

## 6.18. CRITERIOS DE BLOQUEO DE RELEASE

Las siguientes condiciones **bloquean automáticamente** el pase a producción:

| Condición | Bloquea |
|-----------|:-------:|
| Cualquier prueba de alarma crítica (A-01 a A-13, I-01 a I-10) fallida | SÍ |
| Alarma no suena con modo silencio/DND activado | SÍ |
| Alarma no funciona con app cerrada | SÍ |
| Notificación no llega en <30 segundos con conexión normal | SÍ |
| Ficha del Alerta no valida todos los campos obligatorios | SÍ |
| Cascada de mensajes no confirma recepción en 3+ canales | SÍ |
| Custodia escolar permite retiro sin DNI autorizado | SÍ |
| Tasa de éxito global < 95% | SÍ |
| Cualquier bug crítico de seguridad (S-01 a S-14) | SÍ |
| Simulacro integrador (SIM-01 a SIM-12) fallido | SÍ |

---

*Septiembre 2026*
*Basado en: Documento A (Anexo Operativo 07-A Rev 0 V2), Documento C (Anexo Operativo 07-C Rev 1 V2), AT-01 (Rev 0 V2), AT-02 (Rev 0 V2)*
*Consolidado Institucional 2026 – PECl-UNS*
