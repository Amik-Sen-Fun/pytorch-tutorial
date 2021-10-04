# pytorch-tutorial
Learning stuff for B.Tech Project

To write high quality codes let's learn Object Oriented Programming in Python first

## Object Oriented Programming in Python

### Basics
There are basically 4 principles of OOP
- Inheritance
- Polymorphism
- Encapsulation
- Abstraction

We will look all of these in python

- A class is basically a blue print to define a more complex data structure. To create a class do :
```python
class Dogs:
    pass
```
- Now let's give some initial value to our object, for that we use the \__init__function, this is done by:
```python
class Dogs:
    # class attribute
    alias = "Doggo"    

    def __init__(self, name, kind, age):
        # self.stuff means instance attributes
        self.name = name
        self.age = age
        self.kind = kind   

d = Dogs("Tommy", "Husky", 12)
print(d.name, d.kind) # To access the attributes of a class instance
```
- Class attribute : The variables that are present for an instamnce as well as the class in general
```python
# In the above example 
>>> print(Dogs.alias)   # prints : Doggo
>>> print(d.alias)      # prints : Doggo
```
- Instance Attribute : The variables that are defined for a particular class instance 
```python
# In the above example
print(d.name, d.kind) # works, but these are specific to d instance
```
- Similarly we can define functions (methods) in a class such as:
```python
class Dogs:
    # class attribute
    alias = "Doggo"

    def __init__(self, name, kind, age):
        # self.stuff means instance attributes
        self.name = name
        self.age = age
        self.kind = kind

    def bark(self):
        print(f"{self.name} is barking....")

d = Dogs("Tommy", "Husky", 12)
print(d.name, d.kind) # To access the attributes of a class instance
d.bark() # Output : "Tommy is barking...."
```
### Special Functions or D under methods
The functions start with a leading double underscore and end with them.
Some of them are :
- **\__init__** : Used to initialise an instance
- **\__str__** : Used when the object is converted to string or when you try to print the object
```python
# Class code above 
    def __str__(self):
        informtation = f"{self.name} + is a Dog of age {self.age}"
        return information

print(d) 
# OUTPUT : "Tommy is a Dog of age 12"
```
- **\__eq__** : Used to define comparison between instances of class
```python
# Class code above
    def __eq__(self, other):
        return self.age == other.age and self.kind == other.kind
        # This condition will be used to see whether two instances are equal or not
``` 
### Decorators and Other Methods
Now, if there is a function which doesnot has self as a parameter then it can only be called as a class method. Example:
```python
# Class code above
    def hey(name):
        return f"Hey!! {name}"

print(d.hey())             # Will give error
print(Dogs.hey('Tommy'))   # Will print "Hey Tommy"
```
To make it accessible to users we define a decorator as:
```python
# Class code above
    @staticmethod
    def hey(name):
        return f"Hey!! {name}"

print(d.hey('Tommy'))      # Will print "Hey Tommy"
print(Dogs.hey('Tommy'))   # Will print "Hey Tommy"
```
### Decorators in Python
- A Decorator is a function that takes another function as an argument and extends the functinality of the parent function without changing it. This could be rawly implemented as : 

```python
def seDecorator(func):
    def wrapper():
        print('Start')
        func()
        print('End')
    return wrapper

def PrintName():
    print('Amik')

PrintName = seDecorator(PrintName)
PrintName()

# Start
# Amik
# End
```
- This same thing can be implemented using Decorator: 
```python
def seDecorator(func):
    def wrapper():
        print('Start')
        func()
        print('End')
    return wrapper

@seDecorator
def PrintName():
    print('Amik')

# Start
# Amik
# End
```
- Now, a problem is that we might not know the exact number of arguments of the functions so for that we use *args* and *kwargs*

```python
def seDecorator(func):
    def wrapper(*args, **kwargs):
        print('Start')
        result = func(*args, **kwargs)
        print('End')
        return result
    return wrapper

@seDecorator
def PrintName():
    print('Amik')

# Start
# Amik
# End
```
### Inheritence
- A method by which a class can take on the attributes and methods of another class. The derived class is called 'child class' and the other class is known as 'parent class'. In this way the parent class is extended and methods can be overrided. 
```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age  = age 

class SoftwareEngineer(Employee):
    pass

class Designer(Employee):
    pass

se = SoftwareEngineer()
# Here this will give an error as SoftwareEngineer has inherited the __init__ for Software

se = SoftwareEngineer('Amik','22')
# This works fine now
```
- Now, there could be an init function in the child class as well, this is handled as :
```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age  = age

class SoftwareEngineer(Employee):
    # super() is used to access function of parent class
    def __init__(self, name, age, level):
        super().__init__(name,age)
        self.level = level

class Designer(Employee):
    pass

se = SoftwareEngineer()
# Here this will give an error as SoftwareEngineer has inherited the __init__ for Software

se = SoftwareEngineer('Amik','22', 'Senior')
# This works fine now
```
### Polymorphism 
-  Helps us to define functions with same name and use them in situations accordingly, the child function gets used and the parent class function is overridden.

### Encapsulation:
- Encapsulation is the process or method to contain the information.
- Encapsulation, problems are solved at the implementation level.
- Encapsulation is a method to hide the data in a single entity or unit along with a method to protect information from outside. 
-  Encapsulation can be implemented using by access modifier i.e. private, protected and public.
  - \_ (single underscore)   : means protected  (accessible)
  - Nothing                  : means public
  - \_\_ (double underscore) : means private (cannot be accessed at all) 
    - Getter and Setter functions are created to access and modify data
- In encapsulation, the data is hidden using methods of getters and setters.

### Abstraction
- Data Abstraction is the property by virtue of which only the essential details are displayed to the user. The trivial or the non-essentials units are not displayed to the user. Ex: A car is viewed as a car rather than its individual components.
- We can implement abstraction using abstract class and interfaces.

### Properties
- There are some ways to set the getters and setters using decoratives:
```python
class A:
    def __init__(self):
        self._salary = None
    
    @property
    def salary(self):
        return self._salary
    
    @salary.setter
    def salary(self, value):
        return self._salary = value
	
    # used to delete the value after use
    @salary.deleter
    def salary(self):
        del self._salary

# After defining like that
se = A()
se.salary = 6000
print(se.salary) # prints 6000 
```


