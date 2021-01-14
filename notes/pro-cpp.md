
# Professional C++, 4ème édition
# PART I - Introduction to Professional C++
## CHAPTER 1: A Crash Course in C++ and the Standard Library

Vocabulaire :
```cpp
using namespace std; // using directive
using std::cout;     // using declaration
```

Neasted namespace (C++17) :
```cpp
namespace MyLibraries::Networking::FTP {
/* ... */
}
```

Hexadecimal floating-point literals (C++17) : `0x3.ABCp-10`, `0Xb.cp12l`.

std::byte (C++17), dans `<cstddef>`

Initializer for if statements (C++17) `if (<initializer> ; <conditional_expression>) { <body> }`

`[[fallthrough]]` (C++17)
```
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

Initializer for switch statements (C++17) `switch (<initializer> ; <expression>) { <body> }`
