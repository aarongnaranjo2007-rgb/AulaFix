# Requisitos funcionales, priorización MoSCoW y MVP
## 1. Requisitos funcionales

Partiendo de los casos de uso de nuestras *user personas* (`01-problema.md`), estas son las 18 funcionalidades principales del sistema:

### Autenticación y gestión de perfil (Séneca / iPasen)
1. El usuario puede iniciar sesión en la plataforma con sus credenciales oficiales de iPasen / Séneca sin necesidad de registrarse manualmente.
2. El usuario puede consultar su perfil y rol asignado automáticamente (profesorado, alumnado o personal de conserjería/mantenimiento) obtenido de la sesión educativa.
3. El usuario puede cerrar sesión de forma segura invalidando su token local en el dispositivo.

### Reporte de averías e incidencias
4. El usuario puede seleccionar la ubicación exacta del desperfecto en un selector multinivel (tipo de espacio: aula, pasillo, baño, patio, instalación deportiva; planta; detalle específico).
5. El usuario puede categorizar la avería dentro de las áreas técnicas del centro (TIC / Informática, Fontanería, Electricidad, Cerrajería / Mobiliario, Patios / Exteriores).
6. El usuario puede adjuntar una fotografía del desperfecto tomada en directo con la cámara del móvil o seleccionada de la galería.
7. El usuario puede redactar un título breve y una descripción explicativa de la avería detectada.
8. El usuario puede consultar en la pantalla de reporte si ya existe una avería abierta en esa misma ubicación para evitar duplicar avisos.

### Consulta y seguimiento
9. El usuario puede consultar en tiempo real el listado de sus incidencias reportadas y su estado actual (*Pendiente*, *En revisión*, *En reparación*, *Resuelta*, *Desestimada*).
10. El usuario puede consultar el cuadro general de incidencias públicas del centro para conocer qué zonas o aulas están afectadas antes de impartir clase o utilizarlas.
11. El usuario puede filtrar y buscar incidencias por ubicación, categoría técnica o estado de resolución.

### Gestión y mantenimiento (Conserjería, Coordinación TIC y Mantenimiento)
12. El usuario con rol de gestión puede visualizar la bandeja de entrada unificada de incidencias con ordenación por antigüedad y gravedad.
13. El usuario con rol de gestión puede actualizar el estado de una incidencia a lo largo de su ciclo de vida (*Pendiente* ➔ *En revisión* ➔ *En reparación* ➔ *Resuelta* / *Desestimada*).
14. El usuario con rol de gestión puede clasificar y modificar el nivel de prioridad operativa de la avería (*Baja*, *Media*, *Alta*, *Urgente*).
15. El usuario con rol de gestión puede añadir notas técnicas internas y observaciones sobre la reparación (visibles solo para el equipo de mantenimiento).
16. El usuario con rol de gestión puede asignar nominalmente una incidencia a un encargado o servicio concreto (conserje, coordinador TIC o técnico municipal).

### Funcionalidades avanzadas
17. El usuario puede escanear un código QR colocado en la entrada del espacio (aula, aseo, cuadro eléctrico, pista exterior) para precargar automáticamente la ubicación en el formulario de reporte.
18. El usuario con rol de gestión puede visualizar métricas básicas del centro (volumen de incidencias por zona, tiempo medio de resolución y desglose por categorías) y exportar el resumen mensual en CSV.

---

## 2. Priorización MoSCoW

**Must have** (sin esto no sirve — 8 de 18, cumpliendo la regla de máximo el 50 %):

| # | Requisito |
|---|---|
| 1 | Iniciar sesión con credenciales de Séneca/iPasen (o modo mock educativo) |
| 2 | Obtener rol y sincronizar usuario automáticamente (Docente, Alumno, Mantenimiento) |
| 4 | Seleccionar ubicación multinivel (espacio, planta y detalle) para aulas, baños, pasillos o patios |
| 5 | Categorizar la avería (TIC, Fontanería, Electricidad, Mobiliario, Exteriores) |
| 6 | Adjuntar una fotografía obligatoria del desperfecto desde el dispositivo |
| 7 | Introducir título y descripción detallada del problema |
| 9 | Consultar el estado en tiempo real de las incidencias reportadas por el propio usuario |
| 13 | Actualizar el estado del ciclo de vida de la avería (*Pendiente* ➔ *En reparación* ➔ *Resuelta*) |

