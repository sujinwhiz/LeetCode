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

        boolean[] seen = new boolean[1001];

         for(int num : num1) {
            seen[num] = true;
         }
         int count = 0;
         for(int num :num2) {
            if(seen[num]) {
                seen[num] = false;
                num1[count++] = num;
            }
         }

         int[] result = new int[count];
         for(int i = 0; i < count; ++i) {
            result[i] = num1[i];
         }

         return result;
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
## 9. Plus One
``` java
class Solution {
    public int[] plusOne(int[] digits) {
        
         if(digits[digits.length - 1] < 9) {
            digits[digits.length - 1] += 1;
            return digits;
        }
        int i = digits.length - 1;
        while(i >= 0 ) {
            if(digits[i] == 9) {
                digits[i] = 0;
                --i;
            }
            else {
                digits[i] += 1;
                break;
            }
        }
        if(i == -1) {
            digits = new int[digits.length + 1];
            digits[0] = 1;
            return digits;
        }    
        return digits;
    }
}
```
## 10. Search Insert Position
``` java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;
        int mid  = 0;
        while(low <= high) {
            mid = (low + high) / 2;
            if(target > nums[mid]) low = mid + 1;
            else if(target < nums[mid]) high = mid - 1;
            else{
                return mid;
            } 
        }
        return  high + 1;
    }
}
```
## 11.Third Maximum Number
``` java
class Solution {
    public int thirdMax(int[] nums) {
         Integer first = null, second = null, third = null;
         for(int num : nums) {
            if ((first != null && num == first) || 
                (second != null && num == second) || 
                (third != null && num == third)) {
                continue;
            }
            if(first == null || num > first) {
                third = second;
                second = first;
                first = num;
            }
            else if(second == null || num > second) {
                third = second;
                second = num;
            }
            else if(third == null || num > third) {
                third = num;
            }
         }

         return third == null ? first : third;
    }
  
}
```
## 12. Max Consecutive Ones
 ``` java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int maxcount = 0;
        for(int i = 0; i < nums.length; ++i) {
            if(nums[i] == 1) {
                ++count;
                if(count > maxcount) maxcount = count;
            }
            else count = 0;
        }
       return maxcount;
    }

}
```
## 13. Running Sum of 1D Array
``` java
class Solution {
    public int[] runningSum(int[] nums) {
        for(int i = 1; i < nums.length; ++i) {
            nums[i] += nums[i - 1];
        }
        return nums;
    }
    
}
```
## 14. Richest Customer Wealth
``` java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int maxWealth = Integer.MIN_VALUE;
        for(int[] customer : accounts) {
            int totWealth = 0;
            for(int bank : customer) {
                totWealth += bank;
            }
            if(maxWealth < totWealth ) {
                maxWealth = totWealth;
            }
        }
        return maxWealth;
    }
}
```
## 15. Shuffle the array
``` java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int[] shuffledarr = new int[nums.length];
        for(int i = 0,j = 0; i < n; ++i) {
            shuffledarr[j++] = nums[i];
            shuffledarr[j++] = nums[n + i];
        }
        return shuffledarr;
    }
}
```
## 16. Kids with greatest no of candies
``` java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        List<Boolean> list = new ArrayList<>();
        int maxCandy = Integer.MIN_VALUE;
        for(int candy : candies) {
           maxCandy = Math.max(maxCandy, candy);
        }
        for(int candy : candies) {
            list.add(candy + extraCandies >= maxCandy);
        }
        return list;
    }
}
```
## 17. No of good pairs
``` java
class Solution {
    public int numIdenticalPairs(int[] nums) {
        int goodPairs = 0;
        HashMap<Integer, Integer> hm = new HashMap<>();
        for(int num : nums) {
            int count = hm.getOrDefault(num,0);
            goodPairs += count;
            hm.put(num, count + 1);
        }
        return goodPairs;
    }
}
```
## 18. How many no are smaller than current number
``` java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
         int n = nums.length;
         int[] result = new int[n];
         int[] sortedArray = nums.clone();
         Arrays.sort(sortedArray);

         for(int i = 0; i < n; ++i) {
            result[i] = findIndexOf(nums[i],sortedArray);
         }
         return result;
    }
    public int findIndexOf(int num, int[] sortedArray) {
        int low = 0;
        int high = sortedArray.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (sortedArray[mid] < num) {
                low = mid + 1; 
            } else {
                high = mid - 1; 
            }
        }
        return low; 
    }
}
```
## 19. Create target array in the given order
``` java
class Solution {
    public int[] createTargetArray(int[] nums, int[] index) {
      ArrayList<Integer> list = new ArrayList<>();
      int n = nums.length;
      for(int i = 0; i < n; ++i) {
          list.add(index[i],nums[i]);
      }
      return list.stream().mapToInt(Integer :: intValue).toArray();

    }
}
```
## 20. Check if the sentence is Pangram
``` java
class Solution {
    public boolean checkIfPangram(String sentence) {
        if(sentence.length() < 26) return false;
        boolean[] ch = new boolean[26];
        int count = 0;
        for(int i = 0; i < sentence.length(); ++i) {
            if(! ch[sentence.charAt(i) - 'a']) {
                ch[sentence.charAt(i) - 'a'] = true;
                ++count;
            }
        }
        return count == 26;
    }
}
```
## 21. Count items matching a rules
``` java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        int count = 0;
        char c = ruleKey.charAt(0);
        int keyIndex = c == 't' ? 0 : c == 'c'? 1 : 2;

        for(List<String> item : items) {
            if(item.get(keyIndex).equals(ruleValue)) ++count;
        }

        return count;

    }
}
```
## 22. Find the Highest Altitude
``` java
class Solution {
    public int largestAltitude(int[] gain) {
        int maxAlti = 0;
        int newAlti = 0;
        for(int i = 0; i < gain.length; ++i) {
            newAlti += gain[i];
            if(newAlti > maxAlti) {
                maxAlti = newAlti;
            }
        }
        return maxAlti;
    }
}
```
## 23. Flipping an image
``` java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        for(int[] row : image) {
            int left = 0, right = row.length - 1;
            while(left <= right) {
                int temp = row[right] ^ 1;
                row[right] = row[left] ^ 1;
                row[left] = temp;
                left++;
                right--;
            }
        }
        return image;
    }
}
```
## 24. Cell with odd values in a matrix
``` java
class Solution {
    public int oddCells(int m, int n, int[][] indices) {
        int oddCells = 0;
        int[][] cells = new int[m][n];

        for(int[] index : indices) {
            int row = index[0];
            int col = index[1];

            for(int i = 0; i < n; ++i) {
                cells[row][i] += 1;
            }

            for(int i = 0; i < m; ++i) {
                cells[i][col] += 1;
            }
             
        }
        for(int[] cell : cells) {
            for(int num : cell) {
                if(num % 2 != 0) ++oddCells;
            }
        }
    
        return oddCells;
        
    }
}
```
## 25. Matrix Diagonal Sum
```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int diagonalSum = 0;
        int n = mat.length;
        for(int  i = 0; i < n; ++i) {
            diagonalSum += mat[i][i];
            if(i != n - i - 1) {
                diagonalSum += mat[i][n - i - 1];
            }
        }
        return diagonalSum;
    }
}
```
## 26. Find Num with even no.of digits
```java
class Solution {
    public int findNumbers(int[] nums) {
        int findNumbers = 0;
        for(int i = 0; i < nums.length; ++i) {
            if((int)(Math.log10(nums[i]) + 1) % 2 == 0) ++findNumbers;
        }
        return findNumbers;
 
    }
}
```
## 27. Find N Unique Integers Sum up to Zero
```java
class Solution {
    public int[] sumZero(int n) {
        int[] sol = new int[n];
        int index = 0;
        for(int i = 1; i <= n / 2; ++i) {
            sol[index++] = i;
            sol[index++] = -i;
        }
        if(n % 2 != 0){
            sol[index] = 0;
        }
        return sol;
    }
}
```
## 28. Lucky Numbers in a Matrix
```java
class Solution {
    public List<Integer> luckyNumbers(int[][] matrix) {
        List<Integer> list = new ArrayList<>();
        int index = 0;
        for(int i = 0; i < matrix.length; ++i) {
            boolean isLucky = true;
            int rmin = Integer.MAX_VALUE;
            for(int j = 0; j < matrix[i].length; ++j) {
                if(matrix[i][j] < rmin) {
                    rmin = matrix[i][j];
                    index = j;
                }
            }

            for(int row = 0; row < matrix.length; ++row) {
                if(matrix[row][index] > rmin) {
                    isLucky = false;
                    break;
                }
            }
            if(isLucky) list.add(rmin);

        }

        return list;
    }
}
 
```
## 29. Build Array from Permutation
```java
class Solution {
    public int[] buildArray(int[] nums) {
        int[] ans = new int[nums.length];
        int index = 0;
        for(int num : nums) {
            ans[index++] = nums[num];
        }
        return ans;
    }
}
```
## 30. Transpose Matrix
```java
class Solution {
    public int[][] transpose(int[][] matrix) {
        int rowLen = matrix.length;
        int colLen = matrix[0].length;
        int[][] sol = new int[colLen][rowLen];
        for(int col = 0; col < colLen; ++col) {
            for(int row = 0; row < rowLen; ++row) {
                 sol[col][row] = matrix[row][col];
            }
        }
        return sol;
    }
}
```


 


 
