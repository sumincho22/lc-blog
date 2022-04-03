---
layout: post
title:  "Valid Palindrome"
date:   2022-04-03 14:05:00 +0000
categories: easy string
---
# Description
- Have two pointers left and right and converge them only for alpha-numeric characters
- If s[l] and s[r] are not the same, return False

# Code
{% highlight ruby %}
def isPalindrome(self, s: str) -> bool:
    l, r = 0, len(s) - 1
    
    while l < r:
        while l < r and not s[l].isalnum():
            l += 1
        while r > l and not s[r].isalnum():
            r -= 1
        
        if s[l].lower() != s[r].lower():
            return False
        
        l += 1
        r -= 1
    
    return True
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(1) space

# Best Solution
{% highlight ruby %}
def isPalindrome(self, s):
    newS= [i.lower() for i in s if i.isalnum()]
    return newS == newS[::-1]
{% endhighlight %}