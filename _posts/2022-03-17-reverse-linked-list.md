---
layout: post
title:  "Reverse Linked List"
date:   2022-03-17 16:55:00 +0000
categories: easy linked list
---
# Description
1. Iterate through the original linked list and put them in a stack
2. Pop the stack until empty; change the next values to previous nodes

# Code
{% highlight ruby %}
def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
    # 1. Iterate through the head, storing all the nodes in a stack
    # 2. Iterate through the stack by popping, and override the next values to the prev
    ret = head
    
    stack = []
    
    curr = head
    while curr:
        # if curr is on last node
        if not curr.next:
            ret = curr
            break
        
        stack.append(curr)
        
        curr = curr.next
    
    curr = ret
    while stack:
        curr.next = stack.pop()
        curr = curr.next
        
        if not stack:
            curr.next = None
    
    return ret
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(n) space

# Best Solution
{% highlight ruby %}
def reverseList(self, head):
    """
    :type head: ListNode
    :rtype: ListNode
    """
    cur, prev = head, None
    while cur:
        cur.next, prev, cur = prev, cur, cur.next
    return prev
{% endhighlight %}