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

![MVC Exercise UML Diagram](/images/2/2.17.p.9.exerciseuml.png)

_Right-click and select "Open image in new tab" to view larger_

The purpose of each method will be further described below. 

### `Person` Class

* `__init__()` - constructor that initializes all attributes based on parameters
* `last_name()` - getter for `last_name` attribute---it should be implemented as a property
* `get_first_name()` - getter for `first_name` attribute---it should be implemented as a property
* `get_age()` - getter for `age` attribute---it should be implemented as a property
* `happy_birthday()` - method to increase person's `age` attribute by $1$
* `__str__()` - method that overrides the built-in `Object` class `__str__()` method. It should return a string in the form `"first_name last_name: age"`

### `Student` Class

* `__init__()` - constructor that initializes all attributes (including in super class) based on parameters
* `student_id()` - getter for `student_id` attribute---it should be implemented as a property
* `grade_level()` - getter for `grade_level` attribute---it should be implemented as a property
* `happy_birthday()` - method to increase student's `age` and `grade_level` attribute by $1$
* `__str__()` - method that overrides the built-in `Object` class `__str__()` method. It should return a string in the form `"first_name last_name: age (student_id - grade_level)"`

### `Teacher` Class

* `__init__()` - constructor that initializes all attributes (including in super class) based on parameters
* `classroom()` - getter for `classroom` attribute---it should be implemented as a property
* `salary()` - getter for `salary` attribute---it should be implemented as a property
* `happy_birthday()` - method to increase teacher's `age` by $1$ and `salary` attribute by $1000$
* `__str__()` - method that overrides the built-in `Object` class `__str__()` method. It should return a string in the form `"first_name last_name: age (classroom - $salary)"`

### `View` Class

* `show_menu()` - a method to show a menu of options to the user. The user should be prompted to input **exactly** one of the options listed below, which is returned as a String. The wording of the menu is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
   * "add student" - add a student
   * "add teacher" - add a teacher
   * "list people" - list the people
   * "exit" - exit the program
* `add_student()` - a method to add a new student to the system. The user should input a list of parameters for each attribute as they are listed in the constructor for `Student`, separated by spaces. The wording of the prompt is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
   * Example: "Smith John 25 123456 13"
* `add_teacher()` - a method to add a new teacher to the system. The user should input a list of parameters for each attribute as they are listed in the constructor for `Teacher`, separated by spaces. The wording of the prompt is up to you. The method should return whatever was input by the user, without any error checking (that is done in the Controller)
* `list_people()` - a method to list all `Person` objects in the `persons` list given as a parameter. Each one should be prefixed by an index starting at $0$, incrementing by one for each `Person` in the list. 
   * Example: "0) Smith John: 25 (geology - $1000)
* `show_error()` - a method to display an error to the user. The parameter `error` should be printed to the screen, prefixed by "Error: "

_Hint: use `sys.stdin.readline()` to read an entire line of input anywhere in your code. Don't forget to import `sys` as well!_

### `Controller` Class

* `main()` - the main method for this program. It should simply instantiate a new instance of the Controller class, and then call the `run()` method of that object.
* `__init__()` - the constructor for the Controller object. It initialize the `persons` attribute to an empty list, as well as a `View` object stored in the `view` attribute. 
* `run()` - this method consists of a loop that will execute the program until it is terminated. It will call the `showMenu()` method of the view to show a menu to the user (see above). Finally, it will parse the string returned by the call to `showMenu()` and call additional appropriate methods in the `Controller` or `View` class to complete the operation. If the user inputs "exit" then it should terminate. Otherwise, the program will repeatedly display the menu to the user until "exit" is chosen. If at any time the user provides input that cannot be properly parsed, the controller should call the `showError()` method in the `View` class and restart the process (loop back to the beginning) by showing the menu again.
* `add_student()` - this method will receive the string input by the user from the `add_student()` method in `View`, parse the input, and call the appropriate methods to create a new `Student` object and add it to the first empty slot in the `persons` list.
* `add_teacher()` - this method will receive the string input by the user from the `add_teacher()` method in `View`, parse the input, and call the appropriate methods to create a new `Teacher` object and add it to the first empty slot in the `persons` list.
* `persons()` - these methods are a getter and setter for the `persons` attribute. They should be implemented as a property. It is for testing purposes only.

## Sample Execution

A sample execution of the program is shown below. 

![Sample Program Execution](/images/2/2.17.p.9.sample.png)

## Grading

### Structure

{Check It!|assessment}(test-3416583454)

{Check It!|assessment}(test-1104470273)

{Check It!|assessment}(test-845982740)

{Check It!|assessment}(test-3746962485)

{Check It!|assessment}(test-3109390640)

### Functionality

{Check It!|assessment}(test-1533527332)

{Check It!|assessment}(test-1355293558)

{Check It!|assessment}(test-3808852464)

{Check It!|assessment}(test-3597936585)

{Check It!|assessment}(test-1788523734)

{{% notice info %}}

# Person

```python
class Person:

    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age

    @property
    def last_name(self):
        return self.__last_name

    @property
    def first_name(self):
        return self.__first_name

    @property
    def age(self):
        return self.__age

    def happy_birthday(self):
        self.__age = self.__age + 1

    def __str__(self):
        return "{} {}: {}".format(self.first_name, self.last_name, self.age)

```

# Student

```python
from Person import Person


class Student(Person):
    
    def __init__(self, last_name, first_name, age, student_id, grade_level):
        super().__init__(last_name, first_name, age)
        self.__student_id = student_id
        self.__grade_level = grade_level
        
    @property
    def student_id(self):
        return self.__student_id
    
    @property
    def grade_level(self):
        return self.__grade_level
    
    def happy_birthday(self):
        super().happy_birthday()
        self.__grade_level = self.__grade_level + 1
        
    def __str__(self):
        return "{} ({} - {})".format(super().__str__(), self.student_id, self.grade_level)
```

# Teacher

```python
from Person import Person


class Teacher(Person):
    
    def __init__(self, last_name, first_name, age, classroom, salary):
        super().__init__(last_name, first_name, age)
        self.__classroom = classroom
        self.__salary = salary
        
    @property
    def classroom(self):
        return self.__classroom
    
    @property
    def salary(self):
        return self.__salary
        
    def __str__(self):
        return "{} ({} - ${})".format(super().__str__(), self.classroom, self.salary)
```

# View

```python
import sys


class View:
        
    def show_menu(self):
        print("Please enter one of the following options:")
        print("  add student")
        print("  add teacher")
        print("  list people")
        print("  exit")
        try:
            inp = sys.stdin.readline()
            return inp.strip()
        except Exception:
            return ""
        
    def add_student(self):
        print("Please enter the following items for the new student, all on the same line")
        print("LastName FirstName Age StudentID GradeLevel")
        try:
            inp = sys.stdin.readline()
            return inp.strip()
        except Exception:
            return ""
        
    def add_teacher(self):
        print("Please enter the following items for the new teacher, all on the same line")
        print("LastName FirstName Age Classroom Salary")
        try:
            inp = sys.stdin.readline()
            return inp.strip()
        except Exception:
            return ""
        
    def list_people(self, persons):
        i = 0
        for p in persons:
            print("{}) {}".format(i, p))
            i += 1
            
    def show_error(self, error):
        print("Error: {}".format(error))
```

# Controller

```python
from Person import Person
from Student import Student
from Teacher import Teacher
from View import View

import sys


class Controller:
    
    @staticmethod
    def main(args):
        Controller().run()
        
    def __init__(self):
        self.__persons = []
        self.__view = View()
        
    @property
    def persons(self): 
        return self.__persons
    
    @persons.setter
    def persons(self, value):
        self.__persons = value
        
    def run(self):
        while True:
            inp = self.__view.show_menu()
            if inp == "add student":
                self.add_student(self.__view.add_student())
            elif inp == "add teacher":
                self.add_teacher(self.__view.add_teacher())
            elif inp == "list people":
                self.__view.list_people(self.__persons)
            elif inp == "exit":
                break
            else:
                self.__view.show_error("Invalid Input!")
                
    def add_student(self, inp):
        splits = inp.split(" ")
        try:
            p = Student(splits[0], splits[1], int(splits[2]), int(splits[3]), int(splits[4]))
            self.__persons.append(p)
        except Exception:
            self.__view.show_error("Unable to parse input!")
            
    def add_teacher(self, inp):
        splits = inp.split(" ")
        try:
            p = Teacher(splits[0], splits[1], int(splits[2]), splits[3], int(splits[4]))
            self.__persons.append(p)
        except Exception:
            self.__view.show_error("Unable to parse input!")

            
# main guard
if __name__ == "__main__":
    Controller.main(sys.argv)
```

{{% / notice %}}
