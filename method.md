> This article was originally published on [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

Follow me:
- [@shinokada](https://twitter.com/shinokada)
- [Medium](https://medium.com/@shinichiokada)

# Method and Associated Functions

> Methods are defined within the context of a struct and their first parameter is always `self`, which represents the instance of the struct the method is being called on. - The Rust Programming Language

Associated functions don’t take `self` as a parameter and they are not methods because they don’t have an instance of the struct to work with.

A good example is `String::from` function.

We use the `::` syntax with the struct name to call this associated function whereas we use `.` when we call a method.

A common associated function is a `new` function that returns a value of the type the associated function is associated with.

```rust runnable
struct Point {
    x: i32,
    y: i32
}

impl Point {
    fn new() -> Point {
        Point {
            x: 5_i32,
            y: 4_i32
        }
    }

}

fn main () {
    let p1 = Point::new();
    let mut p2 = Point::new();
    p2.x = 8;
    p2.y = 9;
    println!{"x: {}, y: {}", p1.x, p1.y};
    println!("x: {}, y: {}", p2.x, p2.y );
}
```

## Final code

```rust runnable
struct Solution {
    nums: Vec<i32>,
}

impl Solution {
    pub fn single_number(&self) -> i32 {
        let mut ans: i32 = 0;
        for n in &self.nums {
            ans ^= n;
        }
        ans
    }
}

fn main() {
    let ans = Solution {
        nums: vec![2, 2, 1, 1, 5],
    };
    println!("{}", ans.single_number());
}
```

Line 7–11: We create a mutable variable `ans` with the type of `i32` . Using `for` loop, we iterate `&self.nums` using `ans ^=n`.

We adjust the above code to the LeetCode environment.

```rust
impl Solution {
    pub fn single_number(nums: Vec<i32>) -> i32 {
        let mut ans: i32 = 0;
        for n in nums {
            ans ^= n;
        }
        ans        
    }
}
```