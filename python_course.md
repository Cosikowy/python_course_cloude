# Extended Python Learning Path: Variables & Flow Control

I'll expand each module to include 10 exercises, providing a more comprehensive learning path for your students.

## Level 1: Functional Programming Approach

### Module 1: Variable Types & Basic Manipulation

**Exercise 1: Number Variables**
```python
# Have students calculate area and perimeter of shapes
def calculate_rectangle_area(length, width):
    return length * width

def calculate_circle_area(radius):
    return 3.14 * radius * radius

def calculate_triangle_area(base, height):
    return 0.5 * base * height
```

**Exercise 2: String Manipulation**
```python
# String operations
def greet_user(name):
    return "Hello, " + name + "!"

def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count

def reverse_string(text):
    return text[::-1]
```

**Exercise 3: List Operations**
```python
# List manipulation
def find_maximum(numbers):
    return max(numbers)

def filter_even_numbers(numbers):
    return [num for num in numbers if num % 2 == 0]

def calculate_average(numbers):
    if not numbers:
        return 0
    return sum(numbers) / len(numbers)
```

**Exercise 4: Dictionary Manipulation**
```python
# Dictionary operations
def create_student_record(name, age, subjects):
    return {"name": name, "age": age, "subjects": subjects}

def update_grade(student_record, subject, grade):
    if "grades" not in student_record:
        student_record["grades"] = {}
    student_record["grades"][subject] = grade
    return student_record

def get_student_average(student_record):
    if "grades" not in student_record or not student_record["grades"]:
        return 0
    grades = student_record["grades"].values()
    return sum(grades) / len(grades)
```

**Exercise 5: Type Conversion**
```python
def convert_to_integers(string_numbers):
    return [int(num) for num in string_numbers]

def format_price(price):
    return f"${price:.2f}"

def extract_numbers(text):
    result = []
    current_number = ""
    for char in text:
        if char.isdigit() or char == '.':
            current_number += char
        elif current_number:
            try:
                if '.' in current_number:
                    result.append(float(current_number))
                else:
                    result.append(int(current_number))
                current_number = ""
            except ValueError:
                current_number = ""
    
    if current_number:
        try:
            if '.' in current_number:
                result.append(float(current_number))
            else:
                result.append(int(current_number))
        except ValueError:
            pass
            
    return result
```

**Exercise 6: Tuples and Sets**
```python
def create_coordinate(x, y):
    return (x, y)

def calculate_distance(point1, point2):
    return ((point2[0] - point1[0])**2 + (point2[1] - point1[1])**2)**0.5

def find_unique_elements(items):
    return list(set(items))

def count_unique_words(text):
    words = text.lower().split()
    return len(set(words))
```

**Exercise 7: Boolean Logic**
```python
def is_leap_year(year):
    return (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0)

def check_password_strength(password):
    has_digit = any(char.isdigit() for char in password)
    has_upper = any(char.isupper() for char in password)
    has_lower = any(char.islower() for char in password)
    has_special = any(not char.isalnum() for char in password)
    is_long_enough = len(password) >= 8
    
    return all([has_digit, has_upper, has_lower, has_special, is_long_enough])

def is_valid_email(email):
    if '@' not in email:
        return False
    
    username, domain = email.split('@')
    if not username or not domain:
        return False
    
    if '.' not in domain:
        return False
        
    domain_parts = domain.split('.')
    if len(domain_parts) < 2 or not all(domain_parts):
        return False
        
    return True
```

**Exercise 8: Working with Date and Time**
```python
from datetime import datetime, timedelta

def format_date(date_obj):
    return date_obj.strftime("%A, %B %d, %Y")

def days_between_dates(date1, date2):
    delta = abs(date2 - date1)
    return delta.days

def add_working_days(start_date, num_days):
    # Add working days (excluding weekends)
    current_date = start_date
    working_days_added = 0
    
    while working_days_added < num_days:
        current_date += timedelta(days=1)
        if current_date.weekday() < 5:  # Monday to Friday (0-4)
            working_days_added += 1
            
    return current_date
```

**Exercise 9: File Handling Basics**
```python
def read_file_lines(filename):
    with open(filename, 'r') as file:
        return file.readlines()

def count_words_in_file(filename):
    with open(filename, 'r') as file:
        content = file.read()
        words = content.split()
        return len(words)

def save_data_to_file(data, filename):
    with open(filename, 'w') as file:
        file.write(data)
    return f"Data saved to {filename}"
```

