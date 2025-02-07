# Question: 448.Find All Numbers Disappeared in an Array

Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return an array of all the integers in the range `[1, n]` that do not appear in `nums`.

### Example 1:
**Input:** `nums = [4,3,2,7,8,2,3,1]`  
**Output:** `[5,6]`

### Example 2:
**Input:** `nums = [1,1]`  
**Output:** `[2]`

### Constraints:
- `n == nums.length`
- `1 <= n <= 10^5`
- `1 <= nums[i] <= n`

---

## Solution Approach

### My Idea:
1. We need to find numbers that are missing from the given array within the range `[1, n]`.
2. Since the values in `nums` range from `1` to `n`, we can use an array to track the presence of numbers.
3. Create an array `arr` of size `n+1` and mark the indices corresponding to the values in `nums`.
4. Then iterate through the auxiliary array and identify the indices that remain unmarked, as they correspond to missing numbers.

### Implementation:
```java
import java.util.*;

class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        //List to keep track of not included numbers in nums
        List<Integer> list =  new ArrayList<>();
        //Have an array that gets filled if the nums contains the number. 
        int[] arr = new int[nums.length + 1];
        for(int i = 0; i < nums.length; i++){
            arr[nums[i]] = nums[i];
        }
        //check if auxillary array contains any positions that did not get replaced starting from index 1.
        for(int i = 1; i < arr.length; i++){
            //if not found, add to the list.
            if(arr[i] == 0){
                list.add(i);
            }
        }
        return list;
    }

}
```
### Performance Visualization

Below is a screenshot that demonstrates the runtime performance of the solution:
<img src="./Images/FindAllNumbersDisappearedInAnArray.png" alt="Runtime Performance" width="600">

### Complexity Analysis:
- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(n)`