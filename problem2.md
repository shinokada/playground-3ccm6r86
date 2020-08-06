> This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

# Problem 2: Number of Steps to Reduce a Number to Zero

In [this problem](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/), you input a non-negative integer `num` and return the number of steps to reduce it to zero. If the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

For example:

```
Input: num = 14
Output: 6
Explanation: 
Step 1) 14 is even; divide by 2 and obtain 7.
Step 2) 7 is odd; subtract 1 and obtain 6.
Step 3) 6 is even; divide by 2 and obtain 3.
Step 4) 3 is odd; subtract 1 and obtain 2.
Step 5) 2 is even; divide by 2 and obtain 1.
Step 6) 1 is odd; subtract 1 and obtain 0.

Input: num = 8
Output: 4
Explanation: 
Step 1) 8 is even; divide by 2 and obtain 4.
Step 2) 4 is even; divide by 2 and obtain 2.
Step 3) 2 is even; divide by 2 and obtain 1.
Step 4) 1 is odd; subtract 1 and obtain 0.
```

This is a good example that we can use the Modulus/Remainder operator and the compound assignment operators.

## Python Solution

```python runnable
class Solution:
    def numberOfSteps (self, num: int) -> int:
        steps = 0
        while num > 0:
            if num % 2 == 0:
                num /= 2 
            else:
                num -=1 
            steps += 1
        return steps

ans = Solution()
print(ans.numberOfSteps(14))
print(ans.numberOfSteps(8))
```

Line: 3–10: We use a `while` loop for `num > 0`. If the modulus is 0, then it must be an even number so we divide the `num` by 2 using a compound assignment `/=2`, otherwise, we subtract 1 using a compound assignment `-=1`. We increase the `steps` by 1. Finally, we return the `steps`.

We adjust the above code to the LeetCode environment.

```python
class Solution:
    def numberOfSteps (self, num: int) -> int:
        steps = 0
        while num > 0:
            if num % 2 == 0:
                num //= 2
            else:
                num -=1
            steps += 1
        return steps
```

## Rust Solution

```rust runnable
struct Solution {
    num: i32,
}

impl Solution {
    pub fn number_of_steps (&mut self) -> i32 {
        let mut steps = 0;
        while self.num > 0 {
            if self.num % 2 == 0 {
                self.num /= 2;
            } else {
                self.num -=1;
            }
            steps += 1;
        }
        steps
    }
}

fn main() {
    let ans1 = Solution {
        num : 14,
    };
    let ans2 = Solution {
        num : 8,
    };
    println!("{}", ans1.number_of_steps());
    println!("{}", ans2.number_of_steps());
}
```

In Rust, we take the same steps as we did in Python.

Line 7–16: We assign 0 to a mutable variable `steps`. While `self.num` is greater than 0, we use the compound assignment `/=2` if `self.num` 's remainder is 0, otherwise, we subtract 1, and increase the number of step by 1.

We adjust the above code to the LeetCode environment.

```rust
impl Solution {
    pub fn number_of_steps (mut num: i32) -> i32 {
        let mut steps = 0;
        while num > 0 {
            if num % 2 == 0 {
                num /= 2;
            } else {
                num -=1;
            }
            steps += 1;
        }
        steps
    }
}
```