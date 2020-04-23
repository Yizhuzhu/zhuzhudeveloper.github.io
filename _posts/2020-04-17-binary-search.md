---
category: algorithm
tags: Binary Search
---

# Binary Search
## Characteristic
* Sequence in order
* Time Complexity O(logn)
* Space Complexity O(1)
### Perfect Code
```
        if len(nums) == 0:
            return 0
        if nums[-1] < target:
            return len(nums)
        if nums[0]>target:
            return 0
        left = 0
        right = len(nums) - 1
        while(left<right):
            mid = left + (right-left) // 2
            if(nums[mid]<target):
                left = mid + 1
            else:
                right = mid
        return left
```
### LeetCode 34: Find First and Last Position of Element in Sorted Array
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.       
Your algorithm's runtime complexity must be in the order of O(log n).       
If the target is not found in the array, return [-1, -1].
```
        res = [-1,-1]
        if len(nums) == 0:
            return res
        if nums[-1] < target or nums[0] > target:
            return res
        left = 0
        right = len(nums)-1
        # Look for the first one
        while(left < right):
            mid = left + (right - left)//2
            if(nums[mid]<target):
                left=mid+1
            else:
                right=mid
        if(nums[left]==target):
            res[0] = left
        else: return res
        left = 0
        right = len(nums)-1
        # Look for the right one
        while(left<right):
            mid = left + (right-left)//2 + 1
            if(nums[mid]>target):
                right=mid-1
            else:
                left=mid
        res[1] = right
        return res
```
### LeetCode 33: Search in Rotated Sorted Array
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.    
(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).     
You are given a target value to search. If found in the array return its index, otherwise return -1.      
You may assume no duplicate exists in the array.       
Your algorithm's runtime complexity must be in the order of O(log n).
```
        if len(nums) == 0:
            return -1
        # Binary Search to find the pivot
        left = 0
        right = len(nums) - 1
        while(left<right):
            mid = left + (right-left)//2 
            if(nums[right]<nums[mid]):
                left = mid + 1
            else:
                right = mid
        pivot = left
        # Choose one part to do binary search again, looking for the target
        if(nums[-1]>=target or pivot == 0):
            left = pivot
            right = len(nums) - 1
        else:
            left = 0
            right = pivot-1
        while(left<right):
            mid = left + (right-left)//2
            if(nums[mid]<target):
                left = mid + 1
            else:
                right = mid
        if(nums[left]==target):
            return left
        else:
            return -1
```
### LeetCode 154: Find Minimum in Rotated Sorted Array II
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.     
(i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).     
Find the minimum element.           
The array may contain duplicates.
```
        while(left<right):
            mid = left + (right-left)//2
            if(nums[mid]<nums[right]):
                right = mid
            elif(nums[mid]>nums[right]):
                left = mid + 1
            else:
                right = right -1
        return nums[left]
```
