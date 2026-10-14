# KUBO — Detección del problema

KUBO es una app que te dice *cuánto puedes gastar esta semana sin dejar de ahorrar*. No se conecta a tu banco y no te pide apuntar cada gasto: introduces tus ingresos, tus gastos fijos y cuánto quiere ahorrar este mes, y KUBO te devuelve un solo número para toda la semana.

La idea nace de una situación muy habitual: llega el fin de semana, quieres salir a cenar, comprobar si puedes comprarte algo o hacer un plan, y para saber si puedes permitírtelo acabas abriendo la app del banco y haciendo cuentas mentales entre la compra, el ocio y las facturas. Muchas veces ni así lo tienes claro, y al final gastas a ojo o directamente te privas por si acaso.

Cuando llega un imprevisto —la luz viene más cara, una avería, un gasto que no tocaba— hoy se paga quitándole dinero a otras facturas o tirando de tarjeta, y el ahorro del mes se evapora sin que lo vieras venir.

---

## 1. La necesidad

### El problema

La gente no sabe *cuánto puede gastar cada semana sin cargarse el ahorro, y cuando llega un imprevisto (una factura que viene más cara, una avería), **se lo come el ahorro sin darse cuenta*. A final de mes, el ahorro es lo que sobra, si sobra algo.

Dos consecuencias concretas:

- *El gasto variable es un vacío.* El dinero de la compra, el ocio y el transporte se escapa sin medida; no hay un número que diga "esto es lo que puedes gastar esta semana".
- *Los imprevistos no tienen red.* Hoy se pagan quitándole dinero a otras facturas o tirando de tarjeta, y el ahorro del mes desaparece.

### ¿A quién afecta?

A personas con ingresos ajustados que quieren ahorrar pero no pueden dedicarle tiempo a las cuentas cada día. El gesto más frecuente: mirar la cuenta bancaria para comprobar cuánto queda, varias veces por semana.

### Frecuencia

En nuestras entrevistas, las tres personas consultadas revisan su situación económica *cada día o cada pocos días* (una a diario, otra cada dos días, otra "depende de lo que tenga que pagar"). El imprevisto que rompe el mes: al menos uno cada 2-3 meses.

### Impacto

- *Económico:* el objetivo de ahorro se pierde una o dos veces al año por un desvío pequeño.
- *Emocional:* ansiedad de no saber si vas a llegar a fin de mes; la revisión de la cuenta se convierte en un hábito de comprobación que no tranquiliza. Una persona entrevistada lo resume así: "Ahora mismo no sé lo que me queda para final de mes y tampoco lo quiero saber".

### Evidencias

*Entrevistas propias (3):* personas reales de nuestro entorno, con permiso para usar sus datos y citas:

> "Verificando los gastos en la aplicación del banco diariamente, no llevo unas cuentas exactas." — Elisa, 25 a. Mira el banco cada día para tranquilizarse, pero no lleva cuentas exactas.

> "Como a veces me escriben para los gastos del veterinario, otras veces los gatos comen más, no llevo un control exhaustivo." — Clara, 24 a. Dejó de llevar cuentas porque los gastos imprevistos de sus gatos rompían su sistema.

> *Lo que más pereza me da es introducir los gastos. Llevo el Excel al día, pero es una rutina monótona y pesada; me gustaría algo más visual, con gráficos claros y donde sea muy fácil verificar en qué se va el dinero de un vistazo.

## 2. Usuarios objetivo

Las personas usuarias objetivo se han definido a partir del cuestionario realizado a jugadores habituales. Se han creado dos perfiles con situaciones de uso diferentes: una persona que utiliza la aplicación principalmente para decidir qué jugar sola y otra que la utiliza para encontrar un juego compatible con un grupo.

### User persona 1 — Alex Morales

> Persona basada en un usuario real entrevistado. Se utiliza un nombre ficticio para preservar su privacidad.

