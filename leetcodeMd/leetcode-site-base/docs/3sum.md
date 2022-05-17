---
id: 3sum
title: 3Sum
sidebar_label: 3Sum
---
## Description
<div class="description">
<p>Given an integer array nums, return all the triplets <code>[nums[i], nums[j], nums[k]]</code> such that <code>i != j</code>, <code>i != k</code>, and <code>j != k</code>, and <code>nums[i] + nums[j] + nums[k] == 0</code>.</p>

<p>Notice that the solution set must not contain duplicate triplets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [-1,0,1,2,-1,-4]
<strong>Output:</strong> [[-1,-1,2],[-1,0,1]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = []
<strong>Output:</strong> []
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 3000</code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    nums.sort((a,b) => a -b);
    const result = {};
    for(let i = 0; i < nums.length - 2; i++) {
        let left = i + 1;
        let right = nums.length - 1;
        while(left < right) {
            const sum = nums[i] + nums[left] + nums[right];
            if (sum === 0) {
                const key = nums[i].toString() + nums[left].toString()  + nums[right].toString();
                result[key] = [ nums[i] , nums[left] , nums[right] ];
            }
            
            if(sum < 0) {
                left +=1;
            } else {
                right -=1;
            }
        }
    }
    
    return Object.values(result);
};
```