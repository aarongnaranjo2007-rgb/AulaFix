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

## 2. Las personas

Tres personas reales de nuestro entorno, con roles distintos frente a la aplicación. Cada una justifica una parte del producto.

---

### User persona 1 — Elisa Lucena 

> "Verificando los gastos en la aplicación del banco diariamente, no llevo unas cuentas exactas."

| Campo | Dato |
|---|---|
| Edad | 25 años |
| Ocupación | Integradora social |
| Ubicación | San Fernando |
| Dispositivo | Móvil iPhone |
| Conectividad | WiFi |
| Momento de uso | Noches, en casa, en el sofá |
| Contexto | Revisa la app del banco a diario para comprobar que no se ha pasado |

#### Necesidades

- Saber en 5 segundos cuánto le queda este mes sin abrir la app del banco y recorrer apuntes.
- Llegar a fin de mes sin descubrir que se ha pasado de gasto cuando ya es tarde.
- Ahorrar lo que le sobra sin quedarse corta para las facturas del mes siguiente.

#### Frustraciones

- Se da cuenta de que gastó de más cuando el mes ya se le ha acabado: "lo averiguo viendo que había gastado más de lo normal, calculándolo con la calculadora".
- Va "de cabeza": la cuenta de cuánto le queda vive en la memoria, no en un número fiable.
- Los gastos imprevistos se los paga quitándole dinero a las facturas: "de los mismos gastos con los que paga las facturas".
- Tiene que abrir la app del banco a diario para sentir que controla su dinero.

#### Objetivos

- Decidir si puede gastarse algo en 5 segundos, sin abrir el banco.
- Llegar a fin de mes sin sorpresas.
- Ahorrar de forma constante sin esfuerzo diario.

#### Casos de uso

1. Abre la app por la noche y ve su número semanal en 5 segundos.
2. Antes de comprar, consulta si está dentro de su ritmo.
3. Al final de mes, recibe un resumen: lo que ahorró, lo que gastó de más y por qué.

---

### User persona 2 — Clara Romero

> "Ahora mismo no sé lo que me queda para final de mes y tampoco lo quiero saber."

| Campo | Dato |
|---|---|
| Edad | 24 años |
| Ocupación | Dependienta |
| Ubicación | San Fernando |
| Dispositivo | Móvil iPhone |
| Conectividad | WiFi |
| Momento de uso | Fuera de casa, justo antes de hacer una compra |
| Contexto | Vive al día; evita mirar sus números porque le generan ansiedad |

#### Necesidades

- Poder comprarse algo sin tener que hacer cuentas angustiosas antes.
- Que los gastos de sus gatos (comida, veterinario) no arruinen el mes.
- Permitirse sus caprichos sin culpa.

#### Frustraciones

- Se quedó sin dinero antes de cobrar el mes pasado.
- Dejó de llevar cuentas porque lo variable se lo desbarataba: "no llevo un control exhaustivo".
- Evita mirar sus números: "no sé lo que me queda... y tampoco lo quiero saber".
- Termina cada mes sin margen para sus cosas.

#### Objetivos

- Saber antes de comprar si se lo puede permitir.
- Llegar a fin de mes con el ahorro intacto.
- Que la app le diga cuándo puede darse un capricho.

#### Casos de uso

1. Va a comprar y consulta su número semanal antes de pagar.
2. Registra un gasto de 2 toques cuando algo se sale de lo previsto.
3. Recibe un aviso cuando un imprevisto supera su colchón y decide de dónde sacar el dinero.

---

### User persona 3 (Modo Detalle) — Flor Comesaña

> "Lo que más pereza me da es introducir los gastos."

| Campo | Dato |
|---|---|
| Edad | 55 años |
| Ocupación | Autónoma |
| Ubicación | San Fernando |
| Dispositivo | Portátil |
| Conectividad | WiFi |
| Momento de uso | En casa, en el escritorio, a mediodía |
| Contexto | Lleva sus cuentas en un Excel; quiere entender en qué se va el dinero |

#### Necesidades

- Ver en qué se le fue el mes sin tener que revisar el Excel celda a celda.
- Dedicar menos tiempo a apuntar gastos y más a decidir qué hacer con ellos.
- Que el control que ya tiene le sirva también para llegar a fin de mes con margen.

#### Frustraciones

- La parte que más le cuesta es el apuntado: "introducir los gastos".
- Para encontrar un gasto concreto tiene que recorrer la hoja entera.
- Lleva las cuentas al detalle y aun así el día 27 solo le quedan 40 €: controla, pero sin margen.

#### Objetivos

- Saber en qué se gastó el mes en un vistazo.
- Reducir el tiempo dedicado a apuntar.
- Llegar a fin de mes con margen, no solo con control.

#### Casos de uso