**Exercise 10: Advanced String Formatting**
```python
def format_name_badge(first_name, last_name, job_title):
    return f"{first_name} {last_name}\n{job_title}"

def create_table_row(columns, widths):
    row = "|"
    for i, col in enumerate(columns):
        row += f" {col:{widths[i]}} |"
    return row

def format_shopping_receipt(items, prices, quantities):
    receipt = "Item                 Qty   Price    Total\n"
    receipt += "----------------------------------------\n"
    
    total_cost = 0
    for i in range(len(items)):
        item_total = prices[i] * quantities[i]
        total_cost += item_total
        receipt += f"{items[i]:<20} {quantities[i]:>3}  ${prices[i]:>6.2f}  ${item_total:>6.2f}\n"
    
    receipt += "----------------------------------------\n"
    receipt += f"Total:                          ${total_cost:>6.2f}"
    
    return receipt
```

### Module 2: Flow Control in Functions

**Exercise 1: If Statements**
```python
# Grade calculator exercise
def determine_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    elif score >= 70:
        return "C"
    elif score >= 60:
        return "D"
    else:
        return "F"

def can_vote(age, citizenship_years):
    if age >= 18 and citizenship_years >= 5:
        return True
    else:
        return False

def recommend_clothing(temperature):
    if temperature >= 85:
        return "It's hot! Wear shorts and a t-shirt."
    elif temperature >= 70:
        return "It's warm. Wear light clothing."
    elif temperature >= 50:
        return "It's cool. Consider a light jacket."
    elif temperature >= 32:
        return "It's cold. Wear a coat."
    else:
        return "It's freezing! Wear a heavy coat, hat, and gloves."
```

**Exercise 2: For Loops**
```python
# Calculate factorial
def calculate_factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

# Find prime numbers
def find_primes_up_to(n):
    primes = []
    for num in range(2, n + 1):
        is_prime = True
        for i in range(2, int(num**0.5) + 1):
            if num % i == 0:
                is_prime = False
                break
        if is_prime:
            primes.append(num)
    return primes

def sum_even_numbers(numbers):
    total = 0
    for num in numbers:
        if num % 2 == 0:
            total += num
    return total
```

**Exercise 3: While Loops**
```python
# Guessing game logic
def simulate_guessing_game(secret_number, max_attempts):
    attempts = 0
    history = []
    
    while attempts < max_attempts:
        # In a real game, input would be taken from user
        # Here we're just showing the logic
        guess = int(input("Enter your guess: "))
        attempts += 1
        history.append(guess)
        
        if guess == secret_number:
            return {"success": True, "attempts": attempts, "history": history}
        elif guess < secret_number:
            print("Too low!")
        else:
            print("Too high!")
            
    return {"success": False, "attempts": attempts, "history": history}

def find_digit_sum(number):
    total = 0
    
    while number > 0:
        total += number % 10
        number //= 10
        
    return total

def countdown_to_launch(start):
    countdown = []
    
    while start > 0:
        countdown.append(start)
        start -= 1
        
    countdown.append("Liftoff!")
    return countdown
```

**Exercise 4: Nested Loops and Conditional Logic**
```python
# Print a pattern based on conditions
def print_pattern(rows):
    result = []
    for i in range(1, rows + 1):
        line = ""
        for j in range(1, i + 1):
            if j % 2 == 0:
                line += "O "
            else:
                line += "X "
        result.append(line)
    return result

def create_multiplication_table(size):
    table = []
    for i in range(1, size + 1):
        row = []
        for j in range(1, size + 1):
            row.append(i * j)
        table.append(row)
    return table

def find_common_elements(list1, list2):
    common = []
    for item1 in list1:
        for item2 in list2:
            if item1 == item2 and item1 not in common:
                common.append(item1)
    return common
```

**Exercise 5: Break and Continue Statements**
```python
def find_first_negative(numbers):
    for num in numbers:
        if num < 0:
            return num
    return None

def sum_until_negative(numbers):
    total = 0
    for num in numbers:
        if num < 0:
            break
        total += num
    return total

def skip_multiples_of_three(start, end):
    result = []
    for num in range(start, end + 1):
        if num % 3 == 0:
            continue
        result.append(num)
    return result
```

**Exercise 6: Function Returns and Early Exits**
```python
def divide_safely(a, b):
    if b == 0:
        return "Error: Division by zero"
    return a / b

def validate_username(username):
    if len(username) < 3:
        return "Username too short"
    if len(username) > 20:
        return "Username too long"
    if not username.isalnum():
        return "Username can only contain letters and numbers"
    return "Username is valid"

def calculate_discount(price, membership_level):
    if membership_level == "platinum":
        return price * 0.2
    elif membership_level == "gold":
        return price * 0.15
    elif membership_level == "silver":
        return price * 0.1
    else:
        return 0
```

**Exercise 7: List Comprehensions**
```python
def squares_of_numbers(numbers):
    return [num ** 2 for num in numbers]

def filter_strings_by_length(strings, min_length):
    return [s for s in strings if len(s) >= min_length]

def extract_initials(full_names):
    return [name.split()[0][0] + name.split()[1][0] for name in full_names]
```

