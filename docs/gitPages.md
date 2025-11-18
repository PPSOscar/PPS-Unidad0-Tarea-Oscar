# 🌐 3. Publicación de la Documentación con GitHub Pages

Este documento recojo **todo el desarrollo del apartado GitHub Pages**, explicando cómo se ha configurado la publicación automática de la documentación generada con MkDocs mediante la rama `gh-pages`.

---

# 🎯 1. Objetivo de GitHub Pages

El objetivo de este apartado es:

- Publicar la web generada por MkDocs.
- Utilizar la rama `gh-pages` creada automáticamente por GitHub Actions.
- Permitir el acceso público a la documentación desde cualquier navegador.
- Mantener la web siempre actualizada de forma automática.

---

# 📝 2. Requisito previo: tener la rama `gh-pages`

GitHub Pages funciona utilizando una rama especial llamada:

```
gh-pages
```

Esta rama **no se crea manualmente**, sino que la genera automáticamente el workflow de GitHub Actions tras ejecutar:

```bash
mkdocs build
```

Para comprobar que la rama existe:

```bash
git fetch
git branch -a
```

Debería aparecer:

```
remotes/origin/gh-pages
```

---

# ⚙️ 3. Activación de GitHub Pages

Una vez generada la rama, se configuró GitHub Pages:

1. Abrir el repositorio en GitHub.
2. Ir a **Settings**.
3. Seleccionar la opción **Pages** en el menú lateral.
4. En *Source* seleccionar:

   - **Branch:** `gh-pages`
   - **Folder:** `/ (root)`

5. Guardar la configuración.

GitHub mostrará la URL pública donde se publicará la documentación.

---

# 🔗 4. URL pública generada

La URL de acceso a la documentación tiene este formato:

```
https://TuUsuario.github.io/PPS-Unidad0-Tarea-Oscar/
```

Donde:

- `TuUsuario` = tu nombre de usuario de GitHub
- `PPS-Unidad0-Tarea-Tu_nombre` = nombre del repositorio sin `docs/` ni subrutas

Al abrir esa URL, la web generada por MkDocs estará disponible públicamente.

---

# 🔍 5. Verificación del funcionamiento

Para comprobar que GitHub Pages está sirviendo correctamente la documentación:

### ✔ Verificar que la rama `gh-pages` contiene archivos HTML

```bash
git checkout gh-pages
ls -la
```

Deben aparecer:

- `index.html`
- `404.html`
- `css/`
- `js/`
- `search/`

### ✔ Entrar en la URL pública

Basta con abrirla en el navegador.  
Si la página se ve correctamente, GitHub Pages está funcionando.

---

# 🛠 6. Problemas comunes y soluciones

### ❗ La página devuelve 404  
Asegúrate de que:

- Se ha seleccionado **Branch: gh-pages**
- El workflow se ha ejecutado al menos una vez
- La rama contiene un `index.html`

---

### ❗ La web carga pero sin estilos  
Esto ocurre si:

- Se usan rutas erróneas en `mkdocs.yml`
- Se movieron manualmente carpetas dentro de `gh-pages`

Solución: no modificar manualmente la rama `gh-pages`.

---

### ❗ La web muestra contenido raro  
Esto sucede cuando en el `nav:` de `mkdocs.yml` se usan rutas absolutas erróneas.

Debe ser así:

```yaml
nav:
  - Inicio: index.md
  - Git: git.md
```

NO así:

```yaml
nav:
  - Inicio: docs/index.md
```

---

# 📝 7. Conclusión del apartado GitHub Pages

Gracias a este apartado he aprendido:

### 🔹 Cómo publicar documentación automáticamente  
GitHub Pages permite tener la web accesible en todo momento sin subir nada manualmente.

### 🔹 Cómo funciona la rama `gh-pages`  
Es una rama especial dedicada a la publicación, generada automáticamente por el workflow.

### 🔹 Cómo verificar el despliegue  
Revisando la ejecución del workflow y la configuración de Pages.

### 🔹 Cómo resolver problemas frecuentes  
Especialmente los relacionados con rutas y el menú de navegación.

GitHub Pages es una herramienta muy útil y profesional para publicar documentación estática de manera rápida, automática y gratuita.

---

