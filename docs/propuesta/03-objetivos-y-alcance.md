# Fase 3 · Objetivos y alcance · EquipoFaltador

## Introducción

Una vez delimitado el problema de la gestión de incidencias en centros educativos (01-problema.md) y confirmada la viabilidad técnica de su integración con la API de iPasen y la arquitectura MERN (02-viabilidad-tecnica.md), este documento acota con precisión qué metas persigue AulaFix, hasta dónde llega su desarrollo para la defensa final y qué funcionalidades quedan expresamente reservadas para fases posteriores.

El propósito de AulaFix no es abarcar la burocracia académica de Séneca ni competir con software de gestión de activos de grandes corporaciones, sino proporcionar una herramienta ágil, móvil y trazable que resuelva el momento crítico de la detección y subsanación de averías en cualquier dependencia del centro escolar.

---
## 1. Objetivos

### Objetivo general

Proporcionar a la comunidad educativa una plataforma web progresiva (MERN) que centralice, agilice y trace en tiempo real la notificación y resolución de averías e incidencias materiales en todo el centro educativo (aulas, pasillos, aseos y zonas comunes) mediante la validación directa con las credenciales oficiales de Séneca/iPasen, reduciendo el tiempo de reporte y eliminando los canales analógicos informales antes de la defensa final del módulo.

### Objetivos específicos

| ID | Objetivo SMART | Qué se mide | Valor de éxito | Cómo se comprueba |
|:---|:---|:---|:---|:---|
| *OE-01* | Reducir el tiempo medio de notificación de una avería desde cualquier punto del centro por debajo de 30 segundos desde el teléfono móvil. | Tiempo transcurrido (en segundos) desde que el usuario accede al formulario hasta que el ticket queda guardado en MongoDB. | *≤ 30 segundos* en el 90 % de los casos de prueba. | Prueba cronometrada con 3 usuarios reales (Carmen, Manuel y Marcos) en la demo previa a la defensa. |
| *OE-02* | Validar la identidad, rol y código de centro educativo mediante la pasarela proxy de iPasen en menos de 2 segundos sin almacenar contraseñas en el servidor. | Latencia de la petición POST /api/auth/login y verificación de descarte de contraseña en el backend. | *< 2 segundos* de respuesta y *0 contraseñas* persistidas en base de datos o logs. | Monitorización con Thunder Client / Bruno de 10 peticiones concurrentes y auditoría del esquema de MongoDB. |
| *OE-03* | Sincronizar en tiempo real el cambio de estado de un ticket entre el panel de mantenimiento y la interfaz del usuario emisor en menos de 1 segundo. | Tiempo de propagación del nuevo estado (Pendiente → En reparación → Resuelta) en el cliente web. | *< 1 segundo* de retardo visual sin necesidad de recargar manualmente la página completa. | Demostración simultánea con dos dispositivos conectados en la misma red durante la defensa. |
| *OE-04* | Reducir a cero los reportes duplicados de una misma avería en un espacio mediante la advertencia visual previa de incidencias abiertas. | Número de partes duplicados generados sobre un mismo elemento averiado durante una jornada lectiva simulada. | *0 partes duplicados* cuando ya existe una incidencia abierta en el mismo espacio. | Simulación de apertura de incidencia idéntica por dos docentes distintos en la misma aula. |

---
## 2. Alcance

### El MVP