**Exercise 8: Dictionary Comprehensions**
```python
def create_letter_counts(text):
    return {char: text.count(char) for char in set(text)}

def create_number_square_dict(n):
    return {num: num**2 for num in range(1, n+1)}

def filter_dict_by_value(input_dict, threshold):
    return {k: v for k, v in input_dict.items() if v >= threshold}
```

**Exercise 9: Recursion Basics**
```python
def recursive_factorial(n):
    if n <= 1:
        return 1
    return n * recursive_factorial(n-1)

def recursive_fibonacci(n):
    if n <= 0:
        return 0
    if n == 1:
        return 1
    return recursive_fibonacci(n-1) + recursive_fibonacci(n-2)

def recursive_sum(numbers):
    if not numbers:
        return 0
    return numbers[0] + recursive_sum(numbers[1:])
```

**Exercise 10: Advanced Flow Control**
```python
def fizzbuzz(n):
    result = []
    for i in range(1, n+1):
        if i % 3 == 0 and i % 5 == 0:
            result.append("FizzBuzz")
        elif i % 3 == 0:
            result.append("Fizz")
        elif i % 5 == 0:
            result.append("Buzz")
        else:
            result.append(str(i))
    return result

def categorize_numbers(numbers):
    categories = {
        "even": [],
        "odd": [],
        "positive": [],
        "negative": [],
        "zero": []
    }
    
    for num in numbers:
        if num % 2 == 0:
            categories["even"].append(num)
        else:
            categories["odd"].append(num)
            
        if num > 0:
            categories["positive"].append(num)
        elif num < 0:
            categories["negative"].append(num)
        else:
            categories["zero"].append(num)
            
    return categories

def analyze_text(text):
    if not text:
        return {
            "character_count": 0,
            "word_count": 0,
            "sentence_count": 0,
            "uppercase_count": 0,
            "lowercase_count": 0,
            "digit_count": 0
        }
        
    words = text.split()
    sentences = 0
    for char in ['.', '!', '?']:
        sentences += text.count(char)
    
    uppercase_count = sum(1 for char in text if char.isupper())
    lowercase_count = sum(1 for char in text if char.islower())
    digit_count = sum(1 for char in text if char.isdigit())
    
    return {
        "character_count": len(text),
        "word_count": len(words),
        "sentence_count": max(1, sentences),
        "uppercase_count": uppercase_count,
        "lowercase_count": lowercase_count,
        "digit_count": digit_count
    }
```

## Level 2: Object-Oriented Programming Approach

### Module 3: Classes and Objects Basics

**Exercise 1: Creating Simple Classes**
```python
# Convert the shape calculations to OOP
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width
        
    def calculate_area(self):
        return self.length * self.width
        
    def calculate_perimeter(self):
        return 2 * (self.length + self.width)
        
    def is_square(self):
        return self.length == self.width
```

**Exercise 2: Circle Class**
```python
class Circle:
    def __init__(self, radius):
        self.radius = radius
        
    def calculate_area(self):
        return 3.14159 * self.radius ** 2
        
    def calculate_circumference(self):
        return 2 * 3.14159 * self.radius
        
    def calculate_diameter(self):
        return 2 * self.radius
```

**Exercise 3: String and Data Processing with Classes**
```python
# Text analyzer class
class TextAnalyzer:
    def __init__(self, text):
        self.text = text
        
    def count_words(self):
        return len(self.text.split())
        
    def count_vowels(self):
        vowels = "aeiouAEIOU"
        count = 0
        for char in self.text:
            if char in vowels:
                count += 1
        return count
        
    def find_most_common_word(self):
        words = self.text.lower().split()
        word_count = {}
        for word in words:
            if word in word_count:
                word_count[word] += 1
            else:
                word_count[word] = 1
        return max(word_count, key=word_count.get)
        
    def get_word_frequency(self):
        words = self.text.lower().split()
        word_count = {}
        for word in words:
            if word in word_count:
                word_count[word] += 1
            else:
                word_count[word] = 1
        return word_count
```

**Exercise 4: Calculator Class**
```python
class Calculator:
    def __init__(self):
        self.result = 0
        self.history = []
        
    def add(self, value):
        self.result += value
        self.history.append(f"Added {value}")
        return self.result
        
    def subtract(self, value):
        self.result -= value
        self.history.append(f"Subtracted {value}")
        return self.result
        
    def multiply(self, value):
        self.result *= value
        self.history.append(f"Multiplied by {value}")
        return self.result
        
    def divide(self, value):
        if value == 0:
            self.history.append("Division by zero error")
            return "Error"
        self.result /= value
        self.history.append(f"Divided by {value}")
        return self.result
        
    def clear(self):
        self.result = 0
        self.history.append("Cleared")
        return self.result
        
    def get_history(self):
        return self.history
```

