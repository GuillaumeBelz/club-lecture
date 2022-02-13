
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

#### Automatically Joining Threads

`jthread`:

- automatically joins in its destructor.
- supports so-called cooperative cancellation. `std::stop_token, std::stop_source, std::get_stop_token, std::get_stop_source`

```cpp
jthread job { [](stop_token token) {
    while (!token.stop_requested()) {
        //...
    }
} };

job.request_stop();
```

#### Copying and Rethrowing Exceptions

```cpp
exception_ptr current_exception() noexcept;
[[noreturn]] void rethrow_exception(exception_ptr p);
template<class E> exception_ptr make_exception_ptr(E e) noexcept;
```

```cpp
void doSomeWork()
{
    for (int i { 0 }; i < 5; ++i) {
        cout << i << endl;
    }
    cout << "Thread throwing a runtime_error exception..." << endl;
    throw runtime_error { "Exception from thread" };
}

void threadFunc(exception_ptr& err)
{
    try {
        doSomeWork();
    } catch (...) {
        cout << "Thread caught exception, returning exception..." << endl;
        err = current_exception();
    }
}

void doWorkInThread()
{
    exception_ptr error;
    // Launch thread.
    thread t { threadFunc, ref(error) };
    // Wait for thread to finish.
    t.join();
    // See if thread has thrown any exception.
    if (error) {
        cout << "Main thread received exception, rethrowing it..." << endl;
        rethrow_exception(error);
    } else {
        cout << "Main thread did not receive any exception." << endl;
    }
}

int main()
{
    try {
        doWorkInThread();
    } catch (const exception& e) {
        cout << "Main function caught: '" << e.what() << "'" << endl;
    }
}
```

#### ATOMIC OPERATIONS LIBRARY

- `atomic<T>::is_lock_free()`
- `static atomic<T>::is_always_lock_free`
- `atomic_flag`

```cpp
class Foo { private: int m_array[123]; };
class Bar { private: int m_int; };

int main()
{
    atomic<Foo> f;
    // Outputs: 1 0
    cout << is_trivially_copyable_v<Foo> << " " << f.is_lock_free() << endl;
    
    atomic<Bar> b;
    // Outputs: 1 1
    cout << is_trivially_copyable_v<Bar> << " " << b.is_lock_free() << endl;
}
```

```cpp
bool atomic<T>::compare_exchange_strong(T& expected, T desired);

atomic<int> value { 10 };
cout << "Value = " << value << endl;
int fetched { value.fetch_add(4) };
cout << "Fetched = " << fetched << endl;
cout << "Value = " << value << endl;

- Atomic Smart Pointers (C++20) `atomic<std::shared_ptr<T>>`
- Atomic References (C++20) `std::atomic_ref`

- Using Atomic Types

```cpp
void increment(atomic<int>& counter) // or int
{
    for (int i { 0 }; i < 100; ++i) {
        ++counter;
        this_thread::sleep_for(1ms);
    }
}

int main()
{
    atomic<int> counter { 0 }; // or int
    vector<thread> threads;
    for (int i { 0 }; i < 10; ++i) {
        threads.push_back(thread { increment, ref(counter) });
    }
    for (auto& t : threads) {
        t.join();
    }
    cout << "Result = " << counter <<endl;
}

// C++20
void increment(int& counter)
{
    atomic_ref<int> atomicCounter { counter };
    for (int i { 0 }; i < 100; ++i) {
        ++atomicCounter;
        this_thread::sleep_for(1ms);
    }
}

int main()
{
    int counter { 0 };
    vector<thread> threads;
    for (int i { 0 }; i < 10; ++i) {
        threads.push_back(thread { increment, ref(counter) });
    }
    for (auto& t : threads) {
        t.join();
    }
    cout << "Result = " << counter <<endl;
}

```

- Waiting on Atomic Variables (C++20)

```cpp
atomic<int> value { 0 };

