# Primer on C++

## Core syntax and primitives

### Variables and types
### Conditionals
### Strings
### Streams
### Arrays
### Maps
### Loops
### Functions
### Iterators
### Ranges
### References
### Pointers
### Classes
### Structs
### Enums
### Modules
### Standard library

#### Data structures
#### Algorithms

### Templates

## Error handling

### Compile time assertions

- `static_assert()`: Does not require any includes, checks for things known at compile time (_static_)
- `static_assert()` is provided a boolean expression and a string (error message)
- Compiler generates an error if expression doesn't evaluate to `true`
- `static_assert()` is typically used to investigate types
- Most common use case: Examine types within template code

```cpp
#include <type_traits>

template <typename T>
  T Square(T x) {
  static_assert(std::is_floating_point_v<T>,
    "Square requires a floating-point type");
  return x * x;
}

int main() {
  // main.cpp(5): error C2338: static_assert
  // failed: 'Square requires a floating-point type'
  Square("Hello"); 
}
```

### Compile time checks

- C++20 concepts are another form of compile-time checking

```cpp
#include <concepts>

auto Square(std::floating_point auto x) {
  return x * x;
}

int main() {
  Square(2.0);
  // main.cpp(9,3): 'Square': no matching overloaded function found
  // the associated constraints are not satisfied
  // the concept 'std::floating_point<int>' evaluated to false
  Square(2);
}
```

### Run time assertions

- `assert()` takes a boolean expression as an argument, program aborts if it evaluates to `false`

```cpp
#include <iostream>
#include <cassert>

class Character {
public:
  std::string GetName() {
    return "Legolas";
  };
};

void LogName(Character* Player) {
  assert(Player);  
  std::cout << Player->GetName();
}

int main() {
  // Assertion failed: Player, file main.cpp, line 12
  // cpp.exe (process 8640) exited with code 3.
  LogName(nullptr);
}
```

- Possible to provide a second argument to `assert()` (error message)

```cpp
int Divide(int x, int y) {
  // Assertion failed: ("Cannot divide by zero", y != 0), file main.cpp, line 4
  assert(("Cannot divide by zero", y != 0));
  return x/y;
}
```

```cpp
int Divide(int x, int y) {
  // Assertion failed: y != 0 && "Cannot divide by zero", file main.cpp, line 4
  assert(y != 0 && "Cannot divide by zero");
  return x/y;
}
```

- Calls to `assert()` have a performance impact, typically disabled for production
- `#define` a macro called `NDEBUG` (can be done prior to the directive that includes `<cassert>`)

```cpp
#include <iostream>
#define NDEBUG
#include <cassert>

int main() {
  assert(false);
  std::cout << "Program ran successfully";
}
```

- Third-party assert libraries like "boost assert" or "check" provide more features or clearer syntax compared to the standard `assert()`

### Exceptions

- `throw` generates errors called _exceptions_
- `throw` can lead to unreachable code

```cpp
#include <iostream>

int Divide(int x, int y) {
  if (y == 0) {
    throw 0;
    // Unreachable code
    std::cout << "Cannot divide by 0"; 
  }  
  return x / y;
}

int main() { Divide(5, 0); }
```

- `try` block: Contains code that might `throw` an exception
- `catch` block: Contains code that will be called if an exception was thrown
- Instead of immediately terminating, code is executed within the `catch` block, then the program continues as normal

```cpp
#include <iostream>

int main() {
  try {
    throw "Some Error";
  } catch (...) {
    std::cout << "I caught an error";
  }

  std::cout
    << "\nThe program can continue as normal";
}
```

- However, we can choose to return early from a `catch` statement (using normal `return`)
- Note: Exceptions can be a common cause of memory leaks; managed pointers can mitigate this

### Catching specific exceptions

- 

## Idiomatic style and project organization

### Forward declaration
### Headers / cpp files
### Namespaces
### Scope

## File handling and serialization

## Working with libraries

## Testing and debugging










