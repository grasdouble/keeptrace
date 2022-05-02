---
layout: default
title: 001 Two Sum [Easy]
parent: Leetcode
nav_order: 1
---

# Scenario

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Examples

### Example 1

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

### Example 2:

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

### Example 3:

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

## Constraints

```
2 <= nums.length <= 103
-109 <= nums[i] <= 109
-109 <= target <= 109

Only one valid answer exists.
```

# How to proceed

## Define variables

To manage values available in the first parameter (nums), we will use two variable.

```javascript
const comp = {};
let result = [];
```

- `comp` will be an object where we will add a pair of attribute/value for each items in the table until we find the result.

  - The attribute will be defined with the target minus a value in the table.
  - The value will be set with the index of the value in the table.

- `result` will be an array with the index of the two items where the addition of both is equal to the target.

## Iterate on the table `nums`

For each entry in the table we will get the index with `idx` and the value with `elm`.

```javascript
for (const [idx, elm] of nums.entries()) {
```

For each iteration, we will test if `comp` contain a attribute for the current element in the array.

```javascript
if (comp[elm] >= 0) {
```

### If NO

We will add a new attribute in the object.

```javascript
comp[target - elm] = idx;
```

The attribute will be defined with the target minus a value in the table. Like that, if later an element in the table match the attribute we will have the idx for the two elements who match the target if we do the addition of them.

### If YES

We will have at this moment the idx of the two value who match the target if we add them.

```javascript
result = [comp[elm], idx];
break;
```

the first one will be on `comp[elm]` and the second one will be the current value of `idx`.

Then we can stop iterating

# Final Result

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
const twoSum = function (nums, target) {
  const comp = {};
  let result = [];
  for (const [idx, elm] of nums.entries()) {
    if (comp[elm] >= 0) {
      result = [comp[elm], idx];
      break;
    }
    comp[target - elm] = idx;
  }
  return result;
};
```
