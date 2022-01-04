
# Professional C++, 5ème édition

Codes téléchargeables sur www.wiley.com/go/proc++5e

## PART I - Introduction to Professional C++
### Chapitre 1 - A Crash Course in C++ and the Standard Library

- (C++20) : modules

```cpp
// avant C++20
#include <iostream>

// C++20
import <iostream>;
```

```cpp
// in employee.cppm
export module employee;

export struct Employee {
    char firstInitial;
    char lastInitial;
    int employeeNumber;
    int salary;
};

// in main.cpp
import employee;

int main()
{
    // Create and populate an employee.
    Employee anEmployee;
}
```

- (C++20) : `format`

```cpp
// avant C++20
std::cout << "There are " << 219 << " ways I love you." << std::endl;

// C++20
std::cout << std::format("There are {} ways I love you.", 219) << std::endl;
```

- Vocabulaire :

```cpp
using namespace std; // using directive
using std::cout;     // using declaration
```

- Neasted namespace (C++17) :

```cpp
// avant C++17
namespace MyLibraries {
    namespace Networking {
        namespace FTP {
            /* ... */
        }
    }
}

// C++17
namespace MyLibraries::Networking::FTP {
    /* ... */
}
```

- Hexadecimal floating-point literals (C++17) : `0x3.ABCp-10`, `0Xb.cp12l`.

- std::byte (C++17), dans `<cstddef>`

- using enum declaration (C++20) 

```cpp
using enum PieceType;
```

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


### Chapitre 2 - Working with Strings and String Views

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

### Chapitre 3 - Coding with Style


## PART II - Professional C++ Software Design
### Chapitre 4 - Designing Professional C++ Programs
### Chapitre 5 - Designing with Objects

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

### Chapitre 6: Designing for Reuse


### Chapitre 11: ODDS AND ENDS

#### Modules (C++20)

- module interface file `.cppm`

```cpp
// person.cppm
module; // Start of the global module fragment, optional
#include <cstddef> // Include legacy header files, only here

export module person; // Module declaration, begining of module purview

import <string>; // Import declaration

export class Person // Export declaration
{
public:
    Person(std::string firstName, std::string lastName)
        : m_firstName { std::move(firstName) }
        , m_lastName { std::move(lastName) } { }
        
    const std::string& getFirstName() const { return m_firstName; }
    const std::string& getLastName() const { return m_lastName; }
    
private:
    std::string m_firstName;
    std::string m_lastName;
};

// test.cpp
import person; // Import declaration for person module
import <iostream>;
import <string>; // For operator<< for std::string

using namespace std;

int main()
{
    Person person { "Kole", "Webb" };
    cout << person.getLastName() << ", " << person.getFirstName() << endl;
}
```

Export :

```cpp
export namespace DataModel
{
    class Person { /* ... */ };
    class Address { /* ... */ };
    using Persons = std::vector<Person>;
}

export
{
    namespace DataModel
    {
        class Person { /* ... */ };
        class Address { /* ... */ };
        using Persons = std::vector<Person>;
    }
}
```

- module implementation file `.cpp`

```cpp
// person.cppm
export module person; // Module declaration

import <string>;

export class Person
{
public:
    Person(std::string firstName, std::string lastName);
    const std::string& getFirstName() const;
    const std::string& getLastName() const;
    
private:
    std::string m_firstName;
    std::string m_lastName;
};

// person.cpp
module person; // Module declaration, but without the export keyword

// no import person or string, it's implicit

using namespace std;

Person::Person(string firstName, string lastName)
    : m_firstName { move(firstName) }, m_lastName { move(lastName) }
{
}

const string& Person::getFirstName() const { return m_firstName; }
const string& Person::getLastName() const { return m_lastName; }
```

- Submodules

```cpp
// datamodel.person.cppm
export module datamodel.person; // datamodel.person submodule
export namespace DataModel { class Person { /* ... */ }; }

// datamodel.address.cppm
export module datamodel.address; // datamodel.address submodule
export namespace DataModel { class Address { /* ... */ }; }

// datamodel.cppm
export module datamodel; // datamodel module
export import datamodel.person; // Import and export person submodule
export import datamodel.address; // Import and export address submodule
import <vector>;
export namespace DataModel { using Persons = std::vector<Person>; }
```

