---
layout: post
title:  "Group Anagrams"
date:   2022-04-04 18:40:00 +0000
categories: easy array
---
# Description
- Sort strings alphabetically and use them as keys
- The values of this dictionary are lists of same anagrams

# Code
{% highlight ruby %}
def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
    dic = {}
    for s in strs:
        tmp = ''.join(sorted(s))
        l = dic.get(tmp, [])
        l.append(s)
        dic[tmp] = l
    return dic.values()
{% endhighlight %}

# Algorithm Analysis
O(n (k log k)) time where k is the longest string in the list

O(n) space

# Best Solution
{% highlight ruby %}
def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
    ans = collections.defaultdict(list)
    
    for s in strs:
        count = [0] * 26
        for c in s:
            count[ord(c) - ord('a')] += 1
        ans[tuple(count)].append(s)
    return ans.values()
{% endhighlight %}