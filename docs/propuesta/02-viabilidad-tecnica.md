# Requisitos funcionales, priorización MoSCoW y MVP
## 1. Requisitos funcionales

Partiendo de los casos de uso de nuestras *user personas* (`01-problema.md`), estas son las 18 funcionalidades principales del sistema:

### Cuenta y sincronización
1. El usuario puede registrarse en la plataforma con su correo electrónico y una contraseña.
2. El usuario puede iniciar sesión y mantener sus datos sincronizados automáticamente entre dispositivos (móvil y web).
3. El usuario puede recuperar su contraseña mediante un enlace enviado a su correo electrónico.

### Configuración financiera
4. El usuario puede configurar sus ingresos mensuales y sus gastos fijos (alquiler, suministros, suscripciones).
5. El usuario puede definir su objetivo de ahorro mensual.
6. El usuario puede crear *kubos* (topes de gasto por categoría o gastos futuros con fecha, como cumpleaños o seguros).
7. El usuario puede configurar un colchón de imprevistos (como porcentaje o cantidad fija).
8. El usuario puede ajustar su previsión de gastos recurrentes variables (luz, gasolina).

### Control diario y consulta
9. El usuario puede consultar en la pantalla principal su dinero disponible (mensual y repartido por semanas) calculado automáticamente.
10. El usuario puede visualizar avisos de ritmo cuando su gasto se desvía de lo previsto para la semana.
11. El usuario puede registrar un gasto diario en 2 toques (seleccionar categoría/kubo, introducir importe y confirmar).
12. El usuario puede consultar el saldo restante de cada *kubo* en tiempo real.
13. El usuario puede consultar y filtrar el historial de gastos registrados en el mes.

### Gestión de imprevistos y cuadración
14. El usuario puede marcar un gasto como imprevisto para descontarlo directamente del colchón.
15. El usuario puede simular las consecuencias de un desvío y elegir de qué fondo cubrirlo (colchón, gasto flexible o recorte de *kubo*) antes de confirmar.
16. El usuario puede cuadrar un gasto recurrente variable al recibir la factura real (ej. 78 € reales frente a 55 € previstos) y aceptar el ajuste de previsión para el mes siguiente.

### Modo Detalle (Avanzado)
17. El usuario puede importar su extracto bancario en formato CSV y revisar los movimientos clasificados automáticamente en una tabla.
18. El usuario puede visualizar gráficas de distribución de gasto por categoría.

---

## 2. Priorización MoSCoW

**Must have** (sin esto no sirve — 8 de 18, cumpliendo la regla de máximo el 50 %):

| # | Requisito |
|---|---|
| 1 | Registrarse con correo electrónico y contraseña |
| 2 | Iniciar sesión y sincronizar datos entre dispositivos (móvil y web) |
| 4 | Configurar ingresos mensuales y gastos fijos |
| 5 | Definir objetivo de ahorro mensual |
| 6 | Crear *kubos* (categorías de gasto con tope) |
| 9 | Consultar en la pantalla principal el dinero disponible mensual y semanal |
| 10 | Visualizar avisos de ritmo cuando el gasto se desvía de lo previsto |
| 11 | Registrar un gasto diario en 2 toques (categoría + importe + Listo) |

**Should have** (importante para la propuesta de valor completa, pero el producto base sobrevive sin ello):

| # | Requisito |
|---|---|
| 3 | Recuperar contraseña mediante enlace por email |
| 7 | Configurar un colchón de imprevistos (porcentaje o cantidad fija) |
| 8 | Ajustar previsión de gastos recurrentes variables |
| 12 | Consultar el saldo restante de cada *kubo* |
| 13 | Consultar el historial de gastos del mes |
| 14 | Marcar un gasto como imprevisto (descuento del colchón) |
| 15 | Simular consecuencias ante un desvío y elegir de dónde sacar el dinero |
| 16 | Cuadrar gastos variables con la factura real y ajustar el mes siguiente |

**Could have** (si sobra tiempo al final del desarrollo):

| # | Requisito |
|---|---|
| 17 | Importar extracto bancario en CSV con clasificación automática y tabla de movimientos |
| 18 | Visualizar gráficas de gasto por categoría |

**Won't have (No tendremos)** — queda fuera en esta versión y queda por escrito:

| # | Requisito descartado | Por qué queda fuera |
|---|---|---|
| — | Conexión bancaria automática (PSD2) | Requiere licencias/agregadores de pago y choca con los usuarios que desconfían de dar sus claves bancarias. |
| — | Compartir presupuesto en grupo | Requiere lógica multiusuario compleja (tabla `grupos_usuarios` y permisos); se pospone para consolidar primero el uso individual. |
| — | Ranking de ahorro entre amigos | Es una capa social futura que depende de tener el sistema de cuentas y cierres mensuales ya maduro. |
| — | Consejos financieros personalizados | No somos asesores financieros; la herramienta es de control y visibilidad, no de recomendación de inversión. |
| — | Notificaciones push nativas | Al ser una aplicación web (MERN), las alertas se muestran dentro de la interfaz al abrir la app. |

> **Nota de diseño a futuro (dirección técnica para próximas fases):**
> - **Compartir presupuesto en grupo:** se implementará mediante código de invitación sin límite de miembros sobre una colección `grupos_usuarios` en MongoDB.
> - **Ranking de ahorro entre amigos:** utilizará exclusivamente la métrica de **% del objetivo cumplido** — `(ahorro real del mes / objetivo de ahorro) * 100`, con tope en el 100 %. Por privacidad, jamás mostrará sueldos, gastos fijos ni cantidades en euros (evitando además divisiones por cero si un mes no se ahorra).

---

## 3. MVP (Producto Mínimo Viable)

El recorrido mínimo de nuestra *user persona* principal (**Elisa**): **entra, configura su base en minutos, ve su número semanal y registra gastos en segundos para no salirse de su ritmo**. 

Este recorrido se construye **única y exclusivamente con los 8 requisitos Must have**; todo lo demás queda fuera del MVP.

### Recorrido del MVP

1. **Registro e inicio de sesión (Reqs. 1 y 2 — 30 segundos):**
   - Elisa entra en la web desde el móvil y crea su cuenta con su email y contraseña.

2. **Configuración financiera inicial (Reqs. 4, 5 y 6 — 3 minutos, una sola vez):**
   - Introduce sus ingresos mensuales (1.450 €) y sus gastos fijos (780 €).
   - Define su objetivo de ahorro intocable (200 €).
   - Crea sus *kubos* principales para organizar su día a día (ej. «Comida» y «Ocio»).

3. **Consulta de su número y control de ritmo (Reqs. 9 y 10 — 5 segundos al día):**
   - Al terminar la configuración (y cada vez que abre la app), el sistema hace las cuentas por ella y le muestra su cifra clave en grande: *"Te quedan 470 € este mes — 117,50 € por semana"*.
   - Junto al número, ve un indicador claro de estado: *"Vas dentro de tu ritmo previsto"*.

4. **Registro rápido de un gasto (Req. 11 — 10 segundos):**
   - Elisa hace una compra en el supermercado de 45 €.
   - Abre la app, toca el *kubo* «Comida», teclea `45` y pulsa **Listo**.
   - Su pantalla principal se actualiza al instante: *"Te quedan 72,50 € hasta el domingo"*. Si con ese gasto supera la proporción ideal del día de la semana, el indicador cambia a: *"Atención: vas 12 € por encima del ritmo semanal"*.

5. **Continuidad entre dispositivos (Req. 2 — automática):**
   - Por la noche, Elisa inicia sesión desde su portátil con el mismo correo y ve exactamente los mismos 72,50 € disponibles y el gasto de 45 € ya descontado, cerrando su ciclo de control sin tocar una sola hoja de cálculo.

# Requisitos técnicos: frontend e infraestructura
## Frontend (React)

### Bibliotecas adicionales necesarias

