---
layout: post
title: You're up and running!
---
## 1. ¿Cuántas filas son añadidas a la tabla herramientas despues de correr lo siguiente?
~~~~~~~~
try (Connection connection = DriverManager.getConnection(databaseUrl);
     Statement statement = connection.createStatement()){

	connection.setAutocommit(false);
  	statement.executeUpdate("INSERT INTO tools VALUE ('hammer')");
  	statement.executeUpdate("INSERT INTO tools VALUE ('screw')");
  	connection.rollback()
    	connection.setAutocommit(true);
	statement.executeUpdate("INSERT INTO tools VALUE ('drill')");
  	connection.rollback()
}
~~~~~~~~
{: .language-ruby}
- [ ] 0
- [x] 1
- [x] 2
- [ ] 3

## 2. Al ejecutar el siguiente código se crea el objeto B b = nuevo B). ¿Qué valores obtendrán los campos de este objeto durante la deserialización?
~~~~~~~~
class A {
	public int a = 0;
	public A() {
    	a = 1;
    }
}

class B extends A implements Serializable {
	public int b = 0;
	public B() {
    	a = 2;
	b = 3;
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] b.a=0, b.b=0
- [ ] b.a=2, b.b=3
- [x] b.a=1, b.b=3
- [ ] La deserialización no será posible porque la clase A no implementa la interfaz de Serializable
- [ ] b.a=0, b.b=3
- [ ] b.a=1, b.b=0

## 3. ¿Cuales son los dos cambios que pueden ser hechos, independienemente el uno del otro con el fin de que el siguiente código compile?
~~~~~~~~
import java.io.IOException;

class Class1 {
	public Finest(int value){
 		if(Math.random()> 0.5) {
 			throw new IOException();
 		}
 		throw new RuntimeException();
	}
}

class Main{
	public static void main (String[] args){
    	try{
        	Finest fine = new Finest(77);
        } catch (RuntimeException e){
        	e.printStackTrace();
        }
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] Cambie RuntimeExpetion en la línea 1 a java.io.IOException.
- [ ] Agregue throws IOException al método principal así como al constructor de clase Class1.
- [ ] Agregue throws IOException al constructor de clase Class1.
- [ ] Agregue throws IOException al método principal.
- [ ] Agregue throws IOException al constructor de clase Class1 y cambie catch (RuntimeException e) por catch (Exception e) en el método principal (main method).

## 4. ¿Cuál sería el resultado?
~~~~~~

        Stream<String> stringStream = Stream.of("x1", "y2", "z3", "x1");

        var result = stringStream.collect(
                Collectors.groupingBy(s -> s.indexOf("x"),
                        Collectors.joining(":")));

        System.out.println(result);
    
~~~~~~~~
{: .language-ruby}

- [x] {-1=y2:z3, 0=x1:x1}
- [ ] [-1, 0]
- [ ] [y2:z3, x1:x1]
- [ ] Falla la compilación
- [ ] []
- [ ] Se lanza una excepción en tiempo de ejecución.

## 5. ¿Cuál es la salida de la implementación del siguiente código?
~~~~~~~~
class Order {
	long orderId;
  	double amount;
  	public Order(long orderId, double amount){
    	this.orderId = orderId;
      	this.amount = amount;
    }
  	public String toString(){
    	return orderId + ", " + amount;
    }
}

class Y{
	public static void main(String[] args){
    	List<Order> orders = Arrays.asList(
          new Order(1, 50),
          new Order(5, 70),
          new Order(7, 70)
        );
      
      Order order = orders.stream()
        .reduce(new Order(4, 0), (p1, p2) -> new Order(p1.orderId, p1.amount += p2.amount));
      System.out.println(order);
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] 4, 190.0
- [ ] Se lanza una excepción en tiempo de ejecución.
- [ ] 17, 0.0
- [ ] 4, 0.0
- [ ] Error de compilación
- [ ] 17, 190.0

## 6. ¿Que resultado lanza el siguiente fragmento?
~~~~~~~~
String string = "cdd;26;89;b89";
String[] strings = string.split("\\w");
for (String s : strings)
  System.out.print(s + " ");
System.out.print(" ");
strings = string.split("\\D");
for (String s : strings)
  System.out.print(s + " ");
~~~~~~~~
{: .language-ruby}
 - [ ] cdd;26;89;b8 cdd;26;89;b8
 - [x] ;  ;  ;      26 89  89
 - [ ] 26 89 89 cdd;56;89;b89
 - [ ] cdd;26;89;b89 26 89 89

## 7. ¿Cuál será el resultado del programa compilado y ejcutado?
~~~~~~~~
public class StaticQuest12{
    {
        System.out.print("A"); //linea1
    }
    static {
        System.out.print("S"); //linea2
    }
    {
        System.out.print("B"); //linea3
    }
    public StaticQuest12(){
        System.out.print("C");
    }
    static void m(){
        System.out.print("M");
    }
    public static void main (String[] args){
        StaticQuest12.m(); //linea 4
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] La compilación falla en la línea 4
- [ ] La compilación falla en la línea 3
- [ ] ASBM
- [ ] M
- [ ] SCM
- [ ] CM
- [ ] SABM
- [ ] La compilación falla en la línea 2




## 8. ¿Qué código leerá correctamente una linea de un archivo?
~~~
	BufferedReader br = new BufferedReader(new FileReader("data\\file.txt"));
~~~
{: .language-ruby}

- [ ] Opción a:
~~~
	while (String str = br.readLine() ! null)
	System.out.println(str); 
~~~
{: .language-ruby}

- [ ] Opción b:
~~~
	while ((String str = br.readLine()) ! null)
	System.out.println(str); String str;
	while (str = br.readLine() != null)
	System.out.println(str)
~~~

- [ ] Opción c:
~~~
	String str
	while (str = br.readLine() ! null)
	System.out.println(str)
~~~

## 9. ¿Cuál sería el resultado?
~~~~~~

