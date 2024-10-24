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
Here is a comprehensive addition to your Python exam cheat sheet, covering **file system operations**, including explanations and examples:

---

### **File System Operations**

Python provides several methods for interacting with the file system, primarily through the `os` and `shutil` modules for directory handling and the built-in `open()` function for file handling.

#### **File Handling with `open()`**
The `open()` function is used to open a file. You can open a file in different modes:

- `'r'` (Read): Opens the file for reading.
- `'w'` (Write): Opens the file for writing (overwrites the file if it exists).
- `'a'` (Append): Opens the file for appending (adds data to the end).
- `'b'` (Binary mode): Opens the file in binary mode.

##### **Example: Opening and Reading a File**

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

##### **Explanation**: 
- `with open(...) as file:` is a context manager that ensures the file is properly closed after the operation is done.
- `.read()` reads the entire content of the file.

##### **Question**:
What would happen if the file `'example.txt'` does not exist when using mode `'r'`?
- **Answer**: A `FileNotFoundError` is raised.

#### **Writing to a File**

```python
with open('example.txt', 'w') as file:
    file.write("Hello, world!")
```

- This overwrites the file content.

##### **Appending to a File**

```python
with open('example.txt', 'a') as file:
    file.write("\nNew line appended!")
```

##### **Explanation**: The `a` mode appends data at the end of the file without overwriting existing content.

---

### **Working with Directories using `os` and `shutil`**

#### **Creating a Directory**

```python
import os

os.mkdir('new_folder')
```

##### **Explanation**: This creates a new folder named `new_folder` in the current working directory.

##### **Questions**:
1. What function would you use to create all missing intermediate directories?
   - **Answer**: `os.makedirs('path/to/folder')`.

#### **Listing Files in a Directory**

```python
files = os.listdir('folder_path')
print(files)
```

##### **Explanation**: This lists all the files and directories within the specified folder.

---

### **Checking if a File Exists**

```python
import os

if os.path.exists('example.txt'):
    print('File exists!')
else:
    print('File not found!')
```

##### **Explanation**: `os.path.exists()` checks whether the given path exists.

---

### **Removing Files and Directories**

- **Removing a File**: 
  ```python
  os.remove('example.txt')
  ```

- **Removing a Directory**: 
  ```python
  os.rmdir('empty_folder')
  ```

- **Removing a Directory and its Contents**:
  ```python
  import shutil
  shutil.rmtree('folder_with_files')
  ```

##### **Explanation**:
- `shutil.rmtree()` removes a directory and all its contents (files and subdirectories).

##### **Questions**:
1. What will happen if you try to remove a non-empty directory using `os.rmdir()`?
   - **Answer**: It raises an `OSError`.

---

### **Common File System Errors**

- **FileNotFoundError**: Raised when trying to open a file that doesn’t exist.
- **PermissionError**: Raised when there is no permission to access the file or directory.
- **IsADirectoryError**: Raised when a file operation is attempted on a directory.

#### **Example of Handling Errors**:

```python
try:
    with open('non_existent.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("File not found!")
```

---

### **Example Questions Based on File System Operations**:

1. **Write a Python function that creates a directory if it doesn’t exist**.
   
   ```python
   def create_directory(directory_name):
       if not os.path.exists(directory_name):
           os.makedirs(directory_name)
       else:
           print("Directory already exists")
   ```

2. **What is the difference between `os.remove()` and `shutil.rmtree()`?**
   - **Answer**: `os.remove()` deletes a single file, while `shutil.rmtree()` deletes an entire directory and all its contents.

---

### **Loops over Different Data Types**

Python provides versatile loop constructs. Let's explore how to loop through different data types.

#### **Looping through a List**:

```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)
```

#### **Looping through a Dictionary**:

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}
for key, value in my_dict.items():
    print(f'{key}: {value}')
```

#### **Looping through a String**:

```python
for char in 'hello':
    print(char)
```

---

---

### **Error Raising and Handling**

#### **Using `raise` to Trigger an Exception**

```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    else:
        print(f"Valid age: {age}")
```

##### **Explanation**: The `raise` keyword is used to trigger an exception manually.

##### **Question**:
How would you raise a `TypeError` for incorrect data types?
- **Answer**: 

```python
if not isinstance(age, int):
    raise TypeError("Age must be an integer")