**Should have** (importante para la propuesta de valor completa, pero el producto base sobrevive sin ello):

| # | Requisito |
|---|---|
| 3 | Cerrar sesión e invalidar token en el cliente |
| 8 | Comprobar en la pantalla de alta si ya existe una incidencia abierta en esa ubicación (escudo anti-duplicados) |
| 10 | Consultar el cuadro general de averías activas en el centro |
| 11 | Filtrar incidencias por categoría, estado o planta |
| 12 | Visualizar la bandeja unificada de conserjería con ordenación por gravedad y fecha |
| 14 | Clasificar la avería por nivel de prioridad (*Baja*, *Media*, *Alta*, *Urgente*) |

**Could have** (si sobra tiempo al final del desarrollo):

| # | Requisito |
|---|---|
| 15 | Añadir notas técnicas internas en el historial de la avería |
| 16 | Asignación nominal de incidencias a un operario o departamento |
| 17 | Precarga de ubicación mediante escaneo de código QR |
| 18 | Métricas básicas de averías y exportación mensual en CSV |

**Won't have (No tendremos)** — queda fuera en esta versión y queda por escrito:

| # | Requisito descartado | Por qué queda fuera |
|---|---|---|
| — | Notificaciones push nativas al sistema operativo (FCM / APNs) | Al ser una aplicación web (MERN), las actualizaciones se muestran dentro de la interfaz al abrir la app o consultar el panel. |
| — | Comunicación directa bidireccional con el inventario oficial de Séneca | No existe endpoint público de escritura en Séneca para registrar partes de obra sin comprometer la integridad de la base de datos institucional. |
| — | Detección automática de averías mediante Inteligencia Artificial en fotos | Requiere modelos de visión por computador y costes de inferencia innecesarios; la categorización humana en 2 clics es suficiente. |
| — | Geolocalización GPS en interiores | La señal GPS es inestable e inexacta dentro de edificios educativos de varias plantas; el selector jerárquico es mucho más fiable. |
| — | Creación manual de cuentas y registro con correo externo | Rompe el principio de identidad verificada: únicamente acceden usuarios con credenciales activas del sistema educativo andaluz. |

> **Nota de diseño a futuro (dirección técnica para próximas fases):**
> - **Notificaciones push nativas:** se implementarán apoyándose en el Web Push API sobre Service Workers en la PWA, utilizando una colección `suscripciones_push` en MongoDB.
> - **Integración con códigos de barras de inventario de la Junta:** se habilitará un lector de código de barras para escanear las etiquetas oficiales de la Junta de Andalucía pegadas en monitores y torres, asociando el número de serie al parte técnico.

---

## 3. MVP (Producto Mínimo Viable)

El recorrido mínimo de nuestras *user personas* principales (**Carmen**, profesora que detecta una avería, y **Manuel**, conserje que la resuelve): **Carmen entra, reporta una avería con foto y ubicación en menos de 30 segundos; Manuel recibe el parte, lo atiende y cambia el estado a resuelto; Carmen ve el cierre del ticket al instante**.

Este recorrido se construye **única y exclusivamente con los 8 requisitos Must have**; todo lo demás queda fuera del MVP.

### Recorrido del MVP

1. **Inicio de sesión y sincronización (Reqs. 1 y 2 — 15 segundos):**
   - Carmen abre AulaFix desde el navegador de su móvil y pulsa «Acceder con iPasen».
   - Introduce su usuario y contraseña habituales de Séneca. El backend valida contra la API institucional, detecta su rol (*Docente*) y sincroniza su ficha en la base de datos sin obligarla a rellenar ningún formulario de registro.

2. **Selección de ubicación y categorización (Reqs. 4 y 5 — 10 segundos):**
   - Carmen pulsa el botón «Nueva Incidencia».
   - Selecciona en tres toques la zona afectada: *Espacio:* «Baños», *Planta:* «Primera planta», *Detalle:* «Aseos de profesores, lavabo derecho».
   - Marca la categoría técnica correspondiente: «Fontanería».

3. **Foto descriptiva y envío del parte (Reqs. 6 y 7 — 15 segundos):**
   - Toca el botón de cámara, toma una foto del grifo roto perdiendo agua y escribe brevemente: *"El grifo del lavabo derecho no cierra y desborda agua al suelo"*.
   - Pulsa **Enviar incidencia**. El ticket se registra en la base de datos y la imagen queda almacenada en el servicio multimedia.

