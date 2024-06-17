---
title: "Inheritance and Polymorphism"
weight: 35
pre: "7. "
---
{{% youtube Dz0JB0krAA8 %}}

We can also build classes that _inherit_ attributes and methods from another class. This allows us to build more complex structures in our code, better representing the relationships between real world objects.

## Inheritance in UML

As we learned earlier in this chapter, we can represent an inheritance relationship with an open arrow in our UML diagrams, as shown below:

![Person Student UML Diagram](/images/2/2.17.j.7.studentuml.png)

In this diagram, the `Student` class inherits from, or is a subclass of, the `Person` class. 

## Inheritance in Java

To show inheritance in Java, we can use the `extends` keyword after the class name in our class declaration, listing the parent class that we are inheriting from:

```java
public class Student extends Person{
    
}
```

From there, we can quickly implement the code for each attribute and getter method in the new class:

```java
public class Student extends Person{
    private int studentID;
    private int gradeLevel;
    
    public int getStudentID(){ return this.studentID; }
    public int getGradeLevel(){ return this.gradeLevel; }
}
```

## Method Overriding

{{% youtube Ap7rHHgDjyw %}}

Since the subclass `Student` also includes a definition for the method `happyBirthday()`, we say that that method has been _overridden_ in the subclass. We can do this by simply creating the new method in the `Student` class, and prefixing it with the `@Override` annotation:

```java
public class Student extends Person{
    private int studentID;
    private int gradeLevel;
    
    public int getStudentID(){ return this.studentID; }
    public int getGradeLevel(){ return this.gradeLevel; }
    
    @Override
    public void happyBirthday(){
        super.happyBirthday();
        this.gradeLevel += 1;
    }
}
```

Here, we are using the keyword `super` to refer to our parent class. In that way, we can still call the `happyBirthday()` method as defined in `Person`, but extend it by adding our own code as well.

## Inherited Constructors

In addition, we can use the `super()` method to call our parent class's constructor. This must be done as the **first line** of our subclass's constructor:

```java
public class Student extends Person{
    private int studentID;
    private int gradeLevel;
    
    public int getStudentID(){ return this.studentID; }
    public int getGradeLevel(){ return this.gradeLevel; }
    
    public Student(String lastName, String firstName, int age, int studentID, int gradeLevel){
        super(lastName, firstName, age);
        this.studentID = studentID;
        this.gradeLevel = gradeLevel;
    }
    
    @Override
    public void happyBirthday(){
        super.happyBirthday();
        this.gradeLevel += 1;
    }
}
```

## Security

In addition to `private` and `public`, Java also includes a keyword `protected`. This modifier prevents external code from accessing attributes and methods, but will allow any subclasses to access them. In a UML diagram, the protected keyword is denoted by a hash symbol `#` in front of the attribute or method.

## Polymorphism

{{% youtube OUoWtw785ss %}}

Inheritance allows us to make use of _polymorphism_ in our code. Loosely polymorphism allows us to store an instance of a class within the data type of any of its parent classes. By doing so, we can only access the methods and attributes defined by the data type, but any overriden methods will use the implementation from the child class. 

Here's a quick example:

```java
Student steveStudent = new Student("Jones", "Steve", "19", "123456", "13");
Person stevePerson = (Person)steveStudent;

// Can access methods in Person
System.out.println(stevePerson.getFirstName());

// Cannot access methods in Student
System.out.println(stevePerson.getStudentID()); // will not compile

// Can call methods from Person
// This will use the code defined in Student, 
// even though it is stored as a Person.
stevePerson.happyBirthday();
System.out.println(steveStudent.getGradeLevel()); // 14
```

Polymorphism is a very powerful tool in programming, and we'll use it throughout this course as we develop complex data structures. 