### Operators

### Includes

### Preprocessor directives
### Build process

### Operator overloading
### Runtime polymorphism



**Types**

```cpp
int main() {
  // Integer
  int a;
  // Unsigned integers only store positive numbers.
  // As a result, they have a higher positive range.
  unsigned int b;
  // Character
  char c;
  // Short integer
  short d;
  // Long integer
  long e;
  // Floating point integer
  float f;
  // Double-precision floating point integer
  double g;
  // Boolean TRUE or FALSE
  bool h;
  // Automatically infer type. Not a type in itself.
  auto k = 1;
  return 0;
}
```

**Variables**

```cpp
#include <string>

int main() {
  // C-like initialization
  int a = 0;
  // Uniform initialization.
  // Does not allow narrowing conversions.
  int b {0};
  // Constructor initialization
  int c(0);
  char greeting_a[6] = {'H','e','l','l','o','\0'};
  char greeting_b[] = "Hello";
  char* greeting_c = "Hello";
  std::string greeting_d = "Hello";
  return 0;
}
```

**Type qualifiers**

```cpp
#include <atomic>

int main() {
  // a, once defined, is constant and cannot be changed
  const int a = 1;
  // b can only be modified by one thread at a time
  std::atomic<int> b;
  // c can be modified externally. The program will
  // check x's value before using it, even if it hasn't
  // been modified locally.
  volatile int c;
  return 0;
}
```

- Way of expressing additional information about a value through the type system to ensure correctness in the use of the data

**Typedef**

```cpp
#include <iostream>

typedef unsigned char byte;

int main() {
  byte b1 = 'c';
  return 0;
}
```

- Used to add an additional name to a type
- Useful when working with more complex types, making them more human readable

**If / else if / else**

```cpp
#include <iostream>

int main() {
  // One line if statement with optional init
  // statement before condition
  if (int x = 4 ; !x) std::cout << "x is 0" << std::endl;
  else if (x < 0) std::cout << "x is negative" << std::endl;
  // Or you can use a block
  else {
    std::cout << "x is positive" << std::endl;
  }
  return 0;
}
```

**Ternary operator**

```cpp
#include <iostream>

int main() {
  int x = 4;
  x < 0 ? std::cout << "x is negative" << std::endl : std::cout << "x is 0 or positive" << std::endl;
  return 0;
}
```

**Switch**

```cpp
#include <iostream>

int main() {
  int x = 2;
  switch(x) {
  case 1:
    std::cout << "One" << std::endl;
    // You must break the search or it will
    // fall through to the next match.
    break;
  case 2:
    std::cout << "Two" << std::endl;
    break;
  default:
    // If no match is found.
    break;
  }
  return 0;
}
```

**Arrays**

```cpp
#include <iostream>
#include <array>

int main() {
  std::array<int, 5> my_array;
  
  for(size_t i = 0; i < my_array.size(); i++) {
    my_array[i] = i;
  }
  
  std::cout << my_array[2] << std::endl;
  return 0;
}
```

- Stored at contiguous memory locations

**Strings**

```cpp
#include <string>

int main() {
  std::string str1 = "Hello";
  return 0;
}
```

- A string is an array of characters

**Functions**

```cpp
#include <iostream>

// Double the number passed in as 'x', returning
// the new value to the function caller.
int double_number_a(int x) {
  return 2 * x;
}

// Double the number pointed to by 'x', storing
// the result in the original variable.
void double_number_b(int* x) {
  *x *= 2;
}

int main() {
  auto num = 5;
  std::cout << double_number_a(num) << std::endl;
  std::cout << num << std::endl;
  double_number_b(&num);
  std::cout << num << std::endl;
  return 0;
}
```

**Inline functions**

```cpp
#include <iostream>

inline void square(int& x) {
  x *= x;
  return;
}

int main() {
  int num = 5;
  square(num);
  std::cout << num << std::endl;
  return 0;
}
```

