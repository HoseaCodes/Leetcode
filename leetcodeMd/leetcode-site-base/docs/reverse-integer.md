---
id: reverse-integer
title: Reverse Integer
sidebar_label: Reverse Integer
---
## Description
<div class="description">
<p>Given a signed 32-bit integer <code>x</code>, return <code>x</code><em> with its digits reversed</em>. If reversing <code>x</code> causes the value to go outside the signed 32-bit integer range <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code>, then return <code>0</code>.</p>

<p><strong>Assume the environment does not allow you to store 64-bit integers (signed or unsigned).</strong></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> x = 123
<strong>Output:</strong> 321
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> x = -123
<strong>Output:</strong> -321
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> x = 120
<strong>Output:</strong> 21
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;= x &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
      var reverseX = parseInt(x.toString().split('').reverse().join(''));
    if (reverseX < (Math.pow(2, 31) * -1) || reverseX > Math.pow(2, 31) - 1) return 0;
    return reverseX* Math.sign(x);
};
```