---
layout: default
title: 007 Reverse Integer [Easy]
parent: Easy
nav_order: 7
---

# 007 Reverse Integer [Easy]

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

### Examples

#### Example 1:

```
Input: x = 123
Output: 321
```

#### Example 2:

```
Input: x = -123
Output: -321
```

#### Example 3:

```
Input: x = 120
Output: 21
```

#### Example 4:

```
Input: x = 0
Output: 0
```

### Constraints

```
-231 <= x <= 231 - 1
```

## How to proceed

### Check the parameter

We need to know if the parameter is or isn't a negative value.

```javascript
const isNegative = x < 0;
```

### Transform the parameter

The first thing to do is to transform the parameter to an absolute value

```javascript
Math.abs(x);
```

Then, we will transform the absolute value to a string and apply three transformation:

- Split the string to have an array
- Reverse the table (to respect the goal of the requirement)
- Join the table to have back a string

To finish, we will prefix the code with a `+` to transform the string to an integer.

All this transformation will be assigned to `result`.

```javascript
const result = +String(Math.abs(x)).split("").reverse().join("");
```

### Test if the result is a 32-bit signed integer

As we have as constrain to have only a 32-bit signed integer as result, we need to check if it's the case.
To facilitate the test, we will use the hexadecimal value `0x7fffffff`.
If `result` is greater than `0x7fffffff` we will directly return `0`.

```javascript
if (result > 0x7fffffff) return 0;
```

### Test negative value

before to return `result` we need to check the value of `isNegative`.
If yes, we will have to prefix `result` with a minus to return a negative value.
If no, we will return `result` as it is.

## Final Result

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function (x) {
  const isNegative = x < 0;
  const result = +String(Math.abs(x)).split("").reverse().join("");
  // 0x7FFFFFFF maximum value for a signed 32-bit integer
  if (result > 0x7fffffff) return 0;
  return isNegative ? -result : result;
};
```