- Directly include the given function in the caller code sequence
- Ensures that:
  - Function call overhead doesn’t occur
  - Overhead of push/pop variables on the stack is eliminated
  - Overhead of the return call is eliminated
  - Context-specific optimizations can be enabled at compile time
 
**Lambda expressions / functions**

```cpp

```

- 
 
**Variadic functions**

```cpp
#include <iostream>
#include <cstdarg>

int sum(int count, ...) {
  int total, i, temp;
  total = 0;
  va_list args;
  va_start(args, count);
  for(int i = 0; i < count; i++) {
    temp = va_arg(args, int);
    total += temp;
  }
  va_end(args);
  return total;
}

int main() {
  int numbers[3] = {5, 10, 15};
  int sum_of_numbers = sum(3, numbers[0], numbers[1], numbers[2]);
  std::cout << "Sum of the array: " << sum_of_numbers << std::endl;
  return 0;
}
```

- A function with an arbitrary argument count for more flexibility

**Range**

```cpp
#include <iostream>
#include <vector>
 
int main() {
  std::vector<int> v = {0, 1, 2, 3};
  for(const int& i : v) { // access using const reference
    std::cout << i << std::endl;
  }
  int a[] = {4, 5, 6, 7};
  for(auto n : a) { // the initializer can be an array
    std::cout << n << std::endl;
  }
  return 0;
}
```

- More readable equivalent to a traditional loop when iterating over a range of data

**For**

```cpp
#include <iostream>

int main() {
  for (auto i = 1; i <= 3; i++) {
    std::cout << i << std::endl;
  }
  return 0;
}
```

**While**

```cpp
#include <iostream>

int main() {
  auto x = 1;
  while(x <= 3) {
    std::cout << x++ << std::endl;
  }
  return 0;
}
```

**Do while**

```cpp
#include <iostream>

int main() {
  auto x = 1;
  do {
    std::cout << x++ << std::endl;
  } while(x <= 3);
  return 0;
}
```

**Goto**

```cpp
#include <iostream>

int main() {
  int x;
  std::cin >> x;
  if (x < 3) goto cleanup;
  // Program code here
cleanup:
  return 0;
}
```

- Jump beyween code sections
- Can promote bad code decisions

**Pointers**

```cpp
#include <iostream>

int main() {
  int* x; // pointer to type int
  return 0;
}
```

- A pointer is a variable that can hold the address of another variable
- They must have their own type which refers to the type of the data at the address pointed to

```cpp
#include <iostream>

int main() {
  int x[5];
  int* x_ptr = &x[0];
  std::cout << "Value of x_ptr = " << x_ptr << std::endl;
  std::cout << "Value of x_ptr + 1 = " << x_ptr + 1 << std::endl;
  char y[5];
  char* y_ptr = &y[0];
  std::cout << "Value of y_ptr = " << y_ptr << std::endl;
  std::cout << "Value of y_ptr + 1 = " << y_ptr + 1 << std::endl;
  return 0;
}
```

- Pointer arithmetic:
  - Perform integer addition or subtraction operations on pointers
  - Taking the data type’s size into account to return the correct address of the next item

```cpp
#include <iostream>

int main() {
  int x = 5;
  std::cout << "The address of x is " << &x << std::endl;
  return 0;
}
```

- Address resolution operator: **`&`** before a variable name to use it's address in memory rather than the stored value

```cpp
#include <iostream>

int main() {
  int x = 4;  
  int* y = &x;
  std::cout << "The value stored at x is " << *y << std::endl;
  return 0;
}
```

- Deference operator: **`*`** before a variable name to use the value it points to rather than the address stored

**Pass by reference**

```cpp
#include <iostream>

void square(int& x) {
  x *= x;
  return;
}

int main() {
  int x = 2;
  square(x);
  std::cout << x << std::endl;
  return 0;
}
```

- Use the **`&`** symbol as an alternative to passing an address by pointer or passing by value

**Structs**

