---
layout: page
title: Docker
permalink: /docker/
---

# ¿Qué es Docker?

Docker es una plataforma abierta para desarrollar, enviar y ejecutar aplicaciones. Docker te permite separar tus aplicaciones de tu infraestructura, facilitando así la entrega rápida del software. Con Docker, puedes gestionar tu infraestructura de la misma manera en que gestionas tus aplicaciones. Al aprovechar las metodologías de Docker para enviar, probar y desplegar código, puedes reducir significativamente el tiempo entre escribir el código y ejecutarlo en producción.

## La plataforma Docker

Docker proporciona la capacidad de empaquetar y ejecutar una aplicación en un entorno débilmente aislado llamado contenedor. El aislamiento y la seguridad permiten ejecutar muchos contenedores simultáneamente en un solo host. Los contenedores son ligeros y contienen todo lo necesario para ejecutar la aplicación, por lo que no dependes de lo que esté instalado en el host. Puedes compartir contenedores mientras trabajas y asegurarte de que todos los que los compartan obtengan el mismo contenedor que funciona de la misma manera.

Docker ofrece herramientas y una plataforma para gestionar el ciclo de vida de tus contenedores:

- Desarrolla tu aplicación y sus componentes de soporte utilizando contenedores.
- El contenedor se convierte en la unidad para distribuir y probar tu aplicación.
- Cuando estés listo, despliega tu aplicación en tu entorno de producción, ya sea como un contenedor o como un servicio orquestado. Esto funciona igual tanto si tu entorno de producción es un centro de datos local, un proveedor en la nube o una combinación híbrida de ambos.

## ¿Para qué puedo usar Docker?

### Entrega rápida y consistente de aplicaciones

Docker agiliza el ciclo de desarrollo al permitir que los desarrolladores trabajen en entornos estandarizados utilizando contenedores locales que proporcionan las aplicaciones y servicios. Los contenedores son ideales para flujos de trabajo de integración continua y entrega continua (CI/CD).

Ejemplo de escenario:

- Tus desarrolladores escriben código localmente y comparten su trabajo con sus colegas usando contenedores Docker.
- Usan Docker para enviar sus aplicaciones a un entorno de prueba y ejecutar pruebas automáticas y manuales.
- Cuando los desarrolladores encuentran errores, pueden corregirlos en el entorno de desarrollo y volver a desplegarlos en el entorno de prueba para su validación.
- Una vez completadas las pruebas, enviar la corrección al cliente es tan simple como enviar la imagen actualizada al entorno de producción.

### Despliegue y escalado responsivo

La plataforma basada en contenedores de Docker permite cargas de trabajo altamente portátiles. Los contenedores Docker pueden ejecutarse en la computadora portátil de un desarrollador, en máquinas físicas o virtuales en un centro de datos, en proveedores en la nube o en una combinación de estos entornos.

La portabilidad y naturaleza ligera de Docker también facilita la gestión dinámica de cargas de trabajo, escalando hacia arriba o hacia abajo las aplicaciones y servicios según las necesidades empresariales, casi en tiempo real.

### Ejecutar más cargas de trabajo en el mismo hardware

Docker es ligero y rápido. Proporciona una alternativa viable y rentable a las máquinas virtuales basadas en hipervisores, lo que te permite aprovechar mejor la capacidad de tus servidores para alcanzar tus objetivos empresariales. Docker es perfecto para entornos de alta densidad y para despliegues pequeños y medianos donde necesitas hacer más con menos recursos.

## Arquitectura de Docker

Docker utiliza una arquitectura cliente-servidor. El cliente Docker se comunica con el demonio Docker, que realiza el trabajo pesado de construir, ejecutar y distribuir tus contenedores Docker. El cliente y el demonio pueden ejecutarse en el mismo sistema, o puedes conectar un cliente Docker a un demonio Docker remoto. El cliente y el demonio se comunican mediante una API REST, a través de sockets UNIX o una interfaz de red. Otro cliente Docker es Docker Compose, que te permite trabajar con aplicaciones compuestas por un conjunto de contenedores.

![Docker architecture](/images/docker-architecture.png "Docker architecture")

### Docker daemon

El demonio Docker (`dockerd`) escucha solicitudes de la API de Docker y gestiona objetos Docker como imágenes, contenedores, redes y volúmenes. Un demonio también puede comunicarse con otros demonios para gestionar servicios Docker.

### El cliente Docker

El cliente Docker (`docker`) es la forma principal en que muchos usuarios interactúan con Docker. Cuando usas comandos como `docker run`, el cliente envía estos comandos a `dockerd`, que los ejecuta. El comando `docker` utiliza la API de Docker. El cliente Docker puede comunicarse con más de un demonio.

### Docker Desktop