4. **Recepción y actualización de estado por mantenimiento (Req. 13 — 1 minuto):**
   - Manuel (conserje) abre AulaFix desde el ordenador de conserjería.
   - En la bandeja de entrada ve una nueva tarjeta roja en estado *Pendiente* con la foto y la ubicación exacta que envió Carmen.
   - Manuel acude al aseo, corta la llave de paso para evitar inundaciones, vuelve al panel y cambia el estado a *En reparación*.
   - Una vez sustituida la zapata del grifo por el oficial de mantenimiento, Manuel hace clic en el ticket y selecciona el estado *Resuelta*.

5. **Consulta del estado resuelto por la docente (Req. 9 — 5 segundos):**
   - Antes de marcharse del centro, Carmen entra en la pestaña «Mis Incidencias» desde su móvil.
   - Comprueba que la tarjeta del grifo ha pasado de color naranja a verde con el estado *Resuelta*, cerrando el ciclo de comunicación sin haber tenido que bajar a conserjería ni preguntar a nadie por el pasillo.
     
# Requisitos técnicos: frontend e infraestructura
## Frontend (React)

### Bibliotecas adicionales necesarias

| Biblioteca | Para qué | Por qué |
|---|---|---|
| **React Router** (`react-router-dom`) | Navegación entre pantallas (Login, Nueva Incidencia, Mis Incidencias, Panel de Mantenimiento) y protección de rutas privadas según rol. | Es el estándar en el ecosistema React para SPA; permite implementar *Guards* para restringir el panel de gestión únicamente a usuarios con rol de mantenimiento o administración. |
| **Zustand** | Gestión del estado global (sesión de usuario, token JWT, rol activo y filtros de búsqueda). | Mucho más ligero y directo que Redux; evita el *prop drilling* y facilita acceder al perfil del usuario desde cualquier vista sin recargar la aplicación. |
| **Tailwind CSS** | Estilos, maquetación de componentes y diseño adaptado a móviles (*mobile-first*). | Permite construir una interfaz rápida, limpia y accesible desde pantallas de smartphone, garantizando que el reporte se realice en menos de 30 segundos de pie en un pasillo. |
| **Axios** | Peticiones HTTP asíncronas hacia la API REST de Express. | Facilita el uso de interceptores para adjuntar automáticamente la cabecera `Authorization: Bearer <token>` en cada llamada y manejar globalmente las expiraciones de sesión (error 401). |
| **React Hook Form** | Gestión y validación del formulario de alta de incidencias. | Optimiza el rendimiento evitando re-renderizados innecesarios mientras se escribe y asegura que no se envíen reportes sin foto o sin ubicación antes de contactar con el backend. |
| **Lucide React** | Iconografía de la interfaz (iconos de fontanería, electricidad, TIC, aulas, patios, estados). | Librería de iconos SVG sumamente ligera y personalizable; ayuda a identificar las categorías de un vistazo rápido sin saturar la pantalla. |
| **date-fns** | Formateo y cálculo de tiempos transcurridos en las incidencias (*"hace 10 minutos"*, *"hace 2 días"*). | Es modular, ligera e inmutable; permite mostrar fechas amigables en español sin los problemas de sobrepeso de librerías obsoletas. |
| **browser-image-compression** | Compresión automática de fotografías en el cliente antes del envío. | Reduce capturas móviles de 5 MB a menos de 500 KB en el propio navegador antes de transmitirlas, ahorrando ancho de banda y acelerando el reporte bajo redes WiFi escolares lentas. |
| **html5-qrcode** | Lectura de códigos QR pegados en las puertas de las aulas e instalaciones (*Could have*). | Permite acceder a la cámara del navegador de forma directa y decodificar el identificador de la estancia para precargar el formulario sin teclear. |

---

## Infraestructura

### Despliegue por capas

