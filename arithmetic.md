# Arithmetic Operators

| Meaning                              | Python | Rust | Rust Overloading Trait |
| ------------------------------------ | ------ | ---- | ---------------------- |
| Add two numbers                      | +      | +    | std::ops::Add          |
| Subtract right operand from the left | -      | -    | std::ops::Sub          |
| Multiply two numbers                 | *      | *    | std::ops::Mul          |
| Divide left operand by the right one | /      | /    | std::ops::Div          |
| Modulus/Remainder                    | %      | %    | std::ops::Rem          |

Python and Rust share the same symbols as you see in the above table. Rust call it "Remainder" for the "Modulus".

`` runnable rust
fn main() {
    let a = 20;
    let b = a + 1;
    let c = a - 2;
    let d = a * 3;
    let e = a / 4;
    let f = a % 3;
    println!("a: {}, b: {0}+1={}, c: {0}-2={}, d: {0}*3={}, e: {0}/4={}, f: {0}%3={}", a, b, c, d, e, f);
}
``

In Rust you can't use different data types in an operation. For example, if you try to subtract an [unsigned integer](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f#f4ce) from a [singed integer](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f#3e54), it will fail:

`` runnable rust
// This will fail.
fn main() {
    let a = 8u8;
    let b = 2i32;
    println!("{}", a - b);
}
``

You can use [`as` keyword](https://doc.rust-lang.org/std/keyword.as.html) to cast between primitive types.

`` runnable rust
fn main() {
    let a = 8u8;
    let b = 2i32;
    println!("{}", a as i32 - b);
}
``

## Exponent

Python uses `**` symbol for exponents:

`` runnable python
print('2^3 is ', 2**3)
print('3^3 is ', 3**3)
print('3^3.2 is ', 3**3.2)
``

Rust uses `pow`, `powi`, and `powf`: 

`` runnable rust
fn main() {
    println!("2 ^ 3 in Rust: 2u8.pow(3) = {}", 2u8.pow(3));
    println!("2 ^ 3 in Rust: 2i32.pow(3) is {}", 2i32.pow(3));
    println!("3.0 ^ 3 in Rust: 3.0f32.powi(3) {}", 3.0f32.powi(3));
    println!("3.0 ^ 3.2 in Rust: 3.0_f32.powf(3.2) is {}", 3.0_f32.powf(3.2));
    let a = 3;
    let a_cubed = i32::pow(a,3);
    println!("a = {}, a ^ 3 in Rust: i32::pow(a,3) = {}", a, a_cubed);
    let b = 3.1;
    println!("b = {}, b ^ 3 in Rust: f64::powi(b, 3) = {}", b, f64::powi(b, 3));
    println!("b = {}, b ^ PI in Rust: std::f64::consts::PI) = {}", b, f64::powf(b, std::f64::consts::PI) );    
}
``






