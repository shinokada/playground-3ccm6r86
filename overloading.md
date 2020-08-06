# Operator Overloading

Operator overloading is to specify more than one definition for an operator in the same scope. [Python](https://www.programiz.com/python-programming/operator-overloading) and [Rust](https://doc.rust-lang.org/book/ch19-03-advanced-traits.html#default-generic-type-parameters-and-operator-overloading) provide operator overloading. You can find Rust overloadable operators in the [standard library ops module](https://doc.rust-lang.org/std/ops/index.html).


```rust runnable
use std::ops::Add;

#[derive(Debug, Copy, Clone, PartialEq)]
struct Point {
    x: i32,
    y: i32,
}

impl Add for Point {
    type Output = Point;

    fn add(self, other: Point) -> Point {
        Point {x: self.x + other.x, y: self.y + other.y}
    }
}

fn main(){
    let p3: Point = Point {x: 1, y: 0} + Point {x: 2, y: 3};
    println!("{:?}", p3);
}
```