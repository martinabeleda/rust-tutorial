# Ownership in Rust

## What is ownership?

Ownership is a set of rules that govern how Rust manages memory. Languages like Python and Go have a garbage collector to hide memory management from the programmer. This means that the gc must periodically go and look for unused memory and free it. Languages like C and C++ require the program to explicitly allocate and free memory which opens up a whole category of errors that are usually only found at runtime. Rust has an ownership system which executes a series of checks at compile time so that if you violate the rules, the program won't compile.

The ownership model is what enables "fearless concurrency" in Rust.

## Ownership rules

1. Each value in Rust has an _owner_
2. There can only be one owner at a time
3. When an owner goes out of scope, the value is dropped

## Ownership is encoded in types

Allows you to encode who has ownership to some memory and "how". For some type `T`, you have:

Ownership

```rust
T   // You are the owner, which means you are responsible for freeing it
    // Rust implements the `Drop` trait on std lib structs. So memory is 
    // freed when `T` goes out of scope
```
Mutable reference:

```rust
&mut T  // Guarantees that you have exclusive access to `T`.
        // Which means there are no other readers **or** writers
        // This solves a whole class of concurrency bugs related
        // to race conditions
```

Immutable reference:

```rust
&T  // You are not allowed to modify `T` since `T` is shared
```

The magic of rust ownership is that the rust compiler will check that these ownership contracts are not violated for every variable/resource/memory you define in your program. This part of the compiler is referred to as the "borrow checker". Turns out that this model guarantees data races do not exist. Will result in a compile time error (rather than spooky runtime bugs that we get elsewhere).

## Lifetimes

References (`&mut T` and `&T`) have lifetimes that are tracked by the borrow checker. References cannot outlive the lifetime of the original `T`.

Guarantees free only once since the owner is responsible for freeing and the owner will free when `T` goes out of scope. No more "use after free" since the borrow checker enforces that references don't outlive the memory they point to.

## What does this mean for you as a developer?

Basically, rust forces you to use synchronization primitives (like a `Mutex`) if you want to access shared data.
