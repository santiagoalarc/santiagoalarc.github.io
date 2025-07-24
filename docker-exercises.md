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


yum es un comando que se usa en los sistemas operativos que la instación de librerías
la instrucción -y se implementa para designar que las preguntas que se realicen en la instación se escoja la opción *yes* esto con la finalidad de automatizar la instalación.

El comnado respectivo para la creación de la imagen teniendo en cuenta un archico *Dockerfile* ser+ia el siguiente comando:

~~~~~~~~
ducker build -t apache:defora .
~~~~~~~~
{: .language-ruby}

La instrución . hace referencia que el contexto se encuentra en el mismo folder donde se está corriendo el comando, llegado el caso que el archivo *Dockerfile* se encuentre en otra ubicación, entonces reemplazamos el punto por la ubicación del archivo.

Para ejecutar una imagen y crear un comando podemos hacer uso del siguiente comando en la terminal:

~~~~~~~~
docker run -d apache-fedora
~~~~~~~~
{: .language-ruby}

La instrucción -d hace referencia que el proceso va a correr en segundo plano, liberando la terminal para recibir otros comandos
En el ejemplo se coloca apache-fedora porque previamente se ha creado la imagen con dicho nombre.

httpd -D FOREGROUND