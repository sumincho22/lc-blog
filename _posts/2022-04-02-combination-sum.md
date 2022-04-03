---
layout: post
title:  "Combination Sum"
date:   2022-04-02 23:30:00 +0000
categories: medium dynammic programming
---
# Description
- 

# Code
{% highlight ruby %}
def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
    ret = []
    
    def dfs(i, cur, total):
        if total == target:
            ret.append(cur.copy())
            return
        
        if i >= len(candidates) or total > target:
            return
        
        cur.append(candidates[i])
        dfs(i, cur, total + candidates[i])
        cur.pop()
        dfs(i + 1, cur, total)
    
    dfs(0, [], 0)
    
    return ret
{% endhighlight %}

# Algorithm Analysis
O(2^{target}) time

O(n) space

# Best Solution
{% highlight ruby %}
def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
    ret = []
    
    def dfs(i, cur, total):
        if total == target:
            ret.append(cur.copy())
            return
        
        if i >= len(candidates) or total > target:
            return
        
        cur.append(candidates[i])
        dfs(i, cur, total + candidates[i])
        cur.pop()
        dfs(i + 1, cur, total)
    
    dfs(0, [], 0)
    
    return ret
{% endhighlight %}