Docker Desktop es una aplicación fácil de instalar para entornos Mac, Windows o Linux que te permite construir y compartir aplicaciones y microservicios en contenedores. Docker Desktop incluye el demonio Docker (`dockerd`), el cliente Docker (`docker`), Docker Compose, Docker Content Trust, Kubernetes y Credential Helper. Para más información, consulta [Docker Desktop](https://docs.docker.com/desktop/).

### Registros Docker

Un registro Docker almacena imágenes Docker. Docker Hub es un registro público que cualquiera puede usar, y Docker busca imágenes en Docker Hub de forma predeterminada. Incluso puedes ejecutar tu propio registro privado.

Cuando usas los comandos `docker pull` o `docker run`, Docker descarga las imágenes necesarias desde el registro configurado. Cuando usas el comando `docker push`, Docker sube tu imagen al registro configurado.

## Objetos de Docker

Cuando usas Docker, estás creando y utilizando imágenes, contenedores, redes, volúmenes, plugins y otros objetos. Esta sección ofrece una breve descripción de algunos de estos objetos.

### Imágenes

Una imagen es una plantilla de solo lectura con instrucciones para crear un contenedor Docker. A menudo, una imagen se basa en otra imagen, con alguna personalización adicional. Por ejemplo, puedes construir una imagen basada en la imagen `ubuntu`, pero que instale el servidor web Apache y tu aplicación, así como los detalles de configuración necesarios para ejecutarla.

Puedes crear tus propias imágenes o usar las creadas por otros y publicadas en un registro. Para construir tu propia imagen, creas un archivo `Dockerfile` con una sintaxis simple para definir los pasos necesarios para crear y ejecutar la imagen. Cada instrucción en un `Dockerfile` crea una capa en la imagen. Cuando modificas el `Dockerfile` y reconstruyes la imagen, solo se reconstruyen las capas que han cambiado. Esto es parte de lo que hace que las imágenes sean ligeras, pequeñas y rápidas, en comparación con otras tecnologías de virtualización.

### Contenedores

Un contenedor es una instancia ejecutable de una imagen. Puedes crear, iniciar, detener, mover o eliminar un contenedor usando la API de Docker o la CLI. Puedes conectar un contenedor a una o más redes, adjuntarle almacenamiento o incluso crear una nueva imagen basada en su estado actual.

De forma predeterminada, un contenedor está relativamente bien aislado de otros contenedores y de la máquina host. Puedes controlar el nivel de aislamiento de la red, el almacenamiento u otros subsistemas del contenedor respecto a otros contenedores o a la máquina host.

Un contenedor está definido por su imagen, así como por las opciones de configuración que le proporciones al crearlo o iniciarlo. Cuando se elimina un contenedor, cualquier cambio en su estado que no esté almacenado en un almacenamiento persistente desaparece.

### Ejemplo de comando `docker run`

El siguiente comando ejecuta un contenedor basado en Ubuntu, lo conecta interactivamente a tu sesión de línea de comandos local y ejecuta `/bin/bash`.

~~~~~~~~
docker run -i -t ubuntu /bin/bash
~~~~~~~~
{: .language-ruby}

## Dockerfile

Un Dockerfile es un documento de texto que contiene todas las instrucciones que Docker necesita para construir automáticamente una imagen de Docker. Piénsalo como la receta para crear un software empaquetado.

###  ¿Para qué sirve un Dockerfile?
El propósito principal de un Dockerfile es automatizar la creación de imágenes de Docker. En lugar de ejecutar comandos manualmente para instalar software, configurar entornos y copiar archivos, todas estas acciones se definen en el Dockerfile. Esto garantiza que la imagen se construya de la misma manera cada vez, lo que es fundamental para la consistencia y la reproducibilidad en el desarrollo y la implementación de software.

### Componentes clave de un Dockerfile
Un Dockerfile se compone de una serie de instrucciones, cada una en una línea separada, que se ejecutan en orden. Algunas de las instrucciones más comunes incluyen:

| Instrucción  | Descripción     |
| :---------- | :--------------- |
| **FROM** |  Especifica la imagen base sobre la cual se construirá la nueva imagen. Es el punto de partida. Por ejemplo, FROM ubuntu:22.04 indica que la imagen se basará en Ubuntu versión 22.04.   |
| **RUN**   | Ejecuta comandos dentro de la imagen durante el proceso de construcción. Se usa comúnmente para instalar paquetes, crear directorios, etc. Ejemplo: 
~~~~~~~~
RUN apt-get update && apt-get install -y nginx.
~~~~~~~~
{: .language-ruby}
|
|  **COPY** | Copia archivos o directorios del sistema de archivos local al sistema de archivos de la imagen. Ejemplo: COPY . /app.|

