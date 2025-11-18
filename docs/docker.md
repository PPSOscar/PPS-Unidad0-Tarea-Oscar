# 🐳 Desarrollo completo del apartado Docker
## Despliegue local con Docker y NGINX

En este documento recojo **todo el proceso completo** realizado en el apartado de Docker, incluyendo instalación, comandos utilizados, comprobaciones y conclusiones finales. Todo está expresado utilizando **Markdown enriquecido**, con listas, bloques de código y explicaciones claras.

---

# 🔧 1. Preparación del entorno en Kali Linux

Antes de comenzar, se comprobó si Docker estaba instalado:

```bash
docker --version
```

En caso de no estar disponible, se procedió a su instalación:

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
```

> ⚠️ **Nota:** Tras añadir el usuario al grupo `docker` es necesario cerrar sesión y volver a entrar.

Comprobación final del servicio:

```bash
docker ps
```

---

# 📁 2. Obtención de los archivos HTML (rama `gh-pages`)

La documentación generada por MkDocs no se encuentra en la rama `main`, sino en la rama `gh-pages`, producida automáticamente por GitHub Actions.

Cambio de rama:

```bash
git fetch
git checkout gh-pages
```

Listado de archivos generados:

```bash
ls -la
```

Archivos esperados:

- `index.html`
- `404.html`
- `css/`
- `js/`
- `search/`

---

# 🚀 3. Ejecución del contenedor NGINX

Una vez situado en la carpeta correcta (la rama `gh-pages`), se levantó un contenedor NGINX utilizando **bind mount**:

```bash
docker run -d   --name PPSUnidad0-Tarea_Tu_nombre   -p 8085:80   -v $(pwd):/usr/share/nginx/html   nginx
```

## 📌 Explicación del comando

- **-d** → Ejecuta el contenedor en segundo plano.  
- **--name** → Nombre obligatorio del contenedor.  
- **-p 8085:80** → Expone el puerto 80 interno como 8085 en el host.  
- **-v $(pwd):/usr/share/nginx/html** → Monta la carpeta actual donde está `index.html`.  
- **nginx** → Usa la imagen oficial del servidor NGINX.

---

# 🧪 4. Comprobaciones tras el despliegue

### ✔ 4.1 Ver contenedores activos

```bash
docker ps
```

Salida esperada:

```
PPSUnidad0-Tarea_Tu_nombre   nginx   Up ...   0.0.0.0:8085->80/tcp
```

### ✔ 4.2 Inspeccionar configuración del contenedor

```bash
docker inspect PPSUnidad0-Tarea_Tu_nombre
```

Información clave que se verifica:

- Volumen montado  
- Imagen utilizada  
- Puertos expuestos  
- Estado del contenedor  

---

# 🌐 5. Visualización de la documentación

Para comprobar que la documentación se sirve correctamente desde NGINX:

```
http://localhost:8085
```

La página debe mostrarse igual que en GitHub Pages.

---

# 🧹 6. Gestión del contenedor

## ⛔ Detener el contenedor

```bash
docker stop PPSUnidad0-Tarea_Tu_nombre
```

## 🗑️ Eliminar el contenedor

```bash
docker rm PPSUnidad0-Tarea_Tu_nombre
```

---

# 📝 7. Conclusiones del apartado Docker

Gracias a este proceso he aprendido:

### 🔹 Cómo funciona un servidor NGINX sirviendo archivos estáticos  
NGINX es ideal para mostrar HTML, CSS y JavaScript de manera rápida y ligera.

### 🔹 Diferencia entre ramas de desarrollo y ramas de despliegue  
- `main` contiene el código fuente.  
- `gh-pages` contiene la web final.  
Docker debe trabajar **siempre** con esta última.

### 🔹 Montaje de volúmenes en Docker  
El uso de:

```bash
-v $(pwd):/usr/share/nginx/html
```

me enseñó cómo compartir carpetas entre mi máquina y el contenedor.

### 🔹 Reproducir un entorno real de producción  
Pude ver la documentación funcionando igual que lo haría en un servidor real.

En resumen, este apartado me ha permitido entender cómo desplegar de forma segura, reproducible y profesional una web estática generada con MkDocs utilizando Docker y NGINX.

---
