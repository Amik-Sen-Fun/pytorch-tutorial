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
Now, if there is a function which doesnot has self as a parameter then it can only be called as a class method. Example:
```python
# Class code above
    def hey(name):
        return f"Hey!! {name}"

print(d.hey())             # Will give error
print(Dogs.hey('Tommy'))   # Will print "Hey Tommy"
```
