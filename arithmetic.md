> This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

# Arithmetic Operators

| Meaning                              | Python | Rust | Rust Overloading Trait |
| ------------------------------------ | ------ | ---- | ---------------------- |
| Add two numbers                      | +      | +    | std::ops::Add          |
| Subtract right operand from the left | -      | -    | std::ops::Sub          |
| Multiply two numbers                 | *      | *    | std::ops::Mul          |
| Divide left operand by the right one | /      | /    | std::ops::Div          |
| Modulus/Remainder                    | %      | %    | std::ops::Rem          |

Python and Rust share the same symbols as you see in the above table. Rust calls `%`  as **Remainder** instead of the **Modulus**.

We will cover “Rust Overloading Trait” later in the [Operator Overloading](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4).


```rust runnable
fn main() {
    let a = 20;
    let b = a + 1;
    let c = a - 2;
    let d = a * 3;
    let e = a / 4;
    let f = a % 3;
    println!("a: {}, b: {0}+1={}, c: {0}-2={}, d: {0}*3={}, e: {0}/4={}, f: {0}%3={}", a, b, c, d, e, f);
}
```

In Rust you can't use different data types in an operation. For example, if you try to subtract an [unsigned integer](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f#f4ce) from a [singed integer](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f#3e54), it will fail:

```rust runnable
// This will fail.
fn main() {
    let a = 8u8;
    let b = 2i32;
    println!("{}", a - b);
}
```

Rust uses the `as` [keyword](https://doc.rust-lang.org/std/keyword.as.html) to cast between **primitive types**. Please read more about the cast in Rust [here](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f).

```rust runnable
fn main() {
    let a = 8u8;
    let b = 2i32;
    println!("{}", a as i32 - b);
}
```

## Exponent

Python uses `**` symbol for exponents:

```python runnable
print('2^3 is ', 2**3)
print('3^3 is ', 3**3)
print('3^3.2 is ', 3**3.2)
```

Rust uses `pow`, `powi`, and `powf` depends on the type:

```rust runnable
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
```

In Rust, you can annotate a number type like `2u8` or `2_u8`. `u8` is an [unsigned 8-bit integer type](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f) and `i32` is a [signed integer type](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f).

`i32` and `f32` have a group of built-in methods. All the integer types `u8`, `u16`, `u32`, `u64`, `u128`, `i16`,`i32`, `i64` , `i128`, `isize`, and `usize` have the ``pow`` method.

```rust
pub fn pow(self, exp: u32) -> i32
```

The above definition tells you that using the `pow` method raises self to the power of `exp` (which is `u32`) and returns `i32` (a signed integer).

The **floating-point types**, `f32` and `f64` have `powi` and `powf` methods.

`powi` raises a number to an integer power and `powf` raises a number to a floating-point power.

```rust
pub fn powi(self, n: i32) -> f32
pub fn powf(self, n: f32) -> f32
```

## Floor division

In Python we use `//` to find a floor division. For example `5//2=2`.

```python runnable
print('5 // 2 is ', 5//2)
print('-5 // 2 is ', -5//2)
```

[Rust's floating-point types](https://doc.rust-lang.org/book/ch03-02-data-types.html#floating-point-types) has the [floor method](https://doc.rust-lang.org/std/primitive.f64.html#method.floor).

```rust runnable
fn main() {
    println!("5_f32 / 2_f32 is {}", (5_f32 / 2_f32).floor());
    println!("-5_f32 / 2_f32 is {}", (-5_f32 / 2_f32).floor());
}
```