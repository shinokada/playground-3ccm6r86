> This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

Follow me:
- [@shinokada](https://twitter.com/shinokada)
- [Medium](https://medium.com/@shinichiokada)

# Logical Operators

Rust logical operator symbols are different from Python ones.

| Meaning                                | Python | Rust |
| -------------------------------------- | ------ | ---- |
| True if both the operands are true     | and    | &&   |
| True if either of the operands is true | or     | \|\| |
| True if operand is false               | not    | !    |

```rust runnable
fn main() {
    let a = true;
    let b = false;

    let c = !a; 
    let d = a && b;
    let e = a || b; 
    
    println!("
    a: {}, b: {}, 
    c: !{0} is {}, 
    d: {0} && {1} is {}, 
    e: {0} || {1} is {}", 
    a, b, c, d, e);
}
```