---
title: 010 Regular expression matching [Hard]
permalink: /leetcode/010_regular_expression_matching__Hard__/
---

## Description

Given an input string (s) and a pattern (p), implement regular expression matching with support for '.' and '\*' where:

`"."` Matches any single character.​​​​

`"\*"` Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

#### Example 1:

```
Input: s = "aa", p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

#### Example 2:

```
Input: s = "aa", p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

#### Example 3:

```
Input: s = "ab", p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

#### Example 4:

```
Input: s = "aab", p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore, it matches "aab".
```

#### Example 5:

```
Input: s = "mississippi", p = "mis*is*p*."
Output: false
```

#### Constraints:

```
0 <= s.length <= 20
0 <= p.length <= 30
s contains only lowercase English letters.
p contains only lowercase English letters, '.', and '*'.
It is guaranteed for each appearance of the character '*', there will be a previous valid character to match.
```

## How to proceed

This problem is not really a big one, Javascript has a constructor to create an object who will be able to test a string with a regexp.

Firstly, we will create an object `RegExp` using the constructor and pass the var `p` as parameter between the characters `^` and `$` which respectively define the beginning and the end of a string.

```javascript
const re = new RegExp(`^${p}$`);
```

Then we will test the var `s` with the regexp newly created using the function `test` who will return `true` or `false` if the string match the regexp.

## Final Result

```javascript
const isMatch => (s, p) {
  const re = new RegExp(`^${p}$`);
  return re.test(s);
};
```

## For further information

- [Info about RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
