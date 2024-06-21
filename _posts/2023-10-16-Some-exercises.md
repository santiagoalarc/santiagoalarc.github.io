---
layout: post
title: You're up and running!
---
## 1. ¿Que resultado lanza el siguiente fragmento?
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

## 4. ¿Cuántas filas son añadidas a la tabla herramientas despues de correr lo siguiente?
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
- [ ] 1
- [ ] 2
- [ ] 3

## 5. ¿Cuales son los dos cambios que pueden ser hechos, independienemente el uno del otro con el fin de que el siguiente código compile?
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


## 6. ¿Cuál es el resultado?

~~~~~~~~
Stream<String> strings = Stream.of("a1", "b2", "c3", "a1");
var result = strings.collect(Collectors.groupingBy(s -> s.indexOf("a"), 
	Collectors.joining(":")));

System.out.println(result)
~~~~~~~~
{: .language-ruby}

## 7. ¿Cuál es la salida de la implementación del siguiente código?
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


## 8. ¿Cuál será el resultado del programa compilado y ejcutado?
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
- [ ] {-1=b2:c3, 0=a1:a1}
- [ ] [-1, 0]
- [ ] [b2:c3, a1:a1]
- [ ] Falla la compilación
- [ ] []
- [ ] Se lanza una excepción en tiempo de ejecución.

## 10. ¿Cuál sería el resultado?
~~~
        Stream<String> stringStream = Stream.of("nuevo4", "cinco", "tres", "solo");

        var result = stringStream.map(String::length)
                .filter(s -> s <= 5)
                .collect(Collectors.toSet());
        System.out.println(result);
    }
~~~
{: .language-ruby}

## 11. ¿Qué código leerá correctamente una linea de un archivo?
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