| Parte | Dónde | Por qué | Condiciones y límites del plan gratuito |
|---|---|---|---|
| **Frontend** | **Vercel** (Plan *Hobby*) | Integración directa con GitHub: compila automáticamente la rama `main` en producción y proporciona previsualizaciones por cada Pull Request. | Uso no comercial, **100 GB/mes** de transferencia de datos, soporte SSL/HTTPS nativo y despliegues ilimitados. |
| **Backend** | **Render** (Plan *Free Web Service*) | Alojamiento nativo para aplicaciones Node.js/Express con soporte para variables de entorno seguras. | **750 horas/mes** gratuitas y 512 MB de RAM. Entra en suspensión tras **15 minutos de inactividad**, demorando unos 30-50 segundos en reactivarse en la primera petición. |
| **Base de datos** | **MongoDB Atlas** (Plan *M0 Sandbox*) | Base de datos NoSQL gestionada en la nube (DBaaS); clúster alojado en región europea (Frankfurt) con conexión cifrada mediante URI. | **512 MB de almacenamiento**, conexiones simultáneas suficientes y backups automatizados (espacio más que suficiente para miles de tickets de texto). |
| **Almacenamiento Multimedia** | **Cloudinary** (Plan *Free*) | Servidor multimedia especializado para guardar las fotografías de las averías reportadas. | **25 créditos mensuales** (equivalentes a unos 25 GB de almacenamiento o ancho de banda) y optimización/compresión automática de imágenes en la nube. |

### ¿Necesitamos servicios cloud adicionales?

Para el alcance del proyecto y su MVP **no necesitamos contratar servidores dedicados de pago ni pasarelas bancarias**, apoyándonos únicamente en capas gratuitas:

- **Almacenamiento multimedia con Cloudinary (Plan Gratuito):** Es indispensable para no guardar fotos en base64 dentro de MongoDB (lo que saturaría los 512 MB de Atlas). El backend retransmite la imagen a Cloudinary y en la base de datos se guarda únicamente la URL pública segura resultante.
- **Sin CDN de pago externa:** Vercel distribuye todos los assets estáticos del frontend de React a través de su propia red Edge global sin coste adicional.
- **Sin pasarela de pagos:** AulaFix es una plataforma de servicio público educativo sin cobros ni transacciones económicas.
- **Sin costes por la API de Séneca:** La autenticación se conecta a la infraestructura existente de la Junta de Andalucía descubierta por ingeniería inversa, sin requerir suscripciones a proveedores de identidad externos (como Auth0 o Firebase Auth).

# Requisitos técnicos: backend y base de datos
## Backend (Node.js + Express)

### Autenticación y gestión de sesiones

**Sí, desde el MVP.** El sistema implementa autenticación puente conectando con los servidores oficiales de Séneca/iPasen:

- **Inicio de sesión contra Séneca (Must have):** El usuario introduce su usuario y contraseña en el cliente de React. El backend en Express realiza una petición `POST` al endpoint oficial descubierto (`https://seneca.juntadeandalucia.es/api/public/security/oauth/token`) enviando las cabeceras requeridas (`User-Agent: iPasen/...`) y rescata el `access_token`.
- **Sincronización de identidad:** Con el token obtenido, Express consulta `GET generales/info-session`, recupera el nombre completo (`fullname`), rol (`typeProfile`: Alumno o Profesor) y código de centro (`centerCode`), creando o actualizando automáticamente la ficha del usuario en la colección `users` de MongoDB.
- **Gestión de sesiones propias con JWT:** El backend descarta de inmediato la contraseña del usuario (nunca se almacena en base de datos) y emite un **JSON Web Token (JWT) propio** firmado con una clave secreta (`JWT_SECRET`). Este token contiene el `_id` y el `rol` interno del usuario, y se envía en las cabeceras de cada petición posterior mediante los interceptores de Axios con una **validez de 30 días**.
- **Modo Mock Educativo (Contingencia para evaluación):** Mediante la variable de entorno `USE_MOCK_AUTH=true`, el backend permite validar usuarios ficticios locales (ej. Carmen Profesora, Manuel Conserje, Marcos Alumno) para poder defender el proyecto ante el profesor incluso si los servidores de la Junta sufren cortes o mantenimientos.
- **Roles de usuario y control de acceso (RBAC):**
  - `ALUMNO`: Puede reportar averías en cualquier espacio y consultar exclusivamente sus incidencias creadas.
  - `PROFESOR`: Puede reportar averías, consultar su historial y ver el listado general de averías activas del centro.
  - `MANTENIMIENTO` / `CONSERJERIA` / `TIC`: Acceso completo para ver todas las averías, cambiar estados, añadir notas técnicas y clasificar prioridades.

### Bibliotecas principales de Backend

