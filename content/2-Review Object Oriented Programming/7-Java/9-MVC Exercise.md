---
title: "MVC Exercise"
weight: 45
pre: "9. "
---
Let's build a quick program following the MVC architecture style to review working with classes, object, inheritance, and polymorphism. 

## Problem Statement

> Write a program to store a list of students and teachers at a school. The program should have methods to add a student or a teacher, as well as a method to print the entire list.

## UML Diagram

The program should conform to the following UML diagram:

![MVC Exercise UML Diagram](/images/2/2.17.j.9.exerciseuml.png)

_Right-click and select "Open image in new tab" to view larger_

The purpose of each method will be further described below. 

### `Person` Class

* `Person()` - constructor that initializes all attributes based on parameters
* `getLastName()` - getter for `lastName` attribute
* `getFirstName()` - getter for `firstName` attribute
* `getAge()` - getter for `age` attribute
* `happyBirthday()` - method to increase person's `age` attribute by $1$
* `toString()` - method that overrides the built-in `Object` class `toString()` method. It should return a string in the form `"firstName lastName: age"`

### `Student` Class

* `Student()` - constructor that initializes all attributes (including in super class) based on parameters
* `getStudentID()` - getter for `studentID` attribute
* `getGradeLevel()` - getter for `gradeLevel` attribute
* `happyBirthday()` - method to increase student's `age` and `gradeLevel` attribute by $1$
* `toString()` - method that overrides the built-in `Object` class `toString()` method. It should return a string in the form `"firstName lastName: age (studentID - gradeLevel)"`

### `Teacher` Class

* `Teacher()` - constructor that initializes all attributes (including in super class) based on parameters
* `getClassroom()` - getter for `classroom` attribute
* `getSalary()` - getter for `salary` attribute
* `happyBirthday()` - method to increase teacher's `age` by $1$ and `salary` attribute by $1000$
* `toString()` - method that overrides the built-in `Object` class `toString()` method. It should return a string in the form `"firstName lastName: age (classroom - $salary)"`

### `View` Class

* `showMenu()` - a method to show a menu of options to the user. The user should be prompted to input **exactly** one of the options listed below, which is returned as a String. The wording of the menu is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
   * "add student" - add a student
   * "add teacher" - add a teacher
   * "list people" - list the people
   * "exit" - exit the program
* `addStudent()` - a method to add a new student to the system. The user should input a list of parameters for each attribute as they are listed in the constructor for `Student`, separated by spaces. The wording of the prompt is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
   * Example: "Smith John 25 123456 13"
* `addTeacher()` - a method to add a new teacher to the system. The user should input a list of parameters for each attribute as they are listed in the constructor for `Teacher`, separated by spaces. The wording of the prompt is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
* `listPeople()` - a method to list all `Person` objects in the `persons` array given as a parameter. Each one should be prefixed by an index starting at $0$, incrementing by one for each `Person` in the array. Remember that unused array slots will contain the value `null` so that should be considered in your code.  
   * Example: "0) Smith John: 25 (geology - $1000)
* `showError()` - a method to display an error to the user. The parameter `error` should be printed to the screen, prefixed by "Error: "

### `Controller` Class

* `main()` - the main method for this program. It should simply instantiate a new instance of the Controller class, and then call the `run()` method of that object.
* `Controller()` - the constructor for the Controller object. It initialize the `persons` attribute to an array with a maximum size of 20 items, as well as a `View` object stored in the `view` attribute. 
* `run()` - this method consists of a loop that will execute the program until it is terminated. It will call the `showMenu()` method of the view to show a menu to the user (see above). Finally, it will parse the string returned by the call to `showMenu()` and call additional appropriate methods in the `Controller` or `View` class to complete the operation. If the user inputs "exit" then it should terminate. Otherwise, the program will repeatedly display the menu to the user until "exit" is chosen. If at any time the user provides input that cannot be properly parsed, the controller should call the `showError()` method in the `View` class and restart the process (loop back to the beginning) by showing the menu again.
* `addStudent()` - this method will receive the string input by the user from the `addStudent()` method in `View`, parse the input, and call the appropriate methods to create a new `Student` object and add it to the first empty slot in the `persons` array.
* `addTeacher()` - this method will receive the string input by the user from the `addTeacher()` method in `View`, parse the input, and call the appropriate methods to create a new `Teacher` object and add it to the first empty slot in the `persons` array.
* `getPersons()` - this method will simply return the current `persons` attribute as an array. This is for testing purposes only
* `setPersons()` - this method will replace the `persons` attribute with the array provided as a parameter. This is for testing purposes only.

## Sample Execution

A sample execution of the program is shown below. 

![Sample Program Execution](/images/2/2.17.j.9.sample.png)

## Grading

### Structure

{Check It!|assessment}(test-3269626908)

{Check It!|assessment}(test-2757569305)

{Check It!|assessment}(test-2923816668)

{Check It!|assessment}(test-3356253417)

{Check It!|assessment}(test-2664871931)

### Functionality

{Check It!|assessment}(test-3442438399)