**Exercise 5: Shopping Cart Class**
```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price
        
    def __str__(self):
        return f"{self.name}: ${self.price:.2f}"

class ShoppingCart:
    def __init__(self):
        self.items = {}  # Product: quantity
        
    def add_item(self, product, quantity=1):
        if product in self.items:
            self.items[product] += quantity
        else:
            self.items[product] = quantity
            
    def remove_item(self, product, quantity=1):
        if product not in self.items:
            return False
            
        if self.items[product] <= quantity:
            del self.items[product]
        else:
            self.items[product] -= quantity
        return True
        
    def get_total(self):
        total = 0
        for product, quantity in self.items.items():
            total += product.price * quantity
        return total
        
    def get_item_count(self):
        return sum(self.items.values())
        
    def clear(self):
        self.items = {}
        
    def get_receipt(self):
        receipt = "Shopping Cart:\n"
        receipt += "--------------------\n"
        
        for product, quantity in self.items.items():
            subtotal = product.price * quantity
            receipt += f"{product.name} x{quantity}: ${subtotal:.2f}\n"
            
        receipt += "--------------------\n"
        receipt += f"Total: ${self.get_total():.2f}"
        
        return receipt
```

**Exercise 6: TodoList Class**
```python
from datetime import datetime

class Task:
    def __init__(self, description, priority="normal"):
        self.description = description
        self.priority = priority
        self.completed = False
        self.created_date = datetime.now()
        self.completed_date = None
        
    def complete(self):
        self.completed = True
        self.completed_date = datetime.now()
        
    def __str__(self):
        status = "✓" if self.completed else "☐"
        return f"{status} [{self.priority}] {self.description}"

class TodoList:
    def __init__(self, name):
        self.name = name
        self.tasks = []
        
    def add_task(self, task):
        self.tasks.append(task)
        
    def complete_task(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index].complete()
            return True
        return False
        
    def remove_task(self, index):
        if 0 <= index < len(self.tasks):
            del self.tasks[index]
            return True
        return False
        
    def get_pending_tasks(self):
        return [task for task in self.tasks if not task.completed]
        
    def get_completed_tasks(self):
        return [task for task in self.tasks if task.completed]
        
    def get_priority_tasks(self, priority):
        return [task for task in self.tasks if task.priority == priority]
        
    def __str__(self):
        result = f"=== {self.name} ===\n"
        
        for i, task in enumerate(self.tasks):
            result += f"{i+1}. {task}\n"
            
        pending = len(self.get_pending_tasks())
        completed = len(self.get_completed_tasks())
        
        result += f"\nTasks: {len(self.tasks)} total, {pending} pending, {completed} completed"
        return result
```

**Exercise 7: Temperature Converter Class**
```python
class TemperatureConverter:
    @staticmethod
    def celsius_to_fahrenheit(celsius):
        return (celsius * 9/5) + 32
        
    @staticmethod
    def fahrenheit_to_celsius(fahrenheit):
        return (fahrenheit - 32) * 5/9
        
    @staticmethod
    def celsius_to_kelvin(celsius):
        return celsius + 273.15
        
    @staticmethod
    def kelvin_to_celsius(kelvin):
        return kelvin - 273.15
        
    @staticmethod
    def fahrenheit_to_kelvin(fahrenheit):
        celsius = TemperatureConverter.fahrenheit_to_celsius(fahrenheit)
        return TemperatureConverter.celsius_to_kelvin(celsius)
        
    @staticmethod
    def kelvin_to_fahrenheit(kelvin):
        celsius = TemperatureConverter.kelvin_to_celsius(kelvin)
        return TemperatureConverter.celsius_to_fahrenheit(celsius)
        
    def convert(self, value, from_unit, to_unit):
        from_unit = from_unit.lower()
        to_unit = to_unit.lower()
        
        if from_unit == to_unit:
            return value
            
        if from_unit == "celsius" and to_unit == "fahrenheit":
            return self.celsius_to_fahrenheit(value)
        elif from_unit == "celsius" and to_unit == "kelvin":
            return self.celsius_to_kelvin(value)
        elif from_unit == "fahrenheit" and to_unit == "celsius":
            return self.fahrenheit_to_celsius(value)
        elif from_unit == "fahrenheit" and to_unit == "kelvin":
            return self.fahrenheit_to_kelvin(value)
        elif from_unit == "kelvin" and to_unit == "celsius":
            return self.kelvin_to_celsius(value)
        elif from_unit == "kelvin" and to_unit == "fahrenheit":
            return self.kelvin_to_fahrenheit(value)
        else:
            return f"Conversion from {from_unit} to {to_unit} not supported"
```

