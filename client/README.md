AULAFIX — Frontend (Client)

Aplicación web progresiva construida con React 18 y Vite, estilizada con Tailwind CSS y gestionada con Zustand.

##  Estructura prevista
- src/components/: Componentes atómicos e interactivos (tarjetas de incidencias, botones de acción, selectores).
- src/pages/: Vistas de usuario (Inicio de sesión, Reporte rápido, Listado de incidencias del centro, Detalle).
- src/context/: Stores globales de Zustand (estado de autenticación JWT y caché de incidencias).
- src/services/: Configuración del cliente Axios con interceptores automáticos de cabeceras de autorización.

##  Scripts disponibles (UD1)
- npm run dev: Inicia el servidor de desarrollo local con recarga en caliente (HMR).
- npm run build: Genera la versión de producción optimizada en la carpeta dist/.
- npm run test: Ejecuta los tests unitarios con Vitest.
