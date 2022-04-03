---
layout: post
title:  "Binary Tree Level Order Traversal"
date:   2022-04-03 17:00:00 +0000
categories: medium tree
---
# Description
- At current level, add values of all nodes
- Track next level by adding current level's children

# Code
{% highlight ruby %}
def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
    ret = []
    
    level = [root]
    
    while root and level:
        currentNodes = []
        nextLevel = []
        
        for node in level:
            currentNodes.append(node.val)
            if node.left:
                nextLevel.append(node.left)
            if node.right:
                nextLevel.append(node.right)
                
        ret.append(currentNodes)
        level = nextLevel
    
    return ret
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(n) space

# Best Solution
{% highlight ruby %}
def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
    ret = []
    
    level = [root]
    
    while root and level:
        currentNodes = []
        nextLevel = []
        
        for node in level:
            currentNodes.append(node.val)
            if node.left:
                nextLevel.append(node.left)
            if node.right:
                nextLevel.append(node.right)
                
        ret.append(currentNodes)
        level = nextLevel
    
    return ret
{% endhighlight %}