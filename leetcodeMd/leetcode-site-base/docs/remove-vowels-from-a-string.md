---
id: remove-vowels-from-a-string
title: Remove Vowels from a String
sidebar_label: Remove Vowels from a String
---
## Description
<div class="description">
<p>Given a string <code>s</code>, remove the vowels <code>&#39;a&#39;</code>, <code>&#39;e&#39;</code>, <code>&#39;i&#39;</code>, <code>&#39;o&#39;</code>, and <code>&#39;u&#39;</code> from it, and return the new string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcodeisacommunityforcoders&quot;
<strong>Output:</strong> &quot;ltcdscmmntyfrcdrs&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aeiou&quot;
<strong>Output:</strong> &quot;&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var removeVowels = function(s) {
    let array = s.split('');
    for (let letter = 0; letter < array.length; letter++) {
        if(array[letter] === "a") {
           array[letter] = ""
        } else if (array[letter] == 'e') {
            array[letter] = ""
        } else if (array[letter] == 'i') {
            array[letter] = ""
        } else if (array[letter] == 'i') {
            array[letter] = ""
        } else if (array[letter] == 'o') {
            array[letter] = ""
        } else if (array[letter] == 'u') {
            array[letter] = ""
        }
    }
    return array.join("");
};
```