thread job { [&value] {
    cout << "Thread starts waiting." << endl;
    value.wait(0);
    cout << "Thread wakes up, value = " << value << endl;
} };

this_thread::sleep_for(2s);

cout << "Main thread is going to change value to 1." << endl;
value = 1;
value.notify_all();

job.join();
```

#### MUTUAL EXCLUSION

-  Spinlock

```cpp
atomic_flag spinlock = ATOMIC_FLAG_INIT; // Uniform initialization is not allowed.
static const size_t NumberOfThreads { 50 };
static const size_t LoopsPerThread { 100 };

void dowork(size_t threadNumber, vector<size_t>& data)
{
    for (size_t i { 0 }; i < LoopsPerThread; ++i) {
        while (spinlock.test_and_set()) { } // Spins until lock is acquired.
        // Save to handle shared data...
        data.push_back(threadNumber);
        spinlock.clear(); // Releases the acquired lock.
    }
}

int main()
{
    vector<size_t> data;
    vector<thread> threads;
    for (size_t i { 0 }; i < NumberOfThreads; ++i) {
        threads.push_back(thread { dowork, i, ref(data) });
    }
    for (auto& t : threads) {
        t.join();
    }
    cout << format("data contains {} elements, expected {}.\n", data.size(),
    NumberOfThreads * LoopsPerThread);
}
```
- Non-timed Mutex Classes: std::mutex, std::recursive_mutex, and std::shared_mutex. Functions: lock, try_lock, unlock.
- Timed Mutex Classes: : std::timed_mutex, std::recursive_timed_mutex, and std::shared_timed_mutex. Functions: try_lock_for(rel_time) and try_lock_until(abs_time)

#### Locks

**lock_guard**: lock a mutex

- `explicit lock_guard(mutex_type& m);`
- `lock_guard(mutex_type& m, adopt_lock_t);`

**unique_lock**

- `explicit unique_lock(mutex_type& m);`
- `unique_lock(mutex_type& m, defer_lock_t) noexcept;`
- `unique_lock(mutex_type& m, try_to_lock_t);`
- `unique_lock(mutex_type& m, adopt_lock_t);`
- `unique_lock(mutex_type& m, const chrono::time_point<Clock, Duration>& abs_time);`
- `unique_lock(mutex_type& m, const chrono::duration<Rep, Period>& rel_time);`

Acquiring Multiple Locks at Once:

```cpp
mutex mut1;
mutex mut2;
void process()
{
    unique_lock lock1 { mut1, defer_lock };
    unique_lock lock2 { mut2, defer_lock };
    lock(lock1, lock2);
    // Locks acquired.
} // Locks automatically released.
```

**shared_lock**

**scoped_lock**: same as `lock_guard` with multiple mutex.

```cpp
mutex mut1;
mutex mut2;
void process()
{
    scoped_lock locks { mut1, mut2 };
    // Locks acquired.
} // Locks automatically released.
```

#### std::call_once

```cpp
once_flag g_onceFlag;

void initializeSharedResources()
{
    // ... Initialize shared resources to be used by multiple threads.
    cout << "Shared resources initialized." << endl;
}

void processingFunction()
{
    // Make sure the shared resources are initialized.
    call_once(g_onceFlag, initializeSharedResources);
    // ... Do some work, including using the shared resources
    cout << "Processing" << endl;
}

int main()
{
    // Launch 3 threads.
    vector<thread> threads { 3 };
    
    for (auto& t : threads) {
        t = thread { processingFunction };
    }
    
    // Join on all threads
    for (auto& t : threads) {
        t.join();
    }
}
```

#### Examples Using Mutual Exclusion Objects

- **Synchronized Streams (C++20)**. `std::basic_osyncstream` : synchrone output stream.

```cpp
class Counter
{
public:
    Counter(int id, int numIterations)
        : m_id { id }, m_numIterations { numIterations } { }
        
