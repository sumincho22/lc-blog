---
layout: post
title:  "Number of Islands"
date:   2022-03-24 23:50:00 +0000
categories: medium graph
---
# Description
1. Iterate through entire grid O(mn)
2. If encounter "1", use DFS to turn the surrounding "1" into "0"

# Code
{% highlight ruby %}
def numIslands(self, grid: List[List[str]]) -> int:
    # Iterate through entire grid O(mn)
    # If encounter "1", use DFS to turn the surrounding "1" into "0"
    m, n = len(grid), len(grid[0])
    
    count = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == '1':
                self.dfs(grid, i, j)
                count += 1
    
    return count

def dfs(self, grid, i, j):
    # base case
    if  i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] == '0':
        return
    
    grid[i][j] = '0'
    
    self.dfs(grid, i+1, j)
    self.dfs(grid, i-1, j)
    self.dfs(grid, i, j+1)
    self.dfs(grid, i, j-1)
{% endhighlight %}

# Algorithm Analysis
O((mn)^2) time

O(1) space

# Best Solution
{% highlight ruby %}
def numIslands(self, grid: List[List[str]]) -> int:
    m, n = len(grid), len(grid[0])
    
    count = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == '1':
                self.dfs(grid, i, j)
                count += 1
    
    return count
    
    def dfs(self, grid, i, j):
        if  i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] == '0':
            return
        
        grid[i][j] = '0'
        
        self.dfs(grid, i+1, j)
        self.dfs(grid, i-1, j)
        self.dfs(grid, i, j+1)
        self.dfs(grid, i, j-1)
{% endhighlight %}