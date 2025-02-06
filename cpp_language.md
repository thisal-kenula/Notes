# C++

[C programming ↗](/c_language.md)

- Everything you can do in C can do in C++
## Setup

### Install compiler

Just as C

### Compile code

`cd /path/to/folder`

`g++ -o desired_file_name program.cpp`

`./desired_file_name` to run the code

- Some code might work just in newer C++ versions
    
    For that: `g++ -std=c++11 -o hello hello.cpp`
    
## Syntax

```cpp
//header file which lets us work with input and output objects (like cout)
#include <iostream>
// Means we can use names for objects and variables from standard library
using namespace std;

int main() {
// `cout`: object
cout << "Hello world!"; // prints Hello world!
return 0; // Ends `main` function
}
```

### `using namespace std` can be omitted

```cpp
#include <iostream>

int main() {
    std::cout << "Hello world!"; // instead of `using namespace std`
    return 0;
}
```

- No difference in performance
### `<<`: Insertion operator

inserts `"Hello world!"` into `cout`

### Namespaces
- Kinda like modules in Python. (But not exactly)
- Used to avoid name conflicts

```cpp
namespace Person1 {
    void print() {
        cout << "Print from person 1" << endl;
    }
}

namespace Person2 {
    void print() {
        cout << "Print from person 2" << endl;
    }
}
```

```cpp
int main() {
    Person1::print();  // Calls print() from Person1
    Person2::print();  // Calls print() from Person2
}
```

### `namespace` and `include` compared to Python

```python
import math  # like just **include <math>**
print(math.pi) # math::pi
```

```python
from math import *  # like **using namespace math**
print(pi) # pi
```

## Output

```cpp
// Does't add new line at the end
std::cout << "Hello World!"; 
```

### Numbers are also valid

```cpp
    std::cout << "My age is ";
    std::cout << 20;
    // Prints My age is 20
```

### Mix different types

```cpp
int age = 20;
std::string name = "Thisal";
std::cout << name << " is " << age << " years old.";
```

### Use `\n` or `std::endl` for new line

```cpp
std::cout << "Hello world \n";
std::cout << "I'm leaarning C++";
```

```cpp
// using namespace std;
cout << "Hello world" << endl;
```

### Multiple `<<` operators

```cpp
std::cout << "Hello world" << "\n";
```

## Variables

### Declare

```cpp
int myNum = 15;
// or
int myNum;
myNum = 15;
```

- Multiple variables at once
    
    ```cpp
    int x = 5, y = 6, z = 50;
    //or
    int x, y, z;
    x = y = z = 50;
    ```
    
- When variables are declared but not initialized
    
    ```cpp
    int x; // Uninitialized (Contains garbage value)
    cout << x; // 256908176 (Garbage value)
    ```
    
    - Garbage value = whatever arbitrary values were in the memory at the time of allocation
- identifier = variable name

### Variable types

- Numbers
    - `int`
    - `double` : about 15 digit precision
    - `float`: about 6 digit precision
    - Scientific numbers
        
        ```cpp
        float x = 35e3; // double or int also valid; `E` is also valid
        ```
        
- `char`
    
    ```cpp
    char myGrade = 'A';
    cout << myGrade; // A
    ```
    
    ```cpp
    char myGrade = 66; // in ASCII
    cout << myGrade; // B
    ```
    
- `string`
    - literal string: “some text”
    - To use string object: `#include <string>`
        
        Needs for operations like `"Thisal " + "Kenula"`
        
    - Concatenate
        
        ```cpp
        string firstName = "Thisal ";
        string lastName = "Kenula";
        string fullName = firstName.append(lastName); // firstName also change
        //or
        string fullName = firstName + lastName;
        ```
        
    - Length
        
        ```cpp
        string name = "Thisal";
        cout << "Lenght is: " << name.length(); // Lenght is: 6
        //or
        cout << "Lenght is: " << name.size(); // size is an alias to length
        ```
        
    - As arrays
        
        ```cpp
        string name = "Thisal";
        cout << name[0]; // T
        // or
        cout << name.at(0); // T
        ```
        
        - Print last character
            
            ```cpp
            string name = "Thisal";
            cout << name[name.length() - 1];  //l
            ```
            
        - Change characters by index
            
            ```cpp
            name[0] = 'S';
            cout << name; // Shisal
            ```
            
    - `C`-type Strings
        - Because C is an extension of C++

- `bool`
    
    Values are returned in `1` or `0`
    
    ```cpp
    bool isiPhone = true;
    cout << isiPhone; // 1
    ```
    
    - Boolean expressions
        
        ```cpp
        int x = 10;
        int y = 5;
        cout << (x > y); // 1
        ```
        
### Constants

```cpp
const int minutesPerHour = 60;
```

```cpp
// must be assigned with a value initially
const int minutesPerHour; 
minutesPerHour = 60; // error
```

### Garbage values

```cpp
int x;
cout << x; // Might print garbage values (depends on compiler)

```

### `swap` two values

```cpp
int numbers[] = {1, 2, 3, 4, 5};
swap(numbers[0], numbers[1]); // {2, 1, 3, 4, 5}
```

## Array

- Change and access just like Python

### Arrays are fixed sized(Can’t add or remove)
- Use vector library for dynamic size arrays

### Create

```cpp
string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};
int myNum[3] = {10, 20, 30};
// or just
string cars[] = {"Volvo", "BMW", "Ford", "Mazda"};
int myNum[] = {10, 20, 30};
```

### Out of bounds

```cpp
string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};
cout << cars[4]; // Would print garbage value
```