```

---

### **OOP and Pytest (Integrated Example)**

#### **Class Definition and Unit Testing with Pytest**

```python
# class definition
class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b
```

#### **Unit Test for Calculator Class**:

```python
# test_calculator.py
import pytest
from calculator import Calculator

def test_add():
    calc = Calculator()
    assert calc.add(2, 3) == 5

def test_subtract():
    calc = Calculator()
    assert calc.subtract(5, 3) == 2
```

#### **Explanation**:
- **`pytest`**: A testing framework that simplifies the creation of test cases.
- **Fixtures**: Can be used to set up reusable test data.
- **Mocking/Patching**: Used to simulate the behavior of objects or methods in a test.

##### **Question**:
What is the purpose of using `pytest` over `unittest`?
- **Answer**: `pytest` has more concise syntax, allows parameterized testing, and supports advanced features like fixtures and mocks.

---
Let's add more **examples** and **probable midterm questions** based on your syllabus, covering various topics in **basic Python knowledge**, **OOP**, **unit testing with pytest**, **HTTP requests**, **web scraping**, and **file systems**.

---

### **Basic Python Knowledge**

#### **1. Mutable vs Immutable Data Types**

- **Mutable**: Objects that can be changed after creation (e.g., lists, dictionaries).
- **Immutable**: Objects that cannot be changed once created (e.g., strings, tuples).

##### **Example**:

```python
# Mutable: List
my_list = [1, 2, 3]
my_list[0] = 100  # modifies the first element
print(my_list)  # Output: [100, 2, 3]

# Immutable: Tuple
my_tuple = (1, 2, 3)
# my_tuple[0] = 100  # This would raise a TypeError since tuples are immutable
```

##### **Probable Questions**:
1. **What is the difference between mutable and immutable objects? Give an example.**
2. **Predict the output**:

```python
my_string = "hello"
my_string[0] = 'H'  # What happens?
```

---

### **Loops and Conditionals**

#### **2. One-Liner Loop Examples**

```python
# List comprehension to create squares of numbers 0-4
squares = [x**2 for x in range(5)]
print(squares)  # Output: [0, 1, 4, 9, 16]

# Nested list comprehension
matrix = [[i * j for i in range(3)] for j in range(3)]
print(matrix)
```

##### **Probable Questions**:
1. **What is the output of the following list comprehension?**

```python
nums = [x for x in range(10) if x % 2 == 0]
```

2. **What will the following loop print?**

```python
for i in range(1, 4):
    for j in range(i):
        print(i * j)
```

---

### **OOP Concepts**

#### **3. Class, Object, Attributes, and Methods**

##### **Example Class: Person**

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."

# Create an object of the class
person1 = Person("Alice", 30)
print(person1.greet())  # Output: Hello, my name is Alice and I am 30 years old.
```

##### **Probable Questions**:
1. **Define a class `Book` with attributes `title` and `author`. Implement a method `details()` that prints the book's information.**
2. **What is a constructor in OOP? Why is it important?**

#### **4. Dunder Methods (`__init__`, `__str__`, `__repr__`)**

##### **Example**:

```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def __str__(self):
        return f"{self.make} {self.model}"

    def __repr__(self):
        return f"Car('{self.make}', '{self.model}')"

car = Car("Toyota", "Corolla")
print(car)  # Output: Toyota Corolla
print(repr(car))  # Output: Car('Toyota', 'Corolla')
```

##### **Probable Questions**:
1. **Explain the difference between `__str__` and `__repr__` with examples.**
2. **What is the output of the following code:**

```python
class Student:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Student name is {self.name}"

s = Student("John")
print(s)
```

---

### **Unit Testing with `pytest`**

#### **5. Writing Tests for a Simple Calculator Class**

```python
# calculator.py
class Calculator:
    def add(self, x, y):
        return x + y

    def subtract(self, x, y):
        return x - y

# test_calculator.py
import pytest
from calculator import Calculator

def test_add():
    calc = Calculator()
    assert calc.add(3, 4) == 7

def test_subtract():
    calc = Calculator()
    assert calc.subtract(10, 3) == 7  # Incorrect: This will fail
```

##### **Probable Questions**:
1. **Write a pytest function to test the `add()` method in a `MathOperations` class.**
2. **What is a fixture in pytest, and how would you use it to create reusable test objects?**

