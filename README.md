# AulaFix — Sistema de Gestión de Incidencias Escolares

Aplicación web progresiva (MERN) para la notificación, trazabilidad y resolución de averías en centros educativos, autenticada mediante la pasarela de iPasen/Séneca.

Proyecto desarrollado por EquipoFaltador dentro del módulo de Proyecto Intermodular.

---

## 1. Justificación del Proyecto

En los centros educativos, la comunicación de deficiencias materiales (proyectores inoperativos, cerraduras deterioradas, incidencias de fontanería o averías en puestos de informática) se canaliza habitualmente mediante cuadernos manuscritos en conserjería, notas adhesivas o avisos verbales.

Este flujo analógico provoca retrasos en las reparaciones, pérdida de tiempo lectivo, partes duplicados y una ausencia de trazabilidad sobre el estado de las intervenciones. AulaFix digitaliza este proceso permitiendo que el profesorado y el alumnado registren una avería geolocalizada en menos de 30 segundos utilizando sus credenciales oficiales de Séneca, facilitando al personal de mantenimiento un panel unificado para la gestión y cierre de tickets en tiempo real.

---

## 2. Equipo de Desarrollo

| Miembro | Rol Técnico | Responsabilidad Principal |
|---|---|---|
| Gabriel | Backend Lead & API Architect | API REST en Express, proxy OAuth2 contra Séneca y control de acceso mediante JWT. |
| Álvaro | Frontend Lead & UI/UX | Arquitectura React 18, gestión del estado global con Zustand y diseño responsive con Tailwind CSS. |
| Aarón | Database Manager & Security | Modelado de datos en MongoDB Atlas, optimización de consultas/índices y políticas de minimización RGPD. |
| David | DevOps & QA Lead | Automatización CI/CD, despliegues (Vercel/Render), suite de tests y auditoría de Pull Requests. |

---

## 3. Arquitectura y Stack Tecnológico

- Frontend: React 18, Vite, Tailwind CSS, Zustand, React Router DOM, Axios y Lucide React.
- Backend: Node.js (v20 LTS), Express, Mongoose, JSON Web Tokens (JWT), Dotenv y CORS.
- Base de Datos: MongoDB Atlas (M0 Sandbox, réplica europea en Frankfurt).
- Infraestructura de Despliegue: Vercel (Frontend SPA) y Render (Backend Web Service).
- Autenticación Externa: Pasarela proxy contra la API de iPasen (Junta de Andalucía).
- Calidad y Pruebas: Vitest (Frontend), Jest y Supertest (Backend), ESLint y Prettier.

---

## 4. Instrucciones de Despliegue Local

Las dependencias e implementación funcional se desarrollarán a partir de la UD1.

### Requisitos previos
- Node.js versión 20.x LTS o superior.
- Gestor de paquetes npm.
- Conexión a MongoDB Atlas o instancia local activa.

### Puesta en marcha

1. Clonar el repositorio y situarse en la raíz:
```bash
git clone https://github.com/aarongnaranjo2007-rgb/AulaFix.git
cd AulaFix
```

2. Configuración y ejecución del backend:
```bash
cd server
npm install
cp .env.example .env
npm run dev
```

3. En una segunda terminal, configuración y ejecución del frontend:
```bash
cd ../client
npm install
cp .env.example .env
npm run dev
```

---

## 5. Documentación y Enlaces

- Gestión del Proyecto: [Tablero de Tareas en GitHub Projects](https://github.com/aarongnaranjo2007-rgb/AulaFix/projects)
- Acuerdos y Normas: [Contrato de Equipo (docs/CONTRATO.md)](./docs/CONTRATO.md)
- Propuesta Técnica:
  - [Fase 0: Brainstorming de Ideas (00-brainstorming.md)](./docs/propuesta/00-brainstorming.md)
  - [Fase 1: Detección del Problema y User Personas (01-problema.md)](./docs/propuesta/01-problema.md)
  - [Fase 2: Viabilidad Técnica y Definición del MVP (02-viabilidad-tecnica.md)](./docs/propuesta/02-viabilidad-tecnica.md)
  - [Fase 3: Objetivos SMART y Alcance (03-objetivos-y-alcance.md)](./docs/propuesta/03-objetivos-y-alcance.md)
  - [Fase 4: Recursos, Personas y Gestión (04-recursos.md)](./docs/propuesta/04-recursos.md)
