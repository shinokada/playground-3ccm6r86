This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

# Comparison Operators

All the comparison operators are the same in Python and Rust.

| Meaning                  | Python | Rust |
| ------------------------ | ------ | ---- |
| Greater than             | >      | >    |
| Less than                | <      | <    |
| Equal to                 | ==     | ==   |
| Not equal to             | !=     | !=   |
| Greater than or equal to | >=     | >=   |
| Less than or equal to    | <=     | <=   |


```rust runnable
fn main() {
    let a = 7;
    let b = 4;

    let c = a == b; 
    let d = a != b; 
    let e = a < b; 
    let f = a > b; 
    let g = a <= a;
    let h = a >= a;
    println!("
    a: {}, b: {}, 
    c: {0} == {1} is {}, 
    d: {0} != {1} is {}, 
    e: {0}<{1} is {}, 
    f: {0}>{1} is {}, 
    g: {0}<={0} is {}, 
    h: {0}>={0} is {}", 
    a, b, c, d, e, f, g, h);
}
```