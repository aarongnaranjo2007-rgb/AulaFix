# AULAFIX — Gestión de Incidencias Escolares

	⁠Aplicación web progresiva (MERN) para el reporte, seguimiento y resolución ágil de averías materiales en centros educativos, autenticada mediante las credenciales oficiales de iPasen/Séneca.

Desarrollado por *EquipoFaltador* en el marco de Optativa-Desarrollo de Aplicaciones Web Fullstack.

---

## 📌 El Problema

En los centros educativos, la comunicación de desperfectos (proyectores inoperativos, persianas trabadas, sanitarios averiados o fallos de red) se gestiona mediante cuadernos manuscritos en conserjería, notas adhesivas o avisos informales en pasillos. Esta falta de digitalización provoca pérdida de tiempo lectivo, saturación del personal de mantenimiento, quejas duplicadas y una ausencia absoluta de trazabilidad sobre el estado de las reparaciones.

*AULAFIX* sustituye ese circuito analógico por una plataforma web móvil que permite a cualquier docente o alumno reportar una avería geolocalizada en menos de 30 segundos utilizando sus claves habituales de Séneca, al tiempo que proporciona a conserjería y coordinación TIC un cuadro de mandos interactivo para gestionar y cerrar los tickets en tiempo real.

---

## 👥 Equipo de Desarrollo

| Integrante | Rol Técnico | Responsabilidad Principal |
|---|---|---|
| *Gabriel* | Backend Lead & API Architect | API REST en Express, proxy OAuth2 contra Séneca, seguridad JWT y endpoints de incidencias. |
| *Alvaro* | Frontend Lead & UI/UX | Arquitectura React 18, stores de Zustand, diseño responsive con Tailwind CSS y accesibilidad móvil. |
| *Aarón* | Database Manager & Security | Modelado de datos en MongoDB Atlas, optimización de consultas/índices y políticas RGPD. |
| *David* | DevOps & QA Lead | Automatización CI/CD, configuración de entornos (Vercel/Render), suite de tests y control de PRs. |

---

## 🛠️ Stack Tecnológico

•⁠  ⁠*Frontend:* React 18, Vite, Tailwind CSS, Zustand, React Router DOM, Axios, Lucide React.
•⁠  ⁠*Backend:* Node.js (v20 LTS), Express, Mongoose, JSON Web Tokens (JWT), Dotenv, Cors.
•⁠  ⁠*Base de Datos:* MongoDB Atlas (M0 Sandbox, réplica europea en Frankfurt).
•⁠  ⁠*Infraestructura de Despliegue:* Vercel (Frontend SPA) y Render (Backend Web Service).
•⁠  ⁠*Autenticación Externa:* Endpoints OAuth2 de la API de iPasen (Junta de Andalucía).
•⁠  ⁠*Testing & Calidad:* Vitest (Frontend), Jest + Supertest (Backend), ESLint y Prettier.

---

## 🚀 Cómo arrancarlo

	⁠Instrucciones preliminares de configuración del entorno de desarrollo. La implementación funcional y ejecución del código se llevará a cabo durante la **UD1.

### Requisitos previos
•⁠  ⁠Node.js ⁠ >= 20.x.x ⁠ (gestionado preferiblemente mediante ⁠ nvm ⁠ ejecutando ⁠ nvm use ⁠).
•⁠  ⁠Gestor de paquetes ⁠ npm ⁠.
•⁠  ⁠Conexión a MongoDB Atlas o instancia local de MongoDB.

### Puesta en marcha (Prevista para UD1)

```bash
# 1. Clonar el repositorio y situarse en la raíz
git clone https://github.com/aarongnaranjo2007-rgb/Aulafix.git
cd Aulafix

# 2. Configuración y arranque del servidor (Backend)
cd server
npm install
cp .env.example .env
npm run dev

# 3. En una segunda terminal, configuración y arranque del cliente (Frontend)
cd ../client
npm install
cp .env.example .env
npm run dev
