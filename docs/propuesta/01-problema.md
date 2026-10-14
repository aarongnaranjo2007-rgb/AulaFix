# PlayNext — Definición del problema

## Introducción

PlayNext es una aplicación web que ayuda a los jugadores a decidir a qué videojuego jugar según su situación actual. El usuario puede buscar por título, explorar un catálogo o recibir una recomendación adaptada a si va a jugar solo o con amigos, al número de jugadores, la plataforma, el género y el tiempo disponible.

La propuesta nace de una situación habitual: disponer de demasiados juegos y, aun así, no conseguir decidir cuál iniciar. El problema se agrava cuando un grupo de amigos quiere jugar junto, porque deben coincidir en gustos, plataformas, juegos disponibles y número de jugadores compatibles.

---

## 1. Necesidad detectada

### Problema

Los jugadores con bibliotecas digitales amplias sufren **sobrecarga de elección**: poseen muchos videojuegos, pero no saben cuál jugar en un momento concreto. Cuando juegan solos, la indecisión les hace invertir demasiado tiempo navegando por Steam o Epic Games, volver a títulos conocidos o abandonar la decisión sin jugar.

En grupos, el problema incorpora más restricciones: los participantes pueden tener preferencias distintas, no compartir los mismos juegos y necesitar un título compatible con el número de personas conectadas.

### ¿A quién afecta?

El problema afecta principalmente a jugadores habituales de PC, especialmente a quienes utilizan Steam como launcher principal y tienen una biblioteca digital de tamaño medio o grande. También afecta a grupos que se conectan por Discord para jugar juntos.

El cuestionario propio reunió 13 respuestas de jugadores de entre 18 y 26 años. Steam aparece en las 13 respuestas como launcher habitual; algunas personas también mencionaron Epic Games y EA.

### Frecuencia

El problema es frecuente porque 12 de las 13 personas encuestadas afirmaron jugar diariamente o casi todos los días. En las respuestas sobre el tiempo dedicado a decidir, la cifra más repetida fue entre 20 y 30 minutos; algunas personas indicaron una hora o incluso más.

### Impacto

La indecisión reduce el tiempo real de juego y causa frustración. Las consecuencias identificadas son:

- Los usuarios terminan jugando a los mismos pocos títulos.
- Algunos jugadores dejan de jugar porque no encuentran una opción que les convenza.
- Los grupos permanecen en una llamada sin jugar o cada persona termina jugando por separado.
- Los usuarios sienten que no aprovechan los juegos que ya han comprado.

### Evidencias propias

Se realizó un cuestionario titulado “¿Qué juego elijo hoy? - Investigación de usuarios”, con 13 respuestas.

Algunas respuestas representativas fueron:

> “Nos entra ganas de jugar a algo nuevo juntos, empezamos a ver opciones durante 30 minutos y al final acabamos jugando a lo mismo de siempre.”

> “La cantidad que tengo hace que tenga demasiadas opciones y muchas veces con la disparidad entre ellos no me decido y acabo haciendo otra cosa.”

> “No coincidimos en juegos comprados o en gustos/apetito. Algunas veces acabamos jugando a los mismos de siempre o directamente nos quedamos en vc sin jugar juntos.”

> “Que teniendo gran variedad no juego la mitad.”

Además, un participante propuso que el producto tuviera un selector de número de jugadores para evitar recomendaciones incompatibles con el grupo:

> “Ponerle el número de jugadores porque, por ejemplo, no te vaya a coger el Split Fiction si sois 26.”

Estas respuestas validan que la aplicación no debe recomendar únicamente por género: debe tener en cuenta el contexto de juego, especialmente el modo individual o grupal, la plataforma y el número de jugadores.

---

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

## 3. La competencia

Seis soluciones existentes. Ninguna resuelve nuestro problema.

---

### Competidor 1 — Goodbudget

*Qué hace:* reproduce el método de los sobres en digital.

*Fortalezas:* método claro, sin banco, multi-dispositivo, versión web.

*Debilidades:*

> "Manual entry required for free users: The free version doesn't sync with your bank accounts, so you must manually enter every transaction." — Experian

> "La versión gratuita requiere apuntar a mano: la versión gratuita no se sincroniza con tus cuentas bancarias, así que debes introducir manualmente cada transacción." (traducción)

> "Which app to use to keep track of expenses. I have tried goodbudget, couple of more. But stop after a month." — Reddit, r/personalfinance

> "Qué app usar para controlar los gastos. He probado Goodbudget, un par más. Pero lo dejo después de un mes." (traducción)

*Lo que hace bien y nosotros repetimos:* la idea de los sobres (topes por categoría).

*Lo que nosotros mejoramos:* no exigir apuntado diario; el registro es opcional.

---

### Competidor 2 — Monefy

*Qué hace:* registro rápido de gastos e ingresos, con categorías y gráficas.

*Fortalezas:* apuntar es casi inmediato; diseño visual claro.

*Debilidades:*

> "Some user reviews complain of glitches in app and a not so [intuitive interface]." — CNBC, reseñas de apps de presupuesto 2026

> "Algunas reseñas de usuarios se quejan de fallos en la app y de una interfaz poco [intuitiva]." (traducción)

La versión gratuita no se conecta al banco: hay que apuntar cada gasto a mano.

*Lo que hace bien y nosotros repetimos:* la velocidad de registro (nosotros lo llevamos a 2 toques).

*Lo que nosotros mejoramos:* el ahorro como centro del producto; Monefy es un registrador de gastos, no un gestor de ahorro.

---

### Competidor 3 — PocketGuard

