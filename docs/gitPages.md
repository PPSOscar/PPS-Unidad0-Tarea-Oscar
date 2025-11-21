#3. Publicación de la Documentación con GitHub Pages

En este apartado documento y recopilo **todo el desarrollo del apartado GitHub Pages**, explicando cómo he configurado la publicación automática de la documentación generada con MkDocs en la rama _gh-pages_.

---

#1. Objetivo de GitHub Pages

Incluyo en este apartado:

- Publicación de la web generada por MkDocs.
- Utilización de la rama _gh-pages_ (creada automáticamente por GitHub Actions).
- Permitir el acceso público a la documentación desde cualquier navegador.
- Mantener la web siempre actualizada de forma automática.

---

#2. Confirmar que tengo la rama `gh-pages`

GitHub Pages funciona utilizando una rama especial llamada con el mismo nombre

Esta rama **no se crea manualmente**, sino que la genera automáticamente el workflow de GitHub Actions tras ejecutar _mkdocs build_ (comentado en el apartado GitHub Actions, en la creación del archivo _.yml_).

Compruebo que la rama existe con el siguiente comando:

```
git fetch
git branch -a
```
En mi caso, se muestran ambas ramas y se indica con * que estoy situado en la rama _main_.

![rama](img/imagenes_gitPages/rama.png)

---

#3. Configuración de GitHub Pages

Una vez que he comprobado que tengo la rama, configuro GitHub Pages desde mi repositorio de GitHub:

1. Voy a **Settings**.
2. Selecciono la opción **Pages** en el menú lateral.
4. En *Source* selecciono:

   - **Branch:** `gh-pages`
   - **Folder:** `/ (root)`

5. Guardo la configuración.

GitHub muestra la URL pública donde se publicará la documentación.

![ghpages](img/imagenes_gitPages/ghpages.jpg)

---

#4. URL - github.io

Mi URL de acceso a la documentación es la siguiente:

```
https://ppsoscar.github.io/PPS-Unidad0-Tarea-Oscar/gitPages/
```

Es esta URL:

- _ppsoscar_ = mi nombre de usuario de GitHub
- _PPS-Unidad0-Tarea-Oscar_ = nombre del repositorio

Al abrir esa URL, mi web generada por MkDocs está disponible públicamente.

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