1. Importa su extracto bancario en CSV una vez al mes y la app lo reparte entre categorías.
2. Revisa una tabla de movimientos y gráficas por categoría en el portátil.
3. Ajusta su previsión de gastos recurrentes (luz, gasolina) cuando ve desvíos.

# Guion de la Entrevista: ¿Cómo llevas el control de tu dinero, si es que lo llevas?

### Perfil A — Quien NO lleva sus cuentas
* ¿Sabes ahora mismo cuánto te queda para gastar este mes?
* ¿Cuánto crees que te queda esta semana?
* ¿Has intentado alguna vez llevar tus cuentas? ¿Qué pasó?
* ¿Cuándo fue la última vez que te quedaste sin dinero antes del día de cobro?
* ¿De dónde sacaste el dinero la última vez que tuviste un gasto que no esperabas?
* Si te sobran 100 € al final de mes, ¿qué haces con ellos?

### Perfil B — Quien SÍ lleva sus cuentas
* ¿Cómo llevas tus cuentas hoy? (Excel, papel, app...)
* ¿Qué parte de eso te da más pereza?
* ¿Alguna vez has mirado en qué se te fue un mes concreto? ¿Cómo lo averiguaste?
* ¿Cuánto crees que te queda ahora mismo este mes?

---

# Resultados de las Entrevistas

## 1. Elisa Lucena Urbano
* **Edad:** 25 años
* **Perfil:** Tipo B

**¿Cómo llevas el control de tu dinero, si es que lo llevas?**
Metiéndose en la cuenta del banco y mirándolo.

**¿Cómo llevas tus cuentas hoy? (Excel, papel, app...)**
De cabeza, verificando los gastos en la aplicación del banco diariamente; no lleva unas cuentas exactas.

**¿Qué parte de eso te da más pereza?**
Nada.

**¿Alguna vez has mirado en qué se te fue un mes concreto? ¿Cómo lo averiguaste?**
Sí lo ha mirado. Lo averiguó viendo que había gastado más de lo normal, calculándolo con la calculadora.

**¿Cuánto crees que te queda ahora mismo este mes?**
450 € desde primero de mes.

**Esos 450 € que me dices: ¿incluyen lo que ya sabes que vas a pagar este mes (alquiler, luz, facturas) o es lo que ves en la cuenta?**
Sí incluye lo que va a pagar este mes ese dinero.

**La última vez que tuviste un gasto que no esperabas (una factura más alta, un regalo, una reparación), ¿de dónde sacaste el dinero?**
De la propia cuenta, de los mismos fondos con los que paga las facturas.

**Si te sobran 100 € al final de mes, ¿qué haces con ellos?**
Se guardan y se ahorran.

**¿Hay algo de tu dinero que te quite la cabeza y de lo que no te haya preguntado?**
No sabe / no entiende la pregunta.

---

## 2. Clara Romero
* **Edad:** 24 años
* **Ocupación:** Dependienta
* **Perfil:** Tipo A

**¿Cómo llevas el control de tu dinero, si es que lo llevas?**
Depende de lo que tenga que pagar ese mes.

**¿Sabes ahora mismo cuánto te queda para gastar este mes?**
Ahora mismo no sé lo que me queda para final de mes y tampoco lo quiere saber.

**¿Cuánto crees que te queda esta semana?**
No sé cuánto me queda, voy un poco al día.

**¿Has intentado alguna vez llevar tus cuentas? ¿Qué pasó?**
He intentado llevar un control, pero como a veces me escriben para los gastos del veterinario, y otras veces los gatos comen más o tengo que comprar comida para ellos, no llevo un control exhaustivo.

**¿Cuándo fue la última vez que te quedaste sin dinero antes del día de cobro?**
Pues sí, el mes pasado.

**¿De dónde sacaste el dinero la última vez que tuviste un gasto que no esperabas?**
Tengo una cuenta de ahorro en la que había un dinero y cada vez que necesito lo saco de ahí; es para gastos extraordinarios.

**Si te sobran 100 € al final de mes, ¿qué haces con ellos?**
Pues seguramente me dé un capricho, que me doy pocos.

---

## 3. Flor Comesaña
* **Edad:** 55 años
* **Ocupación:** Autónoma
* **Perfil:** Tipo B

**¿Cómo llevas el control de tu dinero, si es que lo llevas?**
Lo llevo con un Excel; cada dos días agrego los movimientos.

**¿Cómo llevas tus cuentas hoy? (Excel, papel, app...)**
Con un Excel.

**¿Qué parte de eso te da más pereza?**
Introducir los gastos.

**¿Alguna vez has mirado en qué se te fue un mes concreto? ¿Cómo lo averiguaste?**
Sí, revisando el Excel uno por uno hasta que di con los gastos.

**¿Cuánto crees que te queda ahora mismo este mes?**
40 € estando a día 27 de septiembre.

**¿Dónde y cuándo suele mirar las cosas del banco o gastar?**
En el portátil, en el escritorio a mediodía.

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
