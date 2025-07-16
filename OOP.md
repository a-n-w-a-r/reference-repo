# Object Oriented Programming

### Python Inheritance

> One of these principles is **Inheritance**, inheritance allows for class methods and variables to be used in new objects known as **Subclasses**.

- This reduces the need to repeat methods preventing duplicates

```python
    class Person:
        # This is a python constructor
        def __init__(self, name, age):
            self.name = name
            self.age = age
        
        def greet(self):
            print(self.name, self.age)

    # Use this class to create an instance of an object
    myPerson = Person("Dio", 17)
    myPerson.greet()
```
**Output**
```
    Dio 17
```
- In the code above we create a **Superclass** called ‘Person’. 
- We can create a person object with a **string name** and an **integer for age**.
- We can use the defined function within the class to **return** an objects name and age.

```python
    class Student(Person):
        def __init__(self, name, age, studentId):
            # This utilises the superclass constructor to initialise name and age
            super().__init__(name, age)
            self.studentId = studentId
        
        def getId(self):
            return print(self.studentId)

    myStudent = Student("Dio", 17, "215A")
    myStudent.greet()
    myStudent.getId()
```
**Output**
```
    Dio 17
    215A
```
- In the code above we made a **subclass** of **Person** called 'Student'.
- We can create an object using the inherited **constructor** and **methods**.
- When inheriting we can add new **attributes** to our object like 'studentId'.

### Python Polymorphism

> **Polymorphism** like **inheritance**, polymorphism is when **multiple** classes **inherit** from a single **superclass**.

- This allows for methods and attributes to be shared across subclasses whilst having unique ones within each subclass.
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def greet(self):
        print(self.name, self.age)

class Student(Person):
    def __init__(self, name, age, studentId):
        super().__init__(name, age)
        self.studentId = studentId
        
    def getId(self):
        return print(self.studentId)

class Teacher(Person):
    # We define a new teacherId attribute
    def __init__(self, name, age, teacherId):
        super().__init__(name, age)
        self.teacherId = teacherId
        
    def getId(self):
        return print(self.teacherId)

myStudent = Student("Dio", 17, "215A")
myStudent.greet()
myStudent.getId()

myTeacher = Teacher("Ceasar", 32, "123B")
myTeacher.getId()
myTeacher.greet()
```
**Output**
```
    Dio 17
    215A
    Ceasar 32
    123B
```
- In the code above we defined a new class named **Teacher** which contained a teacherId.
- We can create many subclasses which can **share** certain attributes like 'name' and 'age'.
- We can create subclasses which hold **unique** values like 'studentId' and 'teacherId'.

### Python Encapsulation

> **Encapsulation** hides sensitive data from users, we use **get** and **set** methods to **update** and **retrieve** data from variables.
- used to keep a class or attribute as ‘Read-only’.
```python
    class Account():
        def __init__(self, password):
            self.__password = password
        
        def getPassword(self):
            return self.__password
        
        def setPassword(self, newPass):
            self.__password = newPass

    # Retrieves password
    myAcc = Account("1234")
    print(myAcc.getPassword())
    # Sets new password
    myAcc.setPassword("4321")
    print(myAcc.getPassword())
```
**Output**
```
    1234
    4321
```
- In the code we defined **get** and **set** methods to set or **return** the account password.
- We can use the get and set methods to keep the variables as **read-only**.
```python
class Account():
    def __init__(self, password):
        self.__password = password
    # This allows a method to be used like an attribute
    @property
    def password(self):
        return self.__password
    # @password.setter lets you define what happens when you set password.
    @password.setter
    def password(self, newPass):
        self.__password = newPass

    # Retrieves password
myAcc = Account("1234")
print(myAcc.password)
# Sets new password
myAcc.password = ("4321")
print(myAcc.password)
```
- In the code above we use the @property decorator to control access to private data.
- With it, you write obj.name instead of obj.get_name().
```python
    @password.setter
```
- It’s the setter part of a property — used to update a value safely.
- With this you write obj.name = new_name instead of obj.set_name(new_name).

### Python Modularity

> Modularity breaks a program into separate, manageable pieces called modules. This makes code easier to understand, reuse, and maintain
- Modularity makes code easier to manage, reuse, and understand.
```python
    # This is person.py
    person = {
        'name':'Gyro',
        'age':24,
        'country':'naples'
    }
    # This is greet.py
    import person
    hello = person.person['name']
    print(hello)
```
**Output**
```
    Gyro
```
- In the code above we have a **person.py** file containing data, our **greet.py** file imports this file and prints the name.
- We use **modularity** to allow files to **communicate** to one another.
- This makes code easier to **maintain** since we can focus on one file at a time.
```python
    # This is person.py
    def myHeight():
        return '1.7m'
    person = {
        'name':'Gyro',
        'age':24,
        'country':'naples'
    }
    # This is greet.py
    # We only import the myHeight method
    from person import myHeight
    print(myHeight())
    # Trying this will return an error as we have not imported it
    hello = person.person['name']
    print(hello)
```
**Output**
```
    1.7m
```
- In the code above we have specified what we want to import from our person.py file.
- This allows for specific values and methods to be shared.