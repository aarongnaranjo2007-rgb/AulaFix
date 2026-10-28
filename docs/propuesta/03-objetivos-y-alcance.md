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
