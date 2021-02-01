
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


## Chapitre 2: Working with Strings and String Views

- C++17 Low-Level Numeric Conversions (C++17). Dans `<charconv>`. Fast conversion. N'alloue pas la memoire.

```cpp
to_chars_result to_chars(char* first, char* last, IntegerT value, int base = 10); 
from_chars_result from_chars(const char* first, const char* last, IntegerT& value, int base = 10);

struct to_chars_result { 
    char* ptr;
    errc ec; 
};

std::string out(10, ' ');
auto [ptr, ec] = std::to_chars(out.data(), out.data() + out.size(), 12345); 
if (ec == std::errc()) { /* Conversion successful. */ }
```

- `string_view` et `string_view_literals` (C++17)

```cpp
using namespace std::string_view_literals;
auto sv = "My string_view"sv;
```

## Chapitre 3: Coding with Style


# PART II - Professional C++ Software Design
## Chapitre 4: Designing Professional C++ Programs
## Chapitre 5: Designing with Objects

- procédurale = qu'est-ce que cette tache fait ?
- objet = qu'est ce que cet objet fait ?

- class = "la pomme est un fruit" => définie les caractéristiques d'une catégorie d'objets
- object = "la pomme qui est posée sur la table est un fruit", instance d'une classe, un exemple concret

Philosophie: classe, composants, propriétés, comportements

Note: objet = debut+fin (lifetime, scope) + interactions

object interactions: has-a (aggregation), is-a (deriving, subclassing, extending, and inheriting). 
Note: dans Game Engine Architecture: "heritage = is-a, composition = has-a, aggregation = uses-a"

heritage = ajouter fonctionnalité, remplacer fonctionnalité, ajouter propriété, (remplacer propriété)

polymorphisme vs réutilisation de code (std::no_copyable)

## Chapitre 6: Designing for Reuse




