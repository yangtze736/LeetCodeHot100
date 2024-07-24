给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

```
class Solution {
    public int trap(int[] height) {
        int[] left = new int[height.length];
        int[] right = new int[height.length];

        int max = 0;
        for (int i  = 0; i < height.length ; i++) {
            left[i] = max;
            max = Math.max(max, height[i]);
        }

        max = 0;
        for (int i = height.length - 1; i >= 0; i--) {
            right[i] = max;
            max = Math.max(max, height[i]);
        }

        int res = 0;
        for (int i = 0; i < height.length; i++) {
            int h = Math.min(left[i], right[i]);
            if (h > height[i]) {
                res += h - height[i];
            }
        }

        return res;
    }
}
```
