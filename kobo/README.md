# Notas para XLSForm / KoboToolbox

Esta carpeta contiene bloques de HTML con estilos *inline* (sin depender de `styles/style.css`), listos para pegar en preguntas tipo `note` dentro de un XLSForm.

## Archivos

| Archivo | Contenido |
|---------|-----------|
| `landing_note.html` | Pantalla de bienvenida: logos, título de la encuesta y cards de duración/confidencialidad/participación/resultados. |
| `consent_note.html` | Información del consentimiento informado (propósito, confidencialidad, procedimientos, riesgos, beneficios, compensación, contacto). |
| `project_note.html` | Bloque con el equipo de investigación. |
| `footer_note.html` | Texto de cierre antes de pasar al consentimiento. |

## Cómo usarlos en el XLSForm

1. En la hoja `survey` del XLSForm, agregá una fila por cada bloque con `type: note`.
2. Pegá el contenido completo del archivo `.html` correspondiente en la columna `label` de esa fila. Enketo (el motor que renderiza los formularios de Kobo) acepta HTML crudo dentro del `label`, no requiere ninguna configuración adicional.
3. Ordená las notas según el flujo que quieran dar a la encuesta (por ejemplo: `landing_note` → `footer_note` → pregunta de consentimiento con `consent_note` como su `label` o como nota previa → `project_note` donde corresponda).
4. La pregunta de aceptar/rechazar el consentimiento (con sus opciones `select_one`) se define aparte en el XLSForm — `consent_note.html` es solo la información, no incluye la pregunta.

## Importante: rutas de imágenes

Los `src="../assets/..."` de estos archivos son rutas relativas a este repositorio y **no van a funcionar dentro de Kobo**, porque el formulario se sirve desde los servidores de Kobo, no desde GitHub. Antes de publicar el formulario:

- Subí cada imagen/ícono como **media del formulario** en Kobo (pestaña "Media" del proyecto) y cambiá el `src` para que apunte solo al nombre de archivo (ej. `src="gamepad_icon.svg"`), **o**
- Alojá las imágenes en una URL pública (por ejemplo, el link "raw" de GitHub) y usá esa URL completa en el `src`.

Si no se hace este ajuste, las notas se van a ver sin imágenes al probar el formulario en Enketo.
