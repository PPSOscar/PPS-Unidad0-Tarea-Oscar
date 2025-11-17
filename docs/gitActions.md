# ⚙️ 2. GitHub Actions – Automatización con Workflow

Este documento recoge **todo el desarrollo del apartado GitHub Actions**, explicando paso a paso cómo se ha configurado el workflow que genera la documentación con MkDocs y la publica automáticamente en la rama `gh-pages`.

---

# 🚀 1. Objetivo del Workflow

El propósito de este workflow es:

- Instalar MkDocs en un runner de GitHub Actions.
- Construir automáticamente la documentación ubicada en `docs/`.
- Generar la carpeta `site/` con el resultado final.
- Publicar esos archivos en la rama `gh-pages`.
- Actualizar GitHub Pages sin intervención manual.

Este proceso transforma cada actualización del repositorio en un despliegue automático.

---

# 📁 2. Ubicación del archivo del workflow

El archivo se crea dentro del directorio:

```
.github/workflows/CreacionDocumentacion.yml
```

> 📌 **Nota:**  
> MkDocs genera HTML a partir de Markdown, pero el workflow es quien se encarga de automatizar ese proceso.

---

# 📝 3. Contenido completo del archivo YAML

Este es el contenido exacto utilizado en el proyecto:

```yaml
name: build-mkdocs

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Setup Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install mkdocs

      - name: Build docs
        run: mkdocs build --clean

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
          publish_branch: gh-pages
```

---

# 🔍 4. Explicación detallada del workflow

## 🟦 4.1 Activación del workflow

```yaml
on:
  push:
    branches:
      - main
```

Esto significa que **cada vez que se haga un `git push` a `main`**, el workflow se activará automáticamente.

---

## 🟩 4.2 Preparación del entorno

El runner utilizado es Ubuntu:

```yaml
runs-on: ubuntu-latest
```

A continuación, se descargan los archivos del repositorio:

```yaml
uses: actions/checkout@v3
```

Y se instala Python:

```yaml
uses: actions/setup-python@v4
with:
  python-version: '3.10'
```

---

## 🟨 4.3 Instalación de MkDocs

```yaml
pip install mkdocs
```

MkDocs es el motor que convierte Markdown → HTML.

---

## 🟧 4.4 Construcción de la documentación

```yaml
mkdocs build --clean
```

Este comando:

- Lee el contenido de `docs/`
- Lo transforma en HTML
- Lo almacena en la carpeta `site/`
- Limpia versiones anteriores

---

## 🟥 4.5 Publicación en GitHub Pages

Se usa la acción oficial **peaceiris/actions-gh-pages**:

```yaml
uses: peaceiris/actions-gh-pages@v3
with:
  github_token: ${{ secrets.GITHUB_TOKEN }}
  publish_dir: ./site
  publish_branch: gh-pages
```

Esto:

- Publica la carpeta `site/`
- En la rama `gh-pages`
- Lo hace automáticamente sin claves manuales

---

# 🌐 5. Resultado

Tras ejecutarse el workflow:

- Se crea o actualiza la rama `gh-pages`
- GitHub Pages utiliza esa rama para mostrar la web pública
- Tu documentación está siempre actualizada sin esfuerzo manual

Puedes consultar la ejecución en:

```
GitHub → Actions → build-mkdocs
```

---

# 📝 6. Conclusión del apartado GitHub Actions

Gracias a este workflow he aprendido:

- Cómo automatizar procesos de construcción y despliegue.
- Cómo funcionan los runners de GitHub Actions.
- Cómo empaquetar documentación en pipelines reales.
- Cómo usar ramas dedicadas para despliegue (`gh-pages`).
- Cómo integrar documentación + automatización + publicación en un solo flujo.

Esto permite mantener un proyecto documentado, organizado y con actualizaciones automáticas, siguiendo prácticas reales del mundo DevOps.

---
