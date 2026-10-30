# Propuesta Técnica y Plan de Gestión de Proyecto: AulaFix

Documento consolidado de propuesta técnica, alcance operativo y recursos para el desarrollo del sistema de incidencias escolares AulaFix.

- Estudio de desarrollo: EquipoFaltador
- Módulo: Optativa Desarrollo de Aplicaciones Web Fullstack
- Integrantes y roles técnicos:
  - Gabriel: Backend Lead & API Architect
  - Álvaro: Frontend Lead & UI/UX
  - Aarón: Database Manager & Security
  - David: DevOps & QA Lead
- Repositorio oficial: https://github.com/aarongnaranjo2007-rgb/AulaFix

---

## 0. Introducción Global del Proyecto

En el ámbito de la Educación Secundaria y la Formación Profesional, la disponibilidad operativa del equipamiento de las aulas condiciona directamente el desarrollo de la actividad lectiva. Incidencias recurrentes como proyectores con lámparas averiadas, terminales informáticos bloqueados, tomas de corriente inutilizadas o averías en sistemas de ventilación y fontanería entorpecen las dinámicas pedagógicas y exigen una respuesta organizativa rápida.

Tradicionalmente, la comunicación y resolución de estos desperfectos en los centros públicos se ha gestionado mediante canales analógicos: cuadernos manuscritos en conserjería, notas adhesivas o avisos verbales informales en pasillos y salas de profesorado. Este método manual introduce graves deficiencias estructurales:
- Pérdida de tiempo lectivo al obligar al docente o delegado a desplazarse físicamente a conserjería para notificar la avería.
- Multiplicidad de avisos duplicados sobre un mismo elemento deteriorado por falta de visibilidad pública.
- Ausencia de trazabilidad para el personal notificador, que desconoce si el problema ha sido registrado, está en vías de reparación o requiere piezas de sustitución.
- Dificultades organizativas para el personal de mantenimiento y coordinación TIC, quienes carecen de un inventario centralizado y priorizado de actuaciones pendientes.

AulaFix responde a esta necesidad mediante el desarrollo de una Aplicación Web Progresiva (PWA) basada en el stack tecnológico MERN (MongoDB, Express, React y Node.js). La herramienta permite a docentes y alumnado abrir un parte geolocalizado en el centro en menos de 30 segundos, validando su identidad de forma segura mediante las credenciales oficiales de Séneca/iPasen sin almacenar contraseñas corporativas. Al mismo tiempo, conserjería y los equipos técnicos disponen de un cuadro de mandos unificado para catalogar, gestionar y cerrar incidencias en tiempo real.

Este documento formal reúne los resultados de las fases de análisis, viabilidad técnica, delimitación de alcance y planificación de recursos desarrolladas por EquipoFaltador, constituyendo el marco de referencia técnico para la implementación práctica que dará comienzo en la Unidad de Desarrollo 1.

---

## 1. Definición del Problema y Justificación

### 1.1. Contexto Operativo y Dolor Detectado
La gestión reactiva de las averías materiales en centros educativos genera un impacto negativo verificable en la operativa escolar:
1. **Ineficiencia temporal en el aula:** Interrumpir una sesión lectiva para acudir a conserjería supone una pérdida media de entre 5 y 10 minutos por avería, desatendiendo transitoriamente al grupo de alumnos.
2. **Saturación por partes duplicados:** Al no existir constancia compartida del estado del aula, varios docentes que imparten clase en un mismo espacio durante la jornada notifican de manera independiente el mismo fallo, duplicando gestiones innecesarias.
3. **Falta de métricas institucionales:** La dirección del centro y las delegaciones carecen de registros históricos fiables para evaluar el tiempo medio de resolución (MTTR), justificar la renovación de equipamiento informático o reclamar garantías a proveedores.

### 1.2. Perfiles de Usuario (User Personas)

| Perfil | Identificador Representativo | Necesidad Principal | Frustración Actual |
|---|---|---|---|
| Docente | Carmen (Profesora de Secundaria) | Notificar una avería al instante desde el dispositivo móvil del aula sin desatender a sus alumnos. | Desconoce si el proyector que notificó días atrás ha sido revisado o si debe buscar un aula alternativa. |
| Mantenimiento / Conserjería | Manuel (Personal de Mantenimiento) | Recibir partes clasificados por criticidad, tipo de avería y aula con información concisa. | Lidiar con cuadernos físicos con notas ambiguas, ilegibles o avisos de palabra que se traspapelan. |
| Alumnado / Delegación | Marcos (Delegado de Grupo) | Consultar si una avería de su aula ya está registrada para no duplicar el aviso. | Avisar de un enchufe defectuoso y comprobar que tres compañeros ya habían ido individualmente a avisar. |

