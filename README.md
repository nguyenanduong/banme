# Introduction
Banme provides a set of syntactic sugars on top of Java so that help to reduce the verbosity and reinforce best practices. Banme is not a new language but a Java extension. A pure Java program can compile with Banme. On the other hand, Banme libraries are compatible and usable in other Java program.

# Features
## Service
Service is a final, stateless class which provides a single responsibility or a set of related responsibilities. Service can be injected with dependencies but cannot be inherited. Banme advocates "Composition over Inheritance" hence improve testability. Banme also favors "Convention over Configuration" and "DRY"

```java
public service FooService 
   implements FooInterface 
   injects FooSayer {

   public void sayHello() {
       // fooSayer is automatically inferred by naming convention
       fooSayer.say("Hello");
   }
   
   public static void main(String[] args) {
       // Auto generated constructor for constructor injection
       FooInterface fooService = new FooService(new FooSayer());
       fooService.sayHello();
   }
}
```

Injects with qualifier:
```java
public service FooService 
   implements FooInterface 
   injects @FooQualifier FooSayer {
   ...
}
```

Override naming convention:
```java
public service FooService 
   implements FooInterface 
   injects FooSayer as myFooSayer {
   ...
}
```

## Entity

Banme entities are value classes which are immutable by default. All args constructor, no arg constructor, getters, and fluent interface for building are auto generated.

```java
public entity Bar {
   int width;
   int height;
}

var bar1 = new Bar(1,1);
var bar2 = bar1.width(2).height(3);
var x = bar1.width;
var y = bar2.height;
assert (x != y);
assert (bar1 != bar2);
```

### Mutable entity
```
public mutable entity Bar {
   int width;
   int height;
}

var bar = new Bar(1,2);
bar.width = 2;
assert bar.width == 2;
```

### Anonymous Entity

```java
var bar = {
   width: 1,
   height: 2
}
```

### Entity Destructuring
```java
var bar = new Bar(1,2);
var { width, height } = bar;
```

# FAQs
