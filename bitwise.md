> This article was originally published on [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

Follow me:
- [@shinokada](https://twitter.com/shinokada)
- [Medium](https://medium.com/@shinichiokada)


# Bitwise Operators

All the Rust and Python Bitwise operators share the same bitwise operator symbols except the bitwise NOT.

| Meaning             | Python | Rust |
| ------------------- | ------ | ---- |
| Bitwise AND         | &      | &    |
| Bitwise OR          | \|     | \|   |
| **Bitwise NOT**     | ~      | !    |
| Bitwise XOR         | ^      | ^    |
| Bitwise right shift | >>     | >>   |
| Bitwise left shift  | <<     | <<   |


```rust runnable
fn main() {
    let a = 1; // 01
    let b = 2; // 10

    let c = a & b;  // Bitwise AND, 0  (01 && 10 -> 00)
    let d = a | b;  // Bitwise OR, 3  (01 || 10 -> 11)
    let e = a ^ b;  // Bitwise exclusive OR, 3  (01 != 10 -> 11)
    let f = a << b; // Left-shift, 4  (Add b number of 0s to the end of a -> '01'+'00' -> 100)
    let f2 = a << 4; // 16 a->'01'+"0000" ->'10000'
    let g = a >> b; // Right-shift, 0 (Remove b number of bits from the end of a -> 01 -> 0)
    let g2 = 31 >> 4; // 0 '11111' -> remove 4 bits from the end ->'1'
    let h = !a; // Bitwise NOT 

    println!("
    a: {a}, b: {b}, 
    c: {a} & {b} is {c}, 
    d: {a} | {b} is {d}, 
    e: {a} ^ {b} is {e},
    f: {a} << {b} is {f},
    f2: {a} << 4 is {f2},
    g: {a} >> {b} is {g},
    g2: {a} >> {b} is {g2},
    h: !{a} = {h}", 
    a=a, b=b, c=c, d=d, e=e, f=f, f2=f2, g=g, g2=g2, h=h);
}
```

[**Bitwise negation**](https://towardsdatascience.com/unsinged-signed-integers-and-casting-in-rust-9a847bfc398f) `!1` returns `-2`. Rust uses the two’s complement to find the bitwise negation for signed types. Rust’s signed integer types are called **the signed two’s complement integer types**.

You can use `1 << n ` to find out exponents of 2.

```rust runnable
fn main() {
   println!("2 ^ 3 = {}",1 << 3 );
   println!("2 ^ 4 = {}",1 << 4 );
   println!("2 ^ 5 = {}",1 << 5 );
}
```