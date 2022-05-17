---
id: decode-string
title: Decode String
sidebar_label: Decode String
---
## Description
<div class="description">
<p>Given an encoded string, return its decoded string.</p>

<p>The encoding rule is: <code>k[encoded_string]</code>, where the <code>encoded_string</code> inside the square brackets is being repeated exactly <code>k</code> times. Note that <code>k</code> is guaranteed to be a positive integer.</p>

<p>You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, <code>k</code>. For example, there will not be input like <code>3a</code> or <code>2[4]</code>.</p>

<p>The test cases are generated so that the length of the output will never exceed <code>10<sup>5</sup></code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;3[a]2[bc]&quot;
<strong>Output:</strong> &quot;aaabcbc&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;3[a2[c]]&quot;
<strong>Output:</strong> &quot;accaccacc&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;2[abc]3[cd]ef&quot;
<strong>Output:</strong> &quot;abcabccdcdcdef&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 30</code></li>
	<li><code>s</code> consists of lowercase English letters, digits, and square brackets <code>&#39;[]&#39;</code>.</li>
	<li><code>s</code> is guaranteed to be <strong>a valid</strong> input.</li>
	<li>All the integers in <code>s</code> are in the range <code>[1, 300]</code>.</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {
    if (!s) return '';
    var count = '';
    var string = '';
    for (let i = 0; i < s.length; i++) {
        // if letter, directily add to string
        if (/[a-z]/.test(s[i])) string += s[i];
        // if number
        else if (/[0-9]/.test(s[i])) count += s[i];
        // if open bracket
        else if (s[i] === '[') {
            i++;
            // keep track of openings
            var open = 1;
            var substring = '';
            while (i < s.length) {
                if (s[i] === ']') {
                    open--;
                    if (open === 0) break;
                }
                else if (s[i] === '[') open++;
                substring += s[i];
                i++;
            }
            count = parseInt(count);
            while (count > 0) {
                string += decodeString(substring);    
                count--;
            }
        }
    }
    return string;    
};
```