- Module Partitions (modules' structure not visible by users)

```cpp
// datamodel.person.cppm
export module datamodel:person; // datamodel:person partition
export namespace DataModel { class Person { /* ... */ }; }

// datamodel.address.cppm
export module datamodel:address; // datamodel:address partition
export namespace DataModel { class Address { /* ... */ }; }

// datamodel.cpp
module datamodel; // Not datamodel:address!
import <iostream>;
using namespace std;
DataModel::Address::Address() { cout << "Address::Address()" << endl; }

// datamodel.cppm
export module datamodel; // datamodel module (primary module interface file)
export import :person; // Import and export person partition
export import :address; // Import and export address partition
import <vector>;
export namespace DataModel { using Persons = std::vector<Person>; }

// main.cpp
import datamodel;
int main() { DataModel::Address a; }
```

- Implementation Partitions

```cpp
// math.cppm
export module math; // math module declaration
export namespace Math
{
    double superLog(double z, double b);
    double lerchZeta(double lambda, double alpha, double s);
}

// math_helpers.cpp
module math:details; // math:details implementation partition
double someHelperFunction(double a) { return /* ... */ ; }

// math.cpp
module math;
import :details;
double Math::superLog(double z, double b) { return /* ... */; }
double Math::lerchZeta(double lambda, double alpha, double s) { return /* ... */; }
```

#### HEADER FILES

- Querying Existence of Headers (C++17)

```cpp
__has_include("filename")
__has_include(<filename>)
```

```cpp
#if __has_include(<optional>)
    #include <optional>
#elif __has_include(<experimental/optional>)
    #include <experimental/optional>
#endif
```

- FEATURE TEST MACROS FOR CORE LANGUAGE FEATURES (C++20)

```cpp
__cpp_range_based_for
__cpp_binary_literals
__cpp_char8_t
__cpp_generic_lambdas
__cpp_consteval
__cpp_coroutines
__has_cpp_attribute(fallthrough)
...
```

## PART IV MASTERING ADVANCED FEATURES OF C++
### Chapitre 25 - Customizing and Extending the Standard Library
### Chapitre 26 - Advanced Templates

- type, non-type, and template template 

```cpp
template <typename Container>
concept ContainerType = requires(Container c)
{
    c.resize(1);
    typename Container::value_type;
};

export template <typename T, ContainerType Container>
class Grid
{
    ...
};

Grid<int, deque<optional<int>>> myDequeGrid;
Grid<int, vector<optional<int>>> myVectorGrid;
Grid<int> myVectorGrid2 { myVectorGrid };
```

- template template parameter

```cpp
export template <typename T,
    template <typename E, typename Allocator = std::allocator<E>> class Container = std::vector>
class Grid
{
    ...
};
```

- VARIADIC TEMPLATES

```cpp
template <typename... Types>
class MyVariadicTemplate { };
```

```cpp
void handleValue(int value) { cout << "Integer: " << value << endl; }
void handleValue(double value) { cout << "Double: " << value << endl; }
void handleValue(string_view value) { cout << "String: " << value << endl; }

void processValues() // Base case to stop recursion
{ /* Nothing to do in this base case. */ }

template <typename T1, typename... Tn>
void processValues(T1 arg1, Tn... args)
{
    handleValue(arg1);
    processValues(args...);
}
```

```cpp
void processValues() // Base case to stop recursion
{ /* Nothing to do in this base case.*/ }

template <typename T1, typename... Tn>
void processValues(T1&& arg1, Tn&&... args)
{
    handleValue(forward<T1>(arg1));
    processValues(forward<Tn>(args)...);
}

int numberOfArguments { sizeof...(args) };
```

- Variable Number of Mixin Classes

```cpp
template <typename... Mixins>
class MyClass : public Mixins...
{
public:
    MyClass(const Mixins&... mixins) : Mixins { mixins }... {}
    virtual ~MyClass() = default;
};

MyClass<Mixin1, Mixin2> a { Mixin1 { 11 }, Mixin2 { 22 } };
```

#### Fold Expressions

- Unary right fold `(pack Ѳ . . .)`
- Unary left fold `(. . . Ѳ pack)`
- Binary right fold `(pack Ѳ . . . Ѳ Init)`
- Binary left fold `(Init Ѳ . . . Ѳ pack)`

```cpp
template <typename... Tn>
void processValues(const Tn&... args)
{
    (handleValue(args), ...);
}

template <typename... Values>
void printValues(const Values&... values)
{
    ((cout << values << endl), ...);
}

template <typename T, typename... Values>
double sumValues(const T& init, const Values&... values)
{
    return (init + ... + values);
}
```

#### METAPROGRAMMING

- consteval (C++20)

```cpp
consteval unsigned long long factorial(unsigned char f)
{
    if (f == 0) { return 1; }
    else { return f * factorial(f - 1); }
}
```

- Loop Unrolling

```cpp
template <int i>
class Loop
{
public:
    template <typename FuncType>
    static inline void run(FuncType func) {
        Loop<i - 1>::run(func);
        func(i);
    }
};

template <>
class Loop<0>
{
public:
    template <typename FuncType>
    static inline void run(FuncType /* func */) { }
};

void doWork(int i) { cout << "doWork(" << i << ")" << endl; }

int main()
{
    Loop<3>::run(doWork);
}
```

- constexpr if (C++17)

```cpp
template <typename TupleType, int n = tuple_size<TupleType>::value>
void tuplePrint(const TupleType& t) {
    if constexpr (n > 1) {
        tuplePrint<TupleType, n - 1>(t);
    }
    cout << get<n - 1>(t) << endl;
}
```

- Using a Compile-Time Integer Sequence with Folding

```cpp
template <typename Tuple, size_t... Indices>
void tuplePrintHelper(const Tuple& t, index_sequence<Indices...>)
{
    ((cout << get<Indices>(t) << endl), ...);
}

template <typename... Args>
void tuplePrint(const tuple<Args...>& t)
{
    tuplePrintHelper(t, index_sequence_for<Args...>());
}

tuple t1 { 167, "Testing"s, false, 2.3 };
tuplePrint(t1);
```

- Using enable_if

```cpp
template <typename T1, typename T2>
enable_if_t<is_same_v<T1, T2>, bool>
    checkType(const T1& t1, const T2& t2)
{
    cout << format("'{}' and '{}' are the same types.", t1, t2) << endl;
    return true;
}

template <typename T1, typename T2>
enable_if_t<!is_same_v<T1, T2>, bool>
    checkType(const T1& t1, const T2& t2)
{
    cout << format("'{}' and '{}' are different types.", t1, t2) << endl;
    return false;
}

int main()
{
    checkType(1, 32);
    checkType(1, 3.01);
    checkType(3.01, "Test"s);
}
```

- Using constexpr if to Simplify enable_if Constructs

```cpp
template <typename T>
void callDoit(const T& [[maybe_unused]] t)
{
    if constexpr (is_base_of_v<IsDoable, T>) {
        t.doit();
    } else {
        cout << "Cannot call doit()!" << endl;
    }
}

template <typename T>
void callDoit(const T& [[maybe_unused]] t)
{
    if constexpr (is_invocable_v<decltype(&IsDoable::doit), T>) {
        t.doit();
    } else {
        cout << "Cannot call doit()!" << endl;
    }
}
```

### Chapitre 27 - Multithreaded Programming with C++

- Race Conditions, data race, `std::hardware_destructive_interference_size`

```cpp
// pointer function
thread t1 { counter, 1, 6 }; 

// function object
thread t1 { Object { 1, 20 } };
thread t2 { object };
thread t3 { std::ref(object) };

// lambda
thread t1 { [](){ ... });

// member function
 thread t { &Object::foo, &object };
 ```










