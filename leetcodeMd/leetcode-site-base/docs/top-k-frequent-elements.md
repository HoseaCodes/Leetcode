---
id: top-k-frequent-elements
title: Top K Frequent Elements
sidebar_label: Top K Frequent Elements
---
## Description
<div class="description">
<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the</em> <code>k</code> <em>most frequent elements</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,1,2,2,3], k = 2
<strong>Output:</strong> [1,2]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>k</code> is in the range <code>[1, the number of unique elements in the array]</code>.</li>
	<li>It is <strong>guaranteed</strong> that the answer is <strong>unique</strong>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Your algorithm&#39;s time complexity must be better than <code>O(n log n)</code>, where n is the array&#39;s size.</p>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    let frequency = {};
    for (let i = 0; i < nums.length; i++) {
        if (frequency[nums[i]]) {
            frequency[nums[i]] += 1
        } else {
            frequency[nums[i]] = 1
        }
    }
    
    let sorted = Object.entries(frequency).sort((a,b)=> b[1] - a[1]) 
    let res = []
    for (let i = 0; i < k; i++) {
        res.push(sorted[i][0])
    }

    return res
};
```