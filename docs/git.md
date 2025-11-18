# 📘 1. Git — Creación del Repositorio y Estructura del Proyecto

Este documento recojo **todo el desarrollo del apartado Git**, explicando paso a paso cómo se ha creado y configurado el repositorio del proyecto, así como la estructura inicial solicitada en la tarea.

---

# 🎯 1. Objetivos del apartado Git

Este apartado permite aprender:

- Cómo crear y clonar un repositorio en GitHub.
- Cómo organizar correctamente la estructura de un proyecto.
- Cómo realizar commits y subir cambios.
- Cómo añadir colaboradores.
- Cómo configurar Git en local.

Es la base sobre la cual se construye todo el proyecto.

---

# 🏗️ 2. Creación del repositorio en GitHub

El primer paso consistió en crear un repositorio en GitHub:

1. Acceder a GitHub → **New repository**.
2. Asignar el nombre obligatorio:

```
PPS-Unidad0-Tarea-Oscar
```

3. Seleccionar visibilidad **Public**. 
4. (Opcional) Añadir README inicial.
5. Crear repositorio y copiar la URL HTTPS.

---

# 💻 3. Clonado del repositorio en Kali Linux

En la terminal se ejecutó:

```bash
git clone https://github.com/TuUsuario/PPS-Unidad0-Tarea-Oscar.git
cd PPS-Unidad0-Tarea-OScar
```

Comprobación de que estamos en la ruta correcta:

```bash
pwd
ls -la
```

---

# 📂 4. Creación de la estructura del proyecto

Se crearon todas las carpetas y archivos necesarios:

```bash
mkdir -p calculator docs .github/workflows
touch calculator/__init__.py calculator/gui.py
touch docs/index.md docs/git.md docs/gitActions.md docs/gitPages.md docs/docker.md docs/evidencias.md docs/conclusiones.md
touch mkdocs.yml requirements.txt README.md
```

De esta forma queda montada toda la estructura base del proyecto.

---

# 🧩 5. Configuración de Git en local

Antes de realizar commits, se configuró la identidad del usuario:

```bash
git config --global user.name "PPSOscar"
git config --global user.email "oscar.polofernandez..."
```

Comprobación:

```bash
git config user.name
git config user.email
```

Esto permite que los cambios subidos al repositorio queden correctamente firmados.

---

# 💾 6. Primer commit y subida al repositorio

Después de crear la estructura:

```bash
git add .
git commit -m "Estructura inicial del proyecto creada"
git push origin main
```

Este commit marca el punto inicial del proyecto, con todos los archivos base.

---

# 👥 7. Añadir colaborador al repositorio

Para permitir supervisión y acceso al profesor, se añadió como colaborador:

Ruta:

```
Repository → Settings → Collaborators → Add collaborator
```

Colaborador añadido:

```
PPS...
```

Esto habilita acceso directo al repositorio para revisión y control.

---

# 📌 8. Comprobaciones realizadas

### ✔ Confirmación de la estructura del proyecto

```bash
ls -R
```

### ✔ Revisión del historial de cambios

```bash
git log --oneline
```

### ✔ Estado del repositorio

```bash
git status
```

---

# 📝 9. Conclusiones del apartado Git

Gracias a este apartado he podido aprender y reforzar:

### 🔹 La importancia del control de versiones  
Git permite mantener el proyecto organizado, documentado y con un historial claro de cambios.

### 🔹 Cómo crear y gestionar repositorios en GitHub  
Incluyendo la subida de cambios, configuración inicial y gestión de colaboradores.

### 🔹 Cómo preparar una estructura completa de proyecto  
Que posteriormente será utilizada por herramientas como MkDocs y GitHub Actions.

### 🔹 Flujo básico de trabajo en un proyecto real  
Clonación, configuración, commits, push, estructura y documentación.

Este apartado sienta las bases para trabajar adecuadamente con automatización, publicación y despliegue en los apartados siguientes.

---