| Campo | Descripción |
|---|---|
| Edad | 22 años |
| Ocupación | Frigorista |
| Ubicación | Estepona |
| Dispositivo principal | PC gaming |
| Launcher habitual | Steam |
| Frecuencia de juego | Juega habitualmente, principalmente por las tardes y noches |
| Contexto de uso | Juega principalmente solo; de forma ocasional juega con amigos mediante Discord |

> “Tengo un montón de juegos, pero no sé a qué jugar y al final acabo entrando en lo mismo de siempre.”

#### Necesidades

- Elegir un juego individual en pocos minutos, sin tener que investigar durante mucho tiempo.
- Encontrar juegos que encajen con su estado de ánimo, género preferido y tiempo libre disponible.
- Descubrir títulos de su biblioteca que había olvidado o dejado sin terminar.
- Saber rápidamente si un juego requiere partidas cortas o una sesión más larga.
- Usar la aplicación sin tener que registrarse, instalar programas adicionales ni conceder permisos innecesarios.

#### Frustraciones

- Tiene demasiados juegos y la cantidad de opciones le genera indecisión.
- Pierde tiempo revisando Steam sin llegar a iniciar ningún juego.
- Acaba jugando siempre a los mismos títulos por ser una elección segura.
- Las recomendaciones generales no tienen en cuenta qué le apetece jugar ese día.
- Puede aburrirse rápidamente si el juego elegido no encaja con el tiempo o la experiencia que busca.
- Desconfía de conectar su cuenta si la aplicación solicita acceso excesivo a sus datos.

#### Objetivos

- Decidir a qué jugar en menos de cinco minutos.
- Aprovechar mejor los juegos que ya posee y descubrir otros que le puedan interesar.
- Dedicar su tiempo libre a jugar, no a buscar o comparar opciones.
- Tener una recomendación clara y explicada, con posibilidad de pedir otra alternativa.

#### Casos de uso principales

1. Alex llega a casa, abre la aplicación y selecciona `Jugar solo`.
2. Indica el género que le apetece, la plataforma y el tiempo que tiene disponible.
3. Pulsa el botón `Sorpréndeme` para recibir una recomendación.
4. Consulta la portada, la valoración, el tiempo estimado de sesión y el motivo de la recomendación.
5. Guarda el juego en favoritos, lo descarta o pide otra opción.
6. Abre la ficha del juego y utiliza el enlace para buscarlo en Steam.

---

### User persona 2 — Laura Torres

> Persona secundaria construida a partir de patrones observados en el cuestionario de usuarios.

| Campo | Descripción |
|---|---|
| Edad | 20 años |
| Ocupación | Estudiante |
| Dispositivo principal | PC gaming y móvil |
| Launchers habituales | Steam y Epic Games |
| Frecuencia de juego | Juega varias veces por semana |
| Contexto de uso | Se conecta por Discord con un grupo variable de entre 3 y 6 amistades |

> “Si somos varios, quiero que me diga juegos que podamos jugar todos; no uno para cuatro cuando estamos seis en Discord.”

#### Necesidades

- Encontrar juegos compatibles con todas las personas conectadas.
- Indicar cuántas personas van a jugar antes de recibir una recomendación.
- Filtrar por modo cooperativo o competitivo, género y plataforma.
- Evitar propuestas que no admitan al número de jugadores del grupo.
- Decidir rápido para empezar a jugar en lugar de debatir durante media hora.

#### Frustraciones

- Sus amistades no siempre tienen comprados los mismos juegos.
- Las recomendaciones genéricas no indican claramente el número máximo de jugadores.
- Los gustos del grupo no siempre coinciden.
- Tras debatir durante demasiado tiempo, el grupo termina jugando siempre a los mismos títulos o cada persona juega por separado.
- No quiere iniciar sesión ni dar permisos a Steam/Epic si la aplicación no explica claramente qué información usará.

#### Objetivos

