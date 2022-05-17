---
id: longest-common-prefix
title: Longest Common Prefix
sidebar_label: Longest Common Prefix
---
## Description
<div class="description">
<p>Write a function to find the longest common prefix string amongst an array of strings.</p>

<p>If there is no common prefix, return an empty string <code>&quot;&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>Output:</strong> &quot;fl&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>Output:</strong> &quot;&quot;
<strong>Explanation:</strong> There is no common prefix among the input strings.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 200</code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 200</code></li>
	<li><code>strs[i]</code> consists of only lower-case English letters.</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    // If the string is empty return empty string
     if (strs.length === 0) return "";
    // The prefix is the start of the word
    let prefix = strs[0];
    // Iterate over the array
    for (let i = 1; i < strs.length; i++)
        // Returns -1 or 0. 0 if the char matches the prefix
        while (strs[i].indexOf(prefix) !== 0) {
            // slices the prefix from the start to the char
            prefix = prefix.substring(0, prefix.length - 1);
            if (prefix.length === 0) return "";
        }        
    return prefix;
};
// Time: O(n), where n is the sum of all the characters in all strins
// Space: O(1)
```