---
layout: page
title: Revisión de código
permalink: /code-review/
---

[Code Review By Google](https://google.github.io/eng-practices/review/reviewer)

# CODE REVIEW

Dentro de la revisón de código, cuando se ba a hacer un comentario se puede utilizar el prefijo **"NIT:"** para indicar que la observación o sugerencia es sobre un detalle meno, no crítico o de estilo, que no afecta la funcionalidad princila del código.

Aquí tienes la traducción del texto, manteniendo el contexto de revisión de código:

---

## Qué buscar en una revisión de código

**Nota:** Siempre asegúrate de tener en cuenta el **Estándar de Revisión de Código** al considerar cada uno de estos puntos.

---

### Diseño
Lo más importante a cubrir en una revisión es el **diseño general del CL**. ¿Las interacciones de las distintas piezas de código en el CL tienen sentido? ¿Este cambio pertenece a tu base de código o a una librería? ¿Se integra bien con el resto de tu sistema? ¿Es un buen momento para añadir esta funcionalidad?

---

### Funcionalidad
¿Este CL hace lo que el desarrollador pretendía? ¿Lo que el desarrollador pretendía es bueno para los **usuarios** de este código? Los "usuarios" suelen ser tanto los usuarios finales (cuando se ven afectados por el cambio) como los desarrolladores (quienes tendrán que "usar" este código en el futuro).

En su mayoría, esperamos que los desarrolladores prueben los CLs lo suficientemente bien como para que funcionen correctamente cuando lleguen a la revisión de código. Sin embargo, como revisor, aún debes pensar en los **casos límite**, buscar **problemas de concurrencia**, intentar pensar como un usuario y asegurarte de que no haya **errores** que puedas ver solo leyendo el código.

**Puedes** validar el CL si lo deseas; el momento más importante para que un revisor verifique el comportamiento de un CL es cuando tiene un **impacto en el usuario**, como un **cambio de interfaz de usuario (UI)**. Es difícil entender cómo algunos cambios afectarán a un usuario solo leyendo el código. Para cambios como esos, puedes pedirle al desarrollador que te haga una demostración de la funcionalidad si es demasiado incómodo aplicar el CL y probarlo tú mismo.

Otro momento en el que es particularmente importante pensar en la funcionalidad durante una revisión de código es si hay algún tipo de **programación paralela** en el CL que teóricamente podría causar **deadlocks** (interbloqueos) o **race conditions** (condiciones de carrera). Este tipo de problemas son muy difíciles de detectar solo ejecutando el código y generalmente necesitan que alguien (tanto el desarrollador como el revisor) los analice cuidadosamente para asegurarse de que no se estén introduciendo problemas. (Ten en cuenta que esta es también una buena razón para no usar modelos de concurrencia donde las condiciones de carrera o los deadlocks son posibles; puede hacer que las revisiones de código o la comprensión del código sean muy complejas).

---

### Complejidad
¿El CL es **más complejo de lo que debería ser**? Verifica esto en cada nivel del CL: ¿las líneas individuales son demasiado complejas? ¿Las funciones son demasiado complejas? ¿Las clases son demasiado complejas? "Demasiado complejo" generalmente significa "no se puede entender rápidamente por los lectores de código". También puede significar "es probable que los desarrolladores introduzcan errores cuando intenten llamar o modificar este código".

Un tipo particular de complejidad es el **sobre-ingeniería**, donde los desarrolladores han hecho el código más genérico de lo necesario, o han añadido funcionalidades que no son necesarias actualmente para el sistema. Los revisores deben estar especialmente **vigilantes** con el sobre-ingeniería. Anima a los desarrolladores a resolver el problema que saben que necesita ser resuelto **ahora**, no el problema que el desarrollador especula que **podría** necesitar ser resuelto en el futuro. El problema futuro debe resolverse una vez que llegue y puedas ver su forma y requisitos reales en el universo físico.

---

### Pruebas
Pide **pruebas unitarias, de integración o de extremo a extremo** según corresponda para el cambio. En general, las pruebas deben añadirse en el mismo CL que el código de producción, a menos que el CL esté gestionando una **emergencia**.

Asegúrate de que las pruebas en el CL sean **correctas, sensatas y útiles**. Las pruebas no se prueban a sí mismas, y rara vez escribimos pruebas para nuestras pruebas; un humano debe asegurarse de que las pruebas son válidas.

¿Las pruebas realmente fallarán cuando el código esté roto? Si el código cambia por debajo de ellas, ¿empezarán a producir falsos positivos? ¿Cada prueba hace afirmaciones simples y útiles? ¿Las pruebas están separadas adecuadamente entre los diferentes métodos de prueba?

Recuerda que las pruebas también son código que debe mantenerse. No aceptes complejidad en las pruebas solo porque no formen parte del binario principal.

---

### Nomenclatura
¿El desarrollador eligió **buenos nombres** para todo? Un buen nombre es lo suficientemente largo como para comunicar completamente qué es o qué hace el elemento, sin ser tan largo que sea difícil de leer.

---

### Comentarios
¿El desarrollador escribió **comentarios claros** en inglés comprensible? ¿Todos los comentarios son realmente necesarios? Por lo general, los comentarios son útiles cuando **explican por qué** existe algún código, y no deberían explicar **qué** está haciendo algún código. Si el código no es lo suficientemente claro para explicarse a sí mismo, entonces el código debería simplificarse. Hay algunas excepciones (las expresiones regulares y los algoritmos complejos a menudo se benefician enormemente de los comentarios que explican lo que están haciendo, por ejemplo), pero la mayoría de los comentarios son para información que el propio código no puede contener, como el razonamiento detrás de una decisión.

También puede ser útil mirar los comentarios que estaban allí antes de este CL. Quizás haya un TODO que se pueda eliminar ahora, un comentario que desaconseje hacer este cambio, etc.

Ten en cuenta que los comentarios son diferentes de la **documentación** de clases, módulos o funciones, que en su lugar deberían expresar el propósito de una pieza de código, cómo debe usarse y cómo se comporta cuando se usa.

---

### Estilo
Tenemos **guías de estilo** en Google para todos nuestros lenguajes principales, e incluso para la mayoría de los lenguajes menores. Asegúrate de que el CL siga las guías de estilo apropiadas.

Si deseas mejorar algún punto de estilo que no esté en la guía de estilo, antepón tu comentario con "Nit:" para que el desarrollador sepa que es una **minucia** que crees que mejoraría el código pero no es obligatoria. No impidas que se envíen CLs basándose solo en preferencias de estilo personales.

El autor del CL no debe incluir cambios de estilo importantes combinados con otros cambios. Dificulta ver qué se está cambiando en el CL, hace que las fusiones y reversiones sean más complejas y causa otros problemas. Por ejemplo, si el autor quiere reformatear todo el archivo, haz que te envíe solo el reformateo como un CL, y luego envíe otro CL con sus cambios funcionales después de eso.

---

### Consistencia
¿Qué pasa si el código existente es **inconsistente con la guía de estilo**? Según nuestros **principios de revisión de código**, la guía de estilo es la autoridad absoluta: si algo es requerido por la guía de estilo, el CL debe seguir las directrices.

En algunos casos, la guía de estilo hace recomendaciones en lugar de declarar requisitos. En estos casos, es una cuestión de juicio si el nuevo código debe ser consistente con las recomendaciones o con el código circundante. Tiende a seguir la guía de estilo a menos que la inconsistencia local sea demasiado confusa.

Si ninguna otra regla se aplica, el autor debe mantener la consistencia con el código existente.

De cualquier manera, anima al autor a registrar un error y añadir un TODO para limpiar el código existente.

---

### Documentación
Si un CL cambia la forma en que los usuarios construyen, prueban, interactúan o lanzan código, verifica si también **actualiza la documentación asociada**, incluyendo READMEs, páginas g3doc y cualquier documentación de referencia generada. Si el CL elimina o desaprueba código, considera si la documentación también debería eliminarse. Si falta documentación, pídela.

---

### Cada Línea
En el caso general, revisa **cada línea de código** que se te haya asignado. Algunas cosas como archivos de datos, código generado o grandes estructuras de datos a veces puedes escanearlas, pero no escanees una clase, función o bloque de código escrito por humanos y asumas que lo que hay dentro está bien. Obviamente, algunos códigos merecen un escrutinio más cuidadoso que otros; esa es una decisión que debes tomar, pero al menos debes asegurarte de que **entiendes** lo que hace todo el código.

Si te resulta demasiado difícil leer el código y esto está ralentizando la revisión, debes hacérselo saber al desarrollador y esperar a que lo aclare antes de intentar revisarlo. En Google, contratamos grandes ingenieros de software, y tú eres uno de ellos. Si no puedes entender el código, es muy probable que otros desarrolladores tampoco puedan. Así que también estás ayudando a futuros desarrolladores a entender este código cuando le pides al desarrollador que lo aclare.

Si entiendes el código pero no te sientes cualificado para hacer alguna parte de la revisión, **asegúrate de que haya un revisor** en el CL que esté cualificado, particularmente para problemas complejos como privacidad, seguridad, concurrencia, accesibilidad, internacionalización, etc.

**Excepciones**
¿Qué pasa si no tiene sentido que revises cada línea? Por ejemplo, eres uno de varios revisores en un CL y se te puede pedir:
* Que revises solo ciertos archivos que forman parte de un cambio más grande.
* Que revises solo ciertos aspectos del CL, como el diseño de alto nivel, implicaciones de privacidad o seguridad, etc.

En estos casos, anota en un comentario qué partes revisaste. Prefiere dar **LGTM con comentarios**.

Si, en cambio, deseas conceder LGTM después de confirmar que otros revisores han revisado otras partes del CL, anótalo explícitamente en un comentario para establecer expectativas. Intenta **responder rápidamente** una vez que el CL haya alcanzado el estado deseado.

---

### Contexto
A menudo es útil mirar el CL en un **contexto amplio**. Normalmente, la herramienta de revisión de código solo te mostrará unas pocas líneas de código alrededor de las partes que se están cambiando. A veces tienes que mirar el archivo completo para asegurarte de que el cambio realmente tiene sentido. Por ejemplo, podrías ver solo cuatro líneas nuevas añadidas, pero cuando miras el archivo completo, ves que esas cuatro líneas están en un método de 50 líneas que ahora realmente necesita ser dividido en métodos más pequeños.

También es útil pensar en el CL en el contexto del sistema en su conjunto. ¿Este CL está mejorando la salud del código del sistema o está haciendo que todo el sistema sea más complejo, menos probado, etc.? **No aceptes CLs que degraden la salud del código del sistema.** La mayoría de los sistemas se vuelven complejos a través de muchos pequeños cambios que se acumulan, por lo que es importante prevenir incluso pequeñas complejidades en los nuevos cambios.

---

### Cosas Buenas
Si ves algo bueno en el CL, díselo al desarrollador, especialmente cuando abordó uno de tus comentarios de una manera excelente. Las revisiones de código a menudo solo se centran en los errores, pero también deben ofrecer **aliento y aprecio** por las buenas prácticas. A veces es incluso más valioso, en términos de mentoría, decirle a un desarrollador lo que hizo bien que decirle lo que hizo mal.

---

### Resumen
Al hacer una revisión de código, debes asegurarte de que:

* El código está **bien diseñado**.
* La funcionalidad es **buena para los usuarios** del código.
* Cualquier cambio de UI es **sensato y tiene buen aspecto**.
* Cualquier programación paralela se realiza de **forma segura**.
* El código **no es más complejo de lo necesario**.
* El desarrollador **no está implementando cosas que *podría* necesitar** en el futuro pero que no sabe que necesita ahora.
* El código tiene **pruebas unitarias apropiadas**.
* Las pruebas están **bien diseñadas**.
* El desarrollador usó **nombres claros** para todo.
* Los **comentarios son claros y útiles**, y en su mayoría explican **por qué** en lugar de **qué**.
* El código está **documentado apropiadamente** (generalmente en g3doc).
* El código **se ajusta a nuestras guías de estilo**.

Asegúrate de revisar **cada línea** de código que se te ha pedido revisar, mira el **contexto**, asegúrate de que estás **mejorando la salud del código**, y felicita a los desarrolladores por las **cosas buenas** que hacen.