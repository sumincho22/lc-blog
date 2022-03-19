---
layout: post
title:  "Longest Palindromic Substring"
date:   2022-03-19 16:15:00 +0000
categories: medium string
---
# Description
1. Iterate through string, using a helper method for odd and even centers
2. The helper method uses left and right pointers to spread from the center and stops when palindrome is not found, returns the longest palindrome for that center
3. Take the max of the string lengths and return it after the string iteration

# Code
{% highlight ruby %}
def longestPalindrome(self, s: str) -> str:
    ret = ""
    for i in range(len(s)):
        odd = self.helper(s, i, i)
        even = self.helper(s, i, i+1)
        
        ret = max(ret, odd, even, key=len)
    
    return ret

def helper(self, s, l, r):
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    
    return s[l+1:r]
{% endhighlight %}

# Algorithm Analysis
O(n^2) time

O(1) space

# Best Solution
{% highlight ruby %}
def longestPalindrome(self, s: str) -> str:
    ret = ""
    for i in range(len(s)):
        odd = self.helper(s, i, i)
        even = self.helper(s, i, i+1)
        
        ret = max(ret, odd, even, key=len)
    
    return ret

def helper(self, s, l, r):
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    
    return s[l+1:r]
{% endhighlight %}