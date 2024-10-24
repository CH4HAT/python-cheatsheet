# python-cheatsheet
Here’s an improved version of your Python exam cheat sheet, combining detailed explanations and practical examples. I'll make sure to explain each concept fully and provide examples wherever needed. This sheet covers all topics, definitions, scenarios, and examples based on your syllabus.

---

### **1. Basic Python Knowledge**

#### **Variables and Data Types**
- **Variables**: Containers for storing data values.
  - Example:
    ```python
    x = 10  # Integer
    y = "Hello"  # String
    z = 3.14  # Float
    ```

- **Data Types**: Define the type of data stored in variables.
  - Common data types:
    - **int**: Integer numbers (e.g., 10, -5)
    - **float**: Floating-point numbers (e.g., 3.14)
    - **str**: String of characters (e.g., "Hello")
    - **list**: Ordered, mutable collection (e.g., [1, 2, 3])
    - **tuple**: Ordered, immutable collection (e.g., (1, 2, 3))
    - **set**: Unordered collection with no duplicates (e.g., {1, 2, 3})
    - **dict**: Key-value pairs (e.g., {"name": "John", "age": 25})

- **Mutable vs Immutable**:
  - **Mutable**: Can be changed after creation.
    - Examples: lists, dictionaries, sets.
  - **Immutable**: Cannot be changed after creation.
    - Examples: strings, tuples, integers.
  
  Example:
  ```python
  lst = [1, 2, 3]  # Mutable list
  lst[0] = 10
  print(lst)  # Output: [10, 2, 3]
  
  tup = (1, 2, 3)  # Immutable tuple
  # tup[0] = 10  # This will raise a TypeError
  ```

#### **Control Structures**
- **If-Else Statements**:
  ```python
  x = 10
  if x > 5:
      print("x is greater than 5")
  elif x == 5:
      print("x is 5")
  else:
      print("x is less than 5")
  ```

- **Loops**:
  - **For Loop**:
    ```python
    for i in range(5):
        print(i)
    ```
  - **While Loop**:
    ```python
    count = 0
    while count < 5:
        print(count)
        count += 1
    ```

- **One-Liner Loops (List Comprehensions)**:
  ```python
  squares = [x**2 for x in range(5)]
  print(squares)  # Output: [0, 1, 4, 9, 16]
  ```

#### **Functions**
- **Function**: A block of reusable code that performs a specific task.
  - Example:
    ```python
    def add(a, b):
        return a + b
    
    print(add(3, 5))  # Output: 8
    ```

---

### **2. Object-Oriented Programming (OOP)**

#### **Classes and Objects**
- **Class**: A blueprint for creating objects.
  - **Object**: An instance of a class.
  - Example:
    ```python
    class Dog:
        def __init__(self, name, age):
            self.name = name
            self.age = age
        
        def bark(self):
            return "Woof!"
    
    my_dog = Dog("Buddy", 3)  # Object instantiation
    print(my_dog.bark())  # Output: Woof!
    ```

- **Attributes**: Variables that belong to a class or object.
  - **Instance Attributes**: Specific to each object.
    ```python
    class Car:
        def __init__(self, model):
            self.model = model  # Instance attribute
    
    car1 = Car("Toyota")
    print(car1.model)  # Output: Toyota
    ```

#### **Methods**
- **Method**: A function defined inside a class.
  - **Instance Methods**: Operate on an instance of the class.
  - Example:
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age
        
        def greet(self):
            return f"Hello, my name is {self.name}."
    
    p = Person("Alice", 30)
    print(p.greet())  # Output: Hello, my name is Alice.
    ```

#### **Constructor (`__init__`)**
- **Constructor**: Special method called when creating an object to initialize attributes.
  - Example:
    ```python
    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y
    ```

#### **Dunder Methods**
- **Dunder (Double-Underscore) Methods**: Special methods with double underscores.
  - **`__str__`**: String representation of the object.
  - **`__repr__`**: Unambiguous representation for debugging.
  - **`__add__`**: Overload the `+` operator.
  
  Example:
  ```python
  class Point:
      def __init__(self, x, y):
          self.x = x
          self.y = y
      
      def __add__(self, other):
          return Point(self.x + other.x, self.y + other.y)
      
      def __str__(self):
          return f"Point({self.x}, {self.y})"
  
  p1 = Point(1, 2)
  p2 = Point(3, 4)
  p3 = p1 + p2
  print(p3)  # Output: Point(4, 6)
  ```

#### **Inheritance**
- **Inheritance**: Mechanism where one class inherits attributes and methods from another.
  - Example:
    ```python
    class Animal:
        def speak(self):
            return "Animal sound"
    
    class Dog(Animal):  # Dog inherits from Animal
        def speak(self):
            return "Bark!"
    
    d = Dog()
    print(d.speak())  # Output: Bark!
    ```

#### **Polymorphism**
- **Polymorphism**: The ability to define methods in different ways for different classes.
  - Example:
    ```python
    class Bird:
        def speak(self):
            return "Tweet"
    
    class Cat:
        def speak(self):
            return "Meow"
    
    animals = [Bird(), Cat()]
    for animal in animals:
        print(animal.speak())  # Output: Tweet Meow
    ```

---

### **3. Unit Testing with Pytest**

#### **Testing Basics**
- **Unit Testing**: Testing individual units of code (e.g., functions or methods).
- **Pytest**: A testing framework for Python.
  
  Example:
  ```python
  def add(x, y):
      return x + y
  
  def test_add():
      assert add(3, 5) == 8
  ```

#### **Using Fixtures**
- **Fixture**: Provides a fixed baseline or input for the tests.
  - Example:
    ```python
    @pytest.fixture
    def sample_data():
        return [1, 2, 3, 4]
    
    def test_sum(sample_data):
        assert sum(sample_data) == 10
    ```

#### **Mocking and Patching**
- **Mocking**: Creating fake objects or functions for testing purposes.
- **Patching**: Replacing real objects or functions with mocks.
  
  Example:
  ```python
  from unittest.mock import patch

  @patch('requests.get')
  def test_api(mock_get):
      mock_get.return_value.status_code = 200
      response = requests.get('https://example.com')
      assert response.status_code == 200
  ```

---

### **4. HTTP Requests with `httpx`**

#### **HTTP Requests**
- **GET Request**: Retrieve data from a server.
  - Example:
    ```python
    import httpx
    
    response = httpx.get('https://api.github.com')
    print(response.status_code)
    print(response.json())
    ```

- **POST Request**: Send data to a server.
  - Example:
    ```python
    response = httpx.post('https://httpbin.org/post', data={'key': 'value'})
    print(response.json())
    ```

---

### **5. Web Scraping with BeautifulSoup**

#### **Web Scraping Basics**
- **BeautifulSoup**: A library to extract information from HTML documents.

  Example:
  ```python
  from bs4 import BeautifulSoup
  import requests
  
  response = requests.get('https://quotes.toscrape.com/')
  soup = BeautifulSoup(response.text, 'html.parser')
  
  # Extract a quote
  quote = soup.find('span', class_='text').text
  print(quote)
  ```

- **Selecting Elements**:
  ```python
  # Extract all authors
  authors = soup.select('.author')
  for author in authors:
      print(author.text)
  ```

---

### **6. File System Operations**

#### **Reading and Writing Files**
- **Opening a File**:
  ```python
  with open('file.txt', 'r') as f:
      content = f.read()
      print(content)
  ```

-
