---
id: longest-repeating-character-replacement
title: Longest Repeating Character Replacement
sidebar_label: Longest Repeating Character Replacement
---
## Description
<div class="description">
<p>You are given a string <code>s</code> and an integer <code>k</code>. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most <code>k</code> times.</p>

<p>Return <em>the length of the longest substring containing the same letter you can get after performing the above operations</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ABAB&quot;, k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Replace the two &#39;A&#39;s with two &#39;B&#39;s or vice versa.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;AABABBA&quot;, k = 1
<strong>Output:</strong> 4
<strong>Explanation:</strong> Replace the one &#39;A&#39; in the middle with &#39;B&#39; and form &quot;AABBBBA&quot;.
The substring &quot;BBBB&quot; has the longest repeating letters, which is 4.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of only uppercase English letters.</li>
	<li><code>0 &lt;= k &lt;= s.length</code></li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string} s
 * @param {number} k
 * @return {number}
 */
var characterReplacement = function(s, k) {
    // if empty string
    if (!s || s.length === 0) return 0;
    // Track letters
    let map = {};
    let max = 0;
    let currentCountMax = 0;
    let left = 0;
    let currentLetter;
    for (let i = 0; i < s.length; i++) {
        currentLetter = s[i];
        // Count the occurence of the current letter (in the present window)
        // Track num of char occurances
        map[currentLetter] ? map[currentLetter]++ : map[currentLetter] = 1;
        // Update cur_count_max (in the present window)
        if(map[currentLetter] > currentCountMax) currentCountMax = map[currentLetter];
        // Sliding window: Check if the window we are checking is valid or not
        // In case the size of window is bigger than cur_count_max plus max change(k)
        // decrease the count of the leftmost letter and then slide left (left++)
        if (i - left + 1 > currentCountMax + k) {
            map[s[left]] -= 1;
            left++
        } else {
            max = Math.max(max, i - left + 1)
        }
    }
    return max;
};
```