---
title:  const keyword position on C++
tags: cpp
---

# About "const" keyword on C++

Try to always:

* use `const` as a suffix and
* read the declarations from right to left.

### Why is "const" better as a suffix?

`const` applies to the left-hand token, except when there is nothing there then it applies on the right-hand token.

#### Using references

The following two declarations using references are exactly the same:

```cpp
T const& ref; // more natural to read (because 'const' applies to the left hand token by default).
const T& ref;
```

But the following is totally INVALID:

```cpp
T& const ref;  // ref is a const reference to T, but that DOES NOT MAKE SENSE because "Once a reference is created, it cannot be later made to reference another object; it cannot be reseated".
```

Basically we have to remain that:

- Reference identifiers are read-only  (e.g. `T& ref` is valid, but a later `ref = ...` is INVALID).
- The 'const' qualifier cannot be applied to reference indentifiers (e.g. `T& """const""" ref` is INVALID).

#### Using pointers

The following two declarations using pointers are exactly the same:

```cpp
T const* ptr;   // more natural to read (because 'const' applies to the left hand token by default), ptr is a pointer to a 'const' object of type T.
const T* ptr;  // ptr is a pointer to a T object which is 'const'.
// *ptr = T2; is INVALID because the T object being pointed at is 'const'.
// T x = *p; is valid, since it only copies the T object being pointed at.
// ptr = &x; is valid, since ptr can be set to point at other T instances.
```

But the following is totally different:

```cpp
T* const ptr;  // ptr is a const pointer to T, that means that ptr always points at the same T object, but you can change that T object.
```

Finally you have this: the following is a pointer you can't change that points to a T object you can't change.

```cpp
T const* const ptr; // more natural to read (because 'const' applies to the left hand token by default), ptr is a pointer you can't change that points to a T object you can't change.
const T* const ptr;
```

### Conclusion

- (1) `<type>* const <param-name>` is more useful in function parameters. And is not the same as two below.
- (2) `<type> const* <name>` is useful anywhere you want to say -I'm not going to change the data you’re accessing-.
- (3) `const <type>* <name>` same as (2), but AVOID it because it is old-fashioned.
- (4) `<type> const* const <param-name>` is more useful in function parameters that promise dont to change anything.
