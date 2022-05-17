---
id: generate-parentheses
title: Generate Parentheses
sidebar_label: Generate Parentheses
---
## Description
<div class="description">
<p>Given <code>n</code> pairs of parentheses, write a function to <em>generate all combinations of well-formed parentheses</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> ["((()))","(()())","(())()","()(())","()()()"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> ["()"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    const output = [];
    const dfs = (str, open, close) => {
    // Close parentheses can not be more than open parentheses at any 
    // given time to stay valid.
    if (open > close) {
      return;
    }
    // Base case. We now have n pairs of parentheses
    if (open === 0 && close === 0) {
      output.push(str);
      return;
    }
    // Insert open parenthsis and search for the next valid insertion.
    if (open > 0) {
      dfs(`${str}(`, open - 1, close);
    }
    // Insert close parenthsis and search for the next valid insertion.
    if (close > 0) {
      dfs(`${str})`, open, close - 1);
    }
  };
  dfs('', n, n);
  return output;
};
```