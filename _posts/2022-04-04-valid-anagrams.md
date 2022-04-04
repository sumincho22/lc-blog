---
layout: post
title:  "Valid Anagrams"
date:   2022-04-04 18:00:00 +0000
categories: easy array
---
# Description
- Use dictionary to get the counts for s and t

# Code
{% highlight ruby %}
def isAnagram(self, s: str, t: str) -> bool:
    if len(s) != len(t):
        return False
    
    dic_s, dic_t = {}, {}
    
    for i in range(len(s)):
        dic_s[s[i]] = dic_s.get(s[i], 0) + 1
        dic_t[t[i]] = dic_t.get(t[i], 0) + 1
    
    for k, v in dic_s.items():
        if dic_t.get(k) != v:
            return False
    
    return True
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(n) space

# Best Solution
{% highlight ruby %}
def isAnagram(self, s: str, t: str) -> bool:
    if len(s) != len(t):
        return False
    
    dic_s, dic_t = {}, {}
    
    for i in range(len(s)):
        dic_s[s[i]] = dic_s.get(s[i], 0) + 1
        dic_t[t[i]] = dic_t.get(t[i], 0) + 1
    
    for k, v in dic_s.items():
        if dic_t.get(k) != v:
            return False
    
    return True
{% endhighlight %}