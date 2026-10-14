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

## 3. La competencia

Seis soluciones existentes. Ninguna resuelve nuestro problema.

---

### Competidor 1 — Goodbudget

**Qué hace:** reproduce el método de los sobres en digital.

**Fortalezas:** método claro, sin banco, multi-dispositivo, versión web.

**Debilidades:**

> *"¡Se han borrado todos mis sobres al actualizar la aplicación!"* — App Store, reseña de 1 estrella → [Goodbudget, reseñas de App Store](https://apps.apple.com/us/app/goodbudget-budget-planner/id471112395?see-all=reviews)

> *"Llevo años usando esta aplicación y producto. En algún momento de los últimos 2 o 3 años, arruinaron el proceso de conciliación. Indicaron que implementaron una función que algunos usuarios querían y que está causando esto. Me llevó horas y horas descubrir qué demonios estaba pasando con mi banco... Debido a que GB arruinó el proceso normal de conciliación y descarga de transacciones \"liquidadas\". Mi banco estaba estafando a los clientes ocultando depósitos y reembolsos en los extractos y descargas. Con una conciliación adecuada, que finalmente tuve que hacer MANUALMENTE con más de 8 meses de datos para descubrir dónde se estaban introduciendo los errores. Nunca confíes en un banco, y nunca confíes en un proceso de conciliación defectuoso. Ya no soy usuario..."* — App Store, reseña de 1 estrella → [Goodbudget, reseñas de App Store](https://apps.apple.com/us/app/goodbudget-budget-planner/id471112395?see-all=reviews&platform=iphone)

**Lo que hace bien y nosotros repetimos:** la idea de los sobres (topes por categoría).

**Lo que nosotros mejoramos:** no exigir una conciliación manual ni el registro diario de cada gasto; el registro es opcional.

---

### Competidor 2 — Monefy

**Qué hace:** registro rápido de gastos e ingresos, con categorías y gráficas.

**Fortalezas:** apuntar es casi inmediato; diseño visual claro.

**Debilidades:**

> *"Ufff pésimo servicio. No te ayuda en nada, mezcla las cuentas, tiene apartados supuestamente útiles pero no sirven de nada porque al final del día tú mismo tienes que hacer el cuadre de todo. O sea, hacer las cuentas antes aparte, y luego pasarlas a Monefy, si es el caso, cuál es el chiste de tener la aplicación? Intenté reiniciarla varias veces, pero por alguna razón, continúa teniendo datos que nadie ha introducido, generando errores con tus cuentas de manera inevitable."* — App Store, reseña de 1 estrella → [Monefy, reseñas de Google Play](https://play.google.com/store/apps/details?id=com.monefy.app.lite&hl=es)

> *"Antes utilizaba esta aplicación e incluso compré la versión de pago. Ahora es prácticamente inútil si no pagas una suscripción; incluso un Excel es mejor."* — App Store, reseña de 1 estrella → [Monefy, reseñas de App Store](https://apps.apple.com/us/app/monefy-bills-money-tracker/id1212024409?see-all=reviews)

La versión gratuita no se conecta al banco y, además, algunas reseñas describen errores en los datos y la necesidad de revisar las cuentas manualmente.

**Lo que hace bien y nosotros repetimos:** la velocidad de registro (nosotros lo llevamos a 2 toques).

**Lo que nosotros mejoramos:** KUBO calcula un ritmo semanal y prioriza el ahorro, sin obligar al usuario a cuadrar manualmente sus cuentas ni a pagar para utilizar la función principal.

---

### Competidor 3 — PocketGuard

**Qué hace:** calcula lo disponible después de facturas y objetivos.

**Fortalezas:** responde exactamente a "¿cuánto me queda?"; maneja objetivos de ahorro.

**Debilidades:**

> *"Pagué la suscripción anual y parecía funcionar de maravilla durante unos meses. Finalmente, después de muchas horas, logré configurar todo correctamente, pero ahora mi banco no actualiza los datos. Es la segunda vez que sucede. Me comuniqué con soporte y se disculparon, diciendo que su equipo técnico estaba trabajando en ello. Después de seis semanas, decidí eliminar la cuenta y empezar de cero; perdí todo mi trabajo. Y ahora ha vuelto a pasar. Dinero y tiempo perdidos... lo cual es un gran problema en esta situación económica, sobre todo cuando intento administrar mi presupuesto."* — App Store, reseña de 1 estrella → [PocketGuard, reseñas de App Store](https://apps.apple.com/us/app/pocketguard-budget-app/id949414211)

La conexión al banco es un requisito y sus reseñas muestran que, cuando la sincronización falla, el usuario puede perder tiempo y trabajo registrado.

**Lo que hace bien y nosotros repetimos:** la promesa de "un número disponible".

**Lo que nosotros mejoramos:** no pedir credenciales bancarias ni depender de la sincronización del banco; el número se calcula con tres datos que el usuario introduce voluntariamente.

---

### Competidor 4 — Rata y Fina

**Qué hace:** app de control de gastos con un tono directo y sincero. Su lema es *"La única que te dice la verdad"*.

**Fortalezas:**
- Tono diferenciador: *"Las apps de finanzas te tratan como si fueras de cristal. Fina no."*
- Presente en App Store y Google Play.
- Crecimiento rápido: de 5 a 201 valoraciones en pocos meses.

**Debilidades:**
- **Suscripción obligatoria** para todas las funciones: la versión gratuita solo permite registrar un gasto en una sola categoría.
- Tiene una versión gratuita muy limitada y reserva la mayoría de funciones para la suscripción.
- Su propuesta se apoya mucho en el tono y en la estética, pero no ofrece una alternativa gratuita completa.
- El tono directo puede generar rechazo en usuarios que buscan algo más amable.

> *"La aplicación es bonita y aparentemente útil, pero al principio no informa de que es de pago. Después del cuestionario obliga a pagar para poder usarla."* — App Store, reseña de 1 estrella → [Rata y Fina, reseñas de App Store](https://apps.apple.com/es/app/rata-y-fina-control-de-gastos/id6787686922?see-all=reviews)

**Lo que nosotros mejoramos:** KUBO es gratis en su versión base y su tono es amable, no duro.

---

### Competidor 5 — YNAB (You Need A Budget)

**Qué hace:** la app de presupuesto más conocida del mundo. Método de asignar cada euro a una categoría, con objetivos de ahorro.

**Fortalezas:**
- Marca enorme, comunidad activa, educación financiera integrada.
- El ahorro es central: no gastar lo que no tienes.

**Debilidades (reseñas reales de 1 estrella):**

> *"La sincronización con el banco es extremadamente lenta y no se actualiza. A veces pasan días y todavía no muestra los importes correctos ni coincide con la cuenta bancaria. Tampoco es una aplicación fácil de usar."* — App Store, reseña de 1 estrella → [YNAB, reseñas de App Store](https://apps.apple.com/us/app/ynab/id1010865877?see-all=reviews)

> *"No vale la pena, no hace más que lo que hace una hoja de Excel pero por 2.300 MXN al año... De hecho, en una hoja de cálculo puedes registrar cargos parcializados de una tarjeta de crédito; aquí no."* — Google Play, reseña de 1 estrella → [YNAB, reseñas de Google Play](https://play.google.com/store/apps/details?id=com.youneedabudget.evergreen.app&hl=es)

Suscripción de **14,99 $/mes** o **109 $/año**. Las reseñas también señalan problemas de sincronización, cambios de interfaz y un número excesivo de pasos.

**Lo que nosotros mejoramos:** KUBO no exige apuntar nada ni pagar suscripción.

---

### Competidor 6 — Fintonic

**Qué hace:** app española que agrupa cuentas bancarias y clasifica gastos automáticamente.

**Fortalezas:**
- La más usada en España (más de 100.000 valoraciones en Google Play, 4,4/5).
- Conexión bancaria real, clasificación automática.

**Debilidades (reseñas reales de 1 estrella):**

> *"No sincroniza los bancos, no puedes hacer previsiones de gastos porque las han quitado. Ver tus movimientos ahora es un infierno porque están ocultos. La han fastidiado."* — App Store, reseña de 1 estrella → [Fintonic, reseñas de App Store](https://apps.apple.com/es/app/fintonic-ahorra-y-fin%C3%A1nciate/id672220319?see-all=reviews)

> *"La puntilla ha sido que se han reseteado todos los movimientos que tenía reclasificados y divididos por conceptos. Todo el trabajo de clasificación de este año y anteriores se ha perdido, y recuperar esa información es prácticamente imposible. Después de tanto tiempo organizando mis finanzas en Fintonic, que desaparezca sin más es el punto y final. No me vuelve a pasar: vuelvo a Excel, donde mis datos y mi trabajo dependen de mí."* — Google Play, reseña de 1 estrella → [Fintonic, reseñas de Google Play](https://play.google.com/store/apps/details?id=com.fintonic&hl=es)

Requiere **credenciales bancarias** para funcionar y depende de la conexión con las entidades financieras.

**Lo que nosotros mejoramos:** KUBO no pide credenciales ni datos bancarios.

---

### Oportunidades que deja la competencia

1. **Las soluciones actuales tienen fricciones diferentes:** unas dependen de la sincronización bancaria y otras exigen introducir o revisar los gastos manualmente. **Nuestro hueco:** un número semanal calculado con pocos datos y sin conexión bancaria.
2. **Aunque algunas aplicaciones tienen metas de ahorro, KUBO las coloca en el centro del presupuesto:** el objetivo se resta antes de calcular cuánto se puede gastar cada semana.
3. **KUBO propone un colchón de imprevistos con reglas visibles:** ante una subida, el usuario ve qué pasa si la descuenta del colchón, del gasto flexible o de un kubo.
4. **KUBO explica el número semanal:** muestra de dónde sale y cómo cambia si se modifica un ingreso, un gasto fijo o el objetivo de ahorro.

### Resumen

| Competidor | Banco | Apuntar todo | Ahorro primero | Colchón | Explicación |
|---|---|---|---|---|---|
| Goodbudget | No | Sí | No | No | No |
| Monefy | No | Sí | No | No | No |
| PocketGuard | Sí | No | Parcial | No | No |
| Rata y Fina | No | Sí | Parcial | No | No |
| YNAB | Sí | Parcial | Sí | No | Parcial |
| Fintonic | Sí | No | No | No | No |
| **KUBO (nosotros)** | **No** | **Opcional** | **Sí** | **Sí** | **Sí** |

---

## 4. Propuesta de valor única

### Problema actual

A jugadores habituales de PC les cuesta decidir qué videojuego jugar porque tienen demasiadas opciones. Hoy suelen navegar por Steam, buscar listas genéricas o preguntar en Discord, pero estas soluciones no combinan de forma rápida su contexto actual: si están solos o con amigos, cuántas personas son, qué plataforma usan, qué género quieren y cuánto tiempo tienen.

### Propuesta de valor

> A los jugadores de PC que no saben a qué jugar les ocurre que pierden tiempo navegando entre bibliotecas grandes o discutiendo con amigos. Hoy usan Steam, Epic, búsquedas y Discord, pero esas herramientas no les dan una recomendación inmediata según su situación. PlayNext ofrece recomendaciones de videojuegos explicables y aleatorias, filtradas por modo individual o grupo, número de jugadores, plataforma, género y tiempo disponible.

### Diferenciación

PlayNext no pretende sustituir Steam, Epic Games ni una base de datos de videojuegos. Su objetivo es resolver un momento muy concreto: *elegir rápidamente qué jugar ahora*.

El MVP permite usar la aplicación sin cuenta y guarda favoritos y descartados de forma local. La integración con bibliotecas de Steam/Epic y el cálculo de títulos compartidos se plantean como evolución futura, porque los usuarios muestran interés, pero también preocupación por seguridad y permisos.
