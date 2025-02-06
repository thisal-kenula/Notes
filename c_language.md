# C programming

[W3schools](https://www.w3schools.com/c/index.php)

## Why C is faster

### Runs a compiled program rather than interpreted(like Python)

- Interpreted
    
    Translate the code into machine language line by line at runtime using an interpreter(like Python interpreter)
    
- Compiled
    
    The source code is converted into machine language using a compiler first(This is what is saved as an Unix Executable file when interpreting a C code)
    

### Memory management

- Some like python use automatic memory management(garbage collector)
- C offers direct control over memory management

### Abstraction

C operates closer to hardware, providing low level access to memory and system resources

## How to run a C code

1. Save the file
2. Compile the code: `gcc filename.c -o outputname`
3. Run the executable file(compiled file): `./outputname`

### Example code

```c
#include <stdio.h> // header file: imports library

int main() { // int means integer(every function must specify a return type)
  printf("Hello World!"); // printf is a function from <stdio.h> library
  return 0; // ends the main function
}

// The `main()` function should have return type of int because when system knows that program executed successfully when `0` was returned
```

The `main()` function acts as the entry point for the program

### install compiler(ex: gcc)

- Install Xcode command line tools(includes GCC)
    
    `xcode-select --install`
    
- Using Homebrew
    1. install homebrew: `/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"`
    2. Install gcc: `brew install gcc`
- Confirm installation: `gcc --version`

### To view the hexadecimal code of the executable file

`hexdump -C myprogram` or `xxd myprogram`

## Variables and constants

### Numbers

- `int` , `long`, `long long`
    
    
    | Data Type | Typical Size (bytes) | Typical Range (signed) | Typical Range (unsigned) |
    | --- | --- | --- | --- |
    | `int` | 4 | -2,147,483,648 to 2,147,483,647 | 0 to 4,294,967,295 |
    | `long` | 4 or 8
    (depends on the system architecture) | -2,147,483,648 to 2,147,483,647 (4 bytes) / -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (8 bytes) | 0 to 4,294,967,295 (4 bytes) / 0 to 18,446,744,073,709,551,615 (8 bytes) |
    | `long long` | 8 | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 0 to 18,446,744,073,709,551,615 |
    
    ```c
    unsigned int i = -1U;
    printf("%u", i); // prints 4294967295 (4294967296 -1)
    ```
    
- `float`
- `double`
- Scientific numbers
    
    ```c
      float f1 = 12E4; // 'e' is also valid
      printf("%f", f1);
    ```
    
- Set decimal precision
    
    ```c
        printf("%f\n", 3.5); // 3.500000
        printf("%**.1**f", 3.5); // 3.5
    ```
    

### `char`

- Print with ASCII values
    
    ```c
    char a = 66;
      printf("%c", a); // prints 'B'
    ```
    
- When multiple characters stored
    
    ```c
      char myText = 'Thisal';
      printf("%c", myText); // prints 'l' (last character)
    ```
    
- To store multiple characters
    
    ```c
      char myText**[]** = **"**Thisal**"**;
      printf("**%s**", myText);
    ```
    

### Boolean

`#include <stdbool.h>` is necessary for `true` and `false`

- booleans are returned as integers
    
    ```c
    #include <stdio.h>
    #include <stdbool.h>
    
    int main() {
    
        bool perplexity = true;
        printf("%d", perplexity); // prints 1
    
        return 0;
    }
    ```
    
    ```c
    printf("%d", 10 > 9); // prints 1
    // no need of `#include <stdbool.h>` for this
    ```
    

### Strings

```c
// use double quotes
char name[] = "Thisal Kenula";
//or
char name[] = {'T', 'H', 'I', 'S', 'A', 'L', **'\0'**};
printf("%s", name); // THISAL
// **\0** is required to mark end of string
//(No need if using just like arrary of chars)
```

- Character
    
    ```c
    char name[] = "Thisal Kenula";
    printf("%c", name[0]); // prints T
    ```
    
- Unlike python, item assignment is allowed
    
    ```c
    char name[] = "Thisal Kenula";
    name[0] = 'S'; // Shisal Kenula
    ```
    
- Special characters
    
    
    | Escape character | Result | Description |
    | --- | --- | --- |
    | `\'` | ' | Single quote |
    | `\"` | " | Double quote |
    | `\\` | \ | Backslash |
    | `\n` | New line |  |
    | `\t` | Tab |  |
    | `\0` | Null |  |
- String functions
    
    `#include <string.h>` to use
    
    - Length : `strlen`
        
        ```c
        char alphabet[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        printf("%lu", strlen(alphabet));// 26
        printf("%lu", sizeof(alphabet)); // 27 (because sting also includes `\0`)
        
        char alphabet[50] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        printf("%lu", strlen(alphabet));// 26
        printf("%lu", sizeof(alphabet)); // 50
        
        // Don't put 26; beacuse one char is needed store null terminator(\0)
        char alphabet[**27**] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        ```
        
    
    ```c
    char myname[] = "Thisal";
    myname = "Hello"; // is not valid.
    ```
    
    - Append : `strcat`
        
        ```c
        char a[15] = "Thisal"; // Make sure to allocate enough memory
        strcat(a, " Kenula"); // a + "Kenula" is not valid
        printf("%s", a); // Thisal Kenula
        ```
        
    - Copy : `strcpy`
        
        ```c
        char a[] = "Thisal";
        strcpy(a, "Kenula"); // overwrites a
        printf("%s", a); // Kenula
        ```
        
    - Compare : `strcmp`
        
        ```c
        char a[] = "Thisal";
        char b[] = "Kenula";
        char c[] = "Thisal";
        
        printf("%d\n", strcmp(a, b)); // positive number (because "Thisal" > "Kenula")
        printf("%d", strcmp(a, c)); // 0 when equal
        ```
        

### Scope

Same as Python

### Pointers

Refer to memory address

### Create a variable

`int myNum = 15;` 

### Suffix

```c
// suffix letters are not case sensitive

float x = 2.5f; /* `2.5` literal is a double and 
								   asigning it to a float converts 
								   the double to a float 
								   (not recommended)
								   */
double g = 3.14; // (no suffix needed for double)
long double h = 3.14L;

char a = 'a' // no suffix needed)
```

- Integer suffixes
    
    ```c
    unsigned int a = 12345U;
    long b = 123456789L;
    unsigned long c = 1234567890UL;
    long long d = 123456789012345LL;
    unsigned long long e = 123456789012345ULL;
    ```
    

### Memory size

```c
int myInt;
printf("%lu", sizeof(myInt)); // 4 (in bytes)
```

### Type conversion

- Implicitly(automatically)
    
    ```c
    int x = 5/2; // x = 2
    int x = 9.99; // 9
    float x = 5/2; // 2.000000
    float x = 5.0/2; // 2.500000
    float x = 9; // 9.000000 (converts int 9 to float; risky)
    ```
    
- Explicit
    
    ```c
    float x = (float) 5/2; // 2.500000
    ```
    

### Constants

- Create a constant
    
    ```c
    const int MYNUM = 15;
    ```
    
    ```c
    const int MYNUM;
        MYNUM = 10; // error
    ```
    

### Variable scope

- Same as Python

## Format Specifiers

```c
  int x = 15;
  printf(x); // Won't work
```

```c
  int x = 15;
  int y = 20;
  printf("x is %d and y is %d ", x,y);
```

- **`%d`:** Signed `int`
- **`%u`:** Unsigned `int`
- **`%ld`:** Signed `long`
- **`%lu`:** Unsigned `long`
- **`%lld`:** Signed `long long`
- **`%llu`:** Unsigned `long long`
- **`%f`:** `float`
- **`%lf`:** `double`
- **`%c`:** `char`
- **`%s`:** String
- **`%p`** : Pointer

## Operators

### Arithmetic operators

```c
// increment
int x = 1;
++x; // x = 2 or --x ; x = 0 
// Same as x++;
```

```c
// bitwise XOR
5^3 // 101 XOR 011 = 110 = 6
```

### Logical operators

`&&`, `||`, `!`

## Conditional statements

### `if`

```c
if (x == 3) { // Parenthesis are required.
        printf("all are available");
} else if (x == 2) {
    printf("one item is missing");
} else {
    printf("LOST");
}
```

- Ternary operator
    
    ```c
    printf((time < 18) ? "Good day" : "Good evening");
    ```
    
    ```c
    // Also valid
    (time < 18) ? printf("Good day") : printf("Good evening");
    ```
    

### `switch`

```c
int day = 4;
    
switch (day) {
  case 1:
    printf("Monday");
    break;
  case 2:
    printf("Tuesday");
    break;
  case 3:
    printf("Wednesday");
    break;
  case 4:
    printf("Thursday");
    break;
  case 5:
    printf("Friday");
    break;
  case 6:
    printf("Saturday");
    break;
  default:
    printf("Sunday");
    break;
}   
// Prints Thursday
```

- Fall through
    
    ```c
    case 1:
                printf("Monday");
            case 2:
                printf("Tuesday");
            case 3:
                printf("Wednesday");
            case 4:
                printf("Thursday");
            case 5:
                printf("Friday");
            case 6:
                printf("Saturday");
            default:
                printf("Sunday");
    // Prints ThursdayFridaySaturdaySunday
    ```
    

## Loops

- `break` and `continue` just like in Python

### `while`

```c
int i = 0;

while (i < 5) {
  printf("%d, ", i);
  ++i;
} 
// Prints  0, 1, 2, 3, 4
```

### `do...while`

`do...while` loop executes at least once even if the condition is false

```c
do {
    printf("%d, ", i);
    i++;
} while (i < 5);
// Prints  0, 1, 2, 3, 4
```

### `for`

```c
for (int i = 0; i < 5; i++) {
  printf("%d\n", i);
}
// for (expr1; expr2; expr3) {...}
// expr1: executes once (int i can be defined ontside the loop)
// expr2: condition
// expr3: executes each time
```

## Arrays

Arrays are strictly typed

```c
int myNumbers[] = {25, 50, 75, 100};
printf("%d", myNumbers[0]);
```

### Set Array size

Arrays have fixed size in C (Can’t add/remove)

```c
int myNumbers[4]; // Makes an array with 4 integers
int myNumbers[5] = {25, 50, 75, 100}; 
// will automatically convert to {25, 50, 75, 100, 0}
```

### Get Array size

```c
int myNumbers[] = {25, 50, 75, 100};
int length = sizeof(myNumbers)/sizeof(myNumbers[0]);
// Use when looping over an array
```

### Multidimensional arrays

```c
int matrix[2][3] = { {1, 4, 2},
                     {3, 6, 8} };
```

## User Input

```c
int myNum;
printf("Enter a number:");
scanf("%d", &myNum); // &myNum refers to its memory address
printf("Your number is %d", myNum);
```

### Multiple inputs

```c
    int myNum;
    char myChar;
    printf("Enter a number and a character: ");
    scanf("%d %c", &myNum, &myChar);
    printf("%d choose character %c", myNum, myChar);
```

### String input

```c
char myName[20];
printf("Enter your first name:");
scanf("%s", myName); 
// & is not needed here (because arrays in 
// C are already pointers for the first 
// element of the array)
printf("Hello %s", myName);
```

- Inputs only the first word
    
    Space(whitespace, tab etc.) is considered as terminating character
    
    ```
    Enter your first name:Thisal Kenula
    Hello Thisal
    ```
    
- Read a line (including whitespace)
    
    ```c
    char fullName[30];
    printf("Enter your first name:");
    fgets(fullName, sizeof(fullName), stdin);
    // fgets(array to store, maximum number of characters to read, standard input stream(typically Keyboard))
    printf("Hello %s", fullName);
    ```
    

## Functions

```c
void calculateSum(int x, int y) { // `void` means no return(Otherwise specify return type)
    //code
}
```

- `return` like Python
- When working with multiple arguments, function call must have the same number of arguments as parameters, in the same order

### Unlike in python, functions should be declared above the code, before they were called

```c
int main() {
    calculateSum(5, 10);
    return 0;
}

void calculateSum(int x, int y) {
    int sum = x +y;
    printf("%d + %d = %d", x, y, sum);
}

// Will cause error
```

### Array as a parameter

```c
void calculateSum(int numbers[5]) { 
    int sum = 0;
    for(int i=0; i < 5; i++) {
        sum += numbers[i];
    }
    printf("Total is: %d", sum);
}

int main() {
    // calculateSum({1, 3, 4, 5, 6}); is not valid
    int myNum[] = {1, 3, 4, 5, 6}; // {1, 3, 4, 5} will also cause problems
    calculateSum(myNum);
    return 0;
}
```

### For better code organization and maintainability

```c
**void calculateSum(int numbers[5]);** // function declaration

int main() {
    int myNum[] = {1, 2, 3, 4, 5};
    calculateSum(myNum);
    return 0;
}

**void calculateSum(int numbers[5])** { 
    // function definition
    int sum = 0;
    for(int i=0; i < 5; i++) {
        sum += numbers[i];
    }
    printf("Total is: %d", sum);
}
```

- Why is this necessary
    
    ```cpp
    // This would cause errors
    int num1() {
        return num2();
    }
    
    int num2() {
        return 1;
    }
    
    int main() {
        cout << num1();
        return 0;
    }
    ```
    
    ```cpp
    // This won't cause errors
    int num1();
    int num2();
    
    int num1() {
        return num2();
    }
    
    int num2() {
        return 1;
    }
    
    int main() {
        cout << num1();
        return 0;
    }
    ```
    

## Header files

- [`math.h`](https://www.w3schools.com/c/c_ref_math.php)

## File handling

```c
FILE *fptr; // Declare a pointer of type FILE
fptr = fopen(filename, mode); // Open the file (same directory as C file)
fclose(fptr); // Close the file (good practice)
```

### `mode`

`fptr = fopen("filename.txt", "a");`

`w` - overwrite (Creates if doesn’t exist)

`a` - append (Creates if doesn’t exist)

`r` - reads

### Specific folder

```c
fptr = fopen("/Users/thisalkenula/Desktop/file_created.txt", "w");
```

### Write to file

`fprintf(fptr, "Hello World");`

Overwrites or appends depending on the mode

### Read a file

- Read one line
    
    ```c
    FILE *fptr;
        fptr = fopen("/Users/thisalkenula/Desktop/file_created.txt", "r");
        char myString[100];
        // fgets(whereToStore, maximumSizeOfDataToRead, filePointer)
        **fgets(myString, 100, fptr);** // Reads only one line
        printf("%s", myString);
        fclose(fptr);
    ```
    
    - Read line by line
        
        ```c
        fgets(myString, 100, fptr);
        printf("%s", myString); // prints 1st line
        fgets(myString, 100, fptr);
        printf("%s", myString); // Prints 2nd line
        ```
        
        - `fgets` automatically updates when executing
            
            When first line is read, `fptr` (Pointer) gets updated to read the next character
            
- Read multiple lines
    
    ```c
    while(fgets(myString, 100, fptr)) {
      printf("%s", myString);
    }
    ```
    
    - `fgets` return `NULL` at the end of the file
        
        This can be used to check if a file exist
        
        ```c
        FILE *fptr;
        
        // Open a file in read mode
        fptr = fopen("filename.txt", "r");
        
        // Store the content of the file
        char myString[100];
        
        // If the file exist
        if(fptr != NULL) {
        
          // Read the content and print it
          while(fgets(myString, 100, fptr)) {
            printf("%s", myString);
          }
        
        // If the file does not exist
        } else {
          printf("Not able to open the file.");
        }
        
        // Close the file
        fclose(fptr);
        ```
        

## Structs

```c
struct myStruct {
    int myNum;
    char myLetter;
}**;**
```

### Create and access

```c
struct myStruct {
    int myNum;
    char myLetter;
};

int main() {
    struct myStruct s1; // myStruct variable called s1

    // Assign values to mem=bers of s1
    s1.myNum = 23;
    s1.myLetter = 't';

    return 0;
}
```

### Can’t assign strings directly

```c
struct myStruct s1;
// s1.myString = "Thisal" is not valid
strcpy(s1.myString, "Thisal") // #include <string.h>
```

### Assign values at declaration

```c
struct myStruct s1 = {23, 'T', "Thisal"};
// No need for `strcpy` for strings
```

### Copy structs

**`s2 = s1;`**

## Enumeration

Set of named integer constants

```c
enum LEVEL {
    LOW,
    MEDIUM,
    HIGH
};
```

### Use

```c
int main() {
    enum LEVEL myvar = HIGH; // create enum variable and assign value
    return 0;
}
```

- Value of the variables
    
    ```c
    printf("%d", myvar); //2
    ```
    
    By default: `LOW` = 0, `MEDIUM` = 1, `HIGH` = 2 etc.
    
    - Specify value
        
        ```c
        enum LEVEL {
            LOW = 25,
            MEDIUM = 50,
            HIGH= 75
        };
        ```
        
        ```c
        enum LEVEL {
            LOW = 5,
            MEDIUM, // 6
            HIGH // 7
        };
        ```
        

## Memory management

### Memory address

- `*` : Pointer, `&` : Address

```c
int myAge = 21;
printf("%p", &myAge); // 0x7ff7b357f308 (Hexadecimal of that byte)
```

- Pointers
    - Memory address of a specific byte in computer
    
    ```c
    int myAge = 21;
    // use {data type}* {variableName} to createa pointer variable
    int***** ptr = &myAge;
    // int *ptr = &myAge; or int * ptr; are also valid
    ```
    
    - Dereference
        
        ```c
        printf("%p", ptr); // 0x7ff7b764c308
        printf("%d", *****ptr); // 21
        // use `*` to get to value in that address
        ```
        
        - Modify pointer value
            - Will also change the original value
            
            ```cpp
            int myAge = 19;
            int* agePtr = &myAge;
            *agePtr = 20;
            printf("%d", myAge); // 20
            ```
            
    - Array names are pointers
        - Access first item
            
            ```c
            int myNumbers[4] = {25, 50, 75, 100};
            printf("%p\n", myNumbers); // 0x7ff7b0f162f0 (No need `&` 
            // because array name itself is a pointer for first element)
            printf("%p", &myNumbers[0]); // 0x7ff7b0f162f0
            ```
            
        - Access other items
            
            ```c
            int myNumbers[4] = {25, 50, 75, 100};
            printf("%p ", (myNumbers + 1)); // prints address of the second element
            printf("%d", *(myNumbers + 1)); // prints the value of the second element(50)
            ```
            
        - Change values of array
            
            ```c
            int myNumbers[4] = {25, 50, 75, 100};
            *myNumbers = 13;
            *(myNumbers+1) = 15;
            printf("%d, %d", myNumbers[0], myNumbers[1]); // 13, 15
            ```
            
        
        Strings are also arrays
        
    - `NULL`
        
        ```c
        int *ptr = NULL;  // Assign NULL to a pointer
        // ptr doesn't point to any valid memory address
        ```
        
    - Increment pointer
        
        ```c
        int *intPtr = malloc(8); // Allocates 8 bytes (enough for two integers)
        intPtr++; // Moves the pointer 4 bytes ahead to the next integer
        
        char *charPtr = (char*) intPtr; // Reinterprets the same pointer as a char*
        charPtr++; // Moves the pointer 1 byte ahead to the next character
        ```
        

### Allocate(reserve) memory

- Static
    
    Memory reserved for variables before the program runs
    
    ```c
    // Example
    int students[20];
    printf("%lu", sizeof(students)); // 20*4 = 80 bytes
    ```
    
- Dynamic
    - Memory allocated after the program starts running
    - Offers full control over memory
    - Stack memory
        - Reserved for variables declared inside functions
        - Allocates when a function is called and memory is freed on return
        - Recursion that repeats too many times take too much stack memory: **Stack overflow**
        
    - Allocate memory
        
        `#include <stdlib.h>`
        
        - `malloc`: Allocates memory(does not initialize) and returns pointer
            
            If you print the values immediately after allocation, likely to see garbage values(i.e whatever data was there before allocation)
            
            ```c
            int *ptr1 = malloc(size);
            ```
            
        - `calloc`: Allocates memory(initializes) and returns pointer
            
            ```c
            int *intArray = calloc(5, sizeof(int));
            // int *pointer = calloc(amount, size)
            ```
            
            - Allocates memory for 5 integers.(5*4=20bytes)
            - All the bits are initialized to `0`
    - Access memory
        
        ```c
        int *students; // Create pointer for students array
        int numStudents = 12; // Number of students
        students = calloc(numStudents, sizeof(*students)); // sizeof(int), not sizeof(pointer)
        students[0] = 1056; // Store student IDs
        printf("%lu bytes", numStudents * sizeof(*students)); // 48 bytes
        ```
        
    - Typecasting
        
        ```c
        int *ptr1 = malloc(4);
        char *ptr2 = (char*) ptr1; // Typecasting: Tells to treat ptr1 as char*
        *ptr1 = 1684234849;
        printf("%d is %c %c %c %c", *ptr1, ptr2[0], ptr2[1], ptr2[2], ptr2[3]);
        // 1684234849 is a b c d
        ```
        

### Reallocate Memory

- Reserves a different amount of memory while keeping the data
- Tries to resize at the same memory address. If couldn’t, returns new address

```c
int *ptr2 = realloc(ptr1, size) // (oldPointer, newSize)
```

- Assign the result back to the original pointer, as the memory address may change
- Example
    
    ```c
    int *ptr1, *ptr2;
    ptr1 = malloc(4 * sizeof(int)); // 16 bytes are allocated at ptr1
    // But `ptr1` only refers to first item(4 bytes)
    printf("%lu bytes are allocated at %p\n", 4*sizeof(*ptr1), ptr1);
    
    ptr2 = realloc(ptr1, 6 * sizeof(int));
    printf("%lu bytes are allocated at %p", 6 * sizeof(*ptr2), ptr2);
    ```
    
    - `sizeof` doesn’t return the size of memory allocated, but the size of the type that the pointer is pointing
- Error Checking
    - `realloc()` returns `NULL` if unable to allocate more memory
    
    ```c
     int *ptr1, *ptr2;
    ptr1 = malloc(4); // Allocate memory
    
    ptr2 = realloc(ptr1, 6);  // Attempt to resize
    
    if(ptr2 == NULL) {
        printf("Faile to reallocate memory");
    }
    else {
        printf("Success");
        ptr1 = ptr2;
    }
    ```
    

### Deallocate Memory

- Should always free allocated memory when you’re  done using it
(Otherwise stays reserved until program ends)

```c
free(ptr1); // free(pointer)
```

- Set pointer to `NULL` to avoid accidentally using it again
    - If used again, you may corrupt data from other program or this program itself
    
    ```c
    ptr1 = NULL
    ```
    

### Memory leaks

- When dynamic memory is allocated → but never freed
- Happens when a pointer is lost
- Example
    
    ```c
    int x = 5;
    int *ptr;
    ptr = calloc(2, sizeof(*ptr));
    ptr = &x; // The address of the previos allocated memory is now lost
    ```