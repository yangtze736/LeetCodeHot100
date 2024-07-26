```
给你一个整数数组 nums 和一个整数 k ，请你统计并返回 该数组中和为 k 的子数组的个数 。

子数组是数组中元素的连续非空序列。

 
示例 1：

输入：nums = [1,1,1], k = 2
输出：2

示例 2：

输入：nums = [1,2,3], k = 3
输出：2
 

提示：

1 <= nums.length <= 2 * 104
-1000 <= nums[i] <= 1000
-107 <= k <= 107
```

```
import java.util.HashMap;

class Solution {
    public int subarraySum(int[] nums, int k) {
        int res = 0;
        int prefixSum = 0;
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        
        for (int num : nums) {
            prefixSum += num;
            if (map.containsKey(prefixSum - k)) {
                res += map.get(prefixSum - k);
            }
            
            map.put(prefixSum, map.getOrDefault(prefixSum, 0) + 1);
        }
        
        return res;
    }
}
```