# Basic knowledge of JAVA
* public class *classname* { }
* End lines with semicolon
* Typically we want to run our main method inside *public static void main(String[] args){}*
* Types are verified before the code was run
* Expression has a type
* Java program cannot be run without a main methed. But can still be involked.
* **javac** compiler, **java** interpreter

# Declaring Functions
* A function that is part of a class is called method. So in Java, every function is a method
* All parameters of a function must have clear type, and the return value of a function must have a clear type
* Functions in Java return only one value

# Declaring classes
> Java classes can contain methods and/or variables. We say that such methods and variables are “members” of the class. Members can be instance members or static members. Static members are declared with the static keyword. Instance members are any members without the static keyword.

# Class instantiation(实例化)
```
Dog d = new dog()
```
# Static vs. Instance methods. 
> The distinction between static and instance methods is incredibly important. Instance methods are actions that can only be taken by an instance of the class (i.e. a specific object), whereas static methods are taken by the class itself. An instance method is invoked using a reference to a specific instance, e.g. d.bark(), whereas static methods should be invoked using the class name, e.g. Math.sqrt(). Know when to use each.

# Static variables
> Variables can also be static. Static variables should be accessed using the class name, e.g. Dog.binomen as opposed to d.binomen. Technically Java allows you to access using a specific instance, but we strongly encourage you not to do this to avoid confusion.

# Print statement
* if we use `System.out.println` instead of ` System.out.print`, it will bring a automatic newline

# Class
* A class that uses another class is sometimes called a "client" of that class