```cpp
#include <iostream>

struct my_struct {
  int x;
  int y;
};

int main() {
  struct my_struct object1;
  object1.x = 1;
  std::cout << object1.x << std::endl;
  return 0;
}
```

- Structs: User defined data storage objects
- Contain public members by default

**Union**

```cpp
#include <iostream>

union my_data {
  int i;
  float f;
  char str[20];
};

int main() {
  union my_data object1;        
  std::cout << "Size of my_data union: " << sizeof(object1) << std::endl;
  return 0;
}
```

- Special data type that can store different data types at the same memory location
- You can define a union with many members, but only one member can contain a value at any given time
- Provide an efficient way of using the same memory location for multiple purposes
- A union’s size will be the size of the largest constituent type

**Classes**

```cpp
#include <iostream>

class human {
public:
  int height;
  int weight;
};

int main() {
  human john;
  john.height = 180;
  john.weight = 220;
  return 0;
}
```

- User-defined data structure template declared with keyword `class` containing member functions and data

**Methods**

```cpp
#include <iostream>

class human {
public:
  int height;
  int weight;
  int get_height() const {
    return height;
  }
  int get_weight() const {
    return weight;
  }
};

int main() {
  human john;
  john.height = 180;
  john.weight = 220;
  std::cout << john.get_height() << std::endl;
  std::cout << john.get_weight() << std::endl;
  return 0;
}
```

- Functions of a class

**Constructors & destructors**

```cpp
#include <iostream>

class human {
public:
  int height;
  int weight;
  human(int h, int w) {
    height = h;
    weight = w;
  }
  ~human(){};
  int get_height() const {
    return height;
  }
  int get_weight() const {
    return weight;
  }
};

int main() {
  human john(180, 220);
  std::cout << john.get_height() << std::endl;
  std::cout << john.get_weight() << std::endl;
  return 0;
}
```

- Constructor: Optional special member function of a class used to instantiate the class object
- It must take the same name as the class, with no return type
- Destructor: Optional special member function of a class called in the destruction of a class object
- It must take the same name as the class, preceded with `~`, and with no return type

**Encapsulation**
**Inheritance**
**Polymorphism**
**Virtual functions**
**Friend functions**
**Templates**

**Enumerations (enums)**

```cpp
#include <iostream>

enum week {
  mon,
  tue,
  wed,
  thu,
  fri,
  sat,
  sun
};

int main() {
  for(int i = mon; i <= sun; i++) {
      std::cout << i << std::endl; 
  } 
  return 0;
}
```

- User-defined data type
- Used to assign names to integral constants to make a program easier to read and maintain

**Structured bindings**


Slices
Maps

Return Values
Closures
Recursion
Range over built-in types

Structs
Classes
Methods
Interfaces
Enums
Struct Embedding

**Program arguments**

```cpp
#include <iostream>

int main(int argc, char* argv[]) {
  for(auto i = 0; i < argc; i++) {
    std::cout << argv[i] << std::endl;
  }
  return 0;
}
```

**Input & output**

```cpp
#include <iostream>

int main() {
  int x;
  std::cout << "Enter an integer value for x: ";
  std::cin >> x;
  std::cout << "The value at x is now: " << x << std::endl;
  return 0;
}
```

- C++ provides an abstraction built into the iostream header (_streams_), to perform input and output operations
- A stream is an entity that a program can use to either insert or extract data

## Error handling

**Exception handling**

```cpp

```

- 

Errors
Custom Errors

## Idiomatic style and code organization

**Project structure**

```
doc/       Only for software user guide
src/       Only for code: .cpp and .h files. May also contain a contrib/ directory.
test/      Only for integration and unit tests
Makefile   Makefile
Style.md   C++ style guide
_opt/      Everything else that is not required to build/test. Developer notes, scripts, linters, ci stuff, analysis tools etc.
```

**Namespaces**

