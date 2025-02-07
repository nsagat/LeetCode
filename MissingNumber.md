# Question: 268.Missing Number

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

### Example 1:
**Input:**
```java
nums = [3,0,1]
```
**Output:**
```java
2
```
**Explanation:**
`n = 3` since there are 3 numbers, so all numbers are in the range `[0,3]`. `2` is the missing number in the range since it does not appear in `nums`.

### Example 2:
**Input:**
```java
nums = [0,1]
```
**Output:**
```java
2
```
**Explanation:**
`n = 2` since there are 2 numbers, so all numbers are in the range `[0,2]`. `2` is the missing number in the range since it does not appear in `nums`.

### Example 3:
**Input:**
```java
nums = [9,6,4,2,3,5,7,0,1]
```
**Output:**
```java
8
```
**Explanation:**
`n = 9` since there are 9 numbers, so all numbers are in the range `[0,9]`. `8` is the missing number in the range since it does not appear in `nums`.

### Constraints:
- `n == nums.length`
- `1 <= n <= 10^4`
- `0 <= nums[i] <= n`
- All the numbers of `nums` are unique.

## Solution Approach

My initial approach for this problem is by using an additional array where we replace the value encountered in `nums` with the `nums[i]`th position in the array.

### Steps:
1. Create an array `arr` of size `nums.length + 1`.
2. Initialize all positions in `arr` with `-1`.
3. Iterate through `nums` and place each value in its corresponding position in `arr`.
4. Iterate through `arr` and return the index where the value is still `-1`, as this is the missing number.

### Java Implementation
```java
class Solution {
    public int missingNumber(int[] nums) {
         //We can solve this problem by using another array where we replace the value encountered in nums with the nums[i]th position in the array.
        int[] arr = new int[nums.length + 1];
        //make all pos -1 so that we can replace later on and check the position which still has -1 to spot the missing number in the nums.
        for(int i = 0; i < arr.length; i++){
            arr[i] = -1;
        }
        for(int i = 0; i < nums.length; i++){
            arr[nums[i]] = nums[i];
        }
        for(int i = 0; i < arr.length; i++){
            if(arr[i] == -1){
                return i;
            }
        }
        return 0;
    }
}
```

### Performance Visualization

Below is a screenshot that demonstrates the runtime performance of the solution:
<img src="./Images/MissingNumberPerformance.png" alt="Runtime Performance" width="600">


## Complexity Analysis
- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(n)`
