---
layout: page
title: Ejercicios Docker
permalink: /docker-exercise/
---



Crear una imagen Apache con php
~~~~~~~~
FROM fedora:latest

RUN yum install httpd -y
~~~~~~~~
{: .language-ruby}


yum es un comando que se usa en los sistemas operativos para la instación de librerías
la instrucción -y se implementa para designar que las preguntas que se realicen en la instación se escoja la opción *yes* esto con la finalidad de automatizar la instalación.

El comando respectivo para la creación de la imagen teniendo en cuenta un archivo *Dockerfile* sería el siguiente comando:

~~~~~~~~
docker build -t apache:fedora .
~~~~~~~~
{: .language-ruby}

El arguementos . hace referencia que el contexto se encuentra en el mismo folder donde se está corriendo el comando, llegado el caso que el archivo *Dockerfile* se encuentre en otra ubicación, entonces reemplazamos el punto por la ubicación del archivo. La -t es una opción (flag) abreviada para --tag.

Para ejecutar una imagen y crear un comando podemos hacer uso del siguiente comando en la terminal:

~~~~~~~~
docker run -d apache-fedora
~~~~~~~~
{: .language-ruby}

La instrucción -d hace referencia que el proceso va a correr en segundo plano, liberando la terminal para recibir otros comandos
En el ejemplo se coloca apache-fedora porque previamente se ha creado la imagen con dicho nombre.

Al ejecutar la imagen creada hasta el momento en un contenedor, generaría un error ya que se necesita tener una instrución CMD dentro de la imagen, como se agregó lo que va hacer docker es la primera instrucción que encuentre, en este caso tomará la de la imagen de fedora, que si la miramos a detalle está construida por capas también y tendrá una capa con la instrucción CMD 


~~~~~~~~
FROM fedora:latest

RUN yum install httpd -y

CMD httpd -D FOREGROUND
~~~~~~~~
{: .language-ruby}

comando para ejeutar el servicio de apache en primer plano

El siguiente comnado nos permite asignar un nombre al contenedor que sería en este caso *apache* y un puerto que es *80*

docker run -d --name apache -p 80:80 apache-fedora:apache-cmd