    void operator()() const
    {
        for (int i { 0 }; i < m_numIterations; ++i) {
            osyncstream { cout } << "Counter "
                << m_id << " has value " << i << endl;
        }
    }
    
private:
    int m_id;
    int m_numIterations;
};

// Or:
void operator()() const
{
    for (int i { 0 }; i < m_numIterations; ++i) {
        osyncstream syncedCout { cout };
        syncedCout << "Counter " << m_id << " has value " << i << endl;
    }
}
```

- **Using Mutex**

```cpp
class Counter
{
public:
    Counter(int id, int numIterations)
        : m_id { id }, m_numIterations { numIterations } { }
        
    void operator()() const
    {
        for (int i { 0 }; i < m_numIterations; ++i) {
            lock_guard lock { ms_mutex };
            cout << "Counter " << m_id << " has value " << i << endl;
        }
    }
    
private:
    int m_id;
    int m_numIterations;
    inline static mutex ms_mutex;
};
```

- **Using Timed Locks**

```cpp
class Counter
{
public:
    Counter(int id, int numIterations)
        : m_id { id }, m_numIterations { numIterations } { }
        
    void operator()() const
    {
        for (int i { 0 }; i < m_numIterations; ++i) {
        unique_lock lock { ms_timedMutex, 200ms };
            if (lock) {
                cout << "Counter " << m_id << " has value " << i << endl;
            } else {
                // Lock not acquired in 200ms, skip output.
            }
        }
    }
    
private:
    int m_id;
    int m_numIterations;
    inline static timed_mutex ms_timedMutex;
};
```

- **Double-Checked Locking** (anti pattern)
- **magic static**

#### CONDITION VARIABLES

- `std::condition_variable`
- `std::condition_variable_any`

Methods:

- `notify_one();`
- `notify_all();`
- `wait(unique_lock<mutex>& lk);`
- `wait_for(unique_lock<mutex>& lk, const chrono::duration<Rep, Period>& rel_time);`
- `wait_until(unique_lock<mutex>& lk, const chrono::time_point<Clock, Duration>& abs_time);`

#### LATCHES (C++20)

```cpp
latch startLatch { 1 };
vector<jthread> threads;

for (int i { 0 }; i < 10; ++i) {
    threads.push_back(jthread { [&startLatch] {
        // Do some initialization... (CPU bound)
        
        // Wait until the latch counter reaches zero.
        startLatch.wait();
        
        // Process data...
    } });
}

// Load data... (I/O bound)

// Once all data has been loaded, decrement the latch counter
// which then reaches zero and unblocks all waiting threads.
startLatch.count_down();
```

#### BARRIERS (C++20)

```cpp
void completionFunction() noexcept { /* ... */ }

int main()
{
    const size_t numberOfThreads { 4 };
    barrier barrierPoint { numberOfThreads, completionFunction };
    vector<jthread> threads;
    
    for (int i { 0 }; i < numberOfThreads; ++i) {
        threads.push_back(jthread { [&barrierPoint] (stop_token token) {
            while (!token.stop_requested()) {
                // ... Do some calculations ...
                // Synchronize with other threads.
                barrierPoint.arrive_and_wait();
            }
        } });
    }
}
```

#### SEMAPHORES (C++20)

- `std::counting_semaphore` and `std::binary_semaphore` 

Methods:
- `acquire()`
- `try_acquire()`
- `try_acquire_for()`
- `try_acquire_until()`
- `release()`

```cpp
counting_semaphore semaphore { 4 };
vector<jthread> threads;

for (int i { 0 }; i < 10; ++i) {
    threads.push_back(jthread { [&semaphore] {
        semaphore.acquire();
        // ... Slot acquired ... (at most 4 threads concurrently)
        semaphore.release();
    } });
}
```

#### Futures

>  a promise is the input side for a result, a future is the output side

```cpp
future<T> myFuture { ... }; // Is discussed later.
T result { myFuture.get() };