| Biblioteca | Para qué | Por qué |
|---|---|---|
| **Express** | Creación del servidor HTTP, enrutamiento REST y gestión de middlewares. | Framework ligero y minimalista de Node.js, ideal para construir la API intermedia y estructurar controladores limpios. |
| **Mongoose** | Modelado de esquemas (ODM) y conexión con la base de datos MongoDB Atlas. | Permite estructurar y validar los documentos de incidencias y usuarios antes de persistirlos, gestionando relaciones por referencia y subdocumentos. |
| **jsonwebtoken** | Generación y verificación del token JWT de sesión propia. | Facilita una arquitectura de autenticación desacoplada y *stateless*, verificando la identidad del usuario en cada petición mediante un middleware centralizado. |
| **multer** | Procesamiento de peticiones `multipart/form-data` para recibir imágenes. | Gestiona la recepción de la fotografía de la avería en la memoria del servidor (buffer) antes de retransmitirla al servicio de almacenamiento. |
| **cloudinary** | SDK oficial para la subida de imágenes a la nube de Cloudinary. | Permite subir el archivo recibido por multer mediante un flujo de streams y obtener la URL segura (`https`) definitiva para guardarla en MongoDB. |
| **cors** y **dotenv** | Configuración de orígenes cruzados y gestión de variables de entorno. | Imprescindibles para autorizar peticiones desde el dominio de Vercel y ocultar credenciales secretas (URI de Mongo, Cloudinary Secret, JWT Secret) fuera de Git. |

### APIs o servicios externos

| Servicio | Para qué | ¿Necesario en el MVP? | Condiciones y límite del plan gratuito |
|---|---|---|---|
| **API Oficial iPasen / Séneca** | Validación de credenciales educativas y obtención de perfiles y roles reales. | **Sí** (núcleo del Requisito 1; con alternativa mock desacoplada para contingencias). | Gratuito; infraestructura pública oficial de la Junta de Andalucía descubierta mediante ingeniería inversa. |
| **Cloudinary** | Almacenamiento y optimización de las fotografías asociadas a las incidencias. | **Sí** (imprescindible para el Requisito 6 del MVP). | **25 créditos mensuales gratuitos** (~25 GB de almacenamiento/transferencia), más que suficiente para el uso escolar. |

---

## Base de datos (MongoDB)

### Esquema preliminar de colecciones principales

El diseño en MongoDB se organiza en **3 colecciones principales**: `users`, `incidencias` y `historial_estados`.

#### 1. Colección: `users`
Almacena el perfil de cada miembro de la comunidad educativa sincronizado tras su primer acceso mediante la API de iPasen.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único generado por MongoDB. |
| `seneca_id` | `String` | Identificador único proveniente de Séneca/iPasen (`"12345678Z"`), indexado y único. |
| `nombre_completo` | `String` | Nombre y apellidos del usuario (`"Carmen Ortega Ramos"`). |
| `rol` | `String` | Rol en el sistema: `"ALUMNO"`, `"PROFESOR"`, `"MANTENIMIENTO"`, `"ADMIN"`. |
| `centro_code` | `String` | Código oficial del centro escolar (`"11004567"`). |
| `curso` | `String` / `null` | Nivel educativo en caso de alumnado (`"2º FP Grado Superior"`) o `null`. |
| `activo` | `Boolean` | Estado de la cuenta en el sistema (por defecto `true`). |
| `created_at` | `Date` | Fecha del primer inicio de sesión en la plataforma (`ISODate`). |

#### 2. Colección: `incidencias`
Registra cada parte de avería reportado con su estado de resolución, prioridad y ubicación física detallada.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único de la incidencia. |
| `titulo` | `String` | Resumen breve del problema (`"Grifo roto perdiendo agua"`). |
| `descripcion` | `String` | Explicación detallada del fallo detectado. |
| `categoria` | `String` | Área técnica: `"TIC"`, `"Fontaneria"`, `"Electricidad"`, `"Mobiliario"`, `"Patios"`. |
| `ubicacion` | `Object` | Objeto embebido con la localización: `{ tipo: "Banos", planta: "Primera", detalle: "Aseos profesores, lavabo derecho" }`. |
| `foto_url` | `String` | Enlace seguro a la imagen en Cloudinary (`"https://res.cloudinary.com/.../grifo.jpg"`). |
| `estado` | `String` | Estado actual: `"Pendiente"`, `"En_Revision"`, `"En_Reparacion"`, `"Resuelta"`, `"Desestimada"`. |
| `prioridad` | `String` | Nivel de urgencia: `"Baja"`, `"Media"`, `"Alta"`, `"Urgente"` (por defecto `"Media"`). |
| `reportado_por` | `ObjectId` | Referencia al `_id` del usuario emisor en la colección `users`. |
| `asignado_a` | `ObjectId` / `null` | Referencia opcional al `_id` del operario encargado en `users`. |
| `created_at` / `updated_at` | `Date` | Marcas de tiempo de creación y última actualización (`ISODate`). |