        Stream<String> stringStream = Stream.of("nuevo4", "cinco", "tres", "solo");

        var result = stringStream.map(String::length)
                .filter(s -> s <= 5)
                .collect(Collectors.toSet());
        System.out.println(result);
    }
~~~~~~~~
{: .language-ruby}
- [ ] Se lanza una excepción en tiempo de ejecución.
- [x] [5, 4]
- [ ] Fallo de compilación
- [ ] [4, 5]
- [ ] [5, 4, 4]

## 10. Dado el siguiente código para las clases CustomExeption y Custom, ¿Cúal es el resultado?
~~~~~~

class Custom{
    public static void main(String[] args) {
        try{
            exec();
        }catch (CustomException e){
            System.err.print("C");
        }
    }
    public static void exec(){//Linea1
        try {
            throw Math.random() > 0.5 ? new CustomException() : new RuntimeException();
        }catch (RuntimeException re){
            System.err.print("R");
        }
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] R
- [ ] C
- [ ] Tanto C como R
- [ ] CR
- [ ] Una compilación fallida ocurrirá en la línea 1

## 11. ¿Cuál será la salida del programa cuando compule y corra?
~~~~~~~~
public class C21 {
    public static void main(String[] args) {

        List<Integer> date = new ArrayList<>();
        date.add(2017);
        date.add(2018);
        date.add(2019);
        System.out.println(date);
        for (int i = 0; i < date.size(); i++){
            int val = date.get(i);
            date.set(i, ++val);
        }
        System.out.println(date);
	}
}

~~~~~~~~
{: .language-ruby}
- [ ] [2017, 2018, 2019][2018, 2019, 2017]
- [ ] An java.util.ConcurrentModificationException is thrown at runtime.
- [ ] [2017, 2018, 2019][2020, 2019, 2018]
- [ ] [2017, 2018, 2019][2020, 2018, 2019]
- [ ] [2017, 2018, 2019][2017, 2018, 2019]
- [x] [2017, 2018, 2019][2018, 2019, 2020]

## 12. Que 3 declaraciones de parámetros pueden der intesertadas en la línea 1 
(como un tipo de paramtro) asique el programa compile sin warnings?
~~~~~~~~
interface Print{}
    class Animal implements Print{}
    class Mammal extends Animal{}
    class Reptile extends Animal{}
    public class T39 {
        public static void main(String[] args) {

            List<Animal> a = new ArrayList<>();
            List<Mammal> b = new ArrayList<>();
            List<Reptile> c = new ArrayList<>();
            examine(a);
            examine(b);
            examine(c);
        }
        