| Biblioteca | Para qué | Por qué |
|---|---|---|
| **React Router** (`react-router-dom`) | Navegación entre pantallas (Inicio, Configuración, Registro, Modo Detalle) y protección de rutas privadas. | Es el estándar en el ecosistema React para SPA; permite gestionar redirecciones según si el usuario ha iniciado sesión o no sin recargar la página. |
| **Zustand** | Gestión del estado global (sesión de usuario, disponible semanal, *kubos* y configuración del mes). | Mucho más ligero y directo que Redux; evita el *prop drilling* y no requiere envolver la aplicación en múltiples *providers* complejos. |
| **Tailwind CSS** | Estilos, diseño *responsive* (*mobile-first*) y maquetación de componentes. | Permite construir una interfaz limpia y consistente rápidamente mediante clases de utilidad, garantizando que el registro en 2 toques funcione igual de bien en móvil que en escritorio. |
| **Axios** | Peticiones HTTP asíncronas hacia la API REST del backend. | Permite configurar una instancia base y usar *interceptors* para adjuntar automáticamente el token JWT en cada petición y centralizar el manejo de errores (ej. sesión expirada). |
| **React Hook Form** | Gestión y validación de formularios (registro, login, configuración financiera y alta de gastos). | Minimiza los re-renderizados de React al escribir y facilita la validación en el cliente (campos obligatorios, importes numéricos positivos, formato de email) antes de enviar datos al servidor. |
| **Lucide React** | Iconografía de la interfaz (identificación visual de *kubos*, alertas de ritmo y botones de acción). | Librería de iconos SVG ligera y personalizable; resulta clave para que el usuario identifique su *kubo* de un vistazo y registre un gasto en 2 toques. |
| **date-fns** | Cálculo y formateo de fechas (división de semanas del mes, días restantes hasta el domingo y cierres mensuales). | Es modular (*tree-shakeable*) e inmutable; permite operar con fechas en español sin el peso ni los problemas de mantenimiento de librerías antiguas como Moment.js. |
| **Recharts** | Gráficas de distribución de gasto por categoría en el Modo Detalle (*Could have*). | Basada en componentes nativos de React y SVG; es sencilla de integrar y suficiente para representar gráficas de barras y anillos adaptables a móvil y web. |
| **PapaParse** | Lectura y conversión en el navegador del extracto bancario en CSV (*Could have*). | Convierte ficheros CSV a objetos JSON directamente en el cliente en milisegundos, evitando tener que subir y almacenar archivos pesados en el servidor. |

---

## Infraestructura

### Despliegue por capas

| Parte | Dónde | Por qué | Condiciones y límites del plan gratuito |
|---|---|---|---|
| **Frontend** | **Vercel** (Plan *Hobby*) | Integración directa con GitHub: despliega automáticamente la rama `main` en producción y genera enlaces de *preview* por cada Pull Request del equipo. | Uso no comercial (ideal para proyecto académico), **100 GB/mes** de transferencia de datos (*Fast Data Transfer*), SSL automático y despliegues ilimitados. |
| **Backend** | **Render** (Plan *Free Web Service*) | Soporta aplicaciones Node.js/Express de forma nativa conectando el repositorio de Git, con configuración sencilla de variables de entorno. | **750 horas/mes** gratuitas y 512 MB de RAM. El servicio entra en suspensión (*spin down*) tras **15 minutos de inactividad**, tardando unos 30-50 segundos en despertar en la primera petición. |
| **Base de datos** | **MongoDB Atlas** (Plan *M0 Sandbox*) | Base de datos NoSQL gestionada en la nube (DBaaS); permite ubicar el clúster en la misma región europea que el backend (ej. Frankfurt) y conectar mediante una simple cadena URI. | **512 MB de almacenamiento**, RAM y vCPU compartidas, y hasta 500 conexiones simultáneas (de sobra para el volumen de documentos de texto de KUBO). |

### ¿Necesitamos servicios cloud adicionales?

Para el alcance del proyecto y su MVP **no necesitamos contratar servicios cloud de almacenamiento ni pasarelas de pago**, apoyándonos únicamente en lo incluido por defecto o en capas gratuitas:

* **Sin almacenamiento cloud de archivos (tipo AWS S3 o Cloudinary):** Los usuarios no suben fotos ni documentos adjuntos. En caso de implementar la importación de extractos CSV (*Could have*), el archivo se procesa en la memoria del navegador con *PapaParse* y solo se envían los datos estructurados en JSON al backend.
* **Sin CDN externa:** Vercel ya distribuye todos los recursos estáticos del frontend de React a través de su propia red global de entrega de contenidos (Edge Network) sin coste adicional.
* **Sin pasarela de pagos (tipo Stripe):** El proyecto no incluye cobros ni suscripciones de pago.
* **Servicio de correo transaccional (solo para *Should have*):** Para el requisito de recuperación de contraseña por email (Requisito 3), el backend se apoya en **Resend** (plan gratuito de hasta **3.000 correos/mes** y límite de **100 correos/día**), cuyo detalle de integración se especifica en el apartado de Backend.


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
