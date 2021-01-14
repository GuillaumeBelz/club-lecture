
# Professional C++, 4ème édition
# PART I - Introduction to Professional C++
## CHAPTER 1: A Crash Course in C++ and the Standard Library

- Vocabulaire :

```cpp
using namespace std; // using directive
using std::cout;     // using declaration
```

- Neasted namespace (C++17) :

```cpp
namespace MyLibraries::Networking::FTP {
    /* ... */
}
```

- Hexadecimal floating-point literals (C++17) : `0x3.ABCp-10`, `0Xb.cp12l`.

- std::byte (C++17), dans `<cstddef>`

- Initializer for if statements (C++17) `if (<initializer> ; <conditional_expression>) { <body> }`

- `[[fallthrough]]` (C++17)

```cpp
switch (backgroundColor) {
    case Color::DarkBlue:
        doSomethingForDarkBlue();
        [[fallthrough]];
    case Color::Black:
        doSomethingForBlackOrDarkBlue();
        break;
    case Color::Red: // [[fallthrough]] not necessary
    case Color::Green:
        // Code to execute for a red or green background color
        break; 
}
```

- Initializer for switch statements (C++17) `switch (<initializer> ; <expression>) { <body> }`

- Function Return Type Deduction (C++14)

```cpp
auto addNumbers(int number1, int number2)
{
    return number1 + number2;
}
```

- Structured Bindings (C++17)

```cpp
std::array<int, 3> values = { 11, 22, 33 };
auto [x, y, z] = values;

struct Point { double mX, mY, mZ; };
Point point;
point.mX = 1.0; point.mY = 2.0; point.mZ = 3.0; 
auto [x, y, z] = point;
```

- Initialization (C++17) (que `initializer_list<int> ` avec le C++14) :

```cpp
// Copy list initialization
auto a = {11}; // initializer_list<int> 
auto b = {11, 22}; // initializer_list<int>

// Direct list initialization
auto c {11}; // int
auto d {11, 22}; // Error, too many elements.
```


## Chapitre 2: Working with Stringsand String Views

