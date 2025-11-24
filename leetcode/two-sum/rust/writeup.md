# Two Sum - Solution Writeup

## Approach

Use HashMap to achieve O(n) time complexity. For each number, calculate its complement (target - num) and check if it exists in the HashMap. If found, return both indices. Otherwise, store the current number and continue.

## Code Breakdown

```rust
use std::collections::HashMap;
```
Import HashMap for O(1) lookups.

```rust
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
```
LeetCode format - method inside `impl Solution`.

```rust
        let mut map: HashMap<i32, usize> = HashMap::new();
```
Create empty HashMap: key = number, value = index.

```rust
        for (i, &num) in nums.iter().enumerate() {
```
Iterate through array with index and value.

```rust
            let complement = target - num;
```
Calculate what number we need to find (target - current).

```rust
            if let Some(&index) = map.get(&complement) {
```
Check if complement exists in HashMap.

```rust
                return vec![index as i32, i as i32];
```
Found pair - return both indices.

```rust
            }
            map.insert(num, i);
```
Not found - store current number for future lookups.

```rust
        }
        vec![]
    }
}
```
No solution found (shouldn't happen per problem constraints).

## Complexity

- **Time:** O(n) - single pass through array
- **Space:** O(n) - HashMap stores up to n elements

## Example

Input: `nums = [2, 7, 11, 15]`, `target = 9`

| Step | i | num | complement | map | Action |
|------|---|-----|------------|-----|--------|
| 1 | 0 | 2 | 7 | {} | Store {2:0} |
| 2 | 1 | 7 | 2 | {2:0} | Found! Return [0,1] |

