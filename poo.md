
---
layout: page
title: Poo
permalink: /poo/
---

## Encapsulación 

La encapsulación consiste en consolidar datos y métodos para trabajar con ellos en un solo paquete o "cápsula", con la posibilidad de ocultarlos del entorno externo (otros objetos).

Como ya sabe, los datos que caracterizan un objeto se denominan variables de instancia, y las operaciones realizadas con estos datos se denominan métodos de instancia. En un objeto (instancia de clase), estos campos tienen valores específicos. El conjunto de valores de campo define el estado actual del objeto. Aplicar cualquier método a un objeto puede cambiar su estado.

### ¿Qué hace la encapsulación? 

Principalmente, impide el acceso directo a los campos de esta instancia de clase desde otras clases. Las diferentes partes del programa, así como los programas externos, pueden acceder a los datos del objeto únicamente mediante sus métodos. Esto significa que se puede cambiar la forma en que se almacenan los datos en una clase, conservando los métodos utilizados para procesarlos. De esta forma, otros objetos podrán cooperar con los objetos de esta clase tal como lo hacían antes de los cambios.

En la práctica, esto significa que cada clase tiene dos caras: interfaz e implementación.

Interfaz: La interfaz incluye todo lo relacionado con la interacción de este objeto con otros objetos.

Implementación: La implementación implica ocultar a otros objetos todos los detalles no relacionados con el proceso de interacción de los objetos.

Puedes observar el principio de encapsulación en la vida cotidiana. Supongamos que tú, un individuo, eres una instancia de la clase Humano. Todo lo relacionado con tu apariencia (altura, complexión y color de ojos), así como información general como tu nombre y apellidos, es conocido por quienes te rodean. Sin embargo, tus órganos internos están ocultos dentro de tu cuerpo, por lo que otros objetos no tienen acceso directo a ellos. Lo mismo ocurre con los datos personales que no querrías perder ni divulgar, por ejemplo, el PIN de tu tarjeta de cajero automático.

En Java, los modificadores de acceso son responsables de implementar el principio de encapsulación. Se trata de palabras clave que regulan el nivel de acceso a los datos (clases, campos, métodos y constructores). Aprenderás más sobre ellos más adelante en esta lección.

### El modificador static

El modificador static se utiliza para crear métodos y variables (campos) pertenecientes a una clase y no a un objeto.

El campo de datos o método declarado en una clase como estático es común para todos los objetos de esa clase y se denomina campo de clase o método de clase. En otras palabras, pertenecen a una clase y no a una instancia de clase.

Los campos estáticos (campos de clase) presentan varias características en comparación con los campos de instancia:

Característica 1
Los campos estáticos deben usarse sin crear una instancia de clase.
Característica 2
Si un objeto cambia el valor de dicho campo, todos los objetos verán este cambio.

Los métodos estáticos (métodos de clase) se utilizan para trabajar con campos de clase estáticos o únicamente con los datos especificados en sus parámetros. Al igual que los campos de clase, los métodos estáticos presentan varias características:

* Los métodos estáticos no son polimórficos; es decir, la versión del método que se ejecutará se determina en tiempo de compilación.

* Los métodos estáticos pueden invocarse directamente desde métodos de instancia, al igual que los campos de clase estáticos.

* Los métodos estáticos no están vinculados a una instancia de clase y, por lo tanto, no pueden usar las palabras clave this o super para acceder a un objeto específico.

* Los métodos estáticos no pueden acceder directamente a los campos ni a los métodos de instancia. Para acceder a estos, es necesario crear o recibir una referencia al objeto.

Para acceder a campos y métodos estáticos, basta con especificar antes de ellos el nombre de la clase donde están definidos. Por supuesto, también se puede acceder a un método estático mediante una referencia a un objeto, ya que cualquier instancia de clase tiene acceso a los miembros estáticos de la clase. Sin embargo, este acceso será lógicamente incorrecto, dificultará la comprensión del código y generará la advertencia correspondiente, aunque no causará un error de compilación.