#### **6. Mocking in Pytest**

```python
import pytest
from unittest.mock import patch

class ExternalAPI:
    def fetch_data(self):
        return "Real data"

def test_fetch_data():
    with patch.object(ExternalAPI, 'fetch_data', return_value="Mock data"):
        api = ExternalAPI()
        assert api.fetch_data() == "Mock data"
```

##### **Probable Questions**:
1. **What is the purpose of mocking in pytest, and when would you use it?**

---

### **File System Operations**

#### **7. Example of File Reading and Writing**

##### **Reading a File**:

```python
with open('data.txt', 'r') as file:
    content = file.read()
    print(content)
```

##### **Writing to a File**:

```python
with open('output.txt', 'w') as file:
    file.write("This is the output text.")
```

##### **Probable Questions**:
1. **What is the difference between `r+`, `w+`, and `a+` modes in file handling?**
2. **Write a Python program that reads from one file and writes to another.**

---

### **Making HTTP Requests with `httpx`**

#### **8. Sending GET Requests**

```python
import httpx

response = httpx.get('https://api.github.com')
print(response.status_code)
print(response.json())  # Parse JSON response
```

##### **Probable Questions**:
1. **Write a Python function to make a GET request to a given URL and return the response status code.**
2. **What method in `httpx` would you use to send POST data?**

---

### **Web Scraping with BeautifulSoup**

#### **9. Extracting Data from HTML**

##### **Example**:

```python
import httpx
from bs4 import BeautifulSoup

url = "https://quotes.toscrape.com/"
response = httpx.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Finding all quote elements
quotes = soup.find_all('span', class_='text')
for quote in quotes:
    print(quote.text)
```

##### **Explanation**:
- **`find_all()`**: Finds all elements matching the tag and class.
- **`text`**: Extracts text content from HTML.

##### **Probable Questions**:
1. **Explain how `find()` and `find_all()` work in BeautifulSoup with an example.**
2. **Write a Python script to scrape and print all the quotes from a webpage using BeautifulSoup.**

---

### **Advanced File System Operations**

#### **10. Handling File Paths and Directories**

```python
import os

# Create a directory
os.makedirs('my_folder', exist_ok=True)

# Check if a path exists
if os.path.exists('my_folder'):
    print('Directory exists')

# Remove a directory
os.rmdir('my_folder')
```

##### **Probable Questions**:
1. **What is the purpose of `os.makedirs()` vs `os.mkdir()`?**
2. **How would you check if a file exists before attempting to open it?**

#### **Example**:

```python
import os

if os.path.exists('example.txt'):
    with open('example.txt', 'r') as file:
        content = file.read()
    print(content)
else:
    print('File not found')
```

---

### **Error Handling**

#### **11. Raising Custom Errors**

```python
def divide(x, y):
    if y == 0:
        raise ValueError("Cannot divide by zero!")
    return x / y

try:
    divide(10, 0)
except ValueError as e:
    print(e)  # Output: Cannot divide by zero!
```

Here are the **solutions** for the practice questions I shared earlier:

---

### **1. OOP Question**

**Problem**: Define a `BankAccount` class with attributes `balance` and `account_holder`. Write methods to deposit and withdraw money, ensuring the balance doesn't go negative.

**Solution**:

```python
class BankAccount:
    def __init__(self, account_holder, balance=0):
        self.account_holder = account_holder
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"Deposited {amount}, new balance is {self.balance}")
        else:
            print("Deposit amount must be positive.")

    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            print(f"Withdrew {amount}, remaining balance is {self.balance}")
        else:
            print("Insufficient balance or invalid amount.")
            
# Example usage
account = BankAccount("Alice", 100)
account.deposit(50)  # Deposited 50, new balance is 150
account.withdraw(30) # Withdrew 30, remaining balance is 120
account.withdraw(200) # Insufficient balance or invalid amount.
```

---

### **2. File Handling**

**Problem**: Write a Python script that reads a file, counts the number of lines, and writes the count to another file.

**Solution**:

```python
# Assuming input file is 'input.txt' and output file is 'output.txt'

def count_lines(input_file, output_file):
    try:
        with open(input_file, 'r') as infile:
            lines = infile.readlines()
            line_count = len(lines)

        with open(output_file, 'w') as outfile:
            outfile.write(f"Number of lines: {line_count}\n")

        print(f"Line count ({line_count}) has been written to {output_file}")

    except FileNotFoundError:
        print("The file was not found.")

# Example usage
count_lines('input.txt', 'output.txt')
```

---

### **3. Web Scraping**

**Problem**: Using BeautifulSoup, write a script that extracts and prints all the URLs from a webpage.

**Solution**:

```python
import httpx
from bs4 import BeautifulSoup

def extract_urls(url):
    response = httpx.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    # Find all anchor tags <a> and extract href attribute
    links = soup.find_all('a', href=True)
    for link in links:
        print(link['href'])

# Example usage
extract_urls("https://quotes.toscrape.com")
```

---

### **4. Unit Testing**

**Problem**: Write a pytest test function to test the withdrawal method of a `BankAccount` class, ensuring it raises an error if withdrawal exceeds balance.

**Solution**:

```python
import pytest
from bank_account import BankAccount  # Assuming the class is in a file called bank_account.py

def test_withdraw_insufficient_balance():
    account = BankAccount("Alice", 100)
    
    with pytest.raises(ValueError, match="Insufficient balance or invalid amount."):
        account.withdraw(200)  # Trying to withdraw more than balance
```

---

### **5. HTTP Requests**

**Problem**: Write a Python function to make a GET request to a given URL and return the response status code.

**Solution**:

```python
import httpx

def get_status_code(url):
    try:
        response = httpx.get(url)
        return response.status_code
    except httpx.RequestError as e:
        print(f"An error occurred while requesting {e.request.url!r}")
        return None

# Example usage
status_code = get_status_code('https://api.github.com')
print(f"Status Code: {status_code}")  # Output: Status Code: 200
```

---
Here are some **one-liner questions, fill-in-the-blanks, and simple definition-based multiple-choice questions** for your Python exam:

---

### **One-Liner/Fill-in-the-Blank Questions**

1. **Question**: Fill in the blank:  
   Python uses the `__________` keyword to create a class.  
   **Answer**: `class`

2. **Question**: Fill in the blank:  
   The `__________` method is called when an object is created in Python.  
   **Answer**: `__init__`

3. **Question**: Fill in the blank:  
   A dictionary is defined using `{}` and stores data in ____________ pairs.  
   **Answer**: `key-value`

4. **Question**: Fill in the blank:  
   The function `len()` returns the __________ of a string, list, tuple, or dictionary.  
   **Answer**: `length`

5. **Question**: Fill in the blank:  
   In Python, the `__________` function is used to get user input from the console.  
   **Answer**: `input()`

6. **Question**: Fill in the blank:  
   To handle exceptions in Python, we use the `__________` and `__________` blocks.  
   **Answer**: `try`, `except`

7. **Question**: Fill in the blank:  
   A `for` loop in Python is often used to iterate over a __________.  
   **Answer**: `sequence` (like a list, tuple, or string)

8. **Question**: Fill in the blank:  
   The `__________` keyword is used to check if a value exists in a list or tuple.  
   **Answer**: `in`

9. **Question**: Fill in the blank:  
   Python’s `__________` function is used to check the data type of a variable.  
   **Answer**: `type()`

10. **Question**: Fill in the blank:  
   To stop a loop prematurely, you use the `__________` statement.  
   **Answer**: `break`

---

### **Multiple Choice (MCQs)**

1. **Question**: What is the output of `3 * 'Python'`?
   - a) `'Python'`
   - b) `TypeError`
   - c) `'PythonPythonPython'`
   - d) `3`
   - **Answer**: c) `'PythonPythonPython'`

2. **Question**: Which of the following is used to define a function in Python?
   - a) `def`
   - b) `func`
   - c) `lambda`
   - d) `class`
   - **Answer**: a) `def`

3. **Question**: Which method is used to add an item to a list?
   - a) `append()`
   - b) `add()`
   - c) `insert()`
   - d) `extend()`
   - **Answer**: a) `append()`

4. **Question**: What is the output of `print(2 ** 3)`?
   - a) `5`
   - b) `6`
   - c) `8`
   - d) `9`
   - **Answer**: c) `8`

5. **Question**: What will be the output of the following code:  
   `x = [1, 2, 3]`  
   `print(x[1])`
   - a) `1`
   - b) `2`
   - c) `3`
   - d) `IndexError`
   - **Answer**: b) `2`