### Loop through array
- For loop
    
    ```cpp
    int myNumbers[5] = {10, 20, 30, 40, 50};
    for (int i = 0; i < 5; i++) {
        cout << myNumbers[i] << "\n";
    }
    // Or just like C
    ```
    
    ```cpp
    int myNumbers[5] = {10, 20, 30, 40, 50};
    for (int i = 0; i < sizeof(myNumbers) / sizeof(myNumbers[0]); i++) {
        cout << myNumbers[i] << "\n";
    }
    ```
    
- Foreach loop
    
    ```cpp
    string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};
    for (string i : cars) {
        cout << i << "\n";
    }
    ```
    
### Initializing later

```cpp
string cars[5];
cars[0] = "Volvo";
cars[1] = "BMW";
// is valid
```

```cpp
string cars[];
cars[0] = "Volvo";
cars[1] = "BMW";
// is not valid
```

## Operators

`++`: Increment by 1

`--`: Decrement by 1

[Assignment operators](https://www.w3schools.com/cpp/cpp_operators_assignment.asp)

[Comparison operators](https://www.w3schools.com/cpp/cpp_operators_comparison.asp)

- Logical operators
    
    `&&`: and
    
    `||`: or
    
    `!`: not
    
- `++i` vs `i++`
    
    ```cpp
    int i = 10;
    // Pre-increment
    int x = ++i; // increments first and returns updated value
    cout << x; // 11
    ```
    
    ```cpp
    int i = 10;
    // Post-increment
    int x = ++i; // Returns current value before incrementing
    cout << x; // 11
    // Creates temporary copy. Thus **less efficient**
    ```
    
## Input
### `cin`

```cpp
int x;
cout << "Type a number: ";
cin >> x;
cout << "Your number is: " << x;
```

- `x`: Extraction operator
- `cin` considers whitespace as terminating character
    
    ```cpp
    string name;
    cout << "Enter your name: "; 
    cin >> name; // Thisal Kenula
    cout << "Your name is " << name; // Your name is Thisal
    ```
    
### `getline`

```cpp
string name;
cout << "Enter your name: ";
getline(cin, name); // Thisal Kenula
cout << "Your name is " << name; // Your name is Thisal Kenula
```

### Input validation

```cpp
int number;
cout << "Input a number: ";
cin >> number;

if (cin.fail()) {
    cout << "Invalid input!" << endl;
} else {
    cout << "You entered: " << number << endl;
}
```

- If wrong input was provided without input validation, `cin` might enter a failure state. To fix this:
    
    ```cpp
    int number;
    cout << "Input a number: ";
    cin >> number;
    
    if (cin.fail()) {
        **cin.clear(); // Clear the error state
        cin.ignore(numeric_limits<streamsize>::max(), '\n'); // Flush invalid input**
        cout << "Invalid input!" << endl;
        cout << "Input a number: ";
        cin >> number;
    } else {
        cout << "You entered: " << number << endl;
    }
    ```
    
## Math
    
```cpp
cout << max(5, 10); // 10
cout << min(5, 10); // 5
```

- `<cmath>`
    
    ```cpp
    cout << sqrt(64); // 8
    cout << round(2.4); // 2
    cout << log(2); //0.693147
    ```
        
    [C++ Math Reference](https://www.w3schools.com/cpp/cpp_ref_math.asp)
    
## Conditional statements

`if`, `else if`, `else`, `switch`

```cpp
int time = 20;
if (time > 18) {
    cout << "Good evening";
} else {
    cout << "Good afternoon";
}
```

### Ternary operator

```cpp
cout << ((time > 18) ? "Good evening" : "Good afternoon");
```

### `switch`

```cpp
switch (day) {
        case 1:
            cout << "Monday";
            break;
        case 2:
            cout << "Tuesday";
            break;
        case 3:
            cout << "Wednesday";
            break;
        case 4:
            cout << "Thursday";
            break;
    }
```

## Loop

### `while`

```cpp
int i = 0;
    while (i < 5) {
        cout << i << "\n";
        i++;
    }
    // 0 1 2 3 4
```

### `do while`

```cpp
do {
        cout << i << "\n";
        i++;
    }
    while (i < 5);
    // 0 1 2 3 4 5
```

### `for`

```cpp
// for (once; condition(while); everytime)
for (int i = 0; i < 5; i++) {
        cout << i << " ";
}
// 0 1 2 3 4
```

```cpp
for (int i = 0; i < 5;) {
    cout << i << " ";
    i++;
}
// 0 1 2 3 4
```

```cpp
for (int j = 0; j < (N - i); ++j) { // Condition is checked in every iteration
            
}
```

### `foreach`
- Introduced in 2011 (needs a compiler which supports C++11 or later)

```cpp
int myNumbers[5] = {10, 20, 30, 40, 50};
for (int i : myNumbers) {
    cout << i << " ";
}
// 10 20 30 40 50 
```

- Pass by reference is better than creating copies
    
    ```cpp
    for (string& car : cars) {
        cout << car << "\n";
    } 
    // Reference to original elements
    // Changes original elements
    ```
    
    ```cpp
    for (string car : cars) {
        cout << car << "\n";
    }
    // creates a copy for every element
    ```
    
### `break` and `continue` like Python

## Structures(`struct`)

### Declare variable at the same time

```cpp
struct { // Structure declaration
        int myNum;
        string myString;
    } myStructure; // Structure variable

    myStructure.myNum = 1;
    myStructure.myString = "Hey Siri";

    cout << myStructure.myNum;
```

```cpp
struct {
    string brand;
    string model;
    int year;
} myCar1, myCar2; // create multiple variables
```

### Named structures

```cpp
struct myType { 
        int myNum;
        string myString;
    };
    myType myStruct;
    myStruct.myNum = 10;
    cout << myStruct.myNum;
```

## Enumerations (`enum`)

Refer to C

## References

Refer to C

```cpp
string food = "Pizza";
string &meal = food;

meal = "Rice";
cout << food; // Rice
```

## Functions

Refer to C

### Default arguments

```cpp
void printName(string name = "Thisal"); // Default argument here

int main() {
    printName(); // prints "Thisal"
}

void printName(string name) { // No default argument here
    cout << name << "\n";
}
```

### Pass by reference
- Not to be confused with `&` as in memory address

```cpp
void swapNums(int &x, int &y);
// int& x, int& y is also valid

int main() {
    int x = 50;
    int y = 30;
    swapNums(x, y);
    cout << "Now x is " << x << " and y is " << y;
    // Now x is 30 and y is 50
}

void swapNums(int &x, int &y) {
    int z = x;
    x = y;
    y = z;
}
```

- Array
    
    ```cpp
    int finMin(int (&arr)[5]) { // 5 means size of array
        int min = arr[0];
    }
    ```
    
### Pass arrays
- Passes Pointers, not arrays
    
    ```cpp
    void printArray(int numbers[]);
    
    int main() {
        int myNumbers[] = {1, 2, 3, 4, 5};
        printArray(myNumbers);
        // When printArray(myNumbers) is called, myNumbers decays into a pointer
        return 0;
    }
    
    void printArray(int myNumbers[]) {
        // sizeof gives the size of pointer, not the array
        for (int i=0; i < sizeof(myNumbers)/sizeof(myNumbers[0]); i++) {
            cout << myNumbers[i] << ", ";
        }
    }
    ```
    

```cpp
void printArray(int numbers[5]);

int main() {
    int myNumbers[] = {1, 2, 3, 4, 5};
    printArray(myNumbers);
    return 0;
}

void printArray(int myNumbers[5]) {
    for (int i=0; i < 5; i++) {
        cout << myNumbers[i] << ", ";
    }
}
```

### Overloading
- Multiple functions can have same name as long as they have different type of/number of parameters

```cpp
int plusFunc(int x, int y);
float plusFunc(float x, float y);

int main() {
    cout << "Int sum: " << plusFunc(5, 3) << "\n";
    cout << "Float sum: " << plusFunc(3.2f, 6.2f);
    return 0;
}

int plusFunc(int x, int y) {
    return x + y;
}

float plusFunc(float x, float y) {
    return x + y;
}
```

### Return array

```cpp
// Function that returns an array of integers
int* getArray(int size) {
    int* arr = new int[size];  // Dynamically allocate memory for the array
    for (int i = 0; i < size; ++i) {
        arr[i] = i * 2;  // Just an example: fill the array with multiples of 2
    }
    return arr;
}
```

## Classes

### Create

```cpp
class MyClass { // Class
    public: // Access specifier
        // public: attributes & methods that are accesible from outside the class
        // Attributes
        int myNum;
        string myString;
};

int main() {
    MyClass myObj; // Create an object
    myObj.myNum = 10;
    myObj.myString = "Thisal";
    cout << myObj.myNum << " " << myObj.myString; // 10 Thisal
}
```

### Methods
- Initializer method
    
    ```cpp
    class MyClass {
        public:
            int value;
            int myNum;
            string myString;
    
            // Constructor with an initializer list
            MyClass(int i) : value(i), myNum(0), myString("Default") { // Known as **initializer list**
                // Code to run when initializing
            }
    };
    
    int main() {
        MyClass me(5);
        cout << me.value; // 5
    
        return 0;
    } 
    ```
    
    - Explanation
        
        This is kinda like
        
        ```cpp
        MyClass(int i) {
            value = i;
            myNum = 0;
            myString = "Default";
        }
        ```
        
        but better in terms of efficiency and is required for certain cases
        
- Define inside class
    
    ```cpp
    class MyClass {
        public:
            void myMethod() {
                cout << "Hello World";
            }
    };
    
    int main() {
        MyClass myObj;
        myObj.myMethod(); // Hello World
    }
    ```
    
- Define outside class
    
    ```cpp
    class MyClass {
        public:
            void myMethod(); // Method declaration
    };
    
    // Method definition
    void MyClass::myMethod() {
        cout << "Hello World";
    }
    
    int main() {
        MyClass myObj;
        myObj.myMethod(); // Hello World
    }
    ```
    
- Parameters/Return
    
    ```cpp
    class Number {
        public:
            int divideBy2(int value);
    };
    
    int Number::divideBy2(int value) {
        return value/2;
    }
    
    int main() {
        Number myNum;
        cout << myNum.divideBy2(50); // 25
    }
    ```
    
- Constructers
    - Automatically called when an object is created
    - Same name as the class
    - Always `public`
    - No return value
    
    ```cpp
    class MyClass {
        public:
            MyClass() { // Can also be defined outside class
                cout << "Hello World";
            }
    };
    
    int main() {
        MyClass myObj; // Hello World
        return 0;
    }
    ```
    
    - Constructer Parameters
        
        ```cpp
        class Person {
            public:
                string name;
                int age;
                Person(string n, int a) {
                    name = n;
                    age = a;
                }
        };
        
        int main() {
            Person thsl("Thisal", 20);
            cout << thsl.name << " " << thsl.age; // Thisal 20
            return 0;
        }
        ```
        
### Access Specifiers
- `public`  - accessible from outside
- `private` - can’t be accessed or viewed from outside directly
- `protected` - like `private`, but can be accessed in inherited classes
- Members are private by default
    
    ```cpp
    class MyClass {
        int x;   // Private attribute
        int y;   // Private attribute
    };
    ```
    
    - Try to declare attributed as private as often as possible
### Encapsulation
- Declare attributes as `private`, provide `get` and `set` methods
- Increased security of data

```cpp
class Person {
    string name;
    public:
        // Getter
        string getName() {
            return name;
        }
        // Setter
        void setName(string newName) {
            name = newName;
        }
};

int main() {
    Person thsl;
    thsl.setName("Thisal");
    cout << thsl.getName(); // Thisal
}
```

### Inheritance

```cpp
class Vehicle {
    public:
        string brand = "Ford";
};

class Car: public Vehicle {
    public:
        string model = "Mustang";
};

int main(){
    Car myCar;
    cout << myCar.brand << " " << myCar.model;
}
```

- `public Vehicle`
    - `public` : `Vehicle`'s public members accessible as public members of `Car`
    - `protected`: Converts `Vehicle`'s public members into protected members within `Car`
    - `private`: Converts `Vehicle`'s public and protected members into private members within `Car`
- Multilevel
    
    ```cpp
    class MyClass {
        public:
            void myFunction(){
                cout << "Some Command";
            }
    };
    
    class MyChild: public MyClass {};
    class MyGrandChild: public MyChild {};
    
    int main(){
        MyGrandChild myObj;
        myObj.myFunction();
    }
    ```
    
- Multiple
    
    ```cpp
    class myParent1 {
        public:
            void function1() {
                cout << "print from Parent1";
            }
    };
    
    class myParent2 {
        public:
            void function2() {
                cout << "print from Parent2";
            }
    };
    
    class myChild: public myParent1, public myParent2 {};
    
    int main(){
        myChild myObj;
        myObj.function1();
        cout << "\n";
        myObj.function2();
    }
    ```
    
- Polymorphism
    - Override members of the parent
    
    ```cpp
    class Animal {
        public:
            void animalSound() {
                cout << "The animal makes a sound \n";
            }
    };
    
    class Pig: public Animal {
        public:
            void animalSound() {
                cout << "The pig says: wee wee\n";
            }
    };
    
    class Cat: public Animal {
        public:
            void animalSound() {
                cout << "The cat says: meow meow\n";
            }
    };
    
    int main(){
        Animal myAnimal;
        Cat myCat;
        myAnimal.animalSound(); // The animal makes a sound 
        myCat.animalSound(); // The cat says: meow meow
        return 0;
    }
    ```

## Errors

### Raise error

```cpp
int number;
cout << "Enter a positive number: ";
cin >> number;

if (number < 0) {
    throw runtime_error("Negative number entered!"); // Raise error
}
```

### Handle error

```cpp
try {
    int number;
    cout << "Enter a positive number: ";
    cin >> number;

    if (number < 0) {
        throw runtime_error("Negative number entered!"); // Raise error
    }
} catch (const runtime_error &e) {
    cout << "Error: " << e.what() << endl;// Catch and display the error
}
```

### Error types
- `std::logic_error`
- `std::runtime_error`
- `std::invalid_argument`
- `std::out_of_range`
- `std::overflow_error`
- `std::underflow_error`

## Files

`#include <fstream>`
    
- [`fstream` Reference](https://www.w3schools.com/cpp/cpp_ref_fstream.asp)

### Write to a file

```cpp
int main(){
    // Create and open a text file
    ofstream MyFile("filename.txt");
    // Write to the file
    MyFile << "Add this text to the file";
    // Close the file
    MyFile.close();
    return 0;
}
```

### Read a file

```cpp
int main() {
    string myText;
    ifstream MyReadFile("filename.txt");
    // getline reads next line each time (keeps track of of its position internally)
    // returns `false` at end
    while (getline(MyReadFile, myText)) {
        cout << myText << "\n";
    }
    MyReadFile.close();
    return 0;
}
```


## Exceptions

```cpp
int age = 15;
    try {
        if (age >= 18) {
            cout << "Access Granted";
        } else {
            throw(age);
        }
    }
    catch (int age) {
        cout << "Access denied; Age is " << age;
    }
```

### When don’t know type of throw

```cpp
int age = 15;
    try {
        if (age >= 18) {
            cout << "Access Granted";
        } else {
            throw 505;
        }
    }
    catch (...) {
        cout << "Access denied";
    }
```
        
## Date time

Didn’t learn properly

```cpp
time_t timestamp; // Create variable to store date time
time(&timestamp); // Get current time and store
cout << ctime(&timestamp); // Wed Oct 30 04:44:59 2024
```

### Directly store to variable

`time_t timestamp = time(NULL) // NULL pointer`

### Data types(minutes, seconds etc.)
- 24 hour format
- Months start from 0 (December = 11)
- Years are represented relative to 1900 (2024 = 124)
- [Reference](https://www.w3schools.com/cpp/cpp_date.asp)

### Create Timestamps

```cpp
struct tm datetime; // struct of type `tm` called datetime
time_t timestamp; // variable to store datetime in `time_t` format
datetime.tm_year = 2023 - 1900; // Number of years since 1900
datetime.tm_mon = 12 - 1; // Number of months since January
datetime.tm_mday = 17;
datetime.tm_hour = 12;
datetime.tm_min = 30;
datetime.tm_sec = 1;
// Daylight Savings must be specified
// -1 uses the computer's timezone setting
datetime.tm_isdst = -1;

timestamp = mktime(&datetime);
cout << ctime(&timestamp); // Sun Dec 17 12:30:01 2023
```

- Automatically calculates weekday
    
    `cout << datetime.tm_wday; // 0 (for Sunday)`
    
## Templates

Write functions/classes that work with any data type

### Function templates

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(5, 3); // 8
    cout << add(string("Thisal"), string(" Kenula")); // Thisal Kenula

    return 0;
} 
```

### Class templates

```cpp
template <typename T>
class Box {
    public:
        T value;
        Box(T v) : value(v) {}
};

int main() {
    Box<int> myBox(5);
    Box<string> myStrBox("Thisal");

    cout << myBox.value; // 5
    cout << myStrBox.value; // Thisal
    return 0;
} 
```

### Size of array

```cpp
template <size_t N>
int finMin(int arr[N]) { // N means size of array
    int min = arr[0];
}
```
    
## Pointers/Addresses/References

- References available in C++ only

```cpp
int num = 10;
int& ref = num; // Reference
ref = 20; // Changes `num`
cout << num; // 20
```

```cpp
int num = 10;
int* ptr = &num; // &num = Address of num
cout << ptr << "\n"; // Address
cout << *ptr; // value of address in ptr (=num)
```

`int& ref` same as `int &ref` and `int* ptr` same as `int *ptr`
    
## Data Structures in `STL` Library
### `#include <vector>`
- Like array but can dynamically change size
- Vectors are optimized for adding & removing at the **end**
- Use like array (Iteration, indexing)
- Create
    
    ```cpp
    vector<string> cars;
    cars = {"Bently", "Toyota", "BMW", "Benz"};
    ```
    
    or
    
    ```cpp
    vector<string> cars = {"Bently", "Toyota", "BMW", "Benz"};
    ```
    
- `front`/`back`
    
    ```cpp
    vector<string> cars = {"Honda", "Toyota", "BMW", "Benz"};
    cout << cars.front(); // Honda
    cout << cars.back(); // Benz
    ```
    
- `at`
    
    ```cpp
    vector<string> cars = {"Honda", "Toyota", "BMW", "Benz"};
    cout << cars.at(1); // Toyota
    ```
    
    - `at` is better than `[]`
        
        ```cpp
        cout << cars.at(4); // Throws an error
        ```
        
    - Use to change elements as well
        
        ```cpp
        cars.at(1) = "Ferrari";
        ```
        
- Add
    
    ```cpp
    vector<string> cars = {"Honda", "Toyota", "BMW", "Benz"};
    cars.push_back("Tesla"); // Adds to end
    ```
    
- Remove
    
    ```cpp
    cars.pop_back(); // Removes last element
    ```
    
- Size
    
    ```cpp
    vector<string> cars = {"Honda", "Toyota", "BMW", "Benz"};
    cout << cars.size(); // 4
    ```
    
- Check if empty
    
    ```cpp
    vector<string> cars = {"Honda", "Toyota", "BMW", "Benz"};
    cout << cars.empty(); // 0 (=False)
    ```
    
    ```cpp
    vector<string> cars;
    cout << cars.empty(); // 1 (=True)
    ```
    
- Memory management
    - Capacity
        
        Total number of elements the `vector` can hold without reallocating memory
        
        ```cpp
        vector<int> myNums = {1, 2, 3};
        cout << myNums.capacity() << endl; // 3
        myNums.push_back(4); // Adding 4 to the vector will double the capacity
        cout << myNums.capacity() << endl; // 4
        ```
        
    - Reserve Memory
        
        ```cpp
        vector<int> myNums = {1, 2, 3};
        myNums.reserve(6); // Reserve memory for 6 elements
        myNums.push_back(4); // No need to reallocate memory
        cout << myNums.capacity() << endl; // 6
        ```
        
        - No need to do this always, because doubling memory and reallocating strategy works better for most cases
- [Reference](https://www.w3schools.com/cpp/cpp_ref_vector.asp)
### `#include <list>`
- Can’t access random elements
- Can remove/add at anywhere
    
    ```cpp
    list<int> l = {1, 2, 3, 4, 5};
    auto it = l.begin();
    advance(it, 2);
    l.insert(it, 10); // 1, 2, 10, 3, 4, 5
    ```
    
    - Add multiple elements
        
        ```cpp
        // Insert two 10s at the 3rd position
        l.insert(it, 2, 10); // 1, 2, 10, 10, 3, 4, 5, 
        ```
        
- Access/change elements
    
    ```cpp
    list<string> cars = {"Volvo", "Honda", "Toyota", "Nissan"};
    cout << cars.front() << "\n"; // Volvo
    cout << cars.back(); // Nissan
    ```
    
    ```cpp
    list<string> cars = {"Volvo", "Honda", "Toyota", "Nissan"};
    cars.front() = "Mazda";
    cout << cars.front(); // Mazda
    ```
    
- Add elements
    
    ```cpp
    list<string> cars = {"Honda", "Toyota"};
    cars.push_front("Benz");
    cars.push_back("Nissan");
    // Benz, Honda, Toyota, Nissan
    ```
    
- Size, isEmpty, Loop just like vector
### `#include <stack>`
- **Last In First Out**: Can only access elements at the top
- Can’t add elements at the time of declaration
    
    ```cpp
    stack<string> cars = {"Volvo", "BMW"}; // Error
    ```
    
- Can’t change type after declaration
- Add elements
    
    ```cpp
    stack<string> cars;
    cars.push("Volvo");
    cars.push("Honda");
    cars.push("Toyota");
    cars.push("Nissan");
    ```
    
    ```
    Mazda (top element)
    Ford
    BMW
    Volvo
    ```
    
- Access/change top element
    
    ```cpp
    stack<string> cars;
    cars.push("Volvo");
    cars.push("Honda");
    cars.push("Toyota");
    cars.push("Nissan");
    
    cout << cars.top(); // Nissan
    ```
    
    ```cpp
    stack<string> cars;
    cars.push("Volvo");
    cars.push("Honda");
    cars.push("Toyota");
    cars.push("Nissan");
    cars.top() = "Benz";
    cout << cars.top(); // Benz
    ```
    
- Remove last added element
    
    ```cpp
    stack<string> cars;
    cars.push("Volvo");
    cars.push("Honda");
    cars.push("Toyota");
    cars.push("Nissan");
    
    cars.pop();
    
    cout << cars.top(); // Toyota
    ```
    
- `size`, `empty` just like others
### `#include <queue>`
- Like stack, but **First In First Out**
- Can’t change type after declaration
- Can’t add elements at the declaration
- Add/Access/Change elements
    
    ```cpp
    // Add 
    queue<string> cars;
    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");
    cars.push("Mazda");
    // Access
    cout << cars.front() << "\n"; // Volvo
    cout << cars.back(); // Mazda
    // Change
    cars.front() = "Ferrri";
    ```
    
    ```
    Volvo (front (first) element)
    BMW
    Ford
    Mazda (back (last) element)
    ```
    
- Remove front element
    
    ```cpp
    queue<string> cars;
    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");
    cars.push("Mazda");
    
    cars.pop();
    cout << cars.front(); // BMW
    ```
    
- `size`, `empty` just like others
### `#include <deque>`
- Double ended queue
- Type cannot be change after its declared
- Can access by index
- Create
    
    `#include <string>`
    
    ```cpp
    deque<string> cars;
    ```
    
    or
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    ```
    
- Access elements
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cout << cars[1]; // BMW
    ```
    
    ```cpp
    cout << [cars.at](http://cars.at/)(1); // BMW
    // at is better than []
    ```
    
    ```cpp
    cout << cars.front(); // Volvo
    cout << cars.back(); // Mazda
    ```
    
- Change element
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cars.at(0) = "Ferrari";
    ```
    
    ```cpp
    cars[0] = "Ferrari"; // is also valid
    ```
    
- Add elements
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cars.push_front("Tesla");
    cars.push_back("Honda");
    // Tesla, ..., Honda
    ```
    
- Remove elements
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cars.pop_front(); // Removes Volvo
    cars.pop_back(); // Removes Mazda
    ```
    
- Size
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cout << cars.size(); // 4
    ```
    
- Check if empty
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    cout << cars.empty(); // 0 (indicates false)
    ```
    
- Loop through
    
    ```cpp
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    
    for (int i = 0; i < cars.size(); i++) {
        cout << cars.at(i) << "\n";
    }
    ```
    
    ```cpp
    for (string car : cars) {
        cout << car << "\n";
    }
    ```
    
- `stack` and `queue` use `deque` underneath, just restricts other operations. So use `deque` by default
### `#include <set>`
- Sorted automatically
    - Ascending order (Default)
        
        ```cpp
        set<string> cars = {"Honda", "Tesla", "Ford", "Mazda"};
        
        for (string car : cars) {
            cout << car << "\n";
        }
        ```
        
        ```
        Ford
        Honda
        Mazda
        Tesla
        ```
        
    - Descending order
        
        ```cpp
        set<string, greater<string>> cars = {"Honda", "Tesla", "Ford", "Mazda"};
        
        for (string car : cars) {
            cout << car << "\n";
        }
        ```
        
        ```
        Tesla
        Mazda
        Honda
        Ford
        ```
        
- Duplicates are ignored
    
    ```cpp
    set<string> cars = {"Honda", "Tesla", "Ford", "Mazda", "Tesla"};
    for (string car : cars) {
        cout << car << "\n";
    }
    ```
    
    ```
    Ford
    Honda
    Mazda
    Tesla
    ```
    
- Existing elements can’t be changed (Can add or remove)
- Can’t access by index numbers
- Create
    
    ```cpp
    set<string> cars;
    cars = {"Volvo", "BMW", "Ford", "Mazda"};
    ```
    
    ```cpp
    set<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    ```
    
- Insert
    
    ```cpp
    set<string> cars = {"Honda", "Tesla", "Ford", "Mazda"};
    cars.insert("Toyota");
    ```
    
- Remove
    
    ```cpp
    set<string> cars = {"Honda", "Tesla", "Ford", "Mazda"};
    cars.erase("Tesla");
    ```
    
    - Remove all elements
        
        ```cpp
        cars.clear();
        ```
        
- Size
    
    ```cpp
    set<string> cars = {"Honda", "Tesla", "Ford", "Mazda"};
    cout << cars.size(); // 4
    ```
    
- Is Empty
    
    ```cpp
    set<string> cars = {"Honda", "Tesla", "Ford", "Mazda"};
    cout << cars.empty(); // 0 (False)
    ```
    
- Loop through
    
    ```cpp
    for (string car : cars) {
        cout << car << "\n";
    }
    ```
    
### `#include <map>`
- Features
    - Stores elements in Key/Value pairs
    - Accessible by unique keys(instead of index)
    - Automatically sorted in ascending order
- Create/Access
    
    ```cpp
    map<string, int> people = {
        {"Thisal", 20},
        {"John", 32},
        {"Adele", 45}
    };
    
    cout << "Thisal is " << people["Thisal"]; // Thisal is 20
    cout << "Thisal is " << people["Kenula"]; // Thisal is 0
    cout << "Thisal is " << people.at("Kenula"); // Error
    ```
    
    - Use `at` over `[]`
- Change values
    
    ```cpp
    map<string, int> people = {
        {"Thisal", 20},
        {"John", 32},
        {"Adele", 45}
    };
    
    people["Thisal"] = 21;
    ```
    
- Add elements
    
    ```cpp
    map<string, int> people = {
        {"Thisal", 20},
        {"John", 32},
        {"Adele", 45}
    };
    
    people["iPhone"] = 17; // Creates new element
    //or
    people.insert({"iPhone", 17});
    ```
    
    - Can’t add for same key value
        
        ```cpp
        map<string, int> people = {
            {"John", 32},
            {"Adele", 45}
        };
        
        people.insert({"Thisal", 20});
        people.insert({"Thisal", 21});
        
        cout << people.at("Thisal"); // 20
        ```
        
- Remove elements
    
    ```cpp
    map<string, int> people = {
        {"John", 32},
        {"Adele", 45},
        {"Thisal", 21}
    };
    
    people.erase("Thisal");
    
    people.clear(); // Remove all elements
    ```
    
- Size
    
    ```cpp
    map<string, int> people = {
        {"John", 32},
        {"Adele", 45},
        {"Thisal", 21}
    };
    
    cout << people.size(); // 3
    ```
    
- Is empty
    
    ```cpp
    map<string, int> people = {
        {"John", 32},
        {"Adele", 45},
        {"Thisal", 21}
    };
    
    cout << people.empty(); // 0 (indicates false)
    ```
    
- Check if exist
    
    ```cpp
    map<string, int> people = {
        {"John", 32},
        {"Adele", 45},
        {"Thisal", 21}
    };
    
    cout << people.count("Thisal"); // 1 means exist
    cout << people.count("Kenula"); // 0 means doesn't exist
    ```
    
- Loop through
    
    ```cpp
    map<string, int> people = {
        {"John", 32},
        {"Adele", 45},
        {"Thisal", 20}
    };
    
    for (auto person : people) {
        cout << person.first << " is " << person.second << "\n";
    }
    ```
    
    ```
    Adele is 45
    John is 32
    Thisal is 20
    ```
    
    - `auto` : to automatically determine the type
    - `first` : key
    - `second` : value
    - Reverse order
        
        ```cpp
        map<string, int, greater<string>> people = {
            {"John", 32},
            {"Adele", 45},
            {"Thisal", 20}
        };
        ```
        
        ```
        Thisal is 20
        John is 32
        Adele is 45
        ```
        
### Iterators
- Explanation
    
    ```cpp
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    vector<string>::iterator it;
    ```
    
    - Iterator is like a memory address(pointer) but with extra metadata like which item its pointing to
    - `cout << it` wouldn’t print a memory address
    - But `cout << *it` would print the value of the item its currently pointing
- Example
    
    ```cpp
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    // Create vector iterator
    vector<string>::iterator it;
    
    for (it = cars.begin(); it != cars.end(); ++it) {
        cout << *it << "\n";
    }
    ```
    
    - using `auto`
        
        ```cpp
        vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
        
        for (auto it = cars.begin(); it < cars.end(); ++it) {
            cout << *it << "\n";
        }
        ```
        
- `begin` and `end`
    
    ```cpp
    // Used for examples below
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    ```
    
    ```
    0 Volvo 1 BMW 2 Ford 3 Mazda 4 
    begin -> 0
    end -> 4
    ```
    
    - `begin`
        
        ```cpp
        auto it = cars.begin();
        cout << *it; // Volvo
        ++it;
        cout << *it; // BMW
        ```
        
        ```cpp
        auto it = cars.begin() + 1;
        cout << *it; // BMW
        ```
        
    - `end`
        
        ```cpp
        auto it = cars.end(); 
        cout << *it; // Would not print anything
        ```
        
        ```cpp
        auto it = cars.end() - 1; 
        cout << *it; // Mazda
        ```
        
- `auto`
    
    ```cpp
    vector<string>::iterator it = cars.begin();
    ```
    
    Can be simplified to 
    
    ```cpp
    auto it = cars.begin();
    ```
    
- Usage
    - When needed to do actions in a collection
    
    ```cpp
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    
    for (auto it = cars.begin(); it != cars.end();) {
        if (*it == "BMW") {
            it = cars.erase(it); // Remove BMW and update `it`
            // `it` is not just memory address. So it becomes unvalid
            // after an item removes
            // Above line makes returns a new iterator pointing to next
            // element ("Ford")
        }
        else {
            ++it;
        }
    }
    ```
    
- Iterate in reverse
    
    ```cpp
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    
    for (auto it = cars.rbegin(); it != cars.rend(); ++it) {
        cout << *it << " ";
        // Mazda Ford BMW Volvo
    } 
    ```
    
- Iterators work for `vector`, `list`, `deque`, `map`, `set`
### `#include <algorithm>`

[Full reference](https://www.w3schools.com/cpp/cpp_ref_algorithm.asp)

- Sort
    
    ```cpp
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    
    // {"Volvo", "BMW", "Ford", "Mazda"}
    sort(cars.begin(), cars.end());
    // {"BMW", "Ford", "Mazda", "Volvo}
    ```
    
- Search
    
    ```cpp
    // Create a vector called numbers that will store integers
    vector<int> numbers = {1, 7, 3, 5, 9, 2};
    
    // Search for the number 3
    auto it = find(numbers.begin(), numbers.end(), 3);
    ```
    
    - Binary search (on sorted data structure)
        
        ```cpp
        vector<int> numbers = {1, 7, 3, 5, 9, 2};
        
        sort(numbers.begin(), numbers.end());
        
        **// To get first element greater than 5**
        // Must be sorted initially in order to work `upper_bound` properly
        auto it = upper_bound(numbers.begin(), numbers.end(), 5);
        
        cout << *it; // 7
        ```
        
    - `min`
        
        ```cpp
        vector<int> numbers = {1, 7, 3, 5, 9, 2};
        
        auto it = min_element(numbers.begin(), numbers.end());
        
        cout << *it; // 1
        ```
        
    - `max`
        
        ```cpp
        vector<int> numbers = {1, 7, 3, 5, 9, 2};
        
        auto it = max_element(numbers.begin(), numbers.end());
        
        cout << *it; // 9
        ```
        
- Copy
    
    ```cpp
    vector<int> numbers = {1, 7, 3, 5, 9, 2};
    
    vector<int> copied_numbers(6);
    
    copy(numbers.begin(), numbers.end(), copied_numbers.begin());
    ```
    
### Choose correct data structure
        
        ### **1. Access (Read/Write an Element by Index or Key)**
        
        | **Rank** | **Data Structure** | **Time Complexity** | **Notes** |
        | --- | --- | --- | --- |
        | **1** | `array` (built-in or STL) | O(1) | Fastest since it's a fixed-size contiguous memory block. |
        | **2** | `vector` | O(1) | Similar to `array` but with dynamic resizing overhead for initialization. |
        | **3** | `deque` | O(1) for most accesses | Slightly slower than `vector` due to non-contiguous memory blocks. |
        | **4** | `map` / `set` | O(log n) | Binary search tree-based, requiring traversal for lookups. |
        | **5** | `unordered_map` / `unordered_set` | O(1) (average), O(n) (worst) | Hash table-based, very fast in average cases but can degrade with hash collisions. |
        | **6** | `list` | O(n) | Requires sequential traversal to find the element. |
        
        ---
        
        ### **2. Insertion (Add an Element)**
        
        | **Rank** | **Data Structure** | **Time Complexity** | **Notes** |
        | --- | --- | --- | --- |
        | **1** | `unordered_map` / `unordered_set` | O(1) (average), O(n) (worst) | Fastest for adding new elements when order doesn't matter. |
        | **2** | `map` / `set` | O(log n) | Keeps elements sorted while inserting, slower than hash tables but predictable. |
        | **3** | `vector` (end only) | O(1) (amortized) | Efficient when inserting at the end. |
        | **4** | `deque` | O(1) at ends | Efficient at both ends; slower than `vector` for resizing. |
        | **5** | `list` | O(1) | Best for inserting in the middle or at arbitrary positions. |
        | **6** | `vector` (middle) | O(n) | Expensive due to shifting elements when inserting in the middle. |
        
        ---
        
        ### **3. Deletion (Remove an Element)**
        
        | **Rank** | **Data Structure** | **Time Complexity** | **Notes** |
        | --- | --- | --- | --- |
        | **1** | `unordered_map` / `unordered_set` | O(1) (average), O(n) (worst) | Fastest for deleting by key. |
        | **2** | `map` / `set` | O(log n) | Efficient for deleting sorted elements by key or value. |
        | **3** | `list` | O(1) (if iterator known) | Fastest for removing elements when their location is known. |
        | **4** | `deque` (ends only) | O(1) | Efficient at removing elements from the ends. |
        | **5** | `vector` (end) | O(1) | Fastest when removing only the last element. |
        | **6** | `vector` (middle) | O(n) | Expensive due to shifting elements when removing from the middle. |
        
        ---
        
        ### **4. Search (Find an Element)**
        
        | **Rank** | **Data Structure** | **Time Complexity** | **Notes** |
        | --- | --- | --- | --- |
        | **1** | `unordered_map` / `unordered_set` | O(1) (average), O(n) (worst) | Hash-based search, fastest for average cases. |
        | **2** | `map` / `set` | O(log n) | Logarithmic search due to binary search tree structure. |
        | **3** | `vector` (unsorted) | O(n) | Requires linear search unless sorted. |
        | **4** | `deque` | O(n) | Similar to `vector` but slower due to non-contiguous memory. |
        | **5** | `list` | O(n) | Slowest due to sequential traversal and lack of random access. |
        
        ---
        
        ### **5. Memory Efficiency**
        
        | **Rank** | **Data Structure** | **Notes** |
        | --- | --- | --- |
        | **1** | `array` | Fixed size; most memory-efficient. |
        | **2** | `vector` | Slight overhead for dynamic resizing but better memory locality. |
        | **3** | `deque` | Slightly more overhead than `vector` due to multiple memory blocks. |
        | **4** | `unordered_map` / `unordered_set` | Hash table-based, uses extra memory for hash storage. |
        | **5** | `map` / `set` | Tree-based, requires pointers for each node, leading to more overhead. |
        | **6** | `list` | Worst in terms of memory efficiency due to pointers for each node. |
        
        ---
        
        ### **Overall Speed Ranking**
        
        For **general-purpose performance**, use this ranking:
        
        1. `unordered_map` / `unordered_set`
        2. `vector`
        3. `deque`
        4. `map` / `set`
        5. `list`
        
        But always match the **specific operation** to the data structure for the best performance!