```cpp
#include <iostream>

namespace ns_1 {
  void func() {
    std::cout << "Called from ns_1" << std::endl;
  }
}

namespace ns_2 {
  void func() {
    std::cout << "Called from ns_2" << std::endl;
  }
}

int main () {
  ns_1::func();
  ns_2::func(); 
  return 0;
}
```

- Declarative region that provides a named scope to its constituent identifiers
- Useful for organizing and reducing ambiguity in code
- The scope resolution operator `::` is used to access a scope's contents

**Modules**

```cpp
// foo.cpp
export module Foo;

namespace Bar {
  int f_internal() {
    return 10;
  }
  
  export int f() {
    return f_internal();
  }
}
```

```cpp
// main.cpp
import std;
import Foo;

int main() {
  std::cout << Bar::f() << std::endl;
  return 0;
}
```

## Testing and debugging

**Assertions**

```cpp
#include <assert.h>

int main() {
  int x = 1;
  assert(x == 2); // breaks the execution of the program
  return 0;
}
```

- Statements used to explicitly test assumptions made by the programmer
- Will be checked at runtime, or if static at compile time
- Typically used for unit testing

## Concurrency primitives

**Threads**

```cpp
#include <iostream>
#include <thread>

void thread_func() {
  std::cout << "Printing from Thread" << std::endl;
  return NULL;
}

int main() {
  std::thread thread_obj(thread_func);
  thread_obj.join();
  std::cout << "Thread returned" << std::endl;
  return 0;
}
```

- Used to execute one or more subthreads to allow for parallel processing in the same memory space

**Mutex**

```cpp
#include <iostream>
#include <thread>
#include <mutex>

typedef struct data {
  std::mutex mtx;
  int x;
} data;

void thread_func(data* d) { 
  d->mtx.lock()
  d->x = 2;   
  d->mtx.unlock()
  return;
}

int main() {
  data d;
  std::thread thread_obj(thread_func, &d);
  // Wait for thread to return before continuing execution
  thread_obj.join();
  std::cout << "x has safely been modified to " << d.x << std::endl; 
  return 0;
}
```

- Mutual exclusion functionality
- Can be used to serialize access of shared variables between concurrent threads

## Running and deployment
## Profiling and optimization
## Memory management and allocation patterns

**Storage class specifiers**

```cpp
int main() {
  // Defined elsewhere
  extern int a;
  // Automatic storage duration.
  // Also hints to the compiler to place
  // the object in the processor's register
  register int c;
  // Hold value between invocations
  static int b;
  // Thread storage duration
  thread_local int e;
  return 0;
}
```

- Define storage duration of an object

**Heap allocation**

```cpp
#include <iostream>

int main() {
  // Pointer to a heap-reserved integer
  int* p  = new int;
  // You must manually free any memory you allocated
  // on the heap or it will persist (memory leak)
  delete p;
  return 0;
}
```

- Memory can be allocated on the heap
- Heap: Unreserved and relatively large region of memory outside of the program’s memory scope

## Misc

---

Generics
Goroutines
Channels
Channel Buffering
Channel Synchronization
Channel Directions
Select
Timeouts
Non-Blocking Channel Operations
Closing Channels
Range over Channels
Timers
Tickers
Worker Pools
WaitGroups
Rate Limiting
Atomic Counters
Mutexes
Stateful Goroutines
Sorting
Sorting by Functions
Panic
Defer
Recover
String Functions
String Formatting
Text Templates
Regular Expressions
JSON
XML
Time
Epoch
Time Formatting / Parsing
Random Numbers
Number Parsing
URL Parsing
SHA256 Hashes
Base64 Encoding
Reading Files
Writing Files
Line Filters
File Paths
Directories
Temporary Files and Directories
Embed Directive
Testing and Benchmarking
Command-Line Arguments
Command-Line Flags
Command-Line Subcommands
Environment Variables
Logging
HTTP Client
HTTP Server
TCP Server
Context
Spawning Processes
Exec'ing Processes
Signals
Exit

## Credits

- [https://www.cbyexample.com/](https://www.cbyexample.com/)
- 