{Check It!|assessment}(test-163667115)

{Check It!|assessment}(test-496994260)

{Check It!|assessment}(test-2263639856)

{Check It!|assessment}(test-2809305019)

{{% notice info %}}

# Person

```java
public class Person{
    private String lastName;
    private String firstName;
    private int age;
    
    public Person(String lastName, String firstName, int age){
        this.lastName = lastName;
        this.firstName = firstName;
        this.age = age;
    }
    
    public String getLastName(){ return this.lastName; }
    public String getFirstName(){ return this.firstName; }
    public int getAge(){ return this.age; }
    
    public void happyBirthday(){
        this.age = this.age + 1;
    }
    
    @Override
    public String toString(){
        return this.firstName + " " + this.lastName + ": " + this.age;
    }
}
```

# Student

```java
public class Student extends Person{
    private int studentID;
    private int gradeLevel;
    
    public Student(String lastName, String firstName, int age, int studentID, int gradeLevel){
        super(lastName, firstName, age);
        this.studentID = studentID;
        this.gradeLevel = gradeLevel;
    }
    
    public int getStudentID(){ return this.studentID; }
    public int getGradeLevel(){ return this.gradeLevel; }
    
    @Override
    public void happyBirthday(){
        super.happyBirthday();
        this.gradeLevel = this.gradeLevel + 1;
    }
    
    @Override
    public String toString(){
        return super.toString() + " (" + this.studentID + " - " + this.gradeLevel + ")";
    }
}
```

# Teacher

```java
public class Teacher extends Person{
    private String classroom;
    private int salary;
    
    public Teacher(String lastName, String firstName, int age, String classroom, int salary){
        super(lastName, firstName, age);
        this.classroom = classroom;
        this.salary = salary;
    }
    
    public String getClassroom(){ return this.classroom; }
    public int getSalary(){ return this.salary; }
    
    @Override
    public String toString(){
        return super.toString() + " (" + this.classroom + " - $" + this.salary + ")";
    }
}
```

# View

```java
import java.util.Scanner;

public class View{
    
    public String showMenu(){
        System.out.println("Please enter one of the following options:");
        System.out.println("  add student");
        System.out.println("  add teacher");
        System.out.println("  list people");
        System.out.println("  exit");
        try{
            Scanner scanner = new Scanner(System.in);
            String input = scanner.nextLine();
            return input;
        }catch(Exception e){
            return "";
        }
    }
    
    public String addStudent(){
        System.out.println("Please enter the following items for the new student, all on the same line");
        System.out.println("LastName FirstName Age StudentID GradeLevel");
        try{
            Scanner scanner = new Scanner(System.in);
            String input = scanner.nextLine();
            return input;
        }catch(Exception e){
            return "";
        }
    }
    
    public String addTeacher(){
        System.out.println("Please enter the following items for the new teacher, all on the same line");
        System.out.println("LastName FirstName Age Classroom Salary");
        try{
            Scanner scanner = new Scanner(System.in);
            String input = scanner.nextLine();
            return input;
        }catch(Exception e){
            return "";
        }
    }
    
    public void listPeople(Person[] persons){
        System.out.println("The school contains the following people:");
        int i = 0;
        for(Person p : persons){
            if(p == null){
                continue;
            }
            System.out.println(i + ") " + p.toString());
            i++;
        }
    }
    
    public void showError(String error){
        System.out.println("Error: " + error);
    }
}
```

# Controller

```java
public class Controller{
    
    private Person[] persons;
    private View view;
    private int size;
    
    public static void main(String[] args){
        new Controller().run(); 
    }
    
    public Controller(){
        this.persons = new Person[20];
        this.view = new View();
        this.size = 0;
    }
    
    public void run(){
       while(true){
            String input = view.showMenu();
            if(input.equals("add student")){
                addStudent(view.addStudent());
            }else if(input.equals("add teacher")){
                addTeacher(view.addTeacher());
            }else if(input.equals("list people")){
                view.listPeople(persons);
            }else if(input.equals("exit")){
                break;
            }else{
                view.showError("Invalid Input!");
            }
        } 
    }
    
    public void addStudent(String input){
        String[] splits = input.split(" ");
        try{
            Person p = new Student(splits[0], splits[1], Integer.parseInt(splits[2]), Integer.parseInt(splits[3]), Integer.parseInt(splits[4]));
            if(size < 20){
                persons[size++] = p;
            }else{
                view.showError("Array full!");
            }
        }catch(Exception e){
            view.showError("Unable to parse input!");
        }
    }
    
    public void addTeacher(String input){
        String[] splits = input.split(" ");
        try{
            Person p = new Teacher(splits[0], splits[1], Integer.parseInt(splits[2]), splits[3], Integer.parseInt(splits[4]));
            if(size < 20){
                persons[size++] = p;
            }else{
                view.showError("Array full!");
            }
        }catch(Exception e){
            view.showError("Unable to parse input!");
        }
    }
    
    public Person[] getPersons() { return persons; }
    public void setPersons(Person[] input) { persons = input; }
}
```

{{% / notice %}}