6. **Question**: Which operator is used to check if two values are equal?
   - a) `=`
   - b) `==`
   - c) `!=`
   - d) `<>`
   - **Answer**: b) `==`

7. **Question**: Which of the following is **not** a valid Python data type?
   - a) `list`
   - b) `tuple`
   - c) `dict`
   - d) `array`
   - **Answer**: d) `array`

8. **Question**: What will be the output of `bool(0)`?
   - a) `True`
   - b) `False`
   - c) `0`
   - d) `None`
   - **Answer**: b) `False`

9. **Question**: Which of the following can be used to open a file in write mode?
   - a) `'r'`
   - b) `'w'`
   - c) `'x'`
   - d) `'a'`
   - **Answer**: b) `'w'`

10. **Question**: How do you raise an exception in Python?
    - a) `throw`
    - b) `raise`
    - c) `catch`
    - d) `try`
    - **Answer**: b) `raise`

---

### **Short Answer Questions**

1. **Question**: What is a lambda function in Python?  
   **Answer**: A lambda function is an anonymous function defined using the `lambda` keyword. It can have any number of arguments but only one expression. Example: `lambda x: x + 2`.

2. **Question**: What is the difference between a list and a tuple in Python?  
   **Answer**: A list is mutable (can be changed after creation), whereas a tuple is immutable (cannot be changed after creation).

3. **Question**: What is the purpose of the `__init__` method in Python?  
   **Answer**: The `__init__` method is a constructor used to initialize an object’s attributes when a new instance of a class is created.

4. **Question**: What does the `pass` statement do in Python?  
   **Answer**: The `pass` statement is a placeholder in Python, used when a statement is required syntactically, but no action is needed.

5. **Question**: What does the `with` statement do when working with file handling in Python?  
   **Answer**: The `with` statement simplifies file handling by automatically closing the file after the block of code is executed, even if an exception occurs.

---

Here's a comprehensive **Python exam** based on your syllabus, class notes, labs, and probable questions that could appear in the exam. I'll break it down into multiple sections, including **multiple choice questions (MCQs)**, **short answer questions**, **code-based problems**, and **test-driven development (pytest)** questions.

---

### **Python Exam**

#### **Part 1: Multiple Choice Questions (MCQs)**

1. **What is the output of the following code?**  
   ```python
   x = "Python"
   print(x[::-1])
   ```
   - a) `nohtyP`
   - b) `Python`
   - c) `thonPy`
   - d) `Error`
   - **Answer**: a) `nohtyP`

2. **Which of the following is used to handle exceptions in Python?**
   - a) `try`
   - b) `except`
   - c) `raise`
   - d) All of the above
   - **Answer**: d) All of the above

3. **What is the correct syntax to create a class in Python?**
   - a) `class MyClass:`
   - b) `def MyClass:`
   - c) `create class MyClass:`
   - d) `new MyClass:`
   - **Answer**: a) `class MyClass:`

4. **What is the output of the following code?**  
   ```python
   x = [1, 2, 3, 4, 5]
   print(x[1:3])
   ```
   - a) `[1, 2, 3]`
   - b) `[2, 3]`
   - c) `[1, 2]`
   - d) `Error`
   - **Answer**: b) `[2, 3]`

5. **Which of the following methods can be used to add an element to a set?**
   - a) `add()`
   - b) `append()`
   - c) `insert()`
   - d) `extend()`
   - **Answer**: a) `add()`

---

#### **Part 2: Fill-in-the-Blanks**

1. **Fill in the blank:** The keyword `__________` is used to check if a value exists in a sequence (like a list or tuple).  
   **Answer**: `in`

2. **Fill in the blank:** A `__________` is a function inside a class that initializes the attributes of an object.  
   **Answer**: `__init__` (constructor)

3. **Fill in the blank:** The `__________` keyword is used to create a function in Python.  
   **Answer**: `def`

4. **Fill in the blank:** Python’s `__________` method can be used to convert a string into an integer.  
   **Answer**: `int()`

---

#### **Part 3: Short Answer Questions**

