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
## 3. Intersection of two Array 
``` java
class Solution {
     public int[] intersection(int[] nums1, int[] nums2) {
         HashSet<Integer> set = new HashSet<>();
         ArrayList<Integer> list = new ArrayList<>();

         for(int num : nums1) {
            set.add(num);
         }

         for(int num : nums2) {
            if(set.contains(num)) {
                list.add(num);
                set.remove(num);
            }
         }

         int[] arr = new int[list.size()];
         for(int i = 0; i < list.size(); ++i) {
            arr[i] = list.get(i);
         }

         return arr;
    }
}
```  
---
## 4. Move Zeroes
 ``` java
class Solution {
    public void moveZeroes(int[] nums) {
        int lastIndexOfNonZero = 0;
        for(int i = 0; i < nums.length; ++i) {
            if(nums[i] != 0) {
                int temp = nums[i];
                nums[i] = nums[lastIndexOfNonZero];
                nums[lastIndexOfNonZero] = temp;
                lastIndexOfNonZero++;
            }
        }
    }
}
```  
---
## 5. Contains Duplicate
``` java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<Integer>();
        for(int i : nums) {
            if(set.contains(i)) return true;
            set.add(i);
        }
        return false;
    }
}
```  
---
## 6. Majority Element
``` java
class Solution {
    public int majorityElement(int[] nums) {
        int maxcount = 0;
        int majEle = 0;
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int num : nums) {
            int count = map.getOrDefault(num,0) + 1;
            map.put(num,count);
            if(count > maxcount) {
                maxcount = count;
                majEle = num;
            }
        }
        return majEle;
    }
}
```  
---
## 7. Best Time to Buy and Sell Stock
``` java
class Solution {
    public int maxProfit(int[] prices) {
         int minPrice = Integer.MAX_VALUE;
         int maxProfit = 0;

         for(int i = 0; i < prices.length; ++i) {
            if(minPrice > prices[i]) {
                minPrice = prices[i];
            }
            else {
                int currentProfit = prices[i] -  minPrice;
                if(maxProfit < currentProfit) {
                    maxProfit = currentProfit;
                }

            }
         }
         return maxProfit;
    }
}
```  
---
## 8. Palindrome Number
``` java
class Solution {
    public boolean isPalindrome(int x) {
        if(x < 0 || (x % 10 == 0 && x != 0)) return false;
         int originalX = x;
         int newX = 0;
         while(x > 0) {
            int rem = x % 10;
            newX = newX * 10 + rem;
            x /= 10;
         }
         return newX == originalX;
    }
}
```


 
