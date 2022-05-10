---
title: 042 Trapping rain water
permalink: /leetcode/042_trapping_rain_water__Hard__/
---

## Description

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

#### Example 1:

![rainwater example](/keeptrace/assets/img/leetcode/042_trapping_rain_water__hard.png "a title")

```
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
```

#### Example 2:

```
Input: height = [4,2,0,3,2,5]
Output: 9
```

#### Constraints:

```
n == height.length
0 <= n <= 3 * 10^4
0 <= height[i] <= 10^5
```

## How to proceed

### Define a list of variables to help on the calculation

First, we will create two variables to identify the max level of elevation on left and right with `leftMax` and `rightMax`.
They will help to identify which level of water we can have following this two info.

```javascript
let leftMax = 0;
let rightMax = 0;
```

Next, we will create two variables to manage the current position of our cursor on `left` and `right`.
`left` will take as value the first index of height.
`right` will take as value the last index of height.

```javascript
let left = 0;
let right = height.length - 1;
```

Then, a variable to manage the `result`.

```javascript
let result = 0;
```

### Navigate in height to collect water info

To navigate in height we will use a will and iterate on it `while` the index in `right` is greater than the one in `left`.

```javascript
while (left < right) {
```

Next, we will check if the value in height with as index `left` is less than the one using `right`.

```javascript
if (height[left] < height[right]) {
```

#### If yes (the value in height with as index `left` is less than the one using `right`)

First, we will check if the value for `height[left]` is greater than or equal to `leftMax`.

```javascript
if (height[left] >= leftMax) {
```

If it's the case, we will define the value of `leftMax` with `height[left]`.

```javascript
leftMax = height[left];
```

If not, we will add to the value of `result` doing the subtraction of `leftMax` and height[left].

```javascript
result += leftMax - height[left];
```

Then, we will increment left by one.

```javascript
left++;
```

#### If not (height value with index `left` is greater than or equal to that using `right`)

We will do the same things as we did for `left` but for `right` info.

(the only thing do change is the last step. We will decrement `right` by one)

```javascript
} else {
  if (height[right] >= rightMax) {
    rightMax = height[right];
  } else {
    result += rightMax - height[right];
  }
  right--;
}
```

### You should have the amount of water in `result`

At the end of the script, result should contain the amount of water and we can return it.

```javascript
return result;
```

## Final Result

```javascript
const trap = (height) => {
  let leftMax = 0;
  let rightMax = 0;
  let left = 0;
  let right = height.length - 1;
  let result = 0;

  while (left < right) {
    if (height[left] < height[right]) {
      if (height[left] >= leftMax) {
        leftMax = height[left];
      } else {
        result += leftMax - height[left];
      }
      left++;
    } else {
      if (height[right] >= rightMax) {
        rightMax = height[right];
      } else {
        result += rightMax - height[right];
      }
      right--;
    }
  }
  return result;
};
```

## For further information

- [Info about While](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)
