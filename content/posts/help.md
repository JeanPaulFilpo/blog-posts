---
title: "Guía rápida para escribir posts con Hugo y publicarlos en GitHub"
date: 2026-08-30
draft: true
tags: ["hugo", "github", "blog", "publicacion"]
categories: ["blog"]
description: "Todos los comandos básicos para crear, previsualizar, publicar y mantener este blog de Hugo en GitHub."
---

Este post es tu guía de referencia rápida para trabajar con este blog. Aquí te dejo todo lo que necesitas saber para escribir artículos, revisarlos localmente y publicarlos en GitHub.

## 1) Qué es Hugo y cómo se usa aquí

Hugo es un generador de sitios estáticos. En este proyecto, cada entrada del blog está escrita en Markdown y se transforma automáticamente en páginas HTML.

La estructura principal es esta:

- `content/` → los posts y páginas del sitio
- `layouts/` → plantillas del tema
- `static/` → archivos estáticos como imágenes o favicon
- `public/` → la versión compilada del sitio
- `hugo.toml` → configuración principal del blog

## 2) Instalar Hugo en tu Mac

Si aún no lo tienes instalado, ejecuta:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

eval "$(/opt/homebrew/bin/brew shellenv zsh)"
brew install hugo
```

Luego confirma que está funcionando:

```bash
hugo version
```

Si todo salió bien, verás algo como:

```bash
hugo v0.165.0+extended+withdeploy darwin/arm64 ...
```

## 3) Cómo crear un nuevo post

La forma recomendada es usar la terminal:

```bash
hugo new posts/mi-nuevo-post.md
```

Esto crea un archivo en `content/posts/` con un encabezado inicial tipo:

```yaml
---
title: "Mi nuevo post"
date: 2026-08-30
draft: true
tags: []
categories: []
description: ""
---
```

### Campos útiles del front matter

- `title`: nombre del artículo
- `date`: fecha de publicación
- `draft`: si es `true`, no se publica en la vista normal
- `tags`: palabras clave para filtrar
- `categories`: categorías del blog
- `description`: resumen del artículo

Cuando estés listo para publicarlo, cambia:

```yaml
draft: true
```

a:

```yaml
draft: false
```

## 4) Escribir el contenido del post

Los posts viven en Markdown (`.md`). Puedes escribir con textos, listas, enlaces, encabezados y bloques de código.

Ejemplo básico:

```markdown
# Título del artículo

Este es el primer párrafo.

## Subtítulo

- Punto 1
- Punto 2
- Punto 3

```bash
echo "Hola mundo"
```
```

### Recomendaciones para escribir bien

- Usa títulos claros y breves
- Mantén los párrafos cortos
- Añade enlaces a referencias externas
- Usa `tags` y `categories` para organizar el blog
- Si el post aún no está listo, déjalo en `draft: true`

## 5) Previsualizar el sitio localmente

Para levantar el sitio en tu máquina y ver los cambios en tiempo real:

```bash
hugo server -D
```

La opción `-D` incluye los posts en borrador. Si quieres verlo solo en el sitio que ya está publicado, usa:

```bash
hugo server
```

Luego abre en tu navegador:

```text
http://localhost:1313
```

### Si quieres que se actualice más rápido

```bash
hugo server --disableFastRender
```

Esto es útil cuando estás editando y quieres ver cambios con menos demora.

## 6) Generar la versión final del sitio

Cuando ya estés listo para compilar la versión estática del blog:

```bash
hugo
```

Esto genera la carpeta `public/` con todos los archivos HTML listos para publicar.

## 7) Cómo revisar el proyecto antes de subirlo

Puedes chequear el estado del repositorio con:

```bash
git status
```

Y ver lo que se ha modificado:

```bash
git diff
```

Si quieres compilar y confirmar que no hay errores:

```bash
hugo
```

Si la salida termina sin errores, la versión está bien generada.

## 8) GitHub: cómo hacer commit y push

Este repositorio ya está conectado a GitHub con el remoto `origin` y la rama `main`.

### 1. Verifica el estado

```bash
git status
```

### 2. Añade los cambios

```bash
git add .
```

### 3. Haz el commit

```bash
git commit -m "Agregar nuevo post sobre Hugo"
```

### 4. Subelo a GitHub

```bash
git push origin main
```

Esto sube los cambios a la rama principal del repositorio.

## 9) Cómo publicar con GitHub Pages

Este proyecto tiene la base configurada para GitHub Pages:

```toml
baseURL = 'https://jeanpaulfilpo.github.io/blog-posts/'
```

Eso significa que el sitio se publicará bajo una URL tipo:

```text
https://jeanpaulfilpo.github.io/blog-posts/
```

### Opción recomendada

En GitHub, entra a:

1. `Settings`
2. `Pages`
3. Elige la rama que vas a publicar (`main` o `gh-pages`, según tu flujo)
4. Guarda la configuración

Si usas la opción de publicar la carpeta `public` desde un branch de despliegue, normalmente haces esto:

```bash
hugo

git add public

git commit -m "Actualizar sitio generado"

git push origin main
```

Si tu flujo usa `gh-pages`, también puedes hacer:

```bash
git subtree push --prefix public origin gh-pages
```

## 10) Flujo diario recomendado

Aquí va la rutina más útil para escribir posts:

```bash
# 1. Crear el archivo
hugo new posts/mi-post.md

# 2. Editar el contenido
# abrir el archivo en VS Code

# 3. Revisar en local
hugo server -D

# 4. Cuando esté listo
hugo

git add .
git commit -m "Añadir nuevo post"
git push origin main
```

## 11) Insertar ecuaciones con LaTeX

Si quieres poner fórmulas en tus posts, puedes usar KaTeX con este formato:

```markdown
La energía relativista es:

\\[
E = mc^2
\\]

Y la suma de los primeros números naturales es:

\\[
\\sum_{i=1}^{n} i = \\frac{n(n+1)}{2}
\\]

También puedes escribir una fórmula inline como \\(\\log_{10}(x)\\).
```

### Recomendaciones

- Usa `\(...\)` para fórmulas cortas dentro del texto.
- Usa `\[...\]` para ecuaciones en bloque.
- Evita usar `$...$` si quieres evitar conflictos con Markdown.

## 12) Comandos más útiles para recordarte

```bash
hugo version
hugo new posts/nombre-del-post.md
hugo server -D
hugo server
hugo
git status
git add .
git commit -m "mensaje"
git push origin main
```

## 13) Consejos prácticos

- Siempre prueba el sitio con `hugo server -D` antes de publicar.
- Usa `draft: true` para guardar ideas sin publicarlas aún.
- Revisa los nombres de archivos y slugs para que sean sencillos.
- Haz commits pequeños y descriptivos.
- No publiques sin revisar el contenido final en el navegador.

## 13) Resumen rápido

Si quieres un flujo mínimo y funcional:

```bash
hugo new posts/mi-post.md
# editar el archivo
hugo server -D
# cuando esté listo
hugo
git add .
git commit -m "Nuevo post"
git push origin main
```

Y listo: tu artículo queda listo para ser visto en el sitio y publicado en GitHub.

Si quieres, en el siguiente post puedo ayudarte a crear una plantilla profesional para tus posts con ejemplo de portada, imágenes, tags, categorías y una estructura tipo blog editorial.
