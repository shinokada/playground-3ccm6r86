> This article was first published at [Medium](https://towardsdatascience.com/a-comprehensive-tutorial-to-rust-operators-for-beginners-11554b2c64d4)

# Solution using an associated function

Since we learned about the associated function, let’s apply it to this problem.


```rust runnable
struct Solution {
    nums: Vec<i32>,
}

impl Solution {
    fn new(nums: Vec<i32>) -> Solution {
        Solution {
            nums
        }
    }

    pub fn single_number(&self) -> i32 {
        let mut ans: i32 = 0;
        for n in &self.nums {
            ans ^= n;
        }
        ans
    }
}

fn main() {
    let nums1 = vec![2,2,1];
    let nums2 = vec![4,1,2,1,2];
    let ans3 = Solution::new(nums1); 
    let ans4 = Solution::new(nums2);
    println!("{}", ans3.single_number());
    println!("{}", ans4.single_number());
}
```

Line 6–10: We create an associated function, `new` as we have done it before. This `new` function takes one parameter `nums` that is a vector with items of `i32`.

When the parameter names and the struct field names are exactly the same, we can use the **field init shorthand** syntax as `nums` instead of `nums: nums`.

In the main function, we call an associated function, `new` and pass `nums` as an argument. We use *method syntax* to call the `single_number` method on the `ans3` instance.
