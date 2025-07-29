---
layout: page
title: Integración continua
permalink: /continuos-integration/
---

## Todo el mundo envía "commits" a la línea principal cada día
La integración es, ante todo, comunicación. La integración permite a los desarrolladores informar a otros desarrolladores sobre los cambios que han realizado. La comunicación frecuente permite a las personas conocer rápidamente cómo evolucionan los cambios.

El único requisito previo para que un desarrollador haga un "commit" a la línea principal es que pueda construir correctamente su código. Esto, por supuesto, incluye pasar las pruebas de construcción. Como en cualquier ciclo de "commit", el desarrollador primero actualiza su copia de trabajo para que coincida con la línea principal, resuelve cualquier conflicto con esta, y luego construye en su máquina local. Si la construcción pasa, entonces puede subir sus cambios a la línea principal.

Si todo el mundo sube sus cambios a la línea principal con frecuencia, los desarrolladores descubren rápidamente si hay un conflicto entre dos desarrolladores. La clave para solucionar problemas rápidamente es encontrarlos rápidamente. Con los desarrolladores haciendo "commits" cada pocas horas, un conflicto puede detectarse a las pocas horas de producirse; en ese momento, no ha sucedido mucho y es fácil de resolver. Los conflictos que permanecen sin detectar durante semanas pueden ser muy difíciles de resolver.

Los conflictos en la base de código se presentan de diferentes formas. Los más fáciles de encontrar y resolver son los conflictos textuales, a menudo llamados "conflictos de fusión", cuando dos desarrolladores editan el mismo fragmento de código de diferentes maneras. Las herramientas de control de versiones los detectan fácilmente una vez que el segundo desarrollador incorpora la línea principal actualizada a su copia de trabajo. El problema más difícil son los conflictos semánticos. Si mi colega cambia el nombre de una función y yo llamo a esa función en mi código recién añadido, el sistema de control de versiones no nos puede ayudar. En un lenguaje de tipado estático, obtenemos un fallo de compilación, lo cual es bastante fácil de detectar, pero en un lenguaje dinámico no obtenemos ninguna ayuda. E incluso la compilación de tipado estático no nos ayuda cuando un colega realiza un cambio en el cuerpo de una función que yo llamo, alterando sutilmente lo que hace. Por eso es tan importante tener código auto-verificable.

Un fallo en una prueba nos alerta de que hay un conflicto entre los cambios, pero todavía tenemos que averiguar cuál es el conflicto y cómo resolverlo. Dado que solo hay unas pocas horas de cambios entre "commits", hay pocos lugares donde el problema podría estar oculto. Además, como no ha cambiado mucho, podemos usar la depuración diferencial ("Diff Debugging") para ayudarnos a encontrar el error.

Mi regla general es que cada desarrollador debería hacer un "commit" a la línea principal todos los días. En la práctica, aquellos con experiencia en Integración Continua se integran con más frecuencia. Cuanto más frecuentemente nos integramos, menos lugares tenemos que buscar errores de conflicto y más rápidamente los resolvemos.

Los "commits" frecuentes animan a los desarrolladores a dividir su trabajo en pequeños fragmentos de unas pocas horas cada uno. Esto ayuda a seguir el progreso y proporciona una sensación de avance. A menudo, al principio la gente siente que no puede hacer algo significativo en solo unas pocas horas, pero hemos descubierto que la tutoría y la práctica nos ayudan a aprender.