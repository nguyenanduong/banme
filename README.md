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

Injects

## Entity

# FAQs
