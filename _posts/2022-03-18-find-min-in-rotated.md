---
layout: post
title:  "Find Minimum in Rotated Sorted Array"
date:   2022-03-18 11:04:00 +0000
categories: medium array
---
# Description
1. Binary search, look for decreasing point

# Code
{% highlight ruby %}
def findMin(self, nums: List[int]) -> int:
    # O(log n) -> split list in halves recursively
    # Find a position which decreases
    # If not, return origin
    if len(nums) == 1:
        return nums[0]
    
    pos = self.findDecreasing(0, len(nums) - 1, nums)
    
    if pos == -1:
        return nums[0]
    elif pos >= 0 and pos < len(nums):
        return nums[pos]

def findDecreasing(self, left, right, nums):
    # base cases
    if left >= right:
        return -1
    if right - left == 1:
        if nums[left] > nums[right]:
            return right
        else:
            return -1
    
    mid = (left + right) // 2
    
    if nums[mid] > nums[left]:
        return self.findDecreasing(mid, right, nums)
    else:
        return self.findDecreasing(left, mid, nums)
{% endhighlight %}

# Algorithm Analysis
O(log n) time

O(1) space

# Best Solution
{% highlight ruby %}
def findMin(self, num):
    first, last = 0, len(num) - 1
    while first < last:
        midpoint = (first + last) // 2
        if num[midpoint] > num[last]:
            first = midpoint + 1
        else:
            last = midpoint
    return num[first]
{% endhighlight %}