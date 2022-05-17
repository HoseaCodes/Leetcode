---
id: find-the-duplicate-number
title: Find the Duplicate Number
sidebar_label: Find the Duplicate Number
---
## Description
<div class="description">
<p>Given an array of integers <code>nums</code> containing&nbsp;<code>n + 1</code> integers where each integer is in the range <code>[1, n]</code> inclusive.</p>

<p>There is only <strong>one repeated number</strong> in <code>nums</code>, return <em>this&nbsp;repeated&nbsp;number</em>.</p>

<p>You must solve the problem <strong>without</strong> modifying the array <code>nums</code>&nbsp;and uses only constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,4,2,2]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,1,3,4,2]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>nums.length == n + 1</code></li>
	<li><code>1 &lt;= nums[i] &lt;= n</code></li>
	<li>All the integers in <code>nums</code> appear only <strong>once</strong> except for <strong>precisely one integer</strong> which appears <strong>two or more</strong> times.</li>
</ul>

<p>&nbsp;</p>
<p><b>Follow up:</b></p>

<ul>
	<li>How can we prove that at least one duplicate number must exist in <code>nums</code>?</li>
	<li>Can you solve the problem in linear runtime complexity?</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findDuplicate = function(nums) {
    //Traverse the array from start to end.
    //For every element,take its absolute value:
        //if the abs(array[i])‘th element is positive, the element has not encountered before, 
        //else if its negative meaning the element has been encountered before, print the                   absolute value of the current element.
    //Works only when there is only one repeated number and nums containing n + 1 integers where       each integer is in the range [1, n] inclusive.
    //Each encountered element modifies the value in the corresponding index in array and when we       reach an element that already was modified -it means that the index already appeared -          meaning the element is duplicated.
    for (var i = 0; i < nums.length; i++) {
        var absNum = Math.abs(nums[i]);
        // If not seen yet
        if (nums[absNum] >= 0) {
            nums[absNum] *= -1;
        } else {
            return absNum;
        }
    }   
};
```