---
layout: post
title:  "Course Schedule"
date:   2022-03-20 22:45:00 +0000
categories: medium graph
---
# Description
1. Make a graph out of the prerequisites list and use DFS to detect any cycles -> return False

# Code
{% highlight ruby %}
def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
    # We want to find when we can NOT finish the courses
    # Here are the conditions for returning FALSE:
    # 1. the two are prereqs of one another e.g. [[1,0],[0,1]]
    # 2. if a is a prereq of b and b is a prereq of c and c is a prereq of a
    # 2a. [b,a],[c,b],[a,c]
    
    graph = [[] for _ in range(numCourses)]
    visited = [0 for _ in range(numCourses)]
    
    # Create graph
    for x, y in prerequisites:
        graph[x].append(y)
    
    # Visit each node
    for i in range(numCourses):
        if not self.dfs(graph, visited, i):
            return False
    
    return True

def dfs(self, graph, visited, i):
    # If node is being visited, then cycle is found
    if visited[i] == -1:
        return False
    
    # If node is already visited, do not visit again
    if visited[i] == 1:
        return True
    
    # Mark as being visited
    visited[i] = -1
    
    # Visit all its neighbors
    for j in graph[i]:
        if not self.dfs(graph, visited, j):
            return False
    
    # After visiting all its neighbors, mark it as done visited
    visited[i] = 1
    
    return True
{% endhighlight %}

# Algorithm Analysis
O(n^2) time

O(n^2) space

# Best Solution
{% highlight ruby %}
def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
    graph = [[] for _ in range(numCourses)]
    visited = [0 for _ in range(numCourses)]

    for x, y in prerequisites:
        graph[x].append(y)
    
    for i in range(numCourses):
        if not self.dfs(graph, visited, i):
            return False
    
    return True

def dfs(self, graph, visited, i):
    if visited[i] == -1:
        return False
    
    if visited[i] == 1:
        return True
    
    visited[i] = -1
    
    for j in graph[i]:
        if not self.dfs(graph, visited, j):
            return False
    
    visited[i] = 1
    
    return True
{% endhighlight %}