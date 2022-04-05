---
layout: post
title:  "Merge Two Sorted Lists"
date:   2022-04-04 22:00:00 +0000
categories: easy linked list
---
# Description
- Pointers for two lists concurrently
- Add which one is smaller
- At the end, check if one is still not empty

# Code
{% highlight ruby %}
def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
    dummy = ListNode()
    cur = dummy
    while l1 and l2:
        if l1.val < l2.val:
            cur.next = l1
            l1 = l1.next
        else:
            cur.next = l2
            l2 = l2.next
        cur = cur.next
    
    if not l1:
        cur.next = l2
    else:
        cur.next = l1
    
    return dummy.next
{% endhighlight %}

# Algorithm Analysis
O(n) time

O(n) space

# Best Solution
{% highlight ruby %}
def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
    dummy = ListNode()
    cur = dummy
    while l1 and l2:
        if l1.val < l2.val:
            cur.next = l1
            l1 = l1.next
        else:
            cur.next = l2
            l2 = l2.next
        cur = cur.next
    
    if not l1:
        cur.next = l2
    else:
        cur.next = l1
    
    return dummy.next
{% endhighlight %}