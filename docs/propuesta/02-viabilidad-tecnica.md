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
   - Carmen abre AULAFIX desde el navegador de su móvil y pulsa «Acceder con iPasen».
   - Introduce su usuario y contraseña habituales de Séneca. El backend valida contra la API institucional, detecta su rol (*Docente*) y sincroniza su ficha en la base de datos sin obligarla a rellenar ningún formulario de registro.

2. **Selección de ubicación y categorización (Reqs. 4 y 5 — 10 segundos):**
   - Carmen pulsa el botón «Nueva Incidencia».
   - Selecciona en tres toques la zona afectada: *Espacio:* «Baños», *Planta:* «Primera planta», *Detalle:* «Aseos de profesores, lavabo derecho».
   - Marca la categoría técnica correspondiente: «Fontanería».

3. **Foto descriptiva y envío del parte (Reqs. 6 y 7 — 15 segundos):**
   - Toca el botón de cámara, toma una foto del grifo roto perdiendo agua y escribe brevemente: *"El grifo del lavabo derecho no cierra y desborda agua al suelo"*.
   - Pulsa **Enviar incidencia**. El ticket se registra en la base de datos y la imagen queda almacenada en el servicio multimedia.

4. **Recepción y actualización de estado por mantenimiento (Req. 13 — 1 minuto):**
   - Manuel (conserje) abre AULAFIX desde el ordenador de conserjería.
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
- **Sin pasarela de pagos:** AULAFIX es una plataforma de servicio público educativo sin cobros ni transacciones económicas.
- **Sin costes por la API de Séneca:** La autenticación se conecta a la infraestructura existente de la Junta de Andalucía descubierta por ingeniería inversa, sin requerir suscripciones a proveedores de identidad externos (como Auth0 o Firebase Auth).

# Requisitos técnicos: backend y base de datos
## Backend (Node.js + Express)

### Autenticación y gestión de sesiones

**Sí, desde el MVP.** El sistema implementa autenticación propia basada en **correo electrónico y contraseña** para permitir la sincronización automática entre dispositivos (móvil y web):

* **Registro e inicio de sesión (Must have):** El usuario se registra e inicia sesión con su email y contraseña (mínimo 8 caracteres). Las contraseñas nunca se almacenan en texto plano; se guardan encriptadas mediante *hash* utilizando **`bcrypt`** (`bcryptjs`).
* **Gestión de sesiones con JWT:** Al iniciar sesión, el servidor genera un **JSON Web Token (JWT)** firmado con `jsonwebtoken`. El frontend lo guarda y lo envía en cada petición mediante los interceptores de Axios. Configuraremos una **expiración amplia (30 días)** para que el usuario mantenga su sesión abierta en el día a día sin tener que autenticarse constantemente.
* **Sesión por dispositivo:** Cada dispositivo (móvil y ordenador) guarda su propio token local. Iniciar sesión en el móvil no abre la sesión en el ordenador, pero ambos dispositivos consultan y actualizan exactamente los mismos datos en tiempo real porque están asociados al mismo `usuario_id`.
* **Recuperación de contraseña (Should have):** Enlace enviado por correo electrónico con un token temporal (`reset_token`) de un solo uso y caducidad de 1 hora para restablecer la clave.
* **Roles de usuario:** **No existen roles distintos.** Todos los usuarios tienen el mismo nivel de permisos (usuario estándar) y únicamente pueden acceder a sus propios datos financieros, dado que la aplicación es de control personal.

### Bibliotecas principales de Backend

| Biblioteca | Para qué | Por qué |
|---|---|---|
| **Express** | Construcción de la API REST, rutas y *middlewares* | Es el framework estándar de Node.js, ligero y directo para crear endpoints JSON. |
| **Mongoose** | Modelado de esquemas (ODM) y conexión con MongoDB | Valida la estructura de los documentos antes de guardarlos y simplifica las consultas. |
| **bcryptjs** | Encriptación de contraseñas | Estándar de seguridad para generar el *hash* de la contraseña antes de guardarla en base de datos. |
| **jsonwebtoken** | Generación y verificación de tokens JWT | Permite autenticar peticiones de forma *stateless* mediante un *middleware* de rutas privadas. |
| **cors** y **dotenv** | Seguridad de dominios cruzados y variables de entorno | Necesarios para permitir peticiones desde Vercel y ocultar las claves de conexión fuera del código. |

### APIs o servicios externos

