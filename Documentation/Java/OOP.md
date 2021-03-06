# Object-Oriented Programming in Java

## What is Object-Oriented Programming?
From [the article on Object-oriented programming on Wikipedia](https://en.wikipedia.org/wiki/Object-oriented_programming):
> Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).\
\
A feature of objects is that an object's own procedures can access and often modify the data fields of itself (objects have a notion of this or self). In OOP, computer programs are designed by making them out of objects that interact with one another. OOP languages are diverse, but the most popular ones are class-based, meaning that objects are instances of classes, which also determine their types.\
\
Many of the most widely used programming languages (such as C++, Java, Python, etc.) are multi-paradigm and they support object-oriented programming to a greater or lesser degree, typically in combination with imperative, procedural programming. Significant object-oriented languages include: Java, C++, C#, Python, R, PHP, Visual Basic.NET, JavaScript, Ruby, Perl, SIMSCRIPT, Object Pascal, Objective-C, Dart, Swift, Scala, Kotlin, Common Lisp, MATLAB, and Smalltalk.

## Why do we use OOP?
***There are four major benefits to object-oriented programming:***
1. ***Encapsulation:***
   - ***In OOP, you bundle code into a single unit where you can determine the scope of each piece of data.***
   - Data from one class will not be accessible to all other classes unless you implement a specific way to interact with it.
2. ***Abstraction:***
   - ***By using classes, you are able to generalize your object types, simplifying your program.***
   - Don't manage the names and ages of a group of people manually, create a class `Human` that contains each person's name and age.
3. ***Inheritance:***
   - ***Because a class can inherit attributes and behaviors from another class, you are able to reuse more code.***
   - Have multiple people with different roles? Create `Student` and `Instructor` classes and let them inherit from the `Human` class.
4. ***Polymorphism:***
   - ***One class can be used to create many objects, all from the same flexible piece of code.***
   - The `Human` class can have a method `dailyRoutine()` which the `Student` and `Instructor` classes can override to implement their own specific behavior.

[***Source** (excluding examples)*](https://www.codecademy.com/article/cpp-object-oriented-programming)

## How do we implement OOP in Java?
Based on the example given we can create the `Human` class and the inheriting classes `Student` and `Instructor` with their according data:

First we create our base class `Human`:
#### `Human.java`
```Java
public class Human {
    private String name;
    private int age;

    public Human(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return this.age;
    }

    public void dailyRoutine() {
        System.out.println("I am " + this.name + " and I am existing.");
    }
}
```

Then we create the `Student` and `Instructor` classes, which *override* the behavior of the `dailyRoutine()` method.

***Note:** We still need to create the constructors for these two classes, even though they extend `Human`. In this case we just forward the arguments of the conbstructor to the super constructor (the constructor of the parent class). You can customize the behavior of the inheriting classes' constructors if needed.*

#### `Student.java`
```Java
public class Student extends Human {
    public Student(String name, int age) {
        // Calls parent constructor
        super(name, age);
    }

    @Override
    public void dailyRoutine() {
        System.out.println("I am learning more about programming today.");
    }
}
```

#### `Instructor.java`
```Java
public class Instructor extends Human {
    public Instructor(String name, int age) {
        // Calls parent constructor
        super(name, age);
    }

    @Override
    public void dailyRoutine() {
        System.out.println("I am teaching more about programming today.");
    }
}
```
Lastly, we create a `Classroom` class which contains our `main` method to start our example. We create an instance of each of our classes `Human`, `Student` and `Instructor`. We then group them in an array to loop over them - note that the array has the type `Human`, but can still contain instances of classes inheriting from it. Finally, we iterate over the array and run each instance's `dailyRoutine()` method.
#### `Classroom.java`
```Java
public class Classroom {
    public static void main(String[] args) {
        Human bob = new Human("Bob", 35);
        Student alice = new Student("Alice", 42);
        Instructor david = new Instructor("David", 24);

        Human[] people = { bob, alice, david };

        for(int i = 0; i < people.length; i++) {
            people[i].dailyRoutine();
        }
    }
}
```
Running our program results in the following output:
```
$ java Classroom
I am Bob and I am existing.
I am learning more about programming today.
I am teaching more about programming today.
```
As you can see, we have successfully overridden the behaviour of our `dailyRoutine()` method!