if (myFuture.wait_for(0)) { // Value is available.
    T result { myFuture.get() };
} else { // Value is not yet available.
    ...
}
```

```cpp
void doWork(promise<int> thePromise)
{
    // ... Do some work ...
    // And ultimately store the result in the promise.
    thePromise.set_value(42);
}

int main()
{
    // Create a promise to pass to the thread.
    promise<int> myPromise;

    // Get the future of the promise.
    auto theFuture { myPromise.get_future() };
    
    // Create a thread and move the promise into it.
    thread theThread { doWork, move(myPromise) };
    
    // Do some more work...
    
    // Get the result.
    int result { theFuture.get() };
    cout << "Result: " << result << endl;
    
    // Make sure to join the thread.
    theThread.join();
}
```

- `std::packaged_task`

```cpp
int calculateSum(int a, int b) { return a + b; }

int main()
{
    // Create a packaged task to run calculateSum.
    packaged_task<int(int, int)> task { calculateSum };
    
    // Get the future for the result of the packaged task.
    auto theFuture { task.get_future() };
    
    // Create a thread, move the packaged task into it, and
    // execute the packaged task with the given arguments.
    thread theThread { move(task), 39, 3 };
    
    // Do some more work...

    // Get the result.
    int result { theFuture.get() };
    cout << result << endl;
    
    // Make sure to join the thread.
    theThread.join();
}
 ```

#### std::async

- `launch::async`, `launch::deferred`, `launch::async | launch::deferred`

```cpp
int calculate() { return 123; }
int main()
{
    auto myFuture { async(calculate) };
    //auto myFuture { async(launch::async, calculate) };
    //auto myFuture { async(launch::deferred, calculate) };
    
    // Do some more work...
    
    // Get the result.
    int result { myFuture.get() };
    cout << result << endl;
}
```

- note: `async(calculate);` no capture of future = blocking call (blocked in the destructor of the temporary future)

#### Exception Handling

```cpp
int calculate()
{
    throw runtime_error { "Exception thrown from calculate()." };
}

int main()
{
    // Use the launch::async policy to force asynchronous execution.
    auto myFuture { async(launch::async, calculate) };
    
    // Do some more work...
    
    // Get the result.
    try {
        int result { myFuture.get() };
        cout << result << endl;
    } catch (const exception& ex) {
        cout << "Caught exception: " << ex.what() << endl;
    }
}
```

#### std::shared_future

copy constructible, many calls to `get()` possible

```cpp
promise<void> thread1Started, thread2Started;

promise<int> signalPromise;
auto signalFuture { signalPromise.get_future().share() };
//shared_future<int> signalFuture { signalPromise.get_future() };

auto function1 { [&thread1Started, signalFuture] {
    thread1Started.set_value();
    // Wait until parameter is set.
    int parameter { signalFuture.get() };
    // ...
} };

auto function2 { [&thread2Started, signalFuture] {
    thread2Started.set_value();
    // Wait until parameter is set.
    int parameter { signalFuture.get() };
    // ...
} };

// Run both lambda expressions asynchronously.
// Remember to capture the future returned by async()!
auto result1 { async(launch::async, function1) };
auto result2 { async(launch::async, function2) };

// Wait until both threads have started.
thread1Started.get_future().wait();
thread2Started.get_future().wait();

// Both threads are now waiting for the parameter.
// Set the parameter to wake up both of them.
signalPromise.set_value(42);
```

#### EXAMPLE: MULTITHREADED LOGGER CLASS

```cpp
export class Logger
{
public:
    // Starts a background thread writing log entries to a file.
    Logger();
    
    // Gracefully shut down background thread.
    virtual ~Logger();
    
    // Prevent copy construction and assignment.
    Logger(const Logger& src) = delete;
    Logger& operator=(const Logger& rhs) = delete;
    
    // Add log entry to the queue.
    void log(std::string entry);
    
private:
    // The function running in the background thread.
    void processEntries();
    
    // Helper method to process a queue of entries.
    void processEntriesHelper(std::queue<std::string>& queue, std::ofstream& ofs) const;
    
