---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.


¿Que resultado lanza el siguiente feragmento?
```
String string = "cdd;26;89;b89";
String[] strings = string.split("\\w");
for (String s : strings)
  System.out.print(s + " ");
System.out.print(" ");
strings = string.split("\\D");
for (String s : strings)
  System.out.print(s + " ");
```

Al ejecutar el siguiente código se crea el objeto B b = nuevo B). ¿Qué valores obtendrán los campos de este objeto durante la deserialización?
```
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
```
¿Cuál de las siguientes opciones es correcta?
```
Set<Integer> c1 = new LinkedHashSet<>();
LinkedHashSet<Integer> c2 = new HashSet<>();
SortedSet<Integer> c3  = new TreeSet<>();
SortedSet<Integer> c4 = new NavigableSet<>();
LinkedList<Integer> c5 = new ArrayDeque<>();
```

¿Cuántas filas son añadidas a la tabla herramientas despues de correr lo siguiente?
```
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
```

¿Cuales son los dos cambios que pueden ser echos, independienemente eluno del otro con el fin de que el siguiente codigo compile?
```
import java.io.IOException;

class Finest {
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
```
¿Cuál es el resultado?

```
Stream<String> strings = Stream.of("a1", "b2", "c3", "a1");
var result = strings.collect(Collectors.groupingBy(s -> s.indexOf("a"), 
	Collectors.joining(":")));

System.out.println(result)
```
