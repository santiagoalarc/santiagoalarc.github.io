---
layout: page
title: programming paradigms
permalink: /programming-paradigms/
---

# Ataque por Inyección SQL

La **inyección SQL** (SQL Injection) es una de las vulnerabilidades más comunes y peligrosas en aplicaciones web. Permite a un atacante manipular consultas a bases de datos mediante la inserción de código SQL malicioso a través de entradas no validadas del usuario.

---

## 🔍 ¿Qué es la inyección SQL?

La inyección SQL ocurre cuando una aplicación incluye **datos proporcionados por el usuario directamente en una consulta SQL sin sanitizarlos ni validarlos adecuadamente**. Esto permite al atacante alterar la lógica de la consulta, acceder, modificar o eliminar información sensible.

Este tipo de ataque afecta principalmente a aplicaciones que usan bases de datos relacionales como MySQL, PostgreSQL, SQL Server, Oracle, etc.

---

## ⚠️ Ejemplo práctico

Imagina un formulario de inicio de sesión donde el usuario ingresa su nombre y contraseña. La consulta SQL podría verse así:

```sql
SELECT * FROM usuarios WHERE nombre = '$_POST[nombre]' AND password = '$_POST[contraseña]';