| Servicio | Para qué | ¿Necesario en el MVP? | Condiciones y límite del plan gratuito |
|---|---|---|---|
| **Resend** (o SendGrid) | Envío del correo electrónico con el enlace de recuperación de contraseña. | **No** (corresponde al requisito *Should have* #3; el MVP opera con registro y login directo). | **3.000 emails/mes** (con límite de **100 emails/día**) en el plan gratuito de Resend, suficiente para el proyecto. |

---

## Base de datos (MongoDB)

### Esquema preliminar de colecciones principales

El diseño en MongoDB se organiza en **3 colecciones principales**: `users`, `presupuestos` y `movimientos`.

#### 1. Colección: `users`
Almacena la cuenta de cada usuario registrado y los campos de apoyo para la recuperación de contraseña.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único generado por MongoDB. |
| `email` | `String` | Correo electrónico único del usuario (`"elisa@email.com"`). |
| `password_hash` | `String` | Contraseña encriptada con bcrypt (`"$2b$10$..."`). |
| `reset_token` | `String` / `null` | Token temporal para recuperación de contraseña (por defecto `null`). |
| `reset_expires` | `Date` / `null` | Fecha de caducidad del token de recuperación (por defecto `null`). |
| `created_at` | `Date` | Fecha de alta del usuario (`ISODate`). |

#### 2. Colección: `presupuestos` (un documento por usuario y mes)
Guarda la foto financiera del mes, incluyendo la configuración base, el estado del colchón y los *kubos* embebidos.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único del presupuesto mensual. |
| `usuario_id` | `ObjectId` | Referencia al `_id` del usuario en la colección `users`. |
| `mes` | `String` | Mes y año del presupuesto en formato `YYYY-MM` (`"2026-10"`). |
| `ingresos` | `Number` | Ingresos mensuales configurados (`1450`). |
| `gastos_fijos` | `Number` | Suma de gastos fijos mensuales (`780`). |
| `ahorro_objetivo` | `Number` | Cantidad mensual destinada al ahorro (`200`). |
| `colchon` | `Object` | Objeto embebido con el estado del colchón: `{ configurado: 30, acumulado: 70, usado: 0 }`. |
| `kubos` | `Array<Object>` | Lista embebida de categorías con su tope y acumulado: `[{ nombre: "Comida", tope: 250, gastado: 180 }, { nombre: "Ocio", tope: 120, gastado: 45 }]`. |
| `imprevistos` | `Array<Object>` | Registro de desvíos cubiertos: `[{ fecha: "2026-10-15", importe: 23, origen: "colchon", concepto: "Luz" }]`. |
| `created_at` / `updated_at` | `Date` | Marcas de tiempo de creación y última actualización (`ISODate`). |

#### 3. Colección: `movimientos`
Registra cada gasto individual con su fecha exacta. Permite calcular el ritmo de gasto de la semana actual en el MVP (Reqs. 9, 10 y 11) y alimenta el historial y la importación CSV en el Modo Detalle.

| Campo | Tipo | Descripción / Ejemplo |
|---|---|---|
| `_id` | `ObjectId` | Identificador único del movimiento. |
| `usuario_id` | `ObjectId` | Referencia al `_id` del propietario en `users`. |
| `presupuesto_id` | `ObjectId` | Referencia al `_id` del mes correspondiente en `presupuestos`. |
| `mes` | `String` | Mes al que pertenece el gasto (`"2026-10"`). |
| `fecha` | `Date` | Fecha exacta del gasto (`"2026-10-20"`) para calcular la semana en curso. |
| `categoria` | `String` | Nombre del *kubo* al que se imputa (`"Comida"`). |
| `importe` | `Number` | Cantidad gastada (`45.20`). |
| `es_imprevisto` | `Boolean` | Indica si el gasto se descuenta del colchón de imprevistos (`false`). |
| `origen` | `String` | Procedencia del dato: `"registro"` (en 2 toques) o `"csv"` (importado). |

### Relaciones entre colecciones

* **De `users` a `presupuestos` (1:N por referencia):** El campo `presupuestos.usuario_id` relaciona cada presupuesto mensual con su propietario en la colección `users`.
* **Dentro de `presupuestos` (Embebido):** `presupuestos.kubos`, `presupuestos.colchon` y `presupuestos.imprevistos` son objetos y arrays embebidos directamente en el documento del mes. No requieren otra colección porque son pocos elementos por mes y siempre se consultan junto con el presupuesto en la pantalla principal.
* **De `presupuestos` a `movimientos` (1:N por referencia):** Cada gasto registrado en `movimientos` se vincula al usuario (`usuario_id`) y al mes (`presupuesto_id`), actualizando a su vez el acumulado `gastado` del *kubo* correspondiente. Se mantiene en una colección separada para poder filtrar gastos por semanas y soportar la futura carga de extractos CSV sin sobrecargar el documento mensual.

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
| *Zustand* (estado global en React) | Todo el equipo | Documentación oficial y creación de un store de prueba en la primera semana; es ligero y directo. |
| *MongoDB Atlas* (clúster, usuario, conexión con Mongoose) | Miembros 1, 2 | El Miembro 3 configurará el clúster inicial y explicará el paso a paso; documentaremos la conexión en un .env.example. |
| *Despliegue en Vercel y Render* (variables de entorno y CORS) | Todo el equipo | Documentación oficial y hacer un deploy de prueba en la primera semana para dejar resueltos los permisos CORS. |
| *Tailwind CSS* (clases utilitarias) | Todo el equipo | Guía de referencia oficial y apoyo de los Miembros 1 y 2 revisando los componentes visuales. |
| *Autenticación JWT + Interceptores en Axios* |  Todo el equipo | Seguir un flujo estándar paso a paso para conectar el middleware de Express con el cliente de React antes de crear las pantallas. |

---

### ¿Es realista completar el proyecto a tiempo?

*Sí, es realista completar el proyecto en el tiempo disponible porque hemos acotado estrictamente el MVP a los 8 requisitos *Must have.**

* *Alcance controlado:* Hemos dejado fuera del MVP las funciones que requerían mayor carga de desarrollo (la importación y clasificación automática de CSV queda en Could have, las gráficas con Recharts en Could have y el simulador de imprevistos en Should have).
* *Complejidad técnica asumible:* El núcleo del MVP se resuelve con operaciones CRUD estándar (usuarios, presupuesto mensual y movimientos) y aritmética básica (ingresos menos gastos fijos y ahorro objetivo, divididos entre las semanas del mes).
* *Plan de contingencia:* Si la curva de aprendizaje de React o Express nos consume más tiempo del previsto, nos centraremos únicamente en asegurar que el recorrido de Elisa (los 8 Must have) funcione de principio a fin en producción, descartando los requisitos Should y Could have.

---

## 2. Riesgos técnicos

| # | Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|---|
| 1 | *El backend se duerme en Render* (el plan gratuito apaga el servidor tras 15 min de inactividad y tarda ~40 s en despertar) | Alta | Bajo | Mostrar un aviso claro en la pantalla de carga ("Conectando con el servidor...") y lanzar una petición ligera de comprobación (/api/health) nada más abrir la app. |
| 2 | *El equipo no domina React y Zustand a tiempo* | Media | Alto | Empezar maquetando las vistas con datos fijos de prueba (mocks) antes de conectar con el backend y hacer pair programming en los bloqueos. |
| 3 | *Fallos de conexión con MongoDB Atlas o bloqueos de CORS entre Vercel y Render* | Media | Alto | Configurar el clúster de Atlas (permitiendo la IP 0.0.0.0/0) y hacer el primer despliegue conectado entre Vercel y Render en la primera semana, no al final. |
| 4 | *El envío de emails de recuperación de contraseña falla o se bloquea* | Media | Medio | Al ser un requisito Should have, no bloquea el MVP. Se probará en un entorno aislado con el plan gratuito de Resend antes de integrarlo en la rama principal. |
| 5 | *Desviación del alcance (*scope creep)* por querer abarcar demasiadas funciones a la vez | Alta | Alto | Mantener la lista de *Won't have por escrito y no abrir ninguna tarea de Should o Could have hasta que los 8 Must have estén terminados y desplegados. |
| 6 | *Conflictos de *merge en Git y rotura de la rama main* al trabajar 4 personas en paralelo | Media | Medio | Respetar estrictamente el flujo issue → rama → PR → review → merge, trabajando en ficheros separados y prohibiendo hacer *merge de un PR propio. |

---

## 3. Introducción que une todo

Con la fase 1 cerrada, toca responder la segunda pregunta: *¿podemos construirlo?*. La respuesta corta es sí; la larga está en este documento.

El MVP de *KUBO* se apoya en cuatro pilares técnicos: un frontend en React con Tailwind CSS que muestra el número semanal disponible, un backend en Node.js y Express con autenticación por correo electrónico y JWT, MongoDB Atlas para guardar y sincronizar los datos en tiempo real entre móvil y ordenador, y un registro rápido de gastos en 2 toques. Toda la lógica es aritmética básica —ingresos menos gastos fijos menos ahorro objetivo, repartidos entre las semanas del mes—, lo que lo hace realista para el tiempo disponible y las capacidades actuales del equipo.

Este documento recoge los requisitos funcionales priorizados con el método MoSCoW, las decisiones técnicas de frontend, backend, base de datos e infraestructura, la evaluación de capacidades del equipo y los riesgos identificados con sus estrategias de mitigación. Lo que aquí se decide nos da una base sólida para empezar a construir y se podrá ajustar en fases posteriores según avance el desarrollo.
