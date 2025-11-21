# Conclusiones de la Actividad
## 1. Conclusiones sobre Git

Con este apartado he comprendido, a través de la práctica, la importancia de utilizar Git como herramienta de control de versiones distribuida en proyectos, como puede ser esta actividad. He podido organizar las distintas versiones de mis archivos y trabajar con ellos tras publicar las respectivas modificaciones, sabiendo en todo momento qué he cambiado, qué no, cuándo y  evitar así perder trabajo y tiempo.
Además, al trabajar con ramas como _main_ y _gh-pages_, he aprendido a moverme entre ellas y a entender cómo Git mantiene distintos estados del repositorio según la rama en la que esté trabajando (y a no liarla cuando estás trabajando en una, pensando que estás en la otra).
También he reforzado el uso de comandos básicos de Git como _git add_, _git commit_, _git push_ o _git status_, que parecen simples pero realmente son los que sostienen todo el flujo de trabajo.

## 2. Conclusiones sobre GitHub Actions

GitHub Actions ha sido una de las partes más interesantes porque automatiza algo que, de otra forma, tendría que hacerse manualmente.
Crear el _workflow_ me ha permitido entender cómo funciona un archivo _.yml_, qué es un "runner" y cómo se ejecutan tareas en remoto cada vez que hago un _push_.
La automatización del proceso de generación de la documentación de MkDocs me pareció muy útil, ya que convierte el repositorio en algo dinámico. Subo cambios y automáticamente se actualiza la web sin que yo tenga que intervenir.

## 3. Conclusiones sobre GitHub Pages

GitHub Pages ha sido una forma muy sencilla de publicar la documentación de manera pública.
Me ha servido para ver en la práctica cómo una simple rama como _gh-pages_ puede convertirse en una web completa sin necesidad de servidores propios ni configuraciones complicadas.
También me ha ayudado a entender lo importante que es mantener bien organizada la documentación y los enlaces internos, porque cualquier error en las rutas hace que la página deje de funcionar al completo o por partes, dependiendo lo que se ponga mal en la ruta.

## 4. Conclusiones sobre Docker y NGINX

Crear un contenedor con Docker para servir la documentación ha sido útil para reforzar conceptos básicos de virtualización y  despliegue de servicios.
Aunque pueda parecer innecesario teniendo GitHub Pages, este ejercicio es necesario y aporta porque me ha ayudado a entender cómo funcionan los volúmenes _bind mount_ y a cómo levantar un servicio web real dentro de un contenedor.
Al montar la carpeta de la documentación dentro de NGINX he podido comprobar lo versátil que es Docker, ya que con un solo comando tienes un servidor web completamente funcional.

## Conclusión General

La actividad me ha permitido practicar todo el ciclo básico de un proyecto actual en el que se incluyen: control de versiones, automatización, publicación de documentación y despliegue con contenedores.
Se entiende mejor cómo encaja cada herramienta dentro del proceso de desarrollo seguro.
