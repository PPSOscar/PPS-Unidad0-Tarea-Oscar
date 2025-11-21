# Desarrollo completo del apartado Docker

En este apartado documento y recopilo **todo el proceso** realizado en el apartado de Docker, incluyendo instalación, comandos utilizados y comprobaciones.

---

# 1. Preparación del entorno

En primer lugar, compruebo que Docker esté instalado:

```
docker --version
```
En caso de no estar instalado, podemos instalarlo con los siguientes comandos:

```
sudo apt update
sudo apt install -y docker.io
# instalamos también docker-cli 
sudo apt install docker-cli
docker
# Nos debe de mostrar la versión de docker instalada
sudo usermod -aG docker PPSOscar
systemctl restart docker.socket
systemctl restart docker.service
```

Compruebo que el servicio está en funcionamiento:

```bash
docker ps
```
![version](img/imagenes_docker/version2.png)

---

#2. Obtención de los archivos HTML (rama `gh-pages`)

La documentación generada por MkDocs no se encuentra en la rama _main_, sino en la rama _gh-pages_, producida automáticamente por GitHub Actions.

Cambio a la rama _gh-pages_ y listo su contenido:

```
git fetch
git checkout gh-pages
ls -la
```
Rercuerdo que el comando _git fetch_ descarga del repositorio remoto la información nueva

![ghpages](img/imagenes_docker/ghpages.png)

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