### 1.3. Análisis de Alternativas y Carencias de Mercado
El examen de soluciones existentes en el entorno educativo y corporativo revela inconvenientes específicos que justifican el desarrollo de AulaFix:
- **Plataformas ITSM corporativas (Jira Service Management, Zendesk):** Diseñadas para entornos empresariales complejos, presentan una sobrecarga de campos y flujos burocráticos que resultan inviables para un uso ágil durante una clase de 50 minutos.
- **Módulos de inventario administrativo (Séneca Inventario):** Enfocados en la catalogación patrimonial y fiscal de los bienes del centro, no ofrecen una interfaz interactiva de reporte operativo ni seguimiento dinámico de incidencias del día a día.
- **Sistemas de tickets genéricos:** Requieren el alta manual de usuarios y la memorización de nuevas credenciales, lo que desincentiva su adopción masiva entre el profesorado y el alumnado frente a la pasarela centralizada de iPasen.

---

## 2. Viabilidad Técnica y Definición del MVP

### 2.1. Arquitectura y Stack Tecnológico
La selección tecnológica adoptada por EquipoFaltador prioriza la rapidez de carga, la portabilidad entre dispositivos y la minimización de costes de infraestructura:
- **Frontend SPA / PWA:** React 18 inicializado sobre Vite, estilización utilitaria mediante Tailwind CSS y control de estado reactivo mediante Zustand. Garantiza una interfaz ligera, adaptada a pantallas táctiles móviles y lista para funcionar como aplicación web de escritorio.
- **Backend API REST:** Node.js v20 LTS estructurado con el framework Express. Controles de acceso basados en middleware, desacoplamiento modular de rutas y controladores, y gestión de esquemas mediante Mongoose.
- **Persistencia de Datos:** MongoDB Atlas alojado en cluster gestionado M0 Sandbox en Frankfurt (región europea). La naturaleza documental de MongoDB permite representar con flexibilidad el ciclo de vida de los partes y las relaciones entre dependencias y categorías.
- **Seguridad y Control de Acceso:** Autenticación delegada contra una pasarela proxy que valida credenciales frente al directorio corporativo de Séneca, emitiendo tokens JWT sin estado. No se persisten contraseñas corporativas en la base de datos de la aplicación.
- **Infraestructura de Despliegue:** Servicios en la nube sin coste con separación de responsabilidades: Vercel para el despliegue del frontend estático y Render para el servicio web backend.

### 2.2. Requisitos Funcionales y Priorización MoSCoW

| Código | Requisito Funcional | Prioridad MoSCoW | Alcance MVP |
|---|---|---|---|
| RF-01 | Inicio de sesión seguro mediante pasarela proxy de Séneca | Must-have | Sí |
| RF-02 | Formulario de reporte simplificado (selección de aula, categoría y descripción) | Must-have | Sí |
| RF-03 | Listado de incidencias activas filtrado por espacio físico | Must-have | Sí |
| RF-04 | Actualización de estado del ticket (Pendiente, En Proceso, Resuelta) | Must-have | Sí |
| RF-05 | Registro de cierre de ticket con justificación técnica de la intervención | Must-have | Sí |
| RF-06 | Adjunto de fotografía acreditativa del desperfecto | Should-have | No |
| RF-07 | Sincronización bidireccional inmediata mediante WebSockets | Should-have | No |
| RF-08 | Localización y apertura automática mediante lectura de código QR de aula | Could-have | No |
| RF-09 | Exportación de informes mensuales de incidencias y métricas en PDF | Could-have | No |
| RF-10 | Notificaciones nativas Push a través de Service Workers | Won't-have | No |

### 2.3. Definición del Producto Mínimo Viable (MVP)
El MVP se circunscribe a los requisitos funcionales indispensables (Must-have):
1. Validación de acceso mediante credenciales de usuario.
2. Formulario de captura rápida capaz de completarse en menos de medio minuto.
3. Panel de consulta por aula que evidencie averías abiertas para evitar duplicidades.
4. Cuadro de mandos operativo donde el personal de mantenimiento modifique los estados y archive las resoluciones.

---

## 3. Objetivos SMART y Delimitación del Alcance

### 3.1. Objetivo General
Diseñar, construir y desplegar en producción una plataforma web multiplataforma que digitalice de forma integral el circuito de reporte, seguimiento y resolución de averías materiales en centros educativos, garantizando una comunicación transparente y eliminando tiempos muertos de gestión.

### 3.2. Objetivos Específicos (SMART)

| Identificador | Descripción del Objetivo | Indicador de Medición | Valor Objetivo | Método de Comprobación |
|---|---|---|---|---|
| OE-01 | Agilidad en el proceso de reporte | Tiempo transcurrido en completar el envío del formulario | Menor a 30 segundos | Pruebas de usabilidad cronometradas con usuarios reales completando el flujo de alta. |
| OE-02 | Eficiencia y seguridad en la autenticación | Tiempo de respuesta de la pasarela proxy de acceso | Menor a 2 segundos | Auditoría de latencia de red en endpoints de autenticación mediante herramientas de API testing. |
| OE-03 | Trazabilidad del estado de las averías | Tiempo de reflejo en cliente ante un cambio de estado | Menor a 1 segundo | Validación de renderizado en cliente tras la actualización de estado en la API. |
| OE-04 | Supresión total de avisos duplicados | Número de reportes idénticos abiertos en una misma aula | Cero partes redundantes | Verificación funcional del aviso visual en interfaz al consultar un aula con avería abierta. |