#### 3. Colección: `historial_estados`
Registra cada cambio de estado y nota técnica introducida por el equipo de conserjería o mantenimiento, permitiendo auditoría y trazabilidad cronológica.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único del evento de cambio de estado. |
| `incidencia_id` | `ObjectId` | Referencia al `_id` de la avería correspondiente en `incidencias`. |
| `usuario_id` | `ObjectId` | Referencia al `_id` del usuario de mantenimiento que realizó el cambio en `users`. |
| `estado_anterior` | `String` | Estado previo de la incidencia (`"Pendiente"`). |
| `estado_nuevo` | `String` | Nuevo estado asignado (`"En_Reparacion"`). |
| `nota_tecnica` | `String` / `null` | Comentario interno del técnico (`"Cortada llave de paso; esperando zapata"`). |
| `fecha` | `Date` | Fecha y hora exacta del cambio de estado (`ISODate`). |

### Relaciones entre colecciones

- **De `users` a `incidencias` (1:N por referencia):** El campo `incidencias.reportado_por` vincula cada avería con su creador real en `users`. Permite mostrar al usuario solo sus avisos y reflejar en conserjería quién abrió cada parte.
- **Dentro de `incidencias` (Embebido):** `incidencias.ubicacion` es un objeto embebido dentro del propio documento de la avería. No requiere una colección separada porque la localización es un atributo propio e inmutable de la incidencia que siempre se consulta junto a ella.
- **De `incidencias` a `historial_estados` (1:N por referencia):** Cada cambio de estado genera un documento en `historial_estados` referenciando el `incidencia_id`. Se mantiene separado para evitar que el documento principal de la incidencia crezca de forma desmedida y para agilizar las consultas del panel principal.

# Capacidades del equipo, riesgos y la introducción que une todo

## 1. Capacidades del equipo

### Inventario de habilidades

Nivel actual de cada integrante del equipo en las tecnologías clave del proyecto (Sin experiencia / Básico / Intermedio / Avanzado):

| Miembro | React | Node.js / Express | MongoDB | Tailwind CSS | Git |
|---|---|---|---|---|---|
| Aarón | Básico | Básico | Sin experiencia | Sin experiencia | Intermedio |
| Álvaro | Sin experiencia | Sin experiencia | Sin experiencia | Sin experiencia | Básico |
| Gabriel | Básico | Intermedio | Básico | Básico | Sin experiencia |
| David | Básico | Sin experiencia | Básico | Sin experiencia | Básico |

---

### Lagunas de conocimiento

Tecnologías y conceptos que debemos aprender o reforzar para construir el MVP y cómo los vamos a cubrir en equipo:

| Tecnología o concepto | A quién le falta | Cómo lo cubriremos |
|---|---|---|
| *Petición proxy a Séneca y spoofing de User-Agent* | Todo el equipo | Gabriel investigará el módulo de login con Axios en Node.js reproduciendo el curl del APK y compartirá un endpoint funcional en la primera semana. |
| *Subida de imágenes con Multer y Cloudinary* | Aarón, Álvaro, David | Seguir la documentación oficial de Cloudinary SDK para Express; Gabriel preparará el middleware base de subida. |
| *Zustand* (gestión de estado de sesión y rol) | Todo el equipo | Documentación oficial y creación de una tienda simple de prueba para almacenar el token JWT y el rol del usuario. |
| *Tailwind CSS* (maquetación mobile-first) | Aarón, Álvaro, David | Guía de referencia rápida y apoyo de Gabriel para estructurar las tarjetas de incidencias y los selectores de ubicación. |
| *Rutas protegidas con React Router v6* | Todo el equipo | Implementar un componente `<ProtectedRoute allowedRoles={[...]} />` para separar las vistas de Alumnos de las de Conserjería. |

