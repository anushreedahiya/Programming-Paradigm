## Restaurant Ordering System (C++)
A console-based Restaurant Ordering System implemented in C++ using Object-Oriented Programming (OOP) concepts.
The system allows users to view a menu, place orders with quantities, delete items from the order, and generate a formatted bill.

### Features
-Display a categorized restaurant menu
-Add multiple items with custom quantities
-Delete items from the current order
-Generate a formatted bill with total cost
-Demonstrates OOP concepts:
  -Inheritance
  -Polymorphism
  -Dynamic memory allocation
-Menu-driven console interface

### System Design
#### 1. Classes Used
-MenuItem (Base Class)
Represents a generic menu item
a. Stores:
-Item name
-Price
-Quantity
b. Functions:
-calculatePrice()
-display()
-Getter and setter methods
#### 2. Derived Classes
-Beverage
-Appetizer
-Dessert
These inherit from MenuItem and allow easy menu categorization.

### Functional Overview
#### 1. Display Menu
Shows all available items with:
-Item number
-Item name
-Price

#### 2. Add Items to Order
-User selects item number
-Enters quantity
-Item is dynamically added to the order list

#### 3. Delete Item from Order
-Removes a selected item from the current order
-Memory is safely deallocated

#### 4. Display Bill
-Shows ordered items
-Displays quantity, price, and total amount

### Sample Menu Categories
1. Beverages
Americano, Latte, Cappuccino, Frappuccino, etc.
2. Desserts
Tiramisu, Cheesecake, Macaron, Strawberry Shortcake
3. Appetizers
Garlic Bread, Onion Rings, Chicken Nuggets, Ratatouille

### How to Run the Program
-Prerequisites
C++ Compiler (GCC / MinGW / Visual Studio)
C++11 or later
-Compile
g++ restaurant_ordering_system.cpp -o restaurant
-Run
./restaurant

### File Structure
Restaurant-Ordering-System/
│
├── restaurant_ordering_system.cpp
├── README.md

### Technologies Used
-Language: C++
-Libraries:
<iostream>
<iomanip>
<string>

### Concepts Demonstrated
1. Object-Oriented Programming (OOP)
2. Inheritance and Polymorphism
3. Dynamic Memory Management (new / delete)
4. Pointers and Pointer-to-Pointer usage
5. Console formatting using iomanip

### Memory Management
-All dynamically allocated objects are properly deleted
-Prevents memory leaks by cleaning:
Menu items
Ordered items
Order array

### Future Enhancements
-Add file-based order storage
-Apply GST / tax calculations
-Improve UI with colors or GUI
-Replace raw pointers with STL containers (vector)
-Add user authentication

Author
Developed as an academic C++ OOP project for understanding class design, inheritance, and memory handling in 3rd semester of Btech.
