---
layout: post
title:  "Palindromic Substrings"
date:   2022-04-03 14:10:00 +0000
categories: medium string
---
# Description
- Iterate through string and count all the possible palindromic substrings at each index i
- Account for both even and odd starts and spread out to check for palindromes

# Code
{% highlight ruby %}
def countSubstrings(self, s: str) -> int:
    count = 0
    
    for i in range(len(s)):
        count += self.countPal(s, i, i)
        count += self.countPal(s, i, i + 1)
    
    return count

def countPal(self, s, l, r):
    count = 0
    
    while l >= 0 and r < len(s) and s[l] == s[r]:
        count += 1
        
        l -= 1
        r += 1
        
    return count
{% endhighlight %}

# Algorithm Analysis
O(n^2) time

O(1) space

# Best Solution
{% highlight ruby %}
def countSubstrings(self, s: str) -> int:
    count = 0
    
    for i in range(len(s)):
        count += self.countPal(s, i, i)
        count += self.countPal(s, i, i + 1)
    
    return count

def countPal(self, s, l, r):
    count = 0
    
    while l >= 0 and r < len(s) and s[l] == s[r]:
        count += 1
        
        l -= 1
        r += 1
        
    return count
{% endhighlight %}