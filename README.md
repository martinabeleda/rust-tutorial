# Rust Tutorial

An introduction to rust. My goal for this series is to introduce you to rust and my hope is that by the end of this, you'll have an appreciation of the strengths & limitations of the language and (hopefully) be inspired to consider it for future projects.

## What is Rust?

- A "systems programming" built by Mozilla
- "Fast, reliable productive - pick three"
- "Fearless concurrency"
- Community driven and open source

## How is it different?

- Powerful type system - high level abstractions
- Zero cost abstractions - C-like speed
- Borrow checker - safe concurrency without garbage collection
- Modern toolchain - comes with formatting, dependency management, builds, deploy, documentation out of the box

## Where is it useful

- Low level systems programming - interoperable with C/C++. Originally developed for the Firefox browser and "swapping out components" that were in C and are highly concurrent.
- High level systems code: Network servers, databases
- Tools and infrastructure, CLIs 

## What is great about it?

- In rust, a large category of concurrency bugs are _impossible_. The rust compiler will fail with a warning if you have two concurrent write references to a variable. Allows for things like multiple immutable readers but no concurrent mutable and immutable readers which leads to race conditions.
- No more use-after-free. Rust ownership model guarantees at compile time that memory isn't referenced after it is freed (or dropped)
- Rich enums which can contain data too.
- Explicit error handling though the `Result<>` type. Provides syntax for handling errors easily when writing prototyping code but enforces all errors are either explicitly handled or panics on spot.
- Great pattern matching which allows you to handle results, unwrap enums containing data and act on conditionals on the data.
- All tooling is built into the language (cargo)
    - :white_check_mark: Dependency management through direct dependencies and lock files
    - :white_check_mark: Documentation built-in - cargo automatically publishes docs from your docstrings to docs.rs and tests all code examples. Automatically interlinked with other crates (packages)
    - :white_check_mark: Testing built-in
    - :white_check_mark: Interoperability with C/C++/go/Python.

## Any limitations?

- Immature landscape for libraries - if you need something specialized, you need to build it yourself. Slowly getting there.
- Rapid prototyping - Rust forces you to write correct code. Highly involved type system. Forces you to deal with null conditions etc.

## How can I learn it?

I highly recommend the [official Rust book](https://doc.rust-lang.org/book/).

[Rustlings](https://github.com/rust-lang/rustlings) is a tutorial containing beginner examples and exercises.