        static void examine(____________ pets){ //linea 1
            System.out.println("ok!");
        }

~~~~~~~~
{: .language-ruby}

- [x] List<? extends Print>
- [ ] List<? super Animal>
- [ ] List<? extends Print & Comparable>
- [ ] List<? super Print>
- [x] List<? extends Animal>
- [x] List<?>
- [ ] List<? super Object>
- [ ] Only two correct answers

## 13. ¿C
~~~~~~~~
    DIAMANTE(20), RUBI(10), PERLAS(5), CRISTAL();

    private Double cost;
    Exercise13(double cost){
        this.cost = cost;
    }
    public boolean equals(Object other){
        if (this == other)
            return true;
        if (!(other instanceof Exercise13))
            return false;
        return cost.equals(((Exercise13) other).cost);
    }

    public static void main(String[] args) {
        RUBI = PERLAS;
        System.out.println(RUBI);
        System.out.println(RUBI.equals(PERLAS));
    }
~~~~~~~~
{: .language-ruby}
- [ ] El programa no compilará, porque hay 3 errores en el programa
- [ ] El programa no compilará, porque hay 2 errores en el programa
- [ ] El programa no compilará, porque hay 1 error en el programa
- [ ] El programa compilará e imprimirá
	~~~~~~~~
	RUBY
	False
	~~~~~~~~
	{: .language-ruby}





## 13. ¿C
~~~~~~~~

~~~~~~~~
{: .language-ruby}
- [ ] 


## 13. ¿C
~~~~~~~~

~~~~~~~~
{: .language-ruby}
- [ ] 


## 13. ¿C
~~~~~~~~

~~~~~~~~
{: .language-ruby}
- [ ] 


## 3. ¿Cuál de las siguientes opciones es correcta?
~~~~~~~~
Set<Integer> c1 = new LinkedHashSet<>();
LinkedHashSet<Integer> c2 = new HashSet<>();
SortedSet<Integer> c3  = new TreeSet<>();
SortedSet<Integer> c4 = new NavigableSet<>();
LinkedList<Integer> c5 = new ArrayDeque<>();
~~~~~~~~
{: .language-ruby}
- [ ] Sentecia Linea 3 y Linea 5 compilará exitosamente
- [x] Sentecia Linea 1 y Linea 3 compilará exitosamente
- [ ] Solo la sentencia 2 compilará exitosamente
- [ ] Sentecia Linea 1, Linea 3 y Linea 4 compilará exitosamente
- [ ] Solo la sentencia 5 compilará exitosamente
- [ ] Solo la sentencia 3 compilará exitosamente
- [ ] Sentecia Linea 1, Linea 2 y Linea 3 compilará exitosamente
- [ ] Sentecia Linea 3 y Linea 4 compilará exitosamente

## A. ¿Cuál linea contine un constructor valido en la siguiente definición de clase?
~~~~~~~~
public class Six {