1. **What is a lambda function? Provide an example.**  
   **Answer**: A lambda function is an anonymous function in Python defined using the `lambda` keyword. It can have any number of arguments but only one expression.  
   **Example**:  
   ```python
   square = lambda x: x * x
   print(square(5))  # Output: 25
   ```

2. **What is the difference between a list and a tuple in Python?**  
   **Answer**: A list is mutable (can be modified after creation), whereas a tuple is immutable (cannot be modified after creation). Lists are defined using square brackets `[]`, and tuples are defined using parentheses `()`.

3. **What is the purpose of the `self` parameter in Python classes?**  
   **Answer**: The `self` parameter represents the instance of the class and is used to access attributes and methods within the class. It must be the first parameter of any method in the class.

4. **What does the `pass` statement do in Python?**  
   **Answer**: The `pass` statement is a placeholder and does nothing. It is used when a statement is required syntactically but no action is needed.

5. **What is the difference between `==` and `is` in Python?**  
   **Answer**: `==` checks for value equality (whether two objects have the same value), while `is` checks for object identity (whether two objects are the same in memory).

---

#### **Part 4: Coding Questions**

1. **Write a Python function to reverse a string.**
   ```python
   def reverse_string(s):
       return s[::-1]
   
   # Test case
   print(reverse_string("hello"))  # Output: 'olleh'
   ```

2. **Write a Python class `Circle` with a method to calculate the area.**
   ```python
   import math
   
   class Circle:
       def __init__(self, radius):
           self.radius = radius
       
       def area(self):
           return math.pi * self.radius ** 2
   
   # Test case
   circle = Circle(5)
   print(circle.area())  # Output: 78.53981633974483
   ```

3. **Write a Python script to raise a `ValueError` if a negative number is passed to the function.**
   ```python
   def check_positive(n):
       if n < 0:
           raise ValueError("Negative number not allowed")
       return n
   
   # Test case
   try:
       check_positive(-5)
   except ValueError as e:
       print(e)  # Output: 'Negative number not allowed'
   ```

---

#### **Part 5: Object-Oriented Programming (OOP) and Pytest**

1. **Create a class `Person` and write a pytest function to test the object creation.**

   ```python
   # person.py
   class Person:
       def __init__(self, name, age):
           self.name = name
           self.age = age
       
       def greet(self):
           return f"Hello, my name is {self.name} and I am {self.age} years old."
   ```

   ```python
   # test_person.py
   import pytest
   from person import Person
   
   def test_person_creation():
       p = Person("Alice", 30)
       assert p.name == "Alice"
       assert p.age == 30
       assert p.greet() == "Hello, my name is Alice and I am 30 years old."
   ```

---

#### **Part 6: File System Operations**

1. **Write Python code to open a file, read its content, and print it line by line.**
   ```python
   with open('example.txt', 'r') as file:
       for line in file:
           print(line.strip())
   ```

2. **Write Python code to create a file and write some text into it.**
   ```python
   with open('output.txt', 'w') as file:
       file.write("This is an example text.")
   ```

---

#### **Part 7: HTTP Requests and BeautifulSoup**

1. **Use the `httpx` library to make a GET request to an API.**
   ```python
   import httpx
   
   response = httpx.get('https://jsonplaceholder.typicode.com/posts/1')
   print(response.json())
   ```

2. **Use BeautifulSoup to extract all quotes from a webpage (`https://quotes.toscrape.com/`).**
   ```python
   import httpx
   from bs4 import BeautifulSoup
   
   response = httpx.get('https://quotes.toscrape.com/')
   soup = BeautifulSoup(response.text, 'html.parser')
   
   quotes = soup.select('.quote')
   for quote in quotes:
       print(quote.find('span', class_='text').get_text())
   ```

---

### **Sample Exam Problems with Solutions**

1. **What will the following code output?**
   ```python
   for i in range(1, 4):
       print(i ** 2, end=', ')
   ```
   - **Answer**: `1, 4, 9,`

2. **What is the output of the following one-liner?**
   ```python
   print([x for x in range(5) if x % 2 == 0])
   ```
   - **Answer**: `[0, 2, 4]`

3. **Fill in the blank:** The `__________` method in a class defines the string representation of the object.  
   **Answer**: `__str__`

4. **What is the output of this code?**
   ```python
   def f(x):
       if x > 5:
           return True
       else:
           return False
   print(f(10))
   ```
   - **Answer**: `True`

---

