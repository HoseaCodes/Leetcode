---
id: palindrome-partitioning-ii
title: Palindrome Partitioning II
sidebar_label: Palindrome Partitioning II
---
## Description
<div class="description">
<p>Given a string <code>s</code>, partition <code>s</code> such that every substring of the partition is a palindrome.</p>

<p>Return <em>the minimum cuts needed</em> for a palindrome partitioning of <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aab&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> The palindrome partitioning [&quot;aa&quot;,&quot;b&quot;] could be produced using 1 cut.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a&quot;
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ab&quot;
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> consists of lowercase English letters only.</li>
</ul>

</div>

## Solution(python3)
```python3
class Solution:
    def minCut(self, s: str) -> int:
        length = len(s)
        cuts = [i for i in range(length)]

        for i in range(length):
            # Odd size palindrome
            j = 0 # one-character palindrome when j == 0
            while i - j >= 0 and i + j < length and s[i - j] == s[i + j]:
                prev_cuts = cuts[i - j - 1] if i - j - 1 >= 0 else -1
                cuts[i + j] = min(cuts[i + j], prev_cuts + 1)
                j += 1

			# Even size palindrome
            j = 0
            while i - j >= 0 and i + j + 1 < length and s[i - j] == s[i + j + 1]:
                prev_cuts = cuts[i - j - 1] if i - j - 1 >= 0 else -1
                cuts[i + j + 1] = min(cuts[i + j + 1], prev_cuts + 1)
                j += 1

        return cuts[-1]
```