    private int i;
    public Six getInstance(){return new Six();} //linea1
    public void Six(int x){i = x;} //linea2
    public Six Six(){return new Six();} //linea3
    public ~Six(){i=1;} //linea4

}
~~~~~~~~
{: .language-ruby}
- [ ] Linea 1
- [ ] Linea 2
- [ ] Linea 3
- [ ] Linea 4
- [x] Ninguna

## B. ¿Cuál será el resultado de compilar y correl el programa?
~~~~~~~~
public class StaticQuest5 {
    {
        System.out.println(s);
    }
    static {
        System.out.println(s);
    }
    static String s = "T";
    public StaticQuest5(){
        System.out.println(s);
    }
    public static void main(String[] args) {
        new StaticQuest5();
    }
}
~~~~~~~~
{: .language-ruby}
- [x] Fallo en la compilación
- [ ] TT
- [ ] TTT
- [ ] Una excepción es lanzada en el tiempo de ejecución.

## C. ¿Cómo el código antes de la linea 1 necesita ser cambiada para ser cambiada para hacer el codigo compilar? Elige 2 opciones.
~~~~~~~~
public class Value {
    public static void main(String s[]){
	int i = getX();
    }
    private int getX(){ //linea 1
	return 10;
    }
}
//Nota: En Java, los métodos estáticos solo pueden llamar a otros métodos estáticos directamente. El método getX() en su estado actual no es estático, lo que causará un error de compilación
~~~~~~~~
{: .language-ruby}
- [ ] public int getX(){
- [x] private static int getX(){
- [x] public static int getX(){
- [ ] public int static getX(){

## D. ¿Cuál 2 de las siguientes oraciones son correctas sobre constructores?
- [ ] Los constructores no deben tener argumentos si la construcción de superclase no tiene argumentos.
- [x] Los constructores no se heredan.
- [x] La primera declaración de cada constructor es una llamada legal al método super() o this().
- [ ] Los constructores no se pueden sobrecargar.

## E. ¿Cual será la salida como resultado de compilación y ejecución del siguiente código?
~~~~~~~~
public interface I {
    int i = 0;
}
class C implements I {
    static  int i = 1;
}
public class M extends C {
    public static void main(String[] args) {
        System.out.println(++i);
    }
}
//Nota: si la clase M es guardada en otro archivo, el proceso dará como resulado 2, de lo contratio hay un error de compilación.
~~~~~~~~
{: .language-ruby}
- [ ] Se lanza una excepción en tiempo de ejecución.
- [ ] 1
- [ ] 0
- [x] 2
- [x] Error de compilación

## F. ¿Hay algun error en el código?
~~~~~~~~
class N implements T1, T2{
    public void m(){
    }
}
interface T1{
    int VALUE = 1;
    void m();
}
interface T2{
    int VALUE = 2;
    void m();
}
~~~~~~~~
{: .language-ruby}
- [ ] El código compilará bien si m() es removido de una de las interfaces
- [x] El codigo no tiene problemas
- [ ] Se lanza una excepción en tiempo de ejecución. La clase M no puede implementar ambas interfaces porque genera ambigüedad.
- [ ] El código se compilará bien si se elimina VALOR de una de las interfaces.

## G. ¿Cuál será el resultado del siguiente código?
~~~~~~~~
public class E0 {

    public static void main(String[] args) {
        try{
            System.out.println("A" + " " + 1/0);
        }catch (ArithmeticException e){
            System.out.println("B");
        }
    }
}
~~~~~~~~
{: .language-ruby}
- [ ] A
- [x] B
- [ ] AB
- [ ] A B
      
## H. ¿Cuál será el resultado de compilación y ejecución del siguiente pedazo de código?
~~~~~~~~
        String s1 = "abc";
        StringBuffer s2 = new StringBuffer(s1);
        System.out.println(s1.equals(s2) + " ");
        System.out.println(s1 == s2);
~~~~~~~~
{: .language-ruby}
- [x] Fallo en la compilación
- [ ] true false
- [ ] true true
- [ ] false false
- [ ] false true

## I. ¿Cuál de estas es una definición adecuada de una clase Foo que NO PUEDE ser una subclase?

- [ ] class Foo{}
- [ ] abstract class Foo{}
- [ ] public class Foo{}
- [x] final class Foo{}

## J. ¿Cuál interfaz no permite duplicados?

- [x] Set
- [ ] Deque
- [ ] Queue
- [ ] List

## K. ¿Qué tipo de dato debería ser insetado en vez de un TYPE asi que el codigo compile correctamete?
~~~~~~~~
        byte a = 1;
	TYPE b = a + 1;
-- Nota: cuando se hace la suma se
~~~~~~~~
{: .language-ruby}
- [ ] short
- [ ] byte
- [x] long
- [x] int

## L. ¿Cuál es el propósito de la clase Colelction?

- [ ] Para manejar la entrada del usuario.
- [ ] Definir la estructura de los objetos.
- [x] Proporcionar una forma de almacenar y manipular grupos de objetos.
- [ ] Para crear nuevos objetos.


## M. ¿Cuál será el resultado de intentar compilar y ejecutar el siguiente fragmento de código?
~~~~~~~~
        int result = 0;
        for (int i = 5; i > 2; ++i, i = i - 2) {
            result += i;
            System.out.println(result);
            System.out.print("A");
        }
        System.out.println(result);
~~~~~~~~
{: .language-ruby}

- [x] AAA12
- [ ] AA9
- [ ] La compilación falla
- [ ] AAAA14

## N. ¿Qué tipo de conector se utiliza para conectar HDD y/o SSD con otros elementos dentro de una unidad del sistema?

- [ ] PCI
- [ ] SATA
- [ ] DVI
- [ ] USB

## O. Su proyecto busca una manera para que los desarrolladores creen aplicaciones sin tener que lidiar con cargas administrativas. Elija el modelo de servicio en la nube correcto según las necesidades descritas.
- [ ] Software como servicio (SaaS)
- [ ] Infraestructura como servicio (laaS)
- [x] Plataforma como servicio (PaaS)

## P. ¿A qué campo de actividad se refieren los dominios «.com»?
- [ ] Instituciones educacionales
- [x] Empresas comerciales
- [ ] Empresas no comerciales

## Q. ¿Qué es un hash?
- [ ] Una contraseña cifrada
- [ ] Una imagen de texto de datos prácticamente única (A virtually unique text image of data)
- [ ] El resultado de la operación XOR aplicada a un mensaje y una clave de cifrado
- [ ] Una clave privada en cifrado asimétrico

## R. Convierte el número OxAC9 al sistema decimal.

- [ ] 32,856
- [ ] 39,946
- [ ] 15,904
- [x] 41,161

## S. ¿Con qué frecuencia se realizan reuniones stand-up?

- [ ] Dos veces al día: al principio del día y al final.
- [ ] Al comienzo de cada sprint
- [x] Una vez al día
- [ ] Al final de cada sprint
- [ ] Una vez a la semana, generalmente el lunes o viernes.


## T. El método de copia de seguridad se puede ilustrar con el siguiente ejemplo: "Se realiza una copia de seguridad completa el lunes. El martes, sólo se realizan copias de seguridad de los archivos que se modificaron el lunes. El miércoles, sólo se realizan copias de seguridad de los archivos que se modificaron el martes. "?

- [ ] CDP (Continuous Data Protection)
- [x] Incremental
- [ ] Sólo completo
- [ ] No estructurado

## U. Supongamos que abre la URL https://mail.google.com/mail/u/0/#sent en tu navegador. ¿Qué parte de la URL no se utiliza para formar la solicitud HTTP?

- [x] La parte "#sent" que se encuentra al final de la URL
- [ ] La parte "mail" en el nombre de host "mail.google.com"
- [ ] El prefijo de la URL, "https://"
- [ ] El final de la solicitud después del nombre de host, "/mail/u/0/#sent"

## V. ¿Cuál de los siguientes formatos se utiliza para gráficos vectoriales?

- [ ] jpeg
- [ ] gif
- [ ] bmp
- [x] svg
- [ ] png

## W. ¿Cuál de las siguientes codificaciones tiene una longitud fija?
- [ ] UTF-32
- [ ] UTF-8
- [ ] UTF-16
- [x] ASCII

## X. ¿Qué es un nivel (tier) en la arquitectura de una aplicación?

- [ ] El código responsable de almacenar y recuperar los datos. //(Capa de acceso de datos)
- [ ] El código responsable de mostrar una interfaz de usuario. //(Capa de presentación)
- [x] Una separación lógica del código de la aplicación.
- [ ] Una separación física de una aplicación en varias máquinas.
- [ ] El código responsable de la coordinación de aplicaciones.

## Y. ¿Cuál de las siguientes licencias es una licencia copyleft?

- [ ] Licencia Apache
- [ ] Licencia BSD
- [ ] Licencia MIT
- [x] Licencia pública general GNU

## Z. ¿Qué tipo de hipervisor consta de dos partes: un hipervisor delgado que controla el procesador y la memoria, y un sistema operativo de servicio especial que se ejecuta bajo su control y que Microsoft Hyper-V puede presentar como ejemplo?

- [ ] Nativo (Native)
- [ ] Alojado (Hosted)
- [x] Híbrido (Hybrid)


## AA. ¿Cuál de los siguentes métodos es un nombre válido?
- [ ] act!ion()
- [x] $action()
- [ ] /action()
- [ ] action#()

## AB. ¿Cuál será el resultado de compilar y ejecutar el fragmento de código?
~~~~~~~~
        int i = 2;
        int j = 10;
        i = switch (i){
            case 1 -> --j;
            case 2, 3 -> --j;
            case 4 -> --j;
            case 5 -> --j;
            default -> {
                System.out.print(i +j + " " );
                yield i + j;
            }
        };
        System.out.println(i);
~~~~~~~~
{: .language-ruby}

- [ ] 10
- [ ] 10 9
- [ ] 9 9
- [x] 9
- [ ] 8
- [ ] 9 8

## AC. ¿Cuál será el resultado de compilar y ejecutar el programa?
~~~~~~~~
        double d[] = {1, 2, 3};
        Object db = null;
        d = db;
        db = d;
        System.out.println(d == db);
~~~~~~~~
{: .language-ruby}

- [ ] Fallo en la compilación (can't convert double[] to Object)
- [ ] false
- [ ] true
- [ ] Fallo en la compilación (can't convert Object to double[])



