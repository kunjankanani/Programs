# Next Greater Element I

The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.

You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.

For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.

Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.

 

Example 1:
```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
```
Example 2:
```
Input: nums1 = [2,4], nums2 = [1,2,3,4]
Output: [3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3.
- 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.
 ```

## Constraints:

- 1 <= nums1.length <= nums2.length <= 1000
- 0 <= nums1[i], nums2[i] <= 104
- All integers in nums1 and nums2 are unique.
- All the integers of nums1 also appear in nums2.
 

Follow up: Could you find an O(nums1.length + nums2.length) solution?

## Solution

This solution first creates a map from each element in nums2 to its index in the array. This allows us to quickly look up the index of an element in nums2 given its value.

Then, it initializes the result array with -1. This will be the value for queries where there is no next greater element in nums2.

Finally, it iterates over each element in nums1 and finds the next greater element in nums2 using the map. It does this by starting at the index of the current element in nums2 and searching for the first element that is greater than the current element. If it finds such an element, it updates the result array with the value of the next greater element and breaks out of the inner loop. If it reaches the end of the array without finding a next greater element, the result for the current query remains -1.

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {

    // Create a map from each element in nums2 to its index in the array
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums2.length; i++) {
        map.put(nums2[i], i);
    }

    // Initialize the result array with -1
    int[] res = new int[nums1.length];
    Arrays.fill(res, -1);

    // For each element in nums1, find the next greater element in nums2
    for (int i = 0; i < nums1.length; i++) {
        // Get the index of the current element in nums2
        int index = map.get(nums1[i]);

        // Search for the next greater element in nums2 starting from the index of the current element
        for (int j = index + 1; j < nums2.length; j++) {
            if (nums2[j] > nums1[i]) {
                res[i] = nums2[j];
                break;
            }
        }
    }

    return res;

    }
}
```