El Producto Mínimo Viable está estrictamente acotado a los *8 requisitos Must-have* (RF-01 al RF-08) definidos y priorizados en el documento de viabilidad técnica:
[Ver definición completa y recorrido del MVP en 02-viabilidad-tecnica.md#3-mvp-producto-mínimo-viable](./02-viabilidad-tecnica.md#3-mvp-producto-mínimo-viable).

Cualquier funcionalidad catalogada como Should, Could o Won't have queda formalmente excluida del flujo del MVP para garantizar su entrega completa y estable.

### Plataforma

- *Aplicación Web Progresiva (PWA / SPA):* Desarrollada en React 18 con Vite y maquetada con Tailwind CSS bajo enfoque Mobile-First.
- *Acceso universal:* Totalmente funcional desde navegadores móviles (Safari en iOS, Chrome en Android) para docentes y alumnado, y optimizada para pantallas de escritorio (Chrome, Firefox, Edge) en los puestos fijos de conserjería y coordinación TIC.
- *Sin dependencias de tiendas:* No requiere empaquetado ni distribución a través de Google Play Store ni Apple App Store, eliminando barreras de instalación y tiempos de revisión.

### Usuarios y datos

- *Usuarios objetivo:* Docentes, alumnado y personal de conserjería/mantenimiento del centro educativo con cuenta activa en Séneca/iPasen.
- *Volumen de usuarios para validación:* Pruebas de campo con un grupo piloto de 15 a 30 usuarios reales del propio instituto durante la fase de validación.
- *Tratamiento de datos:*
  - Cumplimiento estricto del RGPD: las contraseñas nunca se guardan en base de datos; la memoria del servidor descarta la credencial tras recibir el token de Séneca.
  - Minimización de datos: en la colección users de MongoDB solo se guardan el nombre completo, el identificador de usuario (senecaId), el rol (typeProfile) y el código del centro escolar (centerCode).
- *Modo de contingencia (Datos de prueba / Mock):* El sistema dispone de un interruptor por variable de entorno (USE_MOCK_AUTH=true) que carga un set de datos de prueba predefinidos (3 usuarios de rol docente, conserjería y alumnado, junto a 10 incidencias distribuidas por el centro) para permitir el desarrollo offline y asegurar la defensa ante el tribunal en caso de caída o lentitud de los servidores de la Junta de Andalucía.

### Lo que no haremos

| Qué | Por qué |
|:---|:---|
| *Conexión con el módulo de inventario oficial de Séneca* | No existe API pública documentada para la lectura/escritura de inventario patrimonial de la Junta de Andalucía; requeriría permisos institucionales inaccesibles a nivel académico. |
| *Notificaciones push nativas móviles (FCM / APNs en segundo plano)* | El APK descompilado de iPasen reveló que las notificaciones push oficiales usan un canal HTTP sin cifrado y cerrado a clientes ajenos. Las notificaciones se gestionarán dentro de la propia interfaz web en el MVP. |
| *Gestión de compras, presupuestos y facturas de repuestos* | Desvirtúa el foco del proyecto hacia un ERP contable; la adquisición de material corresponde a la secretaría del centro mediante los canales administrativos oficiales. |
| *Canal de chat bidireccional abierto entre alumnado y mantenimiento* | Supone un riesgo operativo de saturación y requiere moderación de contenidos; la comunicación se estructura exclusivamente mediante notas técnicas y cambios de estado de tickets. |
| *Registro manual de usuarios externos al centro* | La plataforma restringe el acceso exclusivamente a identidades corporativas de Séneca cuyo centerCode coincida con el del instituto autorizado, evitando gestionar altas y bajas de cuentas a mano. |

### Ampliaciones futuras

En caso de disponer de tiempo adicional tras cerrar y defender el MVP, las siguientes mejoras se abordarán en este orden estricto de prioridad:

1. *Notificaciones Push Web mediante Service Workers:* Alertas en el navegador del dispositivo móvil cuando cambie el estado de un ticket en el que el usuario es parte interesada.
2. *Generación e impresión de códigos QR por espacio y puesto:* Pegatinas en aulas, pupitres informáticos y puertas de aseos que precarguen automáticamente la ubicación al escanearlas con la cámara.
3. *Panel analítico para el equipo directivo:* Gráficas de tiempos medios de resolución (MTTR), distribución de averías por planta/categoría e historial de intervenciones para justificar partidas presupuestarias.
4. *Integración con la mensajería interna de Séneca:* Notificación formal al tutor o al equipo directivo ante averías graves o conductas contrarias a las normas de uso de instalaciones aprovechando los endpoints analizados de mensajería.
5. *Modo offline con sincronización en segundo plano (PWA + IndexedDB):* Capacidad para levantar partes en sótanos, calderas o zonas deportivas sin cobertura WiFi/4G, sincronizando las peticiones cuando el terminal recupere conexión.
