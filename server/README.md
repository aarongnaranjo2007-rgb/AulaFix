# AulaFix — Backend (Server)

API REST construida con Node.js y Express, con persistencia en MongoDB Atlas mediante Mongoose y pasarela proxy OAuth2 contra Séneca/iPasen.

##  Estructura prevista
- src/controllers/: Lógica de negocio para autenticación de credenciales, gestión de incidencias y cambio de estados.
- src/middlewares/: Validación de JWT, control de acceso por roles (Profesor, Alumno, Mantenimiento) y sanitización.
- src/models/: Esquemas de MongoDB (User, Incidencia, HistorialEstado).
- src/services/: Proxy HTTP contra la API de iPasen (security/oauth/token e info-session) y proveedor de datos simulados (Mock).

##  Scripts disponibles (UD1)
- npm run dev: Inicia el servidor con recarga automática mediante Nodemon.
- npm run start: Inicia el servidor en modo producción.
- npm run test: Ejecuta la batería de pruebas de integración de endpoints con Jest