**Exercise 8: Contact Management Class**
```python
class Contact:
    def __init__(self, name, email, phone=None):
        self.name = name
        self.email = email
        self.phone = phone
        
    def update_email(self, new_email):
        self.email = new_email
        
    def update_phone(self, new_phone):
        self.phone = new_phone
        
    def __str__(self):
        phone_display = self.phone if self.phone else "N/A"
        return f"{self.name} | {self.email} | {phone_display}"

class ContactManager:
    def __init__(self):
        self.contacts = []
        
    def add_contact(self, contact):
        self.contacts.append(contact)
        
    def find_contact_by_name(self, name):
        matches = []
        for contact in self.contacts:
            if name.lower() in contact.name.lower():
                matches.append(contact)
        return matches
        
    def find_contact_by_email(self, email):
        for contact in self.contacts:
            if contact.email.lower() == email.lower():
                return contact
        return None
        
    def delete_contact(self, email):
        for i, contact in enumerate(self.contacts):
            if contact.email.lower() == email.lower():
                del self.contacts[i]
                return True
        return False
        
    def update_contact(self, email, new_name=None, new_email=None, new_phone=None):
        contact = self.find_contact_by_email(email)
        if not contact:
            return False
            
        if new_name:
            contact.name = new_name
        if new_email:
            contact.email = new_email
        if new_phone:
            contact.phone = new_phone
            
        return True
        
    def get_all_contacts(self):
        return self.contacts
        
    def __str__(self):
        result = "Contact List:\n"
        result += "------------\n"
        
        for i, contact in enumerate(self.contacts):
            result += f"{i+1}. {contact}\n"
            
        result += f"\nTotal Contacts: {len(self.contacts)}"
        return result
```

**Exercise 9: Banking System Classes**
```python
class BankAccount:
    def __init__(self, account_number, holder_name, balance=0):
        self.account_number = account_number
        self.holder_name = holder_name
        self.balance = balance
        self.transaction_history = []
        
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transaction_history.append({"type": "deposit", "amount": amount, "date": "today"})
            return True
        return False
        
    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            self.transaction_history.append({"type": "withdrawal", "amount": amount, "date": "today"})
            return True
        return False
        
    def get_balance(self):
        return self.balance
        
    def get_transaction_history(self):
        return self.transaction_history
        
    def __str__(self):
        return f"Account: {self.account_number} | Holder: {self.holder_name} | Balance: ${self.balance:.2f}"

class SavingsAccount(BankAccount):
    def __init__(self, account_number, holder_name, balance=0, interest_rate=0.01):
        super().__init__(account_number, holder_name, balance)
        self.interest_rate = interest_rate
        
    def add_interest(self):
        interest = self.balance * self.interest_rate
        self.balance += interest
        self.transaction_history.append({"type": "interest", "amount": interest, "date": "today"})
        return interest
        
    def __str__(self):
        return f"{super().__str__()} | Interest Rate: {self.interest_rate:.1%}"

class CheckingAccount(BankAccount):
    def __init__(self, account_number, holder_name, balance=0, overdraft_limit=100):
        super().__init__(account_number, holder_name, balance)
        self.overdraft_limit = overdraft_limit
        
    def withdraw(self, amount):
        if amount > 0 and amount <= (self.balance + self.overdraft_limit):
            self.balance -= amount
            self.transaction_history.append({"type": "withdrawal", "amount": amount, "date": "today"})
            return True
        return False
        
    def __str__(self):
        return f"{super().__str__()} | Overdraft Limit: ${self.overdraft_limit:.2f}"
```

