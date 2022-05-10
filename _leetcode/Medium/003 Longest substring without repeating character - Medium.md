---
title: 003 Longest substring without repeating character
permalink: /leetcode/003_longest_substring_without_repeating_character__Medium__/
---

## Description

Given a string s, find the length of the longest substring without repeating characters.

#### Example 1:

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

#### Example 2:

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

#### Example 3:

```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

#### Example 4:

```
Input: s = ""
Output: 0
```

#### Constraints:

```
0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.
```

## How to proceed

### Define a list of variables to help on the calculation and start to iterate

First, we will create a list of variable who will help us to analyse the content of `s`.

```javascript
const arr = s.split("");
const store = {};
let result = 0;
let firstIndex = 0;
```

- `arr` will contain the content of `s` transformed into an array.

- `store` will be an object who will contain all potential values and their index in `arr` to be able to calculate the result at the end.

- `result` will be use to manage the value to return.

- `firstIndex` will contain the start index to calculate the number of non-repeating characters

After that we will start to iterate in each value of `arr`.

```javascript
arr.forEach((elm, idx) => {
```

#### Identify if the current character is in the store

First, we will check if the character is already in the store.

If yes, we will update `firstIndex` checking which value is the bigger between the index available in the store (with `store[elm]`) and the current value of `firstIndex`.

```javascript
if (store[elm]) {
  firstIndex = Math.max(store[elm], firstIndex);
}
```

#### Update the `store` and the `result`

Now, we will update `store` and the `result` with the current information we have.

`store` will have a new attribute with the current value of `elm` and set it with the current value of `idx` + 1.

> we need to do `idx + 1` to not stay blocked later in the code during comparison it with result, e.g. `Math.max(0, 0 - 0)` (we will see this part more in details later).

```javascript
store[elm] = idx + 1;
```

`result`will be updated checking the biggest value between it current one and the substraction between `store[elm]` and `firstIndex` using `Math.max`.

> the result of `store[elm] - firstIndex` is the number of char between those two index).

```javascript
result = Math.max(result, store[elm] - firstIndex);
```

#### Last but not least

After the all those instructions, we can close the call to `forEach` and return the value of `result`.

```javascript
return result;
```

## Final Result

```javascript
const lengthOfLongestSubstring = (s) => {
  const arr = s.split("");
  const store = {};
  let result = 0;
  let firstIndex = 0;

  arr.forEach((elm, idx) => {
    if (store[elm]) {
      firstIndex = Math.max(store[elm], firstIndex);
    }
    store[elm] = idx + 1;
    result = Math.max(result, store[elm] - firstIndex);
  });
  return result;
};
```

## For further information

- [Info about Array.forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [Info about Math.max](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max)
