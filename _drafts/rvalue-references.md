# Rvalue references

Rvalue references solve at least two problems:

- Implementing move semantics
- Perfect forwarding

### lvalue vs rvalue

There are many definitions out there but maybe the followings are the more easiest to understand.

#### Definition before C++11

`lvalue`: is an expression e that may appear on the left or on the right hand side of an assignment.
```cpp
int a = 10;
int b = 20;
a = b; // ok, a and b are lvalues (because they are variables)
b = a; // ok, idem
```

`rvalue`: is an expression that can only appear on the right hand side of an assignment.
```cpp
// ...
a = a * b; // ok, a is a lvalue but a * b is an rvalue (this is an expression with an operation)
int c = a * b; // ok, idem, c is a lvalue but a * b is an rvalue
a * b = 42; // ERROR, rvalue on left hand side of assignment
```

#### Definition after C++11

`lvalue`: is an expression that refers to a memory location and allows us to take the address of that memory location via the `&` operator.
```cpp
// example 1
int i = 10;
i = 11;      // ok, i is an lvalue (because it is a variable)
int* ptr1 = &i; // ok, i is an lvalue (because it is a variable, and we can get his address)
// example 2
int& foo();
foo() = 42;         // ok, foo() is an lvalue (because returns it is an int&)
int* ptr2 = &foo(); // ok, foo() is an lvalue (because returns it is an int&, and we can get his address)
```

`rvalue`: is an expression that is not an lvalue.
```cpp
int foo();
int j = 0;
j = foo();        // ok, foo() is an rvalue (because returns an int)
int* p = &foo();  // ERROR, cannot take the address of an rvalue (because returns an int, and we cannot get his address)
j = 42;           // ok, 42 is an rvalue (42 is an int)
```