- Encontrar una opción viable para todo el grupo en pocos minutos.
- Evitar discusiones y reducir el tiempo que tardan en decidir.
- Descubrir opciones nuevas, no repetir siempre los mismos juegos.
- Conocer de un vistazo si un juego es cooperativo, competitivo, compatible con el grupo y está disponible en la plataforma elegida.

#### Casos de uso principales

1. Laura está en una llamada de Discord con cuatro amistades y abre la aplicación.
2. Selecciona `Jugar con amigos`.
3. Indica que son cinco jugadores.
4. Marca `Competitivo` o `Cooperativo`, selecciona un género y elige `PC / Steam`.
5. Pulsa `Elegir por el grupo`.
6. Revisa recomendaciones compatibles con cinco jugadores.
7. El grupo abre los detalles del juego, guarda una opción o pide otra recomendación.

---

## 3. Análisis de competencia
### Competidor 1 — Steam (Valve Corporation)
* **Enlace oficial:** [store.steampowered.com](https://store.steampowered.com/)

#### Fortalezas
- Es la tienda digital de PC con el catálogo más masivo y activo del mercado.
- Integra reseñas de usuarios, etiquetas comunitarias (*user tags*), lista de amigos y el sistema *Steam Labs*.
- Máxima adopción: 100% de presencia entre los usuarios de nuestro cuestionario.

#### Debilidades
- **Sobrecarga de elección:** Su interfaz prioriza la venta comercial sobre la recomendación contextual inmediata.
- No resuelve la pregunta directa: *«¿A qué jugamos las personas conectadas en llamada de Discord ahora mismo?»*.
- El buscador no permite filtrar de forma ágil combinando número exacto de integrantes con tiempo de sesión disponible y compatibilidad simultánea.

#### Reseñas reales y quejas de 1 estrella (Trustpilot / Foros de Steam Community)
> ⭐☆☆☆☆ *"El sistema de recomendación es horrible. Tengo cientos de juegos en mi biblioteca y siempre me sugiere lo mismo o juegos que no tienen nada que ver con lo que busco. La biblioteca se vuelve inmanejable cuando acumulas títulos."* — Usuario en Trustpilot.
>
> ⭐☆☆☆☆ *"Steam no ayuda a elegir. Pasamos más de media hora mirando la tienda o la lista de amigos para ver qué podemos jugar juntos y casi nunca encontramos filtros útiles por número exacto de integrantes."* — Crítica en Steam Community Discussions.

**Oportunidad para PlayNext:** Brindar una interfaz ligera, sin sobrecarga comercial, capaz de recomendar con un solo clic según el contexto exacto (solitario o grupo de N personas).

---

### Competidor 2 — HowLongToBeat (IGN Entertainment)
* **Enlace oficial:** [howlongtobeat.com](https://howlongtobeat.com/)

#### Fortalezas
- Base de datos de referencia mundial sobre estimación de duración de videojuegos (historia principal, extras y completista).
- Datos recopilados de partidas reales aportados por la comunidad.
- Imprescindible para jugadores que buscan títulos adaptados a su tiempo disponible.

#### Debilidades
- Está concebida como un buscador de consulta pasiva, no como un asistente de recomendación activa.
- Requiere que el usuario ya tenga en mente el título del videojuego para buscarlo.
- Carece de filtros orientados a multijugador grupal, tamaño del grupo o compatibilidad cruzada.

#### Reseñas reales y quejas de 1 estrella (Foros Reddit r/patientgamers / Web)
> ⭐☆☆☆☆ *"La web es genial si ya sabes a qué quieres jugar, pero no sirve de nada si estás bloqueado mirando la pantalla sin saber qué empezar. Le falta un recomendador inteligente que use su base de datos de horas."* — Usuario en Reddit r/patientgamers.
>
> ⭐☆☆☆☆ *"La interfaz de búsqueda es tosca y no tiene ninguna herramienta para grupos o para descubrir juegos nuevos por tiempo disponible sin tener que tragarse listas infinitas."* — Reseña en foros web.

**Oportunidad para PlayNext:** Emplear la métrica de tiempo de sesión (partidas cortas vs. largas) como un filtro selector directo en el motor de recomendación, ahorrando la búsqueda manual.

---

### Competidor 3 — RAWG Video Games Database
* **Enlace oficial:** [rawg.io](https://rawg.io/)

#### Fortalezas
- Base de datos con más de 500.000 videojuegos y una API abierta muy documentada.
- Clasificación limpia por plataformas, géneros, creadores y valoraciones medias.
- Excelente estética visual para explorar fichas técnicas.

#### Debilidades
- Funciona como una red social/catálogo de descubrimiento infinito, lo que fomenta aún más la parálisis por elección.
- La información de multijugador es genérica (suele indicar solo si tiene o no multijugador, pero no el número exacto de jugadores soportados).
- No cuenta con un recomendador de un solo clic adaptado al grupo.

#### Reseñas reales y quejas de 1 estrella (Google Play Store / Trustpilot)
> ⭐☆☆☆☆ *"Es básicamente una Wikipedia de videojuegos. Entras para buscar una recomendación rápida y terminas scrolleando 40 minutos entre portadas sin decidirte por nada."* — Reseña en Google Play Store.
>
> ⭐☆☆☆☆ *"Faltan datos clave para jugar con amigos. Pone 'multijugador' pero no te dice si admite 3, 4 o más personas hasta que lo investigas por fuera."* — Crítica en foros de videojuegos.

**Oportunidad para PlayNext:** Colocar una capa de decisión guiada por encima del catálogo: número exacto de personas, filtro de modo cooperativo/competitivo y botón directo de decisión.

---

### Oportunidades identificadas para PlayNext
- **Modo 'Sorpréndeme' (Un solo clic):** Para el jugador que no quiere configurar nada y busca romper el bucle de indecisión al instante.
- **Selector de modo:** Separación clara y radical entre `Jugar solo` y `Jugar con amigos`.
- **Filtro central por número de jugadores:** Eliminar de raíz la frustración de recomendar títulos que no cuadran con el grupo en llamada.
- **Transparencia y explicabilidad:** Explicar con una frase por qué se recomienda ese título (*"Recomendado porque sois 4 personas, buscáis cooperativo y tenéis 45 minutos"*).
- **Cero barreras de entrada:** Totalmente funcional sin registro, sin login obligatorio y sin pedir permisos intrusivos de cuentas de terceros.
- **Función de descarte activo:** Si la opción no convence, pulsar 'Siguiente opción' sin que repita títulos ya rechazados en la sesión.


## 4. Propuesta de valor única

### Problema actual

A jugadores habituales de PC les cuesta decidir qué videojuego jugar porque tienen demasiadas opciones. Hoy suelen navegar por Steam, buscar listas genéricas o preguntar en Discord, pero estas soluciones no combinan de forma rápida su contexto actual: si están solos o con amigos, cuántas personas son, qué plataforma usan, qué género quieren y cuánto tiempo tienen.

### Propuesta de valor

> A los jugadores de PC que no saben a qué jugar les ocurre que pierden tiempo navegando entre bibliotecas grandes o discutiendo con amigos. Hoy usan Steam, Epic, búsquedas y Discord, pero esas herramientas no les dan una recomendación inmediata según su situación. PlayNext ofrece recomendaciones de videojuegos explicables y aleatorias, filtradas por modo individual o grupo, número de jugadores, plataforma, género y tiempo disponible.

### Diferenciación

PlayNext no pretende sustituir Steam, Epic Games ni una base de datos de videojuegos. Su objetivo es resolver un momento muy concreto: *elegir rápidamente qué jugar ahora*.

El MVP permite usar la aplicación sin cuenta y guarda favoritos y descartados de forma local. La integración con bibliotecas de Steam/Epic y el cálculo de títulos compartidos se plantean como evolución futura, porque los usuarios muestran interés, pero también preocupación por seguridad y permisos.
