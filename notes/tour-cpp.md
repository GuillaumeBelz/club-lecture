
# Tour of C++, 2ème édition
## Chapitre 1: The Basics

C++ Core Guidelines

- [1] Don’t panic! All will become clear in time; §1.1; [CG: In.0].
- [2] Don’t use the built-in features exclusively or on their own. On the contrary, the fundamental (built-in) features are usually best used indirectly through libraries, such as the ISO C++ standard library (Chapters 8–15); [CG: P.10].
- [3] You don’t have to know every detail of C++ to write good programs.
- [4] Focus on programming techniques, not on language features.
- [5] For the final word on language definition issues, see the ISO C++ standard; §16.1.3; [CG:P.2].
- [6] ‘‘Package’’ meaningful operations as carefully named functions; §1.3; [CG: F.1].
- [7] A function should perform a single logical operation; §1.3 [CG: F.2].
- [8] Keep functions short; §1.3; [CG: F.3].
- [9] Use overloading when functions perform conceptually the same task on different types; §1.3.
- [10] If a function may have to be evaluated at compile time, declare it constexpr; §1.6; [CG: F.4].
- [11] Understand how language primitives map to hardware; §1.4, §1.7, §1.9, §2.3, §4.2.2, §4.4.
- [12] Use digit separators to make large literals readable; §1.4; [CG: NL.11].
- [13] Avoid complicated expressions; [CG: ES.40].
- [14] Avoid narrowing conversions; §1.4.2; [CG: ES.46].
- [15] Minimize the scope of a variable; §1.5.
- [16] Avoid ‘‘magic constants’’; use symbolic constants; §1.6; [CG: ES.45].
- [17] Prefer immutable data; §1.6; [CG: P.10].
- [18] Declare one name (only) per declaration; [CG: ES.10].
- [19] Keep common and local names short, and keep uncommon and nonlocal names longer; [CG:ES.7].
- [20] Avoid similar-looking names; [CG: ES.8].
- [21] Avoid ALL_CAPS names; [CG: ES.9].
- [22] Prefer the {}-initializer syntax for declarations with a named type; §1.4; [CG: ES.23].
- [23] Use auto to avoid repeating type names; §1.4.2; [CG: ES.11].
- [24] Avoid uninitialized variables; §1.4; [CG: ES.20].
- [25] Keep scopes small; §1.5; [CG: ES.5].
- [26] When declaring a variable in the condition of an if-statement, prefer the version with the implicit test against 0; §1.8.
- [27] Use unsigned for bit manipulation only; §1.4; [CG: ES.101] [CG: ES.106].
- [28] Keep use of pointers simple and straightforward; §1.7; [CG: ES.42].
- [29] Use nullptr rather than 0 or NULL; §1.7; [CG: ES.47].
- [30] Don’t declare a variable until you have a value to initialize it with; §1.7, §1.8; [CG: ES.21].
- [31] Don’t say in comments what can be clearly stated in code; [CG: NL.1].
- [32] State intent in comments; [CG: NL.2].
- [33] Maintain a consistent indentation style; [CG: NL.4].


## Chapitre 2: User-Defined Types

## Chapitre 3: Modularity

**Modules**

```cpp
// file Vector.cppm:
module; // this compilation will define a module

// ... here we put stuff that Vector might need for its implementation ...
export module Vector; // defining the module called "Vector"

export class Vector { 
public:
    Vector(int s);
    double& operator[](int i);
    int size();
private:
    double* elem; // elem points to an array of sz doubles int sz;
};

Vector::Vector(int s) : elem{new double[s]}, sz{s} // initialize members
{ 
}

double& Vector::operator[](int i) {
    return elem[i]; 
}

int Vector::size() {
    return sz; 
}

export int size(const Vector& v) { return v.size(); }

// file user.cpp:
import Vector; // get Vector’s interface

#include <cmath> // get the standard-library math function interface including sqrt()

double sqrt_sum(Vector& v) {
    double sum = 0;
    for (int i=0; i!=v.size(); ++i)
        sum+=std::sqrt(v[i]); 
    return sum; // sum of square roots
}
```

```cpp
// math1.cppm
export module math1;

export int add(int fir, int sec);

// math1.cpp
module math1;

int add(int fir, int sec){
    return fir + sec;
}

// main1.cpp
import math1;

int main(){
   add(2000, 20);
}
```

**Structured Binding**

```cpp
struct Entry { string name; int value; };
Entry read_entry(istream& is);
auto [n,v] = read_entry(is);
```

```cpp
map<string,int> m;
for (const auto [key,value] : m) ...
```

## Chapitre 4: Classes

>  By "better", I mean more correct, easier to maintain, more efficient, more elegant, easier to use, easier to read, and easier to reason about.

> A const member function can be invoked for both const and non-const objects, but a non-const member function can only be
> invoked for non-const objects.

- [1] Express ideas directly in code; §4.1; [CG: P.1].
- [11] Avoid ‘‘naked’’ new and delete operations; §4.2.2; [CG: R.11].
- [12] Use resource handles and RAII to manage resources; §4.2.2; [CG: R.1].


## Chapitre 5: Essential operations

## Chapitre 6: Templates

### 6.2.1 Constrained Template Arguments (C++20)

```cpp
template<Element T>
class Vector {
```

### 6.2.3 Template Argument Deduction (C++17)

```cpp
pair p = {1,5.2}; // p is a pair<int,double>
```

### 6.4.3 Compile-Time if (C++17)

```cpp
if constexpr(expression)
```

## Chapitre 7: Concepts and Generic Programming



