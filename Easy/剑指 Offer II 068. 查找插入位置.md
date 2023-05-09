
题目难度：简单

给定一个排序的整数数组 nums 和一个整数目标值 target ，请在数组中找到 target ，并返回其下标。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为 `O(log n)` 的算法。

示例：
```
输入: nums = [1,3,5,6], target = 5
输出: 2

输入: nums = [1,3,5,6], target = 2
输出: 1

输入: nums = [1,3,5,6], target = 7
输出: 4

输入: nums = [1,3,5,6], target = 0
输出: 0

输入: nums = [1], target = 0
输出: 0
```

个人解答：
```C++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target){
        // 二分查找
        int left = 0, right = nums.size() - 1;
        while(left <= right){
            if(nums[(left + right)/2] == target){
                return (left + right)/2;
            }
            else if(nums[(left + right)/2] > target){
                right = (left + right)/2 - 1;
            }
            else if(nums[(left + right)/2] < target){
                left = (left + right)/2 + 1;
            }
        }
        return left;
    }
};
```

经典的二分搜索，log(n)的时间复杂度，本题目的个人解答为极简的二分查找写法，我们主要需要注意的就是while的判断条件，以及left和right的循环变化。