# Question: 217.Contains Duplicate

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

#### Example 1:

**Input:**
```
nums = [1,2,3,1]
```

**Output:**
```
true
```

**Explanation:**
```
The element 1 occurs at the indices 0 and 3.
```
#### Example 2:

**Input:**
```
nums = [1,2,3,4]
```

**Output:**
```
false
```

**Explanation:**
```
All elements are distinct.
```

#### Example 3:

**Input:**
```
nums = [1,1,1,3,3,4,3,2,4,2]
```

**Output:**
```
true
```

---

# Solution

### Approach:
The task is to check if there are duplicates in the array. Initially, I considered a nested loop approach, but I realized that it would result in a time complexity of \(O(n^2)\), which is inefficient for large datasets. Instead, I opted for a solution with linear time complexity \(O(n)\) by using a `HashSet`.

### Key Idea:
A `HashSet` is used to track elements that have already been seen. As we iterate through the array, we check if the current element exists in the set:
- If it does, it means we have found a duplicate, and we return `true`.
- If not, we add the element to the set and continue.

This approach ensures each element is processed only once, resulting in an optimal solution.

---

### Implementation:
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        // O(n) complexity by using HashSet
        HashSet<Integer> dup = new HashSet<>();
        for (int i : nums) {
            if (dup.contains(i)) {
                return true;
            }
            dup.add(i);
        }
        return false;
    }
}
```

---

### Explanation:
1. **HashSet Usage**: The `HashSet` provides an efficient way to check for duplicates since `add` and `contains` operations run in \(O(1)\) average time.
2. **Iteration**: We iterate through the array, and for each element:
   - If the element is already in the `HashSet`, return `true`.
   - Otherwise, add the element to the `HashSet` and proceed.
3. **Return Statement**: If the loop completes without finding duplicates, return `false`.

### Complexity Analysis:
- **Time Complexity**: \(O(n)\), where \(n\) is the number of elements in the array. Each element is processed once.
- **Space Complexity**: \(O(n)\) due to the storage used by the `HashSet`.

---

### Why This Approach?
This solution is optimal compared to the initial nested loop approach (\(O(n^2)\)) because it reduces the time complexity significantly, especially for large arrays. The `HashSet` ensures efficient duplicate detection while maintaining clarity and simplicity in the implementation.