### 3.3. Plataforma y Usuarios
AulaFix se despliega como una aplicación web accesible desde cualquier navegador compatible con estándares web (Chrome, Firefox, Safari, Edge), con diseño adaptativo optimizado para dispositivos móviles en orientación vertical (viewport base de 390px) y vista expandida de escritorio para puestos de conserjería y coordinación.

Se contemplan tres perfiles funcionales:
- **Perfil Notificador (Profesorado y Alumnado):** Acceso a la consulta de estado de dependencias y apertura de nuevos partes.
- **Perfil Mantenimiento (Conserjería y Servicios Técnicos):** Asignación de tareas, cambio de estados intermedios y formalización del cierre de incidencias.
- **Perfil Directivo / Coordinación TIC:** Supervisión general de partes del centro, auditoría de métricas y mantenimiento del catálogo de aulas.

### 3.4. Exclusiones Explícitas (Lo que no se hará)
Para asegurar el cumplimiento estricto de los plazos docentes y la estabilidad del núcleo operativo, se descartan los siguientes elementos:
- Sin integración de sincronización de inventario patrimonial con Séneca (el sistema gestionará su propio catálogo de dependencias).
- Sin envío de notificaciones mediante SMS o mensajería corporativa push de iPasen.
- Sin pasarelas de pago o gestión económica de pedidos y presupuestos de materiales de reparación.
- Sin salas de conversación o canales de mensajería instantánea abierta entre usuarios en la plataforma.

### 3.5. Hoja de Ruta para Ampliaciones Futuras
1. Generación e impresión de etiquetas con códigos QR vinculados a cada espacio para acceso directo al listado del aula.
2. Soporte para funcionamiento offline y sincronización en segundo plano con Service Workers.
3. Panel estadístico avanzado con cálculo automatizado de tiempos medios de respuesta y averías recurrentes.

---

## 4. Gestión de Recursos, Personas y Repositorio

### 4.1. Roles Técnicos y Responsabilidades

| Integrante | Rol Técnico Asignado | Responsabilidad Principal |
|---|---|---|
| Gabriel | Backend Lead & API Architect | Desarrollo de endpoints REST en Express, proxy de acceso Séneca, controladores y seguridad JWT. |
| Álvaro | Frontend Lead & UI/UX | Arquitectura React 18, control de estado global con Zustand, interfaz Tailwind CSS y responsive. |
| Aarón | Database Manager & Security | Modelado de colecciones en Mongoose, configuración de MongoDB Atlas e índices, y RGPD. |
| David | DevOps & QA Lead | Automatización de flujos de integración continua, despliegues en Render y Vercel, y suites de tests. |

### 4.2. Reparto de Trabajo por Módulos Funcionales

| Módulo | Denominación | Responsable Técnico | Apoyo de Desarrollo |
|---|---|---|---|
| M1 | Identidad y Autenticación Delegada | Gabriel | Aarón |
| M2 | Captura y Alta de Incidencias | Álvaro | Gabriel |
| M3 | Consulta de Dependencias y Control de Duplicidad | Aarón | Álvaro |
| M4 | Ciclo de Vida y Panel de Mantenimiento | David | Gabriel |

### 4.3. Acuerdos de Equipo y Normas de Convivencia
Las directrices de trabajo en equipo, tiempos máximos de respuesta y protocolos de resolución de incidencias internas se encuentran regulados formalmente en:
- [Contrato de Equipo (docs/CONTRATO.md)](./CONTRATO.md)

Dicho marco establece un compromiso de respuesta de un máximo de 12 horas hábiles en los canales de comunicación y la obligatoriedad de que toda contribución a la base de código esté respaldada por una rama de tarea y su correspondiente revisión.

### 4.4. Estrategia de Ramas y Políticas de Integración en Git
Se implementa un flujo ordenado basado en GitFlow:
- **Rama `main`:** Rama protegida de despliegue que aloja exclusivamente versiones estables consolidadas.
- **Rama `develop`:** Rama protegida de desarrollo donde se integran las funcionalidades de cada iteración.
- **Ramas de tarea:** Ramas auxiliares originadas a partir de `develop` con nomenclatura `docs/<nombre-tarea>` o `feat/<nombre-tarea>`.
- **Políticas de protección:** Bloqueo de subidas directas (`git push`) en `main` y en `develop`. Todo cambio requiere la tramitación de un Pull Request con la aprobación explícita de al menos un miembro del equipo tras la revisión del código en GitHub.
- **Limpieza de ramas:** Eliminación automática de ramas de tarea en el servidor tras la fusión exitosa del Pull Request correspondiente.

### 4.5. Estructura de Directorios del Proyecto

```text
AulaFix/
├── client/
│   └── README.md
├── server/
│   └── README.md
├── docs/
│   ├── CONTRATO.md
│   ├── PROPUESTA.md
│   └── propuesta/
│       ├── 00-brainstorming.md
│       ├── 01-problema.md
│       ├── 02-viabilidad-tecnica.md
│       ├── 03-objetivos-y-alcance.md
│       └── 04-recursos.md
├── .gitignore
├── .nvmrc
└── README.md
```
