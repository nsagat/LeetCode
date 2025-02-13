## Question: 1365.Smaller Numbers Than The Current Number
### Problem Statement
Given the array `nums`, for each `nums[i]` find out how many numbers in the array are smaller than it. That is, for each `nums[i]` you have to count the number of valid `j's` such that `j != i` and `nums[j] < nums[i]`.

Return the answer in an array.

### Example 1:
**Input:** `nums = [8,1,2,2,3]`  
**Output:** `[4,0,1,1,3]`

### Example 2:
**Input:** `nums = [6,5,4,8]`  
**Output:** `[2,1,0,3]`

### Example 3:
**Input:** `nums = [7,7,7,7]`  
**Output:** `[0,0,0,0]`

## Constraints
- `2 <= nums.length <= 500`
- `0 <= nums[i] <= 100`

---

## Solution Explanation

### Initial Approach - Nested Loop (Brute Force)
The most straightforward approach is to use a nested loop, where we compare each number with every other number in the array. However, this solution has a time complexity of **O(n²)**, making it inefficient for larger inputs.

### Optimized Approach - Using Sorting and a HashMap
A more optimized approach involves:
1. Sorting the array to determine the relative order of elements.
2. Using a **HashMap** to store the first occurrence of each number's position, which directly represents how many smaller numbers come before it.
3. Constructing the result array using the stored values.

### Java Implementation

```java
import java.util.*;

class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int[] tempArr = new int[nums.length];
        int[] result = new int[nums.length];
        
        for(int i = 0; i < nums.length; i++){
            tempArr[i] = nums[i];
        }
        
        Arrays.sort(tempArr);
        
        for (int i = 0; i < tempArr.length; i++) {
            if (!map.containsKey(tempArr[i])) {
                map.put(tempArr[i], i);
            }
        }
        
        for(int i = 0; i < nums.length; i++){
            result[i] = map.get(nums[i]);
        }
        
        return result;
    }
}
```
### Performance Visualization

Below is a screenshot that demonstrates the runtime performance of the solution:
<img src="./Images/HowManyNumbersAreSmallerThanTheCurrentNumber.png" alt="Runtime Performance" width="600">

### Complexity Analysis:
- **Time Complexity:** `O(n log n)` due to sorting.
- **Space Complexity:** `O(n).