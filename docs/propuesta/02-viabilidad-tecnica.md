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



# Requisitos técnicos: backend y base de datos



# Capacidades del equipo, riesgos y la introducción que une todo
