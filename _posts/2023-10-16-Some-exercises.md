---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.


##¿Que resultado lanza el siguiente feragmento?
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

## Al ejecutar el siguiente código se crea el objeto B b = nuevo B). ¿Qué valores obtendrán los campos de este objeto durante la deserialización?
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

## ¿Cuál de las siguientes opciones es correcta?
~~~~~~~~
Set<Integer> c1 = new LinkedHashSet<>();
LinkedHashSet<Integer> c2 = new HashSet<>();
SortedSet<Integer> c3  = new TreeSet<>();
SortedSet<Integer> c4 = new NavigableSet<>();
LinkedList<Integer> c5 = new ArrayDeque<>();
~~~~~~~~
{: .language-ruby}

## ¿Cuántas filas son añadidas a la tabla herramientas despues de correr lo siguiente?
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

## ¿Cuales son los dos cambios que pueden ser hechos, independienemente el uno del otro con el fin de que el siguiente código compile?
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
- [ ] Agregar lanza IOException al constructor de clase Class1.
- [ ] Agregar lanza IOException al método principal.
- [ ] Agregue throws IOException al constructor de clase Class1 y cambie catch (RuntimeException e) por catch (Exception e) en el método principal (main method).


##¿Cuál es el resultado?

~~~~~~~~
Stream<String> strings = Stream.of("a1", "b2", "c3", "a1");
var result = strings.collect(Collectors.groupingBy(s -> s.indexOf("a"), 
	Collectors.joining(":")));

System.out.println(result)
~~~~~~~~
{: .language-ruby}

##¿Cuál es la salida de la implementación del siguiente código?
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

## ¿Cuál será el resultado del programa compilado y ejcutado?

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

## ¿Cuál sería el resultado?
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

## ¿Cuál sería el resultado?
~~~
        Stream<String> stringStream = Stream.of("nuevo4", "cinco", "tres", "solo");

        var result = stringStream.map(String::length)
                .filter(s -> s <= 5)
                .collect(Collectors.toSet());
        System.out.println(result);
    }
~~~
{: .language-ruby}


