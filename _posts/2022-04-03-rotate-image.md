---
layout: post
title:  "Rotate Image"
date:   2022-04-03 00:20:00 +0000
categories: medium matrix
---
# Description
- General pattern:
    - Keep top left as temp value
    - Bottom left to top left
    - Bottom right to bottom left
    - Top right to bottom right
    - Top left (temp) to top right

# Code
{% highlight ruby %}
def rotate(self, matrix: List[List[int]]) -> None:
    """
    Do not return anything, modify matrix in-place instead.
    """
    l, r = 0, len(matrix) - 1
    while l < r:
        top, bottom = l, r
        
        for i in range(r - l):
            top_left = matrix[top][l + i]
            
            matrix[top][l + i] = matrix[bottom - i][l]
            matrix[bottom - i][l] = matrix[bottom][r - i]
            matrix[bottom][r - i] = matrix[top + i][r]
            matrix[top + i][r] = top_left
        
        l += 1
        r -= 1
{% endhighlight %}

# Algorithm Analysis
O(n^2) time

O(1) space

# Best Solution
{% highlight ruby %}
def rotate(self, matrix: List[List[int]]) -> None:
    """
    Do not return anything, modify matrix in-place instead.
    """
    l, r = 0, len(matrix) - 1
    while l < r:
        top, bottom = l, r
        
        for i in range(r - l):
            top_left = matrix[top][l + i]
            
            matrix[top][l + i] = matrix[bottom - i][l]
            matrix[bottom - i][l] = matrix[bottom][r - i]
            matrix[bottom][r - i] = matrix[top + i][r]
            matrix[top + i][r] = top_left
        
        l += 1
        r -= 1
{% endhighlight %}