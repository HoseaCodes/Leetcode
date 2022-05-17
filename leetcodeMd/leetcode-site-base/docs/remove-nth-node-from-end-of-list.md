---
id: remove-nth-node-from-end-of-list
title: Remove Nth Node From End of List
sidebar_label: Remove Nth Node From End of List
---
## Description
<div class="description">
<p>Given the <code>head</code> of a linked list, remove the <code>n<sup>th</sup></code> node from the end of the list and return its head.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" style="width: 542px; height: 222px;" />
<pre>
<strong>Input:</strong> head = [1,2,3,4,5], n = 2
<strong>Output:</strong> [1,2,3,5]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> head = [1], n = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> head = [1,2], n = 1
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is <code>sz</code>.</li>
	<li><code>1 &lt;= sz &lt;= 30</code></li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li><code>1 &lt;= n &lt;= sz</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do this in one pass?</p>

</div>

## Solution(javascript)
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    // move currentNode n steps into list
    let currentNode = head;
    
    for ( let i = 0; i < n; i++) {
        currentNode = currentNode.next;
    }
    
    if (currentNode == null) {
        return head.next;
    }
    
    // move both pointers until currentNode reaches the end of list
    let nodeBeforeRemoved = head;
    
    while(currentNode.next !== null) {
        currentNode = currentNode.next;
        nodeBeforeRemoved = nodeBeforeRemoved.next;
    }
    
    nodeBeforeRemoved.next = nodeBeforeRemoved.next.next;
    
    return head;
    // Time = O(n)
    // Space = O(n)
    
//     let length = 0;
//     let currentNode = head;
    
//     // find length of list
//     while(currentNode !== null) {
//         currentNode = currentNode.next;
//         length++;
//     }
    
//     if (length == n) {
//         return head.next;
//     }
    
//     // find the node to remove
//     let nodeIndex = length - n 
//     let nodeBeforeRemovedIndex = nodeIndex - 1;
//     currentNode = head;
//     for(let i = 0; i < nodeBeforeRemovedIndex; i++) {
//         currentNode = currentNode.next;
//     }
//     currentNode.next = currentNode.next.next;
    
//     return head;
    
//     // Time = O(n)
//     // Space = O(1)
    
    
};
```