> This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

# Problem 1: Single Number

We are going to use this `XOR` to solve the LeetCoder problem called [Single number](https://leetcode.com/problems/single-number/).

In this problem, an array input has a pair of numbers except one, for example `[1, 1, 5, 5, 2]`. You need to find a sing number from this array and in this case the output should be `2`.

More example: When the input is `[2, 2, 1]`, the output should be `1`. When an input is `[4, 1, 2, 1, 2]` the output should be `4`.

This is a good example to use the `XOR` operator.

## Python solution

We briefly go through the Python solution to see how the problem was solved.

```python runnable
from typing import List

class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        ans = 0
        for n in nums:
            ans ^= n
        return ans
        
ans = Solution()
print(ans.singleNumber([4,1,2,1,2,3,3]))
```

Line 1: We use Python `typing` which is [introduced from v3.5](https://docs.python.org/3/library/typing.html).

Line 3–4: After importing `List`, we create a class called `Solution` and method called `singleNumber`.

With [Python type hints](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html), we capitalize the name of the type, and set the name of the type inside the collection in brackets as seen above, `num: List[int]`.

Line 5–8: We set a variable `ans` to 0. Using a `for` loop, we iterate the input array, `nums` using `XOR` compound assignment, `ans ^= n`. This will output the single number from the array.

Line 10–11: We instantiate the class `Solution` and call the method `singleNumber`.

(You can run this Python code without type notations if you are [interested](https://tech.io/snippet/ak3wW3m).)

The following is the solution for the LeetCode environment:

```rust
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        ans = 0
        for n in nums:
            ans ^= n
        return ans
```

# Rust code

Rust [*structs*](https://towardsdatascience.com/learning-rust-by-converting-python-to-rust-259e735591c6) contain named fields. We use a keyword `struct` and set fields with its type within the curly bracket. We put methods into a `impl` block.

## Starting code

```rust runnable
#[allow(dead_code)]
struct Solution {
    nums: Vec<i32>,
}

impl Solution {
    pub fn single_number(&self) -> i32 {
        1
    }
}

fn main() {
    let ans = Solution {
        nums: vec![2,2,1],
    };
    println!("{}", ans.single_number());
}
```

Line 1: We suppress `dead_code` warning.

Line 2–4: Create a `struct` called `Solution` that takes one field `nums `with `Vec<i32>` type. (More on [Vectors](https://towardsdatascience.com/learning-rust-by-converting-python-to-rust-259e735591c6).)

Line 6–10: We create a method `single_number` in `impl Solution`. The `single_number` takes the first parameter `&self` ([More on ](https://towardsdatascience.com/learning-rust-by-converting-python-to-rust-259e735591c6)`self`[ ](https://towardsdatascience.com/learning-rust-by-converting-python-to-rust-259e735591c6).) and we just return `1` for now.

Line 12–17: In the main function, we create an instance and print `1` using the method.

It seems all working so we are going to complete the `single_number` method next.