    // Mutex and condition variable to protect access to the queue.
    std::mutex m_mutex;
    std::condition_variable m_condVar;
    std::queue<std::string> m_queue;
    
    // The background thread.
    std::thread m_thread;

    // Boolean telling the background thread to terminate.
    bool m_exit { false };
};

Logger::Logger()
{
    // Start background thread.
    m_thread = thread { &Logger::processEntries, this };
}

Logger::~Logger()
{
    {
        unique_lock lock { m_mutex };
        // Gracefully shut down the thread by setting m_exit to true.
        m_exit = true;
    }
    
    // Notify condition variable to wake up thread.
    m_condVar.notify_all();
    
    // Wait until thread is shut down. This should be outside the above code
    // block because the lock must be released before calling join()!
    m_thread.join();
}

void Logger::log(string entry)
{
    // Lock mutex and add entry to the queue.
    unique_lock lock { m_mutex };
    m_queue.push(move(entry));
    
    // Notify condition variable to wake up thread.
    m_condVar.notify_all();
}

void Logger::processEntries()
{
    // Open log file.
    ofstream logFile { "log.txt" };
    if (logFile.fail()) {
        cerr << "Failed to open logfile." << endl;
        return;
    }

    // Create a lock for m_mutex, but do not yet acquire a lock on it.
    unique_lock lock { m_mutex, defer_lock };
    
    // Start processing loop.
    while (true) {
        lock.lock();
        
        if (!m_exit) { // Only wait for notifications if we don't have to exit.
            this_thread::sleep_for(1000ms); // Needs import <chrono>;
            m_condVar.wait(lock);
        } else {
            processEntriesHelper(localQueue, logFile);
            break;
        }

        // Condition variable is notified, so something might be in the queue.
        // While we still have the lock, swap the contents of the current queue
        // with an empty local queue on the stack.
        queue<string> localQueue;
        localQueue.swap(m_queue);

        // Now that all entries have been moved from the current queue to the
        // local queue, we can release the lock so other threads are not blocked
        // while we process the entries.
        lock.unlock();

        // Process the entries in the local queue on the stack. This happens after
        // having released the lock, so other threads are not blocked anymore.
        processEntriesHelper(localQueue, logFile);
    }
}

void Logger::processEntriesHelper(queue<string>& queue, ofstream& ofs) const
{
    while (!queue.empty()) {
        ofs << queue.front() << endl;
        queue.pop();
    }
}

void logSomeMessages(int id, Logger& logger)
{
    for (int i { 0 }; i < 10; ++i) {
        logger.log(format("Log entry {} from thread {}", i, id));
    }
}

int main()
{
    Logger logger;
    vector<thread> threads;
    
    // Create a few threads all working with the same Logger instance.
    for (int i { 0 }; i < 10; ++i) {
        threads.emplace_back(logSomeMessages, i, ref(logger));
    }
    
    // Wait for all threads to finish.
    for (auto& t : threads) {
        t.join();
    }
}
```

#### COROUTINES (C++20)

- `co_await`, `co_return`, `co_yield`

```cpp
experimental::generator<int> getSequenceGenerator(int startValue, int numberOfValues)
{
    for (int i { startValue }; i < startValue + numberOfValues; ++i) {
        // Print the local time to standard out, see Chapter 22.
        time_t tt { system_clock::to_time_t(system_clock::now()) };
        tm t;
        localtime_s(&t, &tt);
        cout << put_time(&t, "%H:%M:%S") << ": ";
        // Yield a value to the caller, and suspend the coroutine.
        co_yield i;
    }
}

int main()
{
    auto gen { getSequenceGenerator(10, 5) };
    for (const auto& value : gen) {
        cout << value << " (Press enter for next value)";
        cin.ignore();
    }
}
```

## Part V - C++ Software Engineering

### Chapitre 28 - Maximizing Software Engineering Methods


































