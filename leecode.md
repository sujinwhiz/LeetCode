## 1. Two sum
``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {
         HashMap<Integer,Integer> map = new HashMap<>();
         int differ;
         for(int i = 0; i < nums.length; ++i) {
            differ =  target - nums[i];
            if(map.containsKey(differ)) {
                return new int[]{map.get(differ),i};
            }
            map.put(nums[i],i);
         }
         return new int[]{};
    }
}
```
---
## 2. Single Number
``` java
class Solution {
    public int singleNumber(int[] nums) {
         int result = 0;
         for(int i : nums) {
            result ^= i;
         }
         return result;
    }
}
```
--- 

 