---

### ¿Es realista completar el proyecto a tiempo?

*Sí, es realista completar el proyecto en el tiempo disponible porque hemos acotado estrictamente el MVP a los 8 requisitos *Must have.***

- *Alcance controlado:* Hemos dejado fuera del MVP las tareas más pesadas o accesorias (la exportación a CSV y métricas avanzadas quedan en Could have, el escáner de códigos QR en Could have y las notas técnicas detalladas en Could have).
- *Complejidad técnica asumible:* El núcleo del MVP se resuelve con un flujo CRUD clásico sobre MongoDB (crear incidencia, listar incidencias y actualizar estado) combinado con la subida de una imagen y una pasarela de autenticación que solo requiere consultar dos endpoints de iPasen (`oauth/token` e `info-session`).
- *Plan de contingencia:* Si la conexión directa con los servidores de Séneca presenta problemas técnicos o bloqueos imprevistos, activaremos de inmediato el modo *Mock Educativo* local, garantizando que el tribunal docente pueda evaluar el 100% de la funcionalidad de la app sin retrasos.

---

## 2. Riesgos técnicos

| # | Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|---|
| 1 | *Inestabilidad o bloqueos en la API externa de Séneca/iPasen* | Media | Crítico | Crear desde el día uno un modo mock en Express (`USE_MOCK_AUTH=true`) con usuarios precargados (profesor, conserje, alumno) para trabajar y defender el proyecto sin depender de la Junta. |
| 2 | *El backend se duerme en Render* (el plan gratuito apaga el servidor tras 15 min de inactividad y tarda ~40 s en despertar) | Alta | Bajo | Mostrar un mensaje claro en la pantalla de carga (*"Conectando con el servidor..."*) y configurar un ping periódico con un cron gratuito a `/api/health` durante las horas lectivas. |
| 3 | *Agotamiento de almacenamiento o fallos de subida de fotos en Cloudinary* | Baja | Medio | Comprimir las imágenes en el navegador del cliente antes de enviarlas (máximo 500 KB) con `browser-image-compression` y limitar el tamaño del archivo en Multer a 2 MB. |
| 4 | *El equipo no domina React y Tailwind a tiempo para el MVP* | Media | Alto | Comenzar maquetando las pantallas clave con datos de prueba (*mocks* estáticos) antes de enlazar con la API y programar sesiones de programación por parejas (*pair programming*). |
| 5 | *Desviación del alcance (*scope creep)* por querer abarcar inventarios completos o chat interno* | Alta | Alto | Mantener la lista de *Won't have* por escrito de forma estricta: nadie abre tareas de Should o Could have hasta que los 8 Must have estén desplegados y probados. |
| 6 | *Conflictos de merge en Git y rotura de la rama main al trabajar 4 personas en paralelo* | Media | Medio | Respetar estrictamente el flujo issue ➔ rama ➔ PR ➔ review cruzada ➔ merge, manteniendo el código repartido en módulos claros y prohibiendo mergear PRs propios. |

---

## 3. Introducción que une todo

Con la fase 1 cerrada, toca responder la segunda pregunta: *¿podemos construirlo?*. La respuesta corta es sí; la larga está en este documento.

El MVP de *AulaFix* se apoya en cuatro pilares técnicos: un frontend en React con Tailwind CSS optimizado para su uso en smartphones en cualquier rincón del centro, un backend en Node.js y Express que actúa como pasarela contra la API de Séneca/iPasen emitiendo tokens JWT propios, una base de datos en MongoDB Atlas para persistir de forma estructurada los partes de averías y sus estados, y un servicio multimedia en Cloudinary para almacenar las fotos reales de los desperfectos. La lógica central es un ciclo de vida limpio y directo —reporte con ubicación y foto, inspección por el personal de mantenimiento y cambio de estado a resuelto—, lo que lo hace completamente viable para el tiempo disponible y las capacidades actuales del equipo.

Este documento recoge los 18 requisitos funcionales priorizados con el método MoSCoW, las decisiones de frontend, backend, base de datos e infraestructura gratuita, la evaluación de habilidades del equipo y la matriz de riesgos técnicos con planes de mitigación previos. Lo que aquí se decide nos proporciona una base técnica sólida para empezar a programar y se podrá ajustar de forma controlada a medida que avance el desarrollo.
