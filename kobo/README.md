# Notas para XLSForm / KoboToolbox

Esta carpeta contiene bloques de HTML con estilos *inline* (sin depender de `styles/style.css`), listos para pegar en preguntas tipo `note` dentro de un XLSForm.

## Archivos

| Archivo | Contenido |
|---------|-----------|
| `landing_note.html` | Pantalla de bienvenida: logos, título de la encuesta y cards de duración/confidencialidad/participación/resultados. |
| `consent_note.html` | Información del consentimiento informado (propósito, confidencialidad, procedimientos, riesgos, beneficios, compensación, contacto). |
| `project_note.html` | Bloque con el equipo de investigación. |
| `footer_note.html` | Texto de cierre antes de pasar al consentimiento. |
| `support_header_note.html` | Encabezado de "Recursos de apoyo" (logo, título, subtítulo). Siempre visible. |
| `support_guatemala_note.html` | Recursos de apoyo para Guatemala. Solo debe mostrarse si el país seleccionado es Guatemala. |
| `support_belice_note.html` | Recursos de apoyo para Belice. Solo debe mostrarse si el país seleccionado es Belice. |
| `support_el_salvador_note.html` | Recursos de apoyo para El Salvador. Solo debe mostrarse si el país seleccionado es El Salvador. |
| `support_honduras_note.html` | Recursos de apoyo para Honduras. Solo debe mostrarse si el país seleccionado es Honduras. |
| `support_nicaragua_note.html` | Recursos de apoyo para Nicaragua. Solo debe mostrarse si el país seleccionado es Nicaragua. |
| `support_costa_rica_note.html` | Recursos de apoyo para Costa Rica. Solo debe mostrarse si el país seleccionado es Costa Rica. |
| `support_panama_note.html` | Recursos de apoyo para Panamá. Solo debe mostrarse si el país seleccionado es Panamá. |
| `support_link_note.html` | Enlace a recursos adicionales (mujerescreandovideojuegos.com/directorio.html). Siempre visible. |

## Cómo usarlos en el XLSForm

1. En la hoja `survey` del XLSForm, agregá una fila por cada bloque con `type: note`.
2. Pegá el contenido completo del archivo `.html` correspondiente en la columna `label` de esa fila. Enketo (el motor que renderiza los formularios de Kobo) acepta HTML crudo dentro del `label`, no requiere ninguna configuración adicional.
3. Ordená las notas según el flujo que quieran dar a la encuesta (por ejemplo: `landing_note` → `footer_note` → pregunta de consentimiento con `consent_note` como su `label` o como nota previa → `project_note` donde corresponda).
4. La pregunta de aceptar/rechazar el consentimiento (con sus opciones `select_one`) se define aparte en el XLSForm — `consent_note.html` es solo la información, no incluye la pregunta.

## Recursos de apoyo por país (mostrar solo el país seleccionado)

Las notas `support_*_note.html` están pensadas para que, en la encuesta de mujeres, solo se muestre la información del país que la persona seleccionó en una pregunta anterior. Esto se logra con la columna **`relevant`** del XLSForm, no metiendo lógica dentro del HTML:

1. Tené una pregunta previa `select_one` (por ejemplo, con el nombre `country`) con una opción por país.
2. Agregá `support_header_note` como nota siempre visible (sin `relevant`).
3. Agregá una fila `note` por cada `support_<país>_note.html`, y en la columna `relevant` de cada una poné una condición como `${country} = 'guatemala'`, `${country} = 'belice'`, `${country} = 'el_salvador'`, `${country} = 'honduras'`, `${country} = 'nicaragua'`, `${country} = 'costa_rica'`, `${country} = 'panama'` — ajustá los valores para que coincidan exactamente con los `name` de las opciones de tu pregunta `country` en el XLSForm.
4. Agregá `support_link_note` al final, también siempre visible (sin `relevant`).

Con esto, en cuanto la persona selecciona su país, Enketo oculta automáticamente todas las notas de los demás países y solo deja visible la suya.

## Importante: rutas de imágenes

Los `src="../assets/..."` de estos archivos son rutas relativas a este repositorio y **no van a funcionar dentro de Kobo**, porque el formulario se sirve desde los servidores de Kobo, no desde GitHub. Antes de publicar el formulario:

- Subí cada imagen/ícono como **media del formulario** en Kobo (pestaña "Media" del proyecto) y cambiá el `src` para que apunte solo al nombre de archivo (ej. `src="gamepad_icon.svg"`), **o**
- Alojá las imágenes en una URL pública (por ejemplo, el link "raw" de GitHub) y usá esa URL completa en el `src`.

Si no se hace este ajuste, las notas se van a ver sin imágenes al probar el formulario en Enketo.
