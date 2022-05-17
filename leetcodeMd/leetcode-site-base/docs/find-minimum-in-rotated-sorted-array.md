---
id: find-minimum-in-rotated-sorted-array
title: Find Minimum in Rotated Sorted Array
sidebar_label: Find Minimum in Rotated Sorted Array
---
## Description
<div class="description">
<p>Suppose an array of length <code>n</code> sorted in ascending order is <strong>rotated</strong> between <code>1</code> and <code>n</code> times. For example, the array <code>nums = [0,1,2,4,5,6,7]</code> might become:</p>

<ul>
	<li><code>[4,5,6,7,0,1,2]</code> if it was rotated <code>4</code> times.</li>
	<li><code>[0,1,2,4,5,6,7]</code> if it was rotated <code>7</code> times.</li>
</ul>

<p>Notice that <strong>rotating</strong> an array <code>[a[0], a[1], a[2], ..., a[n-1]]</code> 1 time results in the array <code>[a[n-1], a[0], a[1], a[2], ..., a[n-2]]</code>.</p>

<p>Given the sorted rotated array <code>nums</code> of <strong>unique</strong> elements, return <em>the minimum element of this array</em>.</p>

<p>You must write an algorithm that runs in&nbsp;<code>O(log n) time.</code></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,4,5,1,2]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The original array was [1,2,3,4,5] rotated 3 times.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,5,6,7,0,1,2]
<strong>Output:</strong> 0
<strong>Explanation:</strong> The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [11,13,15,17]
<strong>Output:</strong> 11
<strong>Explanation:</strong> The original array was [11,13,15,17] and it was rotated 4 times. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 5000</code></li>
	<li><code>-5000 &lt;= nums[i] &lt;= 5000</code></li>
	<li>All the integers of <code>nums</code> are <strong>unique</strong>.</li>
	<li><code>nums</code> is sorted and rotated between <code>1</code> and <code>n</code> times.</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMin = function(nums) {
    // let min = nums[0];
    // nums.sort((a,b) => a -b);
    // if (nums[0] < min) return nums[0]
    // return min;
    // Binary Search
    var left = 0,
        right = nums.length - 1
    
    while (left < right){
        var mid = Math.floor((left + right)/2)
        //For an un-rotated sorted array, we can easily understand that there can never be a case where nums[mid] would ever be greater than nums[right]. However, this condition can happen in a rotated array if the mid pointer is residing on the left side of the rotated array. Once we know that the mid pointer is at the left side of the array, we can start to cut down our search to only the right side since we know that the minimum value can never be in the left side. Hence, we update the left pointer to be mid + 1, indicating that we are now searching the right side.


        if (nums[mid] > nums[right]) left = mid + 1
        // This condition will tell us that the subarray that we are currently searching is now a properly sorted array which is un-rotated. To get the minimum value of this subarray, we simply have to keep adjusting the right pointer to the left by setting the mid pointer as the right pointer, cutting down our serach to only the left half of this subarray. Eventually, we will reach the left most element of this subarray.

        else right = mid
    }
    return nums[left]
    //Time = O(logn)
};
```