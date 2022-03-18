---
layout: post
title:  "Reverse Linked List II"
date:   2022-03-18 10:32:00 +0000
categories: medium linked list
---
# Description
1. If left and right are same, it should be same linked list
2. Iterate through linked list, setting 'start' to be at position left - 1 and 'end' to be at position right
3. During this iteration, swap all next values within 'start' and 'end'
4. The next values of 'start' and 'end' should be reflecting the change

# Code
{% highlight ruby %}
def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
    if left == right:
        return head
    curr, prev, start, end = head, None, None, None
    pos = 1
    while curr:
        if pos == left - 1:
            start = curr
            
        if pos >= left and pos <= right:
            if pos == left:
                end = curr
            if pos == right:
                if start:
                    start.next = curr
                if end == head:
                    head = curr
                end.next = curr.next
            
            curr.next, curr, prev = prev, curr.next, curr
        else:
            curr, prev = curr.next, curr
        
        pos += 1
    return head
{% endhighlight %}

# Algorithm Analysis
O(n) time
O(1) space

# Best Solution
{% highlight ruby %}
def reverseBetween(self, head: ListNode, left: int, right: int) -> ListNode:
    if not head or not head.next or left == right:
        return head
    
    dummy_head = ListNode(val=-1, next=head)
    p_prev = dummy_head
    
    # Iterate p_prev to the (left-1)-th node
    for _ in range(left - 1):
        p_prev = p_prev.next
        
    p_cur = p_prev.next # p_cur is at the left-th node
    
    # Within the reverse part, iteratively move the next node of p_cur to the beginning
    for _ in range(right - left):
        p_next = p_cur.next
        p_cur.next = p_next.next
        p_next.next = p_prev.next
        p_prev.next = p_next
    
    return dummy_head.next
{% endhighlight %}