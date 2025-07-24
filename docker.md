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

Docker utiliza una arquitectura cliente-servidor. El cliente Docker se comunica con el Docker daemon, que realiza el trabajo pesado de construir, ejecutar y distribuir tus contenedores Docker. El cliente y el Docker daemon pueden ejecutarse en el mismo sistema, o puedes conectar un cliente Docker a un Docker daemon remoto. El cliente y el Docker daemon se comunican mediante una API REST, a través de sockets UNIX o una interfaz de red. Otro cliente Docker es Docker Compose, que te permite trabajar con aplicaciones compuestas por un conjunto de contenedores.

![Docker architecture](/images/docker-architecture.png "Docker architecture")

### Docker daemon

El Docker daemon (`dockerd`) escucha solicitudes de la API de Docker y gestiona objetos Docker como imágenes, contenedores, redes y volúmenes. Un Docker daemon también puede comunicarse con otros Docker daemons para gestionar servicios Docker.

### El cliente Docker

El cliente Docker (`docker`) es la forma principal en que muchos usuarios interactúan con Docker. Cuando usas comandos como `docker run`, el cliente envía estos comandos a `dockerd`, que los ejecuta. El comando `docker` utiliza la API de Docker. El cliente Docker puede comunicarse con más de un Docker daemon.

### Docker Desktop

Docker Desktop es una aplicación fácil de instalar para entornos Mac, Windows o Linux que te permite construir y compartir aplicaciones y microservicios en contenedores. Docker Desktop incluye el Docker daemon (`dockerd`), el cliente Docker (`docker`), Docker Compose, Docker Content Trust, Kubernetes y Credential Helper. Para más información, consulta [Docker Desktop](https://docs.docker.com/desktop/).

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

También se puede considerar  un contenedor como una capa adicional de ejecución que inicia todo lo que está definido en la imagen. (Instancia en ejecución de una imagen)

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

#### FROM
Especifica la imagen base sobre la cual se construirá la nueva imagen. Es el punto de partida. Por ejemplo:
~~~~~~~~
 `FROM ubuntu:22.04` //Indica que la imagen se basará en Ubuntu versión 22.04.
 ~~~~~~~~
 {: .language-ruby}

FROM le dice a Docker dónde encontrar el punto de partida para tu nueva imagen. Docker tomará la imagen especificada del Docker Hub (o de un registro privado configurado) y la usará como la capa inicial sobre la cual se añadirán las capas de tu Dockerfile.

Sintaxis:

 ~~~~~~~~
FROM <imagen> [AS <nombre>]
 ~~~~~~~~
{: .language-ruby}
o
 ~~~~~~~~
FROM <imagen>:<etiqueta> [AS <nombre>]
 ~~~~~~~~
 {: .language-ruby}
o

~~~~~~~~
FROM <imagen>@<digest> [AS <nombre>]
~~~~~~~~
 {: .language-ruby}

< imagen>: El nombre de la imagen base (ej. ubuntu, node, python).

:< etiqueta> (opcional): La versión o "tag" específica de la imagen que quieres usar (ej. ubuntu:22.04, node:18-alpine). Si no se especifica, Docker usará por defecto la etiqueta latest. Es una buena práctica especificar una etiqueta para asegurar builds consistentes.

@< digest> (opcional): Un digest SHA256 de la imagen. Esto asegura una reproducibilidad absoluta, ya que el digest identifica de forma única el contenido de la imagen.

AS < nombre> (opcional): Utilizado en Dockerfiles multi-etapa (multi-stage builds) para asignar un nombre a esta etapa de construcción.

Ejemplos comunes de FROM
~~~~~~~~
FROM ubuntu:latest: Construye una imagen sobre la última versión de Ubuntu.

FROM node:18-alpine: Utiliza una imagen Node.js versión 18 basada en Alpine Linux, que es más ligera.

FROM python:3.9-slim-buster: Una imagen de Python 3.9 más ligera basada en Debian Buster.

FROM scratch: Una imagen base completamente vacía. Se usa para crear imágenes mínimas "desde cero", como las que contienen solo un binario compilado estáticamente. Es el Dockerfile más pequeño posible.
 ~~~~~~~~
 {: .language-ruby}

#### RUN
Ejecuta comandos dentro de la imagen durante el proceso de construcción. Se usa comúnmente para instalar paquetes, crear directorios, etc. Ejemplo: 
~~~~~~~~
`RUN apt-get update && apt-get install -y nginx`
~~~~~~~~
{: .language-ruby}

#### COPY
Copia archivos o directorios del sistema de archivos local al sistema de archivos de la imagen. Ejemplo: 
~~~~~~~~
`COPY . /app`.
~~~~~~~~
{: .language-ruby}

#### ADD
Similar a COPY, pero con funcionalidades adicionales, como la extracción automática de archivos comprimidos o la descarga de URLs.

#### WORKDIR
El comando WORKDIR en un Dockerfile se usa para establecer el directorio de trabajo para las instrucciones posteriores como RUN, CMD, ENTRYPOINT, COPY, y ADD. Es como usar el comando cd en la línea de comandos de Linux. 📂

##### ¿Cómo funciona WORKDIR?
Cuando especificas WORKDIR /app, todas las instrucciones que sigan a esa línea se ejecutarán dentro del directorio /app del contenedor, a menos que se especifique una ruta absoluta diferente. Si el directorio especificado no existe, Docker lo creará automáticamente.

***Ejemplo***:
Sin WORKDIR:

~~~~~~~~
FROM ubuntu:latest
RUN mkdir /app
RUN cd /app && echo "Hola desde app" > file.txt
CMD cat /app/file.txt
~~~~~~~~
{: .language-ruby}

En este ejemplo, necesitas especificar la ruta completa /app/file.txt para acceder al archivo.

Con WORKDIR:

~~~~~~~~
FROM ubuntu:latest
WORKDIR /app
RUN echo "Hola desde app" > file.txt
CMD cat file.txt
~~~~~~~~
{: .language-ruby}

Aquí, después de WORKDIR /app, las instrucciones RUN y CMD se ejecutan directamente dentro de /app, haciendo que las rutas sean relativas y el Dockerfile más limpio y fácil de leer.

#### EXPOSE
Declara los puertos en los que la aplicación dentro del contenedor escuchará. Es solo una documentación; no publica el puerto automáticamente. Ejemplo: 
~~~~~~~~
`EXPOSE 80`
~~~~~~~~
{: .language-ruby}

#### CMD
Proporciona el comando predeterminado que se ejecutará cuando se inicie un contenedor a partir de la imagen. Solo puede haber una instrucción CMD por Dockerfile.

#### ENTRYPOINT
Similar a CMD, pero está diseñado para que el contenedor se ejecute como un ejecutable. A menudo se utiliza junto con CMD para proporcionar argumentos predeterminados.

#### ENV
Establece variables de entorno dentro de la imagen.

## Orden Sugerido de Comandos en un Dockerfile
Aunque no hay un orden "obligatorio" estricto para todos los comandos (más allá de FROM que siempre va primero), hay un orden recomendado que optimiza el caching de Docker y reduce los tiempos de construcción. La idea principal es colocar las instrucciones que cambian con menos frecuencia al principio y las que cambian con más frecuencia al final. 🚀

Aquí te presento un orden lógico y optimizado:

### FROM
* Propósito: Especifica la imagen base.
* Frecuencia de cambio: Rara vez cambia.
* Ubicación: Siempre es la primera instrucción no comentada.
* Ejemplo:

~~~~~~~~
FROM node:18-alpine
~~~~~~~~
{: .language-ruby}

### ARG y ENV (Variables de Entorno y Argumentos de Construcción)
* Propósito: Define variables que se pueden usar durante la construcción (ARG) o variables de entorno que estarán disponibles en el contenedor en tiempo de ejecución (ENV).
* Frecuencia de cambio: Puede cambiar según configuraciones, pero idealmente se definen temprano.
* Ubicación: Después de FROM.
* Ejemplo:

~~~~~~~~
ARG NODE_VERSION=18
ENV PORT=3000
~~~~~~~~
{: .language-ruby}

### WORKDIR
* Propósito: Establece el directorio de trabajo para las instrucciones posteriores.
* Frecuencia de cambio: Rara vez cambia una vez definido para el proyecto.
* Ubicación: Después de definir variables, antes de copiar archivos de la aplicación.
* Ejemplo:
~~~~~~~~
WORKDIR /app
~~~~~~~~
{: .language-ruby}

### COPY / ADD (Archivos de Dependencias de la Aplicación)
* Propósito: Copia solo los archivos necesarios para instalar las dependencias (ej., package.json, requirements.txt).
* Frecuencia de cambio: Los archivos de dependencias suelen cambiar con menos frecuencia que el código fuente completo.
* Ubicación: Antes de la instrucción de instalación de dependencias. Esto es clave para el caching. Si solo cambian los archivos de código fuente, Docker puede reutilizar la capa de instalación de dependencias.
* Ejemplo (para Node.js):
~~~~~~~~
COPY package.json package-lock.json ./
~~~~~~~~
{: .language-ruby}
* Ejemplo (para Python):
~~~~~~~~
COPY requirements.txt ./
~~~~~~~~
{: .language-ruby}

### RUN (Instalar Dependencias)
* Propósito: Ejecuta comandos para instalar las dependencias de la aplicación (ej., npm install, pip install).
* Frecuencia de cambio: Cambia cuando se añaden o actualizan dependencias.
* Ubicación: Inmediatamente después de copiar los archivos de dependencias.
* Ejemplo:
~~~~~~~~
RUN npm install
~~~~~~~~
{: .language-ruby}
o
~~~~~~~~
RUN pip install -r requirements.txt
~~~~~~~~
{: .language-ruby}

### COPY / ADD (Código Fuente de la Aplicación)
* Propósito: Copia el resto del código fuente de tu aplicación.
* Frecuencia de cambio: Cambia muy frecuentemente durante el desarrollo.
* Ubicación: Después de que todas las dependencias estén instaladas y cacheables. Esto asegura que si solo cambia el código fuente, solo esta capa y las siguientes se reconstruirán, no las de dependencias.
* Ejemplo:
~~~~~~~~
COPY . .
~~~~~~~~
{: .language-ruby}
### EXPOSE
* Propósito: Informa a Docker que el contenedor escuchará en los puertos de red especificados en tiempo de ejecución.
* Frecuencia de cambio: Rara vez cambia.
* Ubicación: Después de copiar el código, ya que es una configuración del contenedor.
* Ejemplo:
~~~~~~~~
EXPOSE 3000
~~~~~~~~
{: .language-ruby}

### CMD y/o ENTRYPOINT
* Propósito: Define el comando predeterminado o el punto de entrada ejecutable cuando se inicia el contenedor.
* Frecuencia de cambio: Generalmente se define una vez.
* Ubicación: Al final del Dockerfile, ya que son las instrucciones finales de ejecución del contenedor.
* Ejemplo (CMD):
~~~~~~~~
CMD ["npm", "start"]
~~~~~~~~
{: .language-ruby}
* Ejemplo (ENTRYPOINT con CMD):
~~~~~~~~
ENTRYPOINT ["/usr/bin/python3"]
CMD ["app.py"]
~~~~~~~~
{: .language-ruby}

Ejemplo Completo de un Dockerfile Optimizado:
Dockerfile
 1. Imagen base
FROM node:18-alpine

 2. Variables de entorno (si aplica)
ENV NODE_ENV=production

 3. Directorio de trabajo
WORKDIR /app

 4. Copiar archivos de dependencias (para aprovechar el caching)
COPY package.json package-lock.json ./

 5. Instalar dependencias
RUN npm install --production

 6. Copiar el resto del código de la aplicación
COPY . .

 7. Exponer puerto
EXPOSE 3000

 8. Comando para iniciar la aplicación
CMD ["npm", "start"]
Seguir este orden te ayudará a construir imágenes Docker de manera más rápida y eficiente, aprovechando al máximo el sistema de caching de Docker.

### ¿Qué es una "Dangling Image" en Docker?
En Docker, una "dangling image" (imagen colgante o huérfana) es una imagen que ya no está asociada a ningún nombre de repositorio y etiqueta (<none>:<none>), pero que sigue ocupando espacio en tu disco. Piensa en ella como una versión anterior de una imagen que creaste, pero que ha sido reemplazada por una versión más nueva con el mismo nombre y etiqueta.