**Exercise 10: Inventory Management System**
```python
class Product:
    def __init__(self, product_id, name, price, quantity=0):
        self.product_id = product_id
        self.name = name
        self.price = price
        self.quantity = quantity
        
    def add_stock(self, amount):
        if amount > 0:
            self.quantity += amount
            return True
        return False
        
    def remove_stock(self, amount):
        if 0 < amount <= self.quantity:
            self.quantity -= amount
            return True
        return False
        
    def update_price(self, new_price):
        if new_price >= 0:
            self.price = new_price
            return True
        return False
        
    def get_value(self):
        return self.price * self.quantity
        
    def __str__(self):
        return f"{self.product_id}: {self.name} - ${self.price:.2f} ({self.quantity} in stock)"

class Inventory:
    def __init__(self):
        self.products = {}  # product_id: Product
        
    def add_product(self, product):
        if product.product_id not in self.products:
            self.products[product.product_id] = product
            return True
        return False
        
    def remove_product(self, product_id):
        if product_id in self.products:
            del self.products[product_id]
            return True
        return False
        
    def get_product(self, product_id):
        return self.products.get(product_id)
        
    def search_products(self, name):
        results = []
        for product in self.products.values():
            if name.lower() in product.name.lower():
                results.append(product)
        return results
        
    def update_stock(self, product_id, quantity_change):
        product = self.get_product(product_id)
        if not product:
            return False
            
        if quantity_change > 0:
            return product.add_stock(quantity_change)
        elif quantity_change < 0:
            return product

### Module 4: Object-Oriented Flow Control

**Exercise 1: Student Grading System**
```python
class Student:
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.grades = {}
        
    def add_grade(self, subject, score):
        self.grades[subject] = score
        
    def get_grade_letter(self, subject):
        if subject not in self.grades:
            return "No grade available"
            
        score = self.grades[subject]
        if score >= 90:
            return "A"
        elif score >= 80:
            return "B"
        elif score >= 70:
            return "C"
        elif score >= 60:
            return "D"
        else:
            return "F"
            
    def calculate_gpa(self):
        if not self.grades:
            return 0.0
            
        total_points = 0
        for score in self.grades.values():
            if score >= 90:
                total_points += 4.0
            elif score >= 80:
                total_points += 3.0
            elif score >= 70:
                total_points += 2.0
            elif score >= 60:
                total_points += 1.0
                
        return total_points / len(self.grades)
        
    def get_highest_grade(self):
        if not self.grades:
            return None
        return max(self.grades.values())
        
    def get_lowest_grade(self):
        if not self.grades:
            return None
        return min(self.grades.values())
```

**Exercise 2: Bank Account Management**
```python
class BankAccount:
    def __init__(self, account_number, holder_name, balance=0):
        self.account_number = account_number
        self.holder_name = holder_name
        self.balance = balance
        self.transaction_history = []
        
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transaction_history.append(f"Deposit: +${amount}")
            return True
        return False
        
    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            self.transaction_history.append(f"Withdrawal: -${amount}")
            return True
        return False
        
    def get_statement(self):
        statement = f"Account: {self.account_number}\nHolder: {self.holder_name}\nBalance: ${self.balance}\n"
        statement += "Recent Transactions:\n"
        
        for transaction in self.transaction_history[-5:]:
            statement += f"- {transaction}\n"
            
        return statement
        
    def transfer(self, target_account, amount):
        if self.withdraw(amount):
            if target_account.deposit(amount):
                self.transaction_history[-1] += f" (Transfer to {target_account.account_number})"
                return True
            else:
                # Rollback if deposit fails
                self.deposit(amount)
                return False
        return False
```

**Exercise 3: Simple Game with OOP**
```python
import random

class GuessingGame:
    def __init__(self, min_num=1, max_num=100, max_attempts=10):
        self.min_num = min_num
        self.max_num = max_num
        self.max_attempts = max_attempts
        self.secret_number = random.randint(min_num, max_num)
        self.attempts = 0
        self.guess_history = []
        self.game_over = False
        
    def make_guess(self, guess):
        if self.game_over:
            return "Game is already over!"
            
        self.attempts += 1
        self.guess_history.append(guess)
        
        if guess == self.secret_number:
            self.game_over = True
            return f"Correct! You found the number in {self.attempts} attempts."
        elif self.attempts >= self.max_attempts:
            self.game_over = True
            return f"Game over! You ran out of attempts. The number was {self.secret_number}."
        elif guess < self.secret_number:
            return "Too low! Try again."
        else:
            return "Too high! Try again."
            
    def get_statistics(self):
        if not self.game_over:
            return "Game is still in progress!"
            
        return {
            "attempts": self.attempts,
            "success": self.secret_number in self.guess_history,
            "history": self.guess_history
        }
        
    def provide_hint(self):
        if self.game_over:
            return "Game is already over!"
            
        if not self.guess_history:
            return f"The number is between {self.min_num} and {self.max_num}."
            
        closest_guess = min(self.guess_history, key=lambda x: abs(x - self.secret_number))
        return f"Your closest guess was {closest_guess}."
```

**Exercise 4: Library Management System**
```python
class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.is_available = True
        
    def __str__(self):
        status = "Available" if self.is_available else "Checked Out"
        return f"{self.title} by {self.author} ({status})"

class Library:
    def __init__(self, name):
        self.name = name
        self.books = {}
        
    def add_book(self, book):
        self.books[book.isbn] = book
        
    def find_book_by_title(self, title):
        matches = []
        for book in self.books.values():
            if title.lower() in book.title.lower():
                matches.append(book)
        return matches
        
    def check_out_book(self, isbn):
        if isbn in self.books:
            book = self.books[isbn]
            if book.is_available:
                book.is_available = False
                return f"Successfully checked out: {book.title}"
            else:
                return f"Sorry, {book.title} is already checked out."
        else:
            return "Book not found in library."
            
    def return_book(self, isbn):
        if isbn in self.books:
            book = self.books[isbn]
            if not book.is_available:
                book.is_available = True
                return f"Successfully returned: {book.title}"
            else:
                return f"Error: {book.title} was not checked out."
        else:
            return "Book not found in library."
