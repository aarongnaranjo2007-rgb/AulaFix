# Fase 4 · Recursos · FixEdu Studio

## Introducción

Este documento detalla los recursos humanos, técnicos y organizativos necesarios para ejecutar el desarrollo de AULAFIX de forma coordinada, profesional y reproducible.

Define la distribución de responsabilidades técnicas y por módulo para los cuatro integrantes del equipo, formaliza los canales de comunicación, enlaza la arquitectura técnica aprobada en la fase 2 y establece la infraestructura de ramas y gestión de tareas que garantizará que cada línea de código llegue a producción mediante revisiones cruzadas obligatorias.

---
## 1. Las personas

### Roles técnicos

Cada integrante asume el liderazgo de una capa técnica del proyecto. El responsable técnico no programa en solitario su capa: define las directrices arquitectónicas, valida los Pull Requests de su área y garantiza la coherencia técnica del código.

| Persona | Rol técnico | De qué responde |
|:---|:---|:---|
| *Gabriel* | *Backend Lead & API Architect* | Arquitectura de la API REST en Express, proxy de autenticación contra Séneca, middleware de autorización JWT, rutas de incidencias y manejo de errores. |
| *Alvaro* | *Frontend Lead & UI/UX* | Arquitectura de la aplicación en React 18, configuración de Zustand para el estado global, maquetación responsive con Tailwind CSS y accesibilidad mobile-first. |
| *Aarón* | *Database Manager & Data Security* | Diseño y modelado de colecciones en MongoDB (Mongoose), optimización de índices, políticas de minimización de datos y cumplimiento del RGPD. |
| *David* | *DevOps & QA Lead* | Configuración de CI/CD, despliegues automáticos en Vercel y Render, suite de tests unitarios (Vitest/Jest), control de versiones y auditoría de Pull Requests. |

### Responsables por módulo

Los 8 requisitos funcionales del MVP (Must-have) se distribuyen en módulos de funcionalidad vertical (desde el modelo de datos hasta la interfaz gráfica). Cada módulo cuenta con un responsable principal y una persona de apoyo:

| Módulo | Requisitos (RF) | Responsable | Apoyo | Alcance del módulo |
|:---|:---|:---|:---|:---|
| *M1: Identidad y Sesión* | RF-01, RF-02 | *Gabriel* | Álvaro | Login contra Séneca, generación y custodia de JWT, middleware de protección de rutas y persistencia mínima de usuario en MongoDB. |
| *M2: Alta de Incidencias* | RF-03, RF-04, RF-05 | *Aarón* | David | Selector en dos pasos de espacio/zona, subida y compresión de fotografías, formulario de reporte rápido y validaciones de cliente. |
| *M3: Consulta y Detección* | RF-06, RF-07 | *David* | Aarón | Panel principal de incidencias, filtros por zona/planta, aviso de incidencia ya existente y vista detallada del ticket. |
| *M4: Ciclo de Vida y Cierre* | RF-08 | *Álvaro* | Gabriel | Cambio interactivo de estados (Pendiente / En reparación / Resuelta), notas de resolución para mantenimiento y refresco automático. |

### Comunicación

Las normas de convivencia, canales oficiales de trabajo, horarios de disponibilidad y acuerdos de nivel de servicio (SLA) para revisión de código están formalizados en nuestro contrato de equipo:
[Ver contrato de equipo en docs/CONTRATO.md](../CONTRATO.md).

Canales principales de trabajo:
- *Discord:* Canal de audio y texto para reuniones diarias (daily standup de 10 minutos) y sesiones de programación por parejas (pair programming).
- *WhatsApp:* Canal exclusivo para avisos urgentes o bloqueos críticos.
- *GitHub Projects & PR Reviews:* Canal formal y asíncrono para la discusión técnica y aprobación de código.

---

## 2. La tecnología

### Stack, servicios y APIs

La arquitectura tecnológica, justificación de librerías y límites de los planes gratuitos están documentados y aprobados en la fase de viabilidad técnica:
[Ver arquitectura detallada y servicios en 02-viabilidad-tecnica.md#sección-2-requisitos-técnicos-frontend-e-infraestructura](./02-viabilidad-tecnica.md#sección-2-requisitos-técnicos-frontend-e-infraestructura).

- *Frontend:* React 18 + Vite + Tailwind CSS + Zustand + React Router v6 + Axios + Lucide React.
- *Backend:* Node.js (v20 LTS) + Express + Mongoose + jsonwebtoken + cors + dotenv.
- *Base de Datos:* MongoDB Atlas (Plan M0 Sandbox, 512 MB, réplica europea en Frankfurt).
- *Infraestructura de Despliegue:* Vercel (Frontend SPA, SSL automático) y Render (Backend Web Service, plan gratuito con ping preventivo).
- *APIs Externas:* API oficial de iPasen (POST security/oauth/token y GET generales/info-session).

### Herramientas de desarrollo

| Para qué | Herramienta | Justificación |
|:---|:---|:---|
| *Editor de código unificado* | *Visual Studio Code* | Extensiones obligatorias compartidas: ESLint, Prettier, Tailwind CSS IntelliSense y GitLens. |
| *Entorno de ejecución Node* | *Node.js v20.x LTS* | Versión fijada mediante archivo .nvmrc en la raíz del repositorio para garantizar paridad absoluta entre los cuatro desarrolladores. |
| *Cliente de pruebas de API* | *Thunder Client / Bruno* | Colección de peticiones JSON versionada dentro del repositorio (tests/api/) para probar endpoints y respuestas de Séneca sin salir de VS Code. |
| *Testing unitario Frontend* | *Vitest + Testing Library* | Integración nativa con Vite, arranque instantáneo y pruebas de componentes y stores de Zustand. |
| *Testing de integración Backend* | *Jest + Supertest* | Estándar para pruebas automatizadas de rutas en Express y validación del middleware de autenticación simulando llamadas a Séneca. |
| *Control de versiones y tablero* | *GitHub + GitHub Projects* | Trazabilidad completa mediante Issues vinculadas a Pull Requests con comprobaciones de estado automáticas. |

---
