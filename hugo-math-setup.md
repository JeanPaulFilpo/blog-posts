# Configurar ecuaciones matemáticas (LaTeX) en Hugo

## Objetivo
Habilitar renderizado de fórmulas matemáticas en un blog Hugo usando el motor KaTeX **embebido de forma nativa en Hugo** (renderizado en build time, sin JavaScript en el cliente). No usar MathJax/KaTeX vía CDN salvo que se indique lo contrario.

## Por qué este método y no CDN client-side
- No agrega JS extra al sitio ni parpadeo de fórmulas sin renderizar al cargar la página.
- Evita un bug conocido de Goldmark (parser markdown de Hugo): convierte `\\` en `<br>` dentro del contenido, lo cual rompe matrices y entornos LaTeX con saltos de línea cuando el renderizado ocurre en el cliente. El passthrough extension evita esto porque preserva el contenido crudo sin tocarlo.

## Pasos

### 1. Config del sitio (`hugo.toml`)
Habilitar el passthrough extension de Goldmark:

```toml
[markup]
  [markup.goldmark]
    [markup.goldmark.extensions]
      [markup.goldmark.extensions.passthrough]
        enable = true
        [markup.goldmark.extensions.passthrough.delimiters]
          block = [['\[', '\]'], ['$$', '$$']]
          inline = [['\(', '\)']]
```

Nota: `$...$` inline queda deshabilitado a propósito para no chocar con signos de precio/moneda en el texto normal. No agregarlo salvo que se pida explícitamente (si se agrega, hay que escapar `\$` en cualquier uso no matemático de `$`).

### 2. Render hook
Crear el archivo `layouts/_default/_markup/render-passthrough.html`:

```gotmpl
{{- $opts := dict "output" "htmlAndMathml" "displayMode" (eq .Type "block") -}}
{{- with try (transform.ToMath .Inner $opts) -}}
  {{- with .Err -}}
    {{- errorf "No se pudo renderizar la fórmula: %s: %s" . $.Position -}}
  {{- else -}}
    {{- .Value -}}
    {{- $.Page.Store.Set "hasMath" true -}}
  {{- end -}}
{{- end -}}
```

### 3. CSS de KaTeX (condicional)
En `layouts/_partials/baseof.html` (o el partial equivalente de `<head>`), incluir el stylesheet solo en páginas que tengan fórmulas:

```gotmpl
{{ if .Page.Store.Get "hasMath" }}
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css">
{{ end }}
```

### 4. Sintaxis en el contenido markdown
- Inline: `\(a^2 + b^2 = c^2\)`
- Bloque: `\[ \frac{1 + \sqrt{5}}{2} \approx 1.618 \]` o `$$ ... $$`

## Verificación
Después de configurar, correr `hugo` (o `hugo server`) y confirmar en el HTML generado que las fórmulas aparecen como `<span class="katex">...</span>` con MathML, no como texto plano con `\(` `\)` literales.

## Alternativa rápida (no recomendada como default)
Si se necesita algo puntual sin tocar la config del sitio, se puede cargar KaTeX por CDN con auto-render en un partial cargado en `<head>`/`<footer>`. Usar solo si el usuario lo pide explícitamente, y advertir sobre el bug de `\\` → `<br>` en matrices.