*Qué hace:* calcula lo disponible después de facturas y objetivos.

*Fortalezas:* responde exactamente a "¿cuánto me queda?"; maneja objetivos de ahorro.

*Debilidades:*

La conexión al banco es un requisito que muchos rechazan: exige entregar credenciales y dejar que miren la cuenta por detrás.

*Lo que hace bien y nosotros repetimos:* la promesa de "un número disponible".

*Lo que nosotros mejoramos:* no pedir credenciales bancarias; el número se calcula con tres datos que el usuario introduce voluntariamente.

---

### Competidor 4 — Rata y Fina

*Qué hace:* app de control de gastos con un tono directo y sincero. Su lema es "La única que te dice la verdad".

*Fortalezas:*
- Tono diferenciador: "Las apps de finanzas te tratan como si fueras de cristal. Fina no."
- Presente en App Store y Google Play.
- Crecimiento rápido: de 5 a 201 valoraciones en pocos meses.

*Debilidades:*
- *Suscripción obligatoria* para todas las funciones: la versión gratuita solo permite registrar un gasto en una sola categoría.
- Solo iOS según algunas fuentes, aunque Appbrain la lista también en Google Play.
- Comunidad muy pequeña (201 valoraciones vs. miles en sus competidores).
- Tono "duro" que puede generar rechazo en usuarios que buscan algo más amable.

*Lo que nosotros mejoramos:* KUBO es gratis en su versión base y su tono es amable, no duro.

---

### Competidor 5 — YNAB (You Need A Budget)

*Qué hace:* la app de presupuesto más conocida del mundo. Método de asignar cada euro a una categoría, con objetivos de ahorro.

*Fortalezas:*
- Marca enorme, comunidad activa, educación financiera integrada.
- El ahorro es central: no gastar lo que no tienes.

*Debilidades (reseñas reales de 1 estrella):*

> "If YNAB's approach makes you miserable and you abandon it after two weeks, it's not worth a penny." — Foro de beancount.io

> "Si el enfoque de YNAB te hace miserable y lo abandonas después de dos semanas, no vale ni un céntimo." (traducción)

Suscripción de *14,99 $/mes* o *109 $/año*. Exige apuntar cada gasto a mano.

*Lo que nosotros mejoramos:* KUBO no exige apuntar nada ni pagar suscripción.

---

### Competidor 6 — Fintonic

*Qué hace:* app española que agrupa cuentas bancarias y clasifica gastos automáticamente.

*Fortalezas:*
- La más usada en España (más de 100.000 valoraciones en Google Play, 4,4/5).
- Conexión bancaria real, clasificación automática.

*Debilidades (reseñas reales de 1 estrella):*

> "Por favor mucho cuidado con los datos personales que envían, tiene muchísimos errores por todos lados, fallo de peticiones y 0 seguridad." — Usuario en redes sociales sobre Fintonic

Requiere *credenciales bancarias* para funcionar.

*Lo que nosotros mejoramos:* KUBO no pide credenciales ni datos bancarios.

---

### Oportunidades que deja la competencia

1. *Ninguna combina las dos cosas:* las que no piden apuntar se conectan al banco; las que no se conectan piden apuntarlo todo. *Nuestro hueco: ni banco ni apuntado constante.*
2. *Ninguna pone el ahorro primero:* todas calculan lo que sobra; ninguna aparta el objetivo antes de dar el número semanal.
3. *Ninguna tiene colchón de imprevistos con reglas visibles:* el desvío se paga quitándole a otra categoría, no desde una bolsa aparte.
4. *Ninguna explica sus cifras:* dicen "te quedan X" pero no muestran de dónde sale ese X.

### Resumen

| Competidor | Banco | Apuntar todo | Ahorro primero | Colchón | Explicación |
|---|---|---|---|---|---|
| Goodbudget | No | Sí | No | No | No |
| Monefy | No | Sí | No | No | No |
| PocketGuard | Sí | No | Parcial | No | No |
| Rata y Fina | No | Sí | Parcial | No | No |
| YNAB | No | Sí | Sí | No | No |
| Fintonic | Sí | No | No | No | No |
| *KUBO (nosotros)* | *No* | *Opcional* | *Sí* | *Sí* | *Sí* |

---
## 4. Propuesta de valor única

### Problema actual

A jugadores habituales de PC les cuesta decidir qué videojuego jugar porque tienen demasiadas opciones. Hoy suelen navegar por Steam, buscar listas genéricas o preguntar en Discord, pero estas soluciones no combinan de forma rápida su contexto actual: si están solos o con amigos, cuántas personas son, qué plataforma usan, qué género quieren y cuánto tiempo tienen.

### Propuesta de valor

> A los jugadores de PC que no saben a qué jugar les ocurre que pierden tiempo navegando entre bibliotecas grandes o discutiendo con amigos. Hoy usan Steam, Epic, búsquedas y Discord, pero esas herramientas no les dan una recomendación inmediata según su situación. PlayNext ofrece recomendaciones de videojuegos explicables y aleatorias, filtradas por modo individual o grupo, número de jugadores, plataforma, género y tiempo disponible.

### Diferenciación

PlayNext no pretende sustituir Steam, Epic Games ni una base de datos de videojuegos. Su objetivo es resolver un momento muy concreto: *elegir rápidamente qué jugar ahora*.

El MVP permite usar la aplicación sin cuenta y guarda favoritos y descartados de forma local. La integración con bibliotecas de Steam/Epic y el cálculo de títulos compartidos se plantean como evolución futura, porque los usuarios muestran interés, pero también preocupación por seguridad y permisos.