Absolutely! Let's create a **full class** with its methods and attributes, and then write a corresponding **pytest** file that thoroughly tests the class. I'll break down everything step-by-step and cover all the essential parts.

### **Class: BankAccount**

This class will model a bank account, with attributes like `account_holder` and `balance`. It will have methods for depositing, withdrawing, and checking the account balance. The pytest file will include tests for all methods.

---

### **Step 1: Define the Class**

```python
# bank_account.py

class BankAccount:
    def __init__(self, account_holder, balance=0):
        """
        Initialize a BankAccount object.

        Parameters:
        account_holder (str): The name of the account holder.
        balance (float): The starting balance. Defaults to 0.
        """
        self.account_holder = account_holder
        self.balance = balance

    def deposit(self, amount):
        """
        Deposit money into the account.

        Parameters:
        amount (float): The amount to deposit.
        
        Raises:
        ValueError: If the amount is less than or equal to 0.
        """
        if amount <= 0:
            raise ValueError("Deposit amount must be greater than 0.")
        self.balance += amount

    def withdraw(self, amount):
        """
        Withdraw money from the account.

        Parameters:
        amount (float): The amount to withdraw.
        
        Raises:
        ValueError: If the amount is greater than the balance or less than 0.
        """
        if amount <= 0:
            raise ValueError("Withdrawal amount must be greater than 0.")
        if amount > self.balance:
            raise ValueError("Insufficient balance.")
        self.balance -= amount

    def get_balance(self):
        """
        Returns the current balance of the account.
        """
        return self.balance

    def __str__(self):
        """
        Returns a string representation of the account.
        """
        return f"BankAccount({self.account_holder}, balance={self.balance})"
```

---

### **Step 2: Pytest for BankAccount**

Next, let's write tests using **pytest** to cover all the functionality of the `BankAccount` class. These tests will verify that deposits, withdrawals, and balance checks behave as expected, including checking for errors.

```python
# test_bank_account.py

import pytest
from bank_account import BankAccount

# Pytest to test the initialization of the class
def test_initialization():
    account = BankAccount("Alice", 100)
    assert account.account_holder == "Alice"
    assert account.get_balance() == 100

# Pytest to test deposit functionality
def test_deposit():
    account = BankAccount("Bob", 50)
    account.deposit(50)
    assert account.get_balance() == 100

# Pytest to check if deposit raises ValueError for negative amounts
def test_deposit_negative_amount():
    account = BankAccount("Bob", 50)
    with pytest.raises(ValueError, match="Deposit amount must be greater than 0."):
        account.deposit(-50)

# Pytest to test withdrawal functionality
def test_withdraw():
    account = BankAccount("Alice", 100)
    account.withdraw(50)
    assert account.get_balance() == 50

# Pytest to check if withdrawal raises ValueError for insufficient balance
def test_withdraw_insufficient_balance():
    account = BankAccount("Alice", 50)
    with pytest.raises(ValueError, match="Insufficient balance."):
        account.withdraw(100)

# Pytest to check if withdrawal raises ValueError for negative amounts
def test_withdraw_negative_amount():
    account = BankAccount("Alice", 50)
    with pytest.raises(ValueError, match="Withdrawal amount must be greater than 0."):
        account.withdraw(-10)

# Pytest to test string representation of BankAccount class
def test_str_representation():
    account = BankAccount("Charlie", 150)
    assert str(account) == "BankAccount(Charlie, balance=150)"
```

---




### **Probable Exam Questions Based on This Example**

1. **Define and implement a class `BankAccount` with methods for depositing and withdrawing money. Make sure to handle invalid deposits and withdrawals.**
   - Expected: A well-defined class with methods and error handling.
   
2. **Write pytest tests to verify the correctness of the `deposit()` and `withdraw()` methods of the `BankAccount` class. Ensure that the tests raise exceptions for invalid operations.**
   - Expected: A set of pytest tests covering normal and edge cases.

3. **Explain the role of the `__str__()` method in a Python class.**
   - Answer: The `__str__()` method returns a string representation of the object, used for printing the object in a human-readable form.

4. **How does pytest handle exceptions in tests, and how can you ensure an exception is raised in a specific scenario?**
   - Answer: Pytest uses `pytest.raises()` to assert that a specific exception is raised during the execution of a code block.

