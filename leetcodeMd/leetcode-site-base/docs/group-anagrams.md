---
id: group-anagrams
title: Group Anagrams
sidebar_label: Group Anagrams
---
## Description
<div class="description">
<p>Given an array of strings <code>strs</code>, group <strong>the anagrams</strong> together. You can return the answer in <strong>any order</strong>.</p>

<p>An <strong>Anagram</strong> is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> strs = ["eat","tea","tan","ate","nat","bat"]
<strong>Output:</strong> [["bat"],["nat","tan"],["ate","eat","tea"]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> strs = [""]
<strong>Output:</strong> [[""]]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> strs = ["a"]
<strong>Output:</strong> [["a"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 100</code></li>
	<li><code>strs[i]</code> consists of lowercase English letters.</li>
</ul>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
    // does not work on all cases
    // let anagrams = {};
    // for (let i = 0; i < strs.length; i++){
    //     let sorted = strs[i].split("").sort().join("");
    //     if(anagrams[sorted]) {
    //         anagrams[sorted] += "," + [strs[i]] 
    //     } else {
    //         anagrams[sorted] = strs[i]
    //     }
    // }
    // let res = [];
    // for (key in anagrams) {
    //     let value = anagrams[key].split(",")
    //     res.push(value)
    // }
    // return res;
    let obj = {};
    for (let str of strs) {
        let letters = str.split("").sort().join("");
        obj[letters] ? obj[letters].push(str) : obj[letters] = [str];
    }
    return Object.values(obj);
};
```