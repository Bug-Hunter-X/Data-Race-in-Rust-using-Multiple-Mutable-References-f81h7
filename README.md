# Data Race in Rust: Multiple Mutable References

This repository demonstrates a common data race error that can occur in Rust when multiple mutable references point to the same variable.  Understanding how to avoid these issues is crucial for writing safe and reliable Rust code.

## The Bug
The `bug.rs` file contains Rust code that creates two mutable references to a single integer.  Attempting to modify the integer through both references simultaneously leads to undefined behavior, causing a data race condition. The outcome may vary depending on compiler optimization and runtime conditions. This code exhibits a data race because it violates Rust's borrowing rules. 

## The Solution
The `bugSolution.rs` file shows one way to fix this problem: using only one mutable reference at a time or refactoring to avoid mutable references altogether. By making sure only one reference to `x` is mutable at a time we can prevent the race condition.  For example, using `RefCell` or an atomic type would prevent this type of error.

## How to Run
1. Clone this repository.
2. Navigate to the repository's directory.
3. Compile and run the `bug.rs` file using `rustc bug.rs && ./bug`
4. Compile and run the `bugSolution.rs` file using `rustc bugSolution.rs && ./bugSolution`

Observe the differences in the output and behavior between the two files.