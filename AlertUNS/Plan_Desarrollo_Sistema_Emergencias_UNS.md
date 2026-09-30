# PLAN DE DESARROLLO: Sistema de Gestión de Emergencias UNS
## App tipo BomberBOT adaptada a la Universidad Nacional del Sur

**Elaborado por:** Asistente de Desarrollo
**Fecha:** 30 de septiembre de 2026
**Para:** Miguel - Universidad Nacional del Sur
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
- **Oficina de Recepción de Avisos de Emergencia**
- **Mayordomos de Edificios**
- **Directores/Decanos**
- **Docentes y Nodocentes**
- **Estudiantes**
- **Familias** (Escuelas Preuniversitarias)
- **Personal de Mantenimiento**
- **Telecomunicaciones**

---

## 2. ARQUITECTURA TÉCNICA RECOMENDADA

### 2.1. Stack Tecnológico

Dado tu background en PHP/MySQL, te propongo una arquitectura híbrida que aproveche tus conocimientos:

| Componente | Tecnología | Justificación |
|------------|------------|---------------|
| **App Móvil** | **React Native** o **Flutter** | Multiplataforma, notificaciones nativas, rendimiento excelente |
| **Backend API** | **Laravel (PHP)** o **Node.js + Express** | Laravel aprovecha tu conocimiento PHP; Node.js ofrece mejor performance en tiempo real |
| **Base de Datos** | **MySQL** (ya dispones) | Compatible con tu infraestructura existente |
| **Panel Web** | **React.js** o **Vue.js** | Interfaces modernas y responsivas |
| **Notificaciones** | **Firebase Cloud Messaging (FCM)** + **APNs** | Sistema estándar para alertas críticas |
| **Tiempo Real** | **WebSockets** (Laravel Reverb / Socket.io) | Actualizaciones instantáneas |
| **Almacenamiento** | **AWS S3** o similar | Para archivos, checklists, evidencias |
| **Autenticación** | **JWT + OAuth2** | Seguridad robusta |

### 2.2. Diagrama de Arquitectura
