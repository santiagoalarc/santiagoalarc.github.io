---
layout: page
title: Fundamentos de Java
permalink: /java-knowledge/
---



Componentes de Java
**JDK** — el Kit de Desarrollo de Java, un conjunto de herramientas para desarrolladores.

**JRE** — el Entorno de Ejecución de Java, el sistema de ejecución de Java. Se utiliza para organizar los procesos de ejecución de programas.

**JVM** — la Máquina Virtual de Java. Es una máquina informática virtual que tiene un conjunto de comandos y un controlador de memoria.


Okay, here's the translated table in Markdown format:

| Operador | Descripción | Tipo | Ejemplo |
|---|---|---|---|
| + | Suma los valores de ambos lados del operador. | Binario | a + b |
| - | Resta el operando derecho del izquierdo. | Binario \<br\> Prefijo Unario | a - b |
|   | Cambia el signo.              | - a |
| * | Multiplica los valores de ambos lados del operador. | Binario | a \* b |
| / | El operador divide el operando izquierdo por el operando derecho (o divide exactamente para enteros). | Binario | a / b |
| % | Divide el operando izquierdo por el derecho y devuelve el resto. | Binario | a % b |
| ++ | Incremento – aumenta el valor del operando en 1. Tiene una forma de prefijo y una de sufijo. | Prefijo Unario \<br\> Sufijo Unario | ++a \<br\> a++ |
| -- | Decremento – disminuye el valor del operando en 1. Tiene una forma de prefijo y una de sufijo. | Prefijo Unario \<br\> Sufijo Unario | --a \<br\> a-- |

Aquí tienes la traducción solicitada:

---

### Optimización en la Compilación

La compilación de aplicaciones Java es diferente de la compilación de aplicaciones en lenguajes de programación tipo C. Un compilador estático transforma el código fuente directamente en comandos de máquina que pueden ejecutarse en la plataforma de destino. El compilador de Java transforma el código fuente en bytecodes JVM portátiles, que son "instrucciones de máquina virtual" para la JVM. En ese momento, el compilador de Java realiza optimizaciones insignificantes, a diferencia de otros compiladores estáticos que realizan optimizaciones durante la ejecución del programa.

Considera varios ejemplos de optimización en la compilación.

El código fuente contiene la siguiente línea de código:
`byte b = 2 + 3;`

Pero no es óptimo gastar tiempo durante la ejecución del programa calculando la suma de dos literales invariantes. Por lo tanto, esto se hace en la etapa de compilación del código, y el bytecode resultante es el siguiente:
`byte b = 5;`

Lo mismo aplica para las variables `final`:
`final int X = 7;`
`int y = 12 + X;`

Dado que el valor de la variable `final` no cambia, la última línea de bytecode se escribirá de la siguiente manera:
`int y = 19;`