```

**Exercise 5: Command Pattern Implementation**
```python
class Command:
    def execute(self):
        pass
    
    def undo(self):
        pass

class Calculator:
    def __init__(self):
        self.value = 0
        self.history = []
    
    def set_value(self, value):
        self.value = value
    
    def execute_command(self, command):
        self.history.append(command)
        command.execute()
    
    def undo_last_command(self):
        if self.history:
            last_command = self.history.pop()
            last_command.undo()
            return True
        return False

class AddCommand(Command):
    def __init__(self, calculator, operand):
        self.calculator = calculator
        self.operand = operand
    
    def execute(self):
        self.calculator.set_value(self.calculator.value + self.operand)
    
    def undo(self):
        self.calculator.set_value(self.calculator.value - self.operand)

class SubtractCommand(Command):
    def __init__(self, calculator, operand):
        self.calculator = calculator
        self.operand = operand
    
    def execute(self):
        self.calculator.set_value(self.calculator.value - self.operand)
    
    def undo(self):
        self.calculator.set_value(self.calculator.value + self.operand)

class MultiplyCommand(Command):
    def __init__(self, calculator, operand):
        self.calculator = calculator
        self.operand = operand
        self.previous_value = calculator.value
    
    def execute(self):
        self.previous_value = self.calculator.value
        self.calculator.set_value(self.calculator.value * self.operand)
    
    def undo(self):
        self.calculator.set_value(self.previous_value)
```

**Exercise 6: State Pattern Implementation**
```python
class TrafficLightState:
    def change_state(self, traffic_light):
        pass
    
    def get_state_name(self):
        pass

class RedState(TrafficLightState):
    def change_state(self, traffic_light):
        traffic_light.set_state(GreenState())
    
    def get_state_name(self):
        return "Red"

class YellowState(TrafficLightState):
    def change_state(self, traffic_light):
        traffic_light.set_state(RedState())
    
    def get_state_name(self):
        return "Yellow"

class GreenState(TrafficLightState):
    def change_state(self, traffic_light):
        traffic_light.set_state(YellowState())
    
    def get_state_name(self):
        return "Green"

class TrafficLight:
    def __init__(self):
        self.state = RedState()
    
    def change(self):
        self.state.change_state(self)
        return self.get_state()
    
    def set_state(self, state):
        self.state = state
    
    def get_state(self):
        return self.state.get_state_name()
```

**Exercise 7: Observer Pattern Implementation**
```python
class Subject:
    def __init__(self):
        self._observers = []
    
    def attach(self, observer):
        if observer not in self._observers:
            self._observers.append(observer)
    
    def detach(self, observer):
        try:
            self._observers.remove(observer)
        except ValueError:
            pass
    
    def notify(self, message=None):
        for observer in self._observers:
            observer.update(message)

class Observer:
    def update(self, message):
        pass

class WeatherStation(Subject):
    def __init__(self):
        super().__init__()
        self.temperature = 0
        self.humidity = 0
        self.pressure = 0
    
    def set_measurements(self, temperature, humidity, pressure):
        self.temperature = temperature
        self.humidity = humidity
        self.pressure = pressure
        self.notify()
    
    def get_temperature(self):
        return self.temperature
    
    def get_humidity(self):
        return self.humidity
    
    def get_pressure(self):
        return self.pressure

class TemperatureDisplay(Observer):
    def __init__(self, weather_station):
        self.weather_station = weather_station
        weather_station.attach(self)
    
    def update(self, message=None):
        temperature = self.weather_station.get_temperature()
        return f"Current temperature: {temperature}°C"
```

**Exercise 8: Strategy Pattern Implementation**
```python
class SortStrategy:
    def sort(self, data):
        pass

class BubbleSortStrategy(SortStrategy):
    def sort(self, data):
        # Simple bubble sort implementation
        sorted_data = data.copy()
        n = len(sorted_data)
        for i in range(n):
            for j in range(0, n - i - 1):
                if sorted_data[j] > sorted_data[j + 1]:
                    sorted_data[j], sorted_data[j + 1] = sorted_data[j + 1], sorted_data[j]
        return sorted_data

class QuickSortStrategy(SortStrategy):
    def sort(self, data):
        # Simple quicksort implementation
        if len(data) <= 1:
            return data
        
        sorted_data = data.copy()
        pivot = sorted_data[len(sorted_data) // 2]
        left = [x for x in sorted_data if x < pivot]
        middle = [x for x in sorted_data if x == pivot]
        right = [x for x in sorted_data if x > pivot]
        
        return self.sort(left) + middle + self.sort(right)

class Sorter:
    def __init__(self, strategy=None):
        self.strategy = strategy if strategy else BubbleSortStrategy()
    
    def set_strategy(self, strategy):
        self.strategy = strategy
    
    def sort(self, data):
        return self.strategy.sort(data)
```

**Exercise 9: Decorator Pattern Implementation**
```python
class Coffee:
    def get_cost(self):
        pass
    
    def get_description(self):
        pass

class SimpleCoffee(Coffee):
    def get_cost(self):
        return 2.0
    
    def get_description(self):
        return "Simple coffee"

class CoffeeDecorator(Coffee):
    def __init__(self, decorated_coffee):
        self.decorated_coffee = decorated_coffee
    
    def get_cost(self):
        return self.decorated_coffee.get_cost()
    
    def get_description(self):
        return self.decorated_coffee.get_description()

class Milk(CoffeeDecorator):
    def __init__(self, decorated_coffee):
        super().__init__(decorated_coffee)
    
    def get_cost(self):
        return self.decorated_coffee.get_cost() + 0.5
    
    def get_description(self):
        return self.decorated_coffee.get_description() + ", milk"

class Sugar(CoffeeDecorator):
    def __init__(self, decorated_coffee):
        super().__init__(decorated_coffee)
    
    def get_cost(self):
        return self.decorated_coffee.get_cost() + 0.2
    
    def get_description(self):
        return self.decorated_coffee.get_description() + ", sugar"

class Vanilla(CoffeeDecorator):
    def __init__(self, decorated_coffee):
        super().__init__(decorated_coffee)
    
    def get_cost(self):
        return self.decorated_coffee.get_cost() + 0.7
    
    def get_description(self):
        return self.decorated_coffee.get_description() + ", vanilla"
```

**Exercise 10: Factory Pattern Implementation**
```python
class Vehicle:
    def get_type(self):
        pass
    
    def get_speed(self):
        pass
    
    def get_passenger_capacity(self):
        pass

class Car(Vehicle):
    def get_type(self):
        return "Car"
    
    def get_speed(self):
        return 120
    
    def get_passenger_capacity(self):
        return 5

class Motorcycle(Vehicle):
    def get_type(self):
        return "Motorcycle"
    
    def get_speed(self):
        return 160
    
    def get_passenger_capacity(self):
        return 2

class Bus(Vehicle):
    def get_type(self):
        return "Bus"
    
    def get_speed(self):
        return 80
    
    def get_passenger_capacity(self):
        return 40

class VehicleFactory:
    @staticmethod
    def create_vehicle(vehicle_type):
        if vehicle_type.lower() == "car":
            return Car()
        elif vehicle_type.lower() == "motorcycle":
            return Motorcycle()
        elif vehicle_type.lower() == "bus":
            return Bus()
        else:
            raise ValueError(f"Unknown vehicle type: {vehicle_type}")
```

## Additional Practice Problems

### Level 1: Functional Programming

**Data Manipulation Problems:**
1. Create a function to count the frequency of each word in a text
2. Create a function to convert a list of tuples into a dictionary
3. Create a function to merge two dictionaries
4. Create a function to filter out duplicate values from a list
5. Create a function to sort a list of strings by their length

**File Handling Problems:**
1. Create a function that reads a CSV file and returns a list of dictionaries
2. Create a function that counts the number of lines in a file
3. Create a function that finds and replaces text in a file
4. Create a function that extracts email addresses from a text file
5. Create a function that generates a report from multiple data files

### Level 2: Object-Oriented Programming

**Complex Project Ideas:**
1. Build a text-based adventure game with different character classes
2. Create a simulated stock trading system with buy/sell orders
3. Design a music player with playlists and songs
4. Develop a simple blogging system with posts and comments
5. Build a hotel reservation system with rooms and bookings

**Design Pattern Implementations:**
1. Singleton pattern for a configuration manager
2. Adapter pattern to convert data formats
3. Composite pattern for a file system structure
4. Builder pattern for complex object creation
5. Chain of responsibility for request handling

## Teaching Notes

When using these exercises in your classroom:

1. Start with simple variable manipulation before moving to more complex flow control.
2. Have students work through the Level 1 exercises before introducing OOP concepts.
3. Encourage students to modify and expand existing exercises to reinforce learning.
4. Use pair programming for more complex exercises.
5. Assign mini-projects that combine multiple concepts.

Each exercise builds incrementally on previous ones, allowing students to progressively develop their Python skills. The OOP exercises in particular showcase how to apply flow control within class methods and illustrate common design patterns that students will encounter in real-world applications.

Would you like me to elaborate on any specific type of exercise or provide more examples for a particular concept?