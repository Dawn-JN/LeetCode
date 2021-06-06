# 剑指offer-03-数组中重复的数字
**题目**

找出数组中重复的数字。
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 

**思路**

1.遍历数组

2.原地交换，数组长度为n，范围0~n-1，做nums[i] = i 形式数组（类似哈希表），当有nums[i] != i时，若有nums[i] = nums[nums[i]]，说明有重复，反之交换nums[i]， nums[nums[i]]位置

**代码**

~~~python
# 遍历
def findRepeatNumber(self, nums):
    """
    :type nums: List[int]
    :rtype: int
    """
    nums.sort()
    for i in range(len(nums) - 1):
        if nums[i] == nums[i + 1]:
            return nums[i]
    return -1


# 原地交换
def findRepeatNumber2(self, nums):
    """
    :type nums: List[int]
    :rtype: int
    """
    temp = 0
    for i in range(len(nums)):
        while nums[i] != i:
            # 判断
            if nums[i] == nums[nums[i]]:
                return nums[i]
            # 交换
            temp = nums[i]
            nums[i] = nums[temp]
            nums[temp] = temp
    return -1
~~~