#### Static methods

La definición de un método de clase como estático depende de los datos que utiliza:

* Todos los datos necesarios se pasan explícitamente (en parámetros).
* Solo se utilizan campos estáticos.

*Ejemplo*: La clase CustomMath no tiene campos de instancia. Los métodos reciben datos a través de sus parámetros; es decir, las instancias de clase no tienen estado. Por ello, los métodos deben declararse como estáticos.

~~~~~~~~
public class CustomMath {
    public static int percent;
    public static int add(int x, int y) {
        return x + y + percent;
    }
    public static int multiply(int x, int y) {
        return x * y;
    }
}
~~~~~~~~
{: .language-ruby}

Limitaciones de los métodos estáticos:

* Los métodos estáticos solo pueden invocar directamente métodos estáticos.
* Los métodos estáticos solo pueden acceder directamente a campos estáticos o a sus propios parámetros.
* No se puede acceder a los métodos estáticos mediante las referencias `this` y `super`.
* Los métodos estáticos pueden sobrecargarse con métodos no estáticos y viceversa.

#### Static fields 

Campos de clase estáticos:

* Se crean al acceder a la clase por primera vez.
* Son comunes a todos los objetos de la clase.
* Existen independientemente de las instancias de la clase.
* Se puede acceder a ellos antes de crear una instancia de la clase.

*Ejemplo*: Definamos la clase DemoStatic, que contiene solo elementos estáticos. El método main() de la clase DemoMain muestra la interacción con los campos y métodos de la clase DemoStatic sin crear una instancia, ya que no es necesario.

~~~~~~~~
public class DemoStatic {
    public static int x;
    public static int y;
    public static int lengthVector() {
        return (int)Math.sqrt(x*x + y*y);
    }
}
public class DemoMain {
    public static void main(String[] args) {
        DemoStatic.x = 3;
        DemoStatic.y = 4;
        System.out.println("length = " + DemoStatic.lengthVector());
    }
}
~~~~~~~~
{: .language-ruby}

## El modificador final

El modificador final se utiliza para definir una implementación final de clases y métodos, así como la invariabilidad de variables y campos.

La palabra clave final es un modificador sin acceso que se aplica a clases, métodos y variables, lo que los hace inmutables (imposibles de heredar o anular). Se puede usar en diversos contextos.

* Variable de referencia: A una variable de referencia declarada como final no se le puede asignar otro objeto. Sin embargo, los datos dentro del objeto sí se pueden modificar.

* Clase: Una clase declarada con final no puede tener sucesores.

* Método: Un método declarado con final no se puede anular; es decir, su cuerpo no se puede modificar en el sucesor.

* Campo de instancia: Un campo de instancia declarado como final solo se inicializa una vez: al declararlo, en el constructor o en el bloque inicializador.

* Variable local: Una variable local o un parámetro de método declarado con final no se puede modificar.

* Campo de clase: Para los campos de clase, el modificador final se suele usar con el modificador static para hacerlos constantes.

## Herencia

### Herencia en cadena

#### Regla 1
Al crear un objeto de subclase, los constructores de todas las superclases en su cadena de herencia se invocan en el orden de su herencia, de superclase a subclase. Esto significa que la cadena de herencia se sigue desde la superclase superior. Luego, los constructores se ejecutan uno a uno, siguiendo la jerarquía de arriba a abajo.

En este ejemplo, solo se declaran los constructores predeterminados en las clases Cat y BritishCat. El constructor de la clase BritishCat no invoca explícitamente al de la clase Cat. Como puede ver, se ejecuta el constructor de la clase Cat.

~~~~~~~~
public class Cat {
    Cat() {
        System.out.println("Cat constructor");
    }
}
public class BritishCat extends Cat {
    BritishCat() {
        System.out.println("British constructor");
    }
}
public class Main {
    public static void main(String[] arg) {
        BritishCat myCat = new BritishCat();
        //Cat constructor
        //British constructor
    }
}
~~~~~~~~
{: .language-ruby}


#### Regla 2
Una invocación explícita (super) a un constructor de superclase debe ser el primer operador en el cuerpo del constructor de la subclase.

En este ejemplo, los constructores de las clases Cat y BritishCat solo se declaran con parámetros. El constructor de la clase BritishCat invoca explícitamente al constructor de la clase Cat como su primera acción.

~~~~~~~~
public class Cat {
    Cat(String name) {
        System.out.println("Cat constructor – name " + name);
    }
}
public class BritishCat extends Cat {
    BritishCat(String name) {
        super(name);
        System.out.println("British constructor");
    }
}
public class Main {
    public static void main(String[] arg) {
        BritishCat myCat = new BritishCat("Mulberry");
    }
}
~~~~~~~~
{: .language-ruby}


#### Regla 3
Si un constructor de subclase no invoca explícitamente a ninguno de los constructores de la superclase, se debe invocar automáticamente el constructor predeterminado de la superclase.

En este ejemplo, se declaran dos constructores en la clase Cat: uno predeterminado y otro con parámetros. La clase BritishCat solo tiene un constructor con parámetros. El constructor de la clase BritishCat no llama explícitamente a ninguno de los constructores de la clase Cat. Como puede ver, se ejecutará el constructor predeterminado de la clase Cat.

~~~~~~~~
public class Cat {
    Cat() {
        System.out.println("Cat default constructor");
    }
    Cat(String name) {
        System.out.println("Cat constructor " + name);
    }
}
public class BritishCat extends Cat {
    BritishCat(String name) {
        System.out.println("British constructor");
    }
}
public class Main {
    public static void main(String[] arg) {
        BritishCat myCat = new BritishCat("Mulberry");
        //Cat default constructor
        //British constructor
    }
}
~~~~~~~~
{: .language-ruby}

#### Regla 4
Si una superclase no tiene un constructor predeterminado y el constructor de la subclase no invoca explícitamente a otro constructor de superclase, el compilador de Java generará un error.

En este ejemplo, solo se declaran constructores con parámetros en las clases Cat y BritishCat. El constructor de la clase BritishCat no invoca explícitamente al de la clase Cat. Esto significa que el constructor predeterminado de la clase Cat debería invocarse automáticamente. El compilador revisa la cadena de constructores y no encuentra un constructor predeterminado en la clase Cat; por lo tanto, genera un error.

Pase el cursor sobre el icono de información para ver una explicación del código.

~~~~~~~~
public class Cat {
    Cat(String name) {
        System.out.println("Cat constructor " + name);
    }
}
public class BritishCat extends Cat {
    BritishCat(String name) { //Compilation error
        System.out.println("British constructor");
    }
}
public class Main {
    public static void main(String[] arg) {
        BritishCat myCat = new BritishCat("Mulberry");
    }
}
~~~~~~~~
{: .language-ruby}

## Abstracción 

La abstracción implica ver una entidad compleja como un sistema único y realizar acciones con ella sin profundizar en los detalles de su estructura interna y funcionamiento.

#### High level

Un nivel alto de abstracción solo proporciona una descripción aproximada de un objeto y no permite modelar su comportamiento fiable.

Por ejemplo, la mayoría de los niños ven a un gato como algo suave y esponjoso.

#### Low level

Un nivel bajo de abstracción hace que un modelo sea demasiado complejo, esté sobrecargado de detalles y, por lo tanto, no sea adecuado para su uso.

Por ejemplo, después de desmontar tu coche hasta el último tornillo, olvidas cómo volver a montarlo.


En programación orientada a objetos (POO), la abstracción se manifiesta en la descripción de clases. En otras palabras, las clases son mecanismos de agrupación y generalización. Así, la agrupación se logra mediante la asignación de objetos similares a la misma clase, y la generalización mediante la jerarquía de clases. Es importante comprender que la abstracción no representa el objeto completo, sino solo un conjunto de sus propiedades significativas.