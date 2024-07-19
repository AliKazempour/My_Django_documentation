# Object-Oriented Programming (OOP) in Python

Object-Oriented Programming (OOP) is a programming paradigm that uses "objects" to design applications and computer programs. Objects can be thought of as instances of classes, which can contain data (attributes) and functions (methods) that operate on the data. Python is an object-oriented language and provides extensive support for OOP.

## Table of Contents

1. Introduction to OOP
2. Classes and Objects
3. Attributes and Methods
4. The `__init__` Method
5. Inheritance
6. Polymorphism
7. Encapsulation
8. Abstraction
9. Special Methods
10. Conclusion

## 1. Introduction to OOP

OOP models real-world entities using classes and objects. The main concepts of OOP include:

- **Classes**: Blueprints for creating objects.
- **Objects**: Instances of classes.
- **Attributes**: Characteristics of an object.
- **Methods**: Functions that belong to an object.
- **Inheritance**: Mechanism for creating a new class using the properties of an existing class.
- **Polymorphism**: Ability to use a common interface for multiple forms (data types).
- **Encapsulation**: Bundling the data and methods that operate on the data within one unit (class), and restricting access to some of the object's components.
- **Abstraction**: Hiding complex implementation details and showing only the necessary features of an object.

## 2. Classes and Objects

### Defining a Class

```python
class Car:
    pass
```

### Creating an Object

```python
my_car = Car()
```

Here, `Car` is a class, and `my_car` is an object (instance) of the `Car` class.

## 3. Attributes and Methods

### Adding Attributes

Attributes are variables that belong to a class.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
```

### Adding Methods

Methods are functions that belong to a class.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
    
    def display_info(self):
        print(f"{self.year} {self.make} {self.model}")
```

### Creating and Using Methods

```python
my_car = Car("Toyota", "Corolla", 2020)
my_car.display_info()  # Output: 2020 Toyota Corolla
```

## 4. The `__init__` Method

The `__init__` method initializes an object’s attributes. It is called automatically when an object is created.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
```

## 5. Inheritance

Inheritance allows a class to inherit attributes and methods from another class.

### Defining a Base Class

```python
class Vehicle:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
```

### Defining a Derived Class

```python
class Car(Vehicle):
    def __init__(self, make, model, year, doors):
        super().__init__(make, model, year)
        self.doors = doors
```

### Creating an Object of the Derived Class

```python
my_car = Car("Toyota", "Corolla", 2020, 4)
print(my_car.make)  # Output: Toyota
print(my_car.doors) # Output: 4
```

## 6. Polymorphism

Polymorphism allows different classes to be treated as instances of the same class through a common interface.

```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

def make_animal_speak(animal):
    print(animal.speak())

dog = Dog()
cat = Cat()

make_animal_speak(dog)  # Output: Woof!
make_animal_speak(cat)  # Output: Meow!
```

## 7. Encapsulation

Encapsulation restricts direct access to some of an object's components, which can prevent the accidental modification of data.

```python
class Computer:
    def __init__(self):
        self.__max_price = 900
    
    def sell(self):
        print(f"Selling Price: {self.__max_price}")
    
    def set_max_price(self, price):
        self.__max_price = price

c = Computer()
c.sell()  # Output: Selling Price: 900

# Changing the price
c.__max_price = 1000
c.sell()  # Output: Selling Price: 900 (still the same)

# Using setter function
c.set_max_price(1000)
c.sell()  # Output: Selling Price: 1000
```

## 8. Abstraction

Abstraction means hiding the complex implementation details and showing only the essential features of the object.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height

rect = Rectangle(10, 20)
print(rect.area())  # Output: 200
```

## 9. Special Methods

Special methods (or magic methods) in Python begin and end with double underscores (`__`). They allow us to define behaviors for built-in operations.

### `__str__` and `__repr__`

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
    
    def __str__(self):
        return f"{self.year} {self.make} {self.model}"
    
    def __repr__(self):
        return f"Car('{self.make}', '{self.model}', {self.year})"

my_car = Car("Toyota", "Corolla", 2020)
print(my_car)        # Output: 2020 Toyota Corolla
print(repr(my_car))  # Output: Car('Toyota', 'Corolla', 2020)
```

### `__len__`, `__getitem__`, and `__setitem__`

```python
class MyList:
    def __init__(self, data):
        self.data = data
    
    def __len__(self):
        return len(self.data)
    
    def __getitem__(self, index):
        return self.data[index]
    
    def __setitem__(self, index, value):
        self.data[index] = value

my_list = MyList([1, 2, 3])
print(len(my_list))     # Output: 3
print(my_list[0])       # Output: 1
my_list[1] = 200
print(my_list[1])       # Output: 200
```

## 10. Conclusion

Object-Oriented Programming in Python provides a powerful and flexible way to structure and manage your code. By understanding and utilizing classes, objects, inheritance, polymorphism, encapsulation, abstraction, and special methods, you can write more organized, reusable, and maintainable code. OOP is a fundamental concept in Python that enhances its simplicity and readability, making it a versatile tool for solving a wide range of programming problems.