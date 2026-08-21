# Proceso de Acreditación — App de afiches

App simple para que los funcionarios vean los afiches del proceso de acreditación
desde el celular, a modo de ayuda de memoria. No necesita instalación: es una
página web con buscador y filtros por etapa.

## 1. Cómo agregar sus PDF reales

1. Copie sus archivos PDF dentro de la carpeta `pdfs/` (reemplace o borre los
   4 de ejemplo).
2. Abra `index.html` con un editor de texto (Bloc de notas, VS Code, etc.).
3. Busque el bloque que dice `const CATALOGO = [` cerca del inicio del `<script>`.
4. Por cada afiche, agregue un bloque así:

```js
{
  archivo: "pdfs/nombre-del-archivo.pdf",
  titulo: "Nombre corto del afiche",
  descripcion: "Una o dos frases explicando de qué trata.",
  etapa: "Nombre de la etapa"   // opcional, agrupa y filtra
}
```

   - `archivo`: debe coincidir EXACTO con el nombre del PDF dentro de `pdfs/`
     (cuidado con mayúsculas, tildes y espacios — mejor evitarlos).
   - `etapa`: agrupa los afiches en chips filtrables arriba de la lista
     (por ejemplo: "Autoevaluación", "Evaluación externa", "Estándares").
     Si lo deja vacío, el afiche aparece en "General".
5. Guarde el archivo. No necesita programar nada más.

## 2. Cómo publicarla para que la vean desde el celular

Los navegadores no permiten abrir `index.html` con doble clic y que cargue los
PDF correctamente (por seguridad). Necesita "servir" la carpeta completa desde
algún lugar. Opciones de más simple a más robusta:

### Opción A — Netlify Drop (la más simple, 2 minutos, gratis)
1. Vaya a https://app.netlify.com/drop desde su computador.
2. Arrastre la carpeta `proceso-acreditacion` completa (con `index.html` y
   `pdfs/` adentro) sobre la página.
3. Netlify le entrega un link (ej: `nombre-al-azar.netlify.app`).
4. Comparta ese link por WhatsApp/correo interno, o genere un código QR del
   link para pegarlo en las salas de personal.

   ⚠️ Importante: si los afiches contienen información sensible o son de uso
   estrictamente interno, revise con TI del hospital si conviene usar esta
   opción pública o la Opción C (servidor interno).

### Opción B — GitHub Pages (gratis, requiere cuenta de GitHub)
1. Cree un repositorio y suba el contenido de la carpeta.
2. Actívelo en Settings → Pages.
3. Obtiene un link tipo `usuario.github.io/repositorio`.

### Opción C — Servidor interno / intranet del hospital (recomendada para uso interno)
Pida a TI que publique la carpeta en un servidor web interno (IIS, Apache,
Nginx, o incluso un simple `python3 -m http.server` en un PC designado dentro
de la red del hospital). Así el contenido queda disponible solo dentro de la
red del hospital, sin salir a internet.

## 3. Uso diario

- Para agregar un afiche nuevo: repita el paso 1, vuelva a subir/publicar la
  carpeta (en Netlify Drop, solo tiene que arrastrarla de nuevo).
- No hace falta que los funcionarios instalen nada: abren el link desde
  Safari/Chrome del celular y queda guardado como acceso directo si quieren
  (en iPhone: compartir → "Agregar a pantalla de inicio").
