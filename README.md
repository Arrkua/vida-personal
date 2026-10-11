# VIDA

VIDA es una aplicación web progresiva personal. La versión inicial guarda los registros en IndexedDB del navegador, no requiere cuenta ni envía datos a servicios externos. Empieza sin registros de demostración.

## Ejecutar en un ordenador

Abre una terminal en esta carpeta y sirve los archivos con cualquier servidor web estático. Por ejemplo, si tienes Python instalado:

```sh
python -m http.server 8000
```

Abre `http://localhost:8000` en el navegador. No abras el archivo HTML directamente: los service workers y algunas funciones de almacenamiento requieren `localhost` o HTTPS.

## iPhone

Para instalar VIDA en la pantalla de inicio, publica los archivos en un servidor HTTPS privado bajo tu control o sirve la aplicación desde un ordenador de tu red local con HTTPS y abre esa dirección en Safari. Toca Compartir y elige **Añadir a pantalla de inicio**. La dirección debe seguir accesible para la primera carga; después, el service worker guarda la interfaz para uso sin conexión.

El flujo incluido de GitHub Pages publica solo los archivos necesarios de la aplicación y requiere un repositorio conectado a GitHub Pages. La página será pública: cualquiera podrá abrir una instalación vacía de VIDA. Los registros no se publican ni se sincronizan, pero el código fuente sí será visible si el repositorio es público.

Safari puede limitar o eliminar el almacenamiento local, especialmente si se limpia el historial/datos del sitio o por falta de uso. IndexedDB no equivale a una copia de seguridad. Exporta copias desde **Más → Ajustes y copias** y guárdalas en un lugar seguro. Importar restaura por identificador y actualiza los registros coincidentes.

## Privacidad, offline y notificaciones

Los registros se guardan en el navegador de ese dispositivo. No hay sincronización entre dispositivos. El service worker almacena la interfaz, mientras IndexedDB conserva los registros locales. La primera visita necesita conexión con el servidor donde alojes la app. Las notificaciones fiables en segundo plano no están activadas: las PWA instaladas en iOS tienen restricciones y esta versión no simula recordatorios.

## Áreas vitales

La taxonomía de áreas y subdivisiones no se precarga porque la especificación solicita respetar la clasificación acordada, pero no incluye sus nombres. Añade y edita áreas desde Ajustes. Las etiquetas actuales son campos de texto; configura la clasificación acordada antes de considerarla definitiva.

## Funciones incluidas

- Inicio con tareas del día, próximos compromisos, recordatorios pendientes, objetivos y áreas.
- Tareas con estado, prioridad, fecha/hora, repetición, recordatorios, objetivos y selección visual de varias áreas y subdivisiones. Las ocurrencias completadas se registran por fecha; las futuras se conservan.
- Plan semanal calculado con la fecha actual y filtros por estado, fecha, prioridad y área.
- Calendario de agenda, día, semana y mes, con navegación de fechas, tareas, eventos y ocurrencias recurrentes.
- Finanzas con movimientos, balance, ingresos, gastos, ahorro neto, tendencia de seis meses, presupuestos mensuales/anuales y objetivos de ahorro.
- Compras con cantidad, precio, estado, totales y marcación como comprado; wishlist separada.
- Alimentación por día y tipo de comida. Introduce alimentos, uno por línea como `avena | 40 | g | con yogur`; cada línea queda guardada con nombre, cantidad, unidad y nota.
- Biblioteca de ejercicios, rutinas con ejercicios vinculados y sesiones que pueden asociarse a una rutina o registrarse libremente.
- Objetivos, notas, checklists con casillas y progreso persistente, regalos, recursos y áreas administrables.
- Búsqueda en los campos y relaciones de todos los módulos; detalle, edición y borrado con confirmación.
- Apariencia clara/oscura/sistema, selección de destinos de la barra inferior, vista inicial del calendario y copias JSON de datos y preferencias.

## Privacidad y límites

El repositorio de GitHub y la aplicación publicada son públicos porque GitHub Pages gratuito no ofrece alojamiento privado. Los datos que introduzcas en VIDA se guardan en el navegador de cada dispositivo; no se suben al repositorio ni se sincronizan. No incluyas datos confidenciales si no aceptas esos límites. Para trasladar información usa exportar/importar.

La app funciona sin conexión después de haber cargado todos los archivos una vez. Las notificaciones solo pueden dispararse mientras VIDA permanece abierta; los navegadores de iPhone no garantizan avisos en segundo plano. Las repeticiones generan ocurrencias en el calendario sin crear duplicados de datos.

La clasificación de áreas no se precarga porque el documento original no contiene los nombres acordados. Puedes crearla en Más → Áreas vitales; cada subdivisión pertenece al área correspondiente. Los datos históricos se guardan por nombre para evitar cambiarlos de forma silenciosa si renombras un área.

La estructura es JavaScript modularizado por funciones dentro de `app.js`, con HTML, estilos, configuración PWA y almacenamiento compartido en IndexedDB. Las funciones avanzadas de análisis deportivo y una experiencia de alimentación con editor visual de filas aún pueden ampliarse; las sesiones y comidas sí se guardan y se pueden recuperar.
