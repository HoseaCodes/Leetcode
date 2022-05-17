---
id: count-of-smaller-numbers-after-self
title: Count of Smaller Numbers After Self
sidebar_label: Count of Smaller Numbers After Self
---
## Description
<div class="description">
<p>You are given an integer array <code>nums</code> and you have to return a new <code>counts</code> array. The <code>counts</code> array has the property where <code>counts[i]</code> is the number of smaller elements to the right of <code>nums[i]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,2,6,1]
<strong>Output:</strong> [2,1,1,0]
<strong>Explanation:</strong>
To the right of 5 there are <b>2</b> smaller elements (2 and 1).
To the right of 2 there is only <b>1</b> smaller element (1).
To the right of 6 there is <b>1</b> smaller element (1).
To the right of 1 there is <b>0</b> smaller element.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1]
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,-1]
<strong>Output:</strong> [0,0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var countSmaller = function(nums) {
    const sortedElements = [];
    const smallerElements = [];
    for (let i = nums.length - 1; i >= 0; i--) {
        let position = binarySearch(nums[i], sortedElements);
        if (sortedElements[position] >= nums[i] || sortedElements.length === 0) {
            sortedElements.splice(position, 0, nums[i]);
        } else {
            position += 1;
            sortedElements.splice(position, 0, nums[i]);
        }
        smallerElements.unshift(position);
    }
    return smallerElements;
};

const binarySearch = (value, nums) => {
    if (nums.length === 0) return 0;
    let left = 0;
    let right = nums.length - 1;
    let mid = left + Math.floor((right - left) / 2);
    while (left !== right) {
        if (value > nums[mid]) {
            // go right
            left = Math.min(mid + 1, right);
        } else if (value < nums[mid]) {
            // go left
            right = Math.max(mid - 1, left);
        } else {
            // sorta go left
            right = mid;
        }
        mid = left + Math.floor((right - left) / 2);
    }
    return left;
};
```