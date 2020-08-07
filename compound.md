> This article was originally published on [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

Follow me:
- [@shinokada](https://twitter.com/shinokada)
- [Medium](https://medium.com/@shinichiokada)


# Compound Assignment Operators

All the Rust and Python compound assignment operators have the same symbols except Rust doesn’t have the equivalence of power assignment `**=`, and floor division assignment `//=`.


| Meaning                                  | Python | Rust |
| ---------------------------------------- | ------ | ---- |
| Arithmetic addition and assignment       | +=     | +=   |
| Arithmetic subtraction and assignment    | -=     | -=   |
| Arithmetic multiplication and assignment | *=     | *=   |
| Arithmetic division and assignment       | /=     | /=   |
| Arithmetic remainder and assignment      | %=     | %=   |
| Bitwise AND and assignment               | &=     | &=   |
| Bitwise OR and assignment                | \|=    | \|=  |
| Bitwise exclusive OR and assignment      | ^=     | ^=   |
| Left-shift and assignmen                 | <<=    | <<=  |
| Right-shift and assignment               | >>=    | >>=  |
| Arithmetic power assignment              | **=    | None |
| Arithmetic floor division assignment     | //=    | None |


```rust runnable
fn main() {
    let mut a = 2;
    println!("a is {}", a);
    a += 5; // Arithmetic addition and assignment, 2 + 5 = 7
    println!("1: a += 5 is {}", a);
    a -= 2; // Arithmetic subtraction and assignment, 7 - 2 = 5
    println!("2: a -= 2 is {}", a);
    a *= 5; // Arithmetic multiplication and assignment, 5 * 5 = 25
    println!("3: a *= 5 is {}", a);
    a /= 2; // Arithmetic division and assignment, 25 / 2 = 12 not 12.5
    println!("4: a /= 2 is {}", a);
    a %= 5; // Arithmetic remainder and assignment, 12 % 5 = 2
    println!("5: a %= 5 is {}", a);
    a &= 2; // Bitwise AND and assignment, 10 && 10 -> 10 -> 2
    println!("6: a &= 2 is {}", a);
    a |= 5; // Bitwise OR and assignment, 010 || 101 -> 111 -> 7
    println!("7: a |= 5 is {}", a);
    a ^= 2; // Bitwise exclusive OR and assignment, 111 != 010 -> 101 -> 5
    println!("8: a ^= 2 is {}", a);
    a <<= 1; // Left-shift and assignment, '101'+'0' -> 1010 -> 10
    println!("9: a <<= 1 is {}", a);
    a >>= 2; // Right-shift and assignment, 101̶0̶ -> 10 -> 2
    println!("10: a >>= 2 is {}", a);
}
```