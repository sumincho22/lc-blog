---
layout: post
title:  "Contains Duplicate"
date:   2022-03-22 23:30:00 +0000
categories: easy array
---
# Description
1. Iterate through to check if count of a number comes up twice using a dictionary

# Code
{% highlight ruby %}
def containsDuplicate(self, nums: List[int]) -> bool:
    d = {}
    for x in nums:
        if not d.get(x):
            d[x] = 1
        else:
            return True
    
    return False
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(n) space

# Best Solution
{% highlight ruby %}
def containsDuplicate(self, nums: List[int]) -> bool:
    return len(nums) != len(set(nums))
{% endhighlight %}