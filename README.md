# Flatten-a-Multilevel-Doubly-Linked-List
"""
# Definition for a Node.
class Node:
    def __init__(self, val, prev, next, child):
        self.val = val
        self.prev = prev
        self.next = next
        self.child = child
"""
class Solution:
    def flatten(self, head: 'Optional[Node]') -> 'Optional[Node]':
        if head is None:
            return None
        r=[]
        def add(head,r):
            if head is None:
                return
            r.append(head.val)
            add(head.child,r)
            add(head.next,r)
        add(head,r)
        d=Node(0,None,None,None)
        temp=d
        for i in r:
            t=Node(i,temp,None,None)
            temp.next=t
            temp=t
        d.next.prev=None
        return d.next
