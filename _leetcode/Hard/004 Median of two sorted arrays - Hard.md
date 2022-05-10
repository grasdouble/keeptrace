---
title: 004 Median of two sorted arrays
permalink: /leetcode/004_Median_of_two_sorted_arrays__Hard__/
---

## Description

Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

Follow up: The overall run time complexity should be O(log (m+n)).

#### Example 1:

```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

#### Example 2:

```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

#### Example 3:

```
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

#### Example 4:

```
Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

#### Example 5:

```
Input: nums1 = [2], nums2 = []
Output: 2.00000
```

#### Constraints:

```
nums1.length == m
nums2.length == n
0 <= m <= 1000
0 <= n <= 1000
1 <= m + n <= 2000
-106 <= nums1[i], nums2[i] <= 106
```

## How to proceed

### Manage arrays with only one value after concatenation

The first simple case to manage is when you have one array with one element and nothing in the other.

In this case, you just have to return the first element in the array after concatenation.

```javascript
const arr = nums1.concat(nums2).sort((a, b) => a - b);
if (arr.length == 1) return arr[0];
```

### Find the median value

Continuing to use the array created previously, the second step will be to find the median value.

For that, we will use the function `Math.floor` with as parameter the length of the array divide by 2 who will give us the most important integer.

This step will give us `mid` who will be use later to navigate in the array.

```javascript
const mid = Math.floor(arr.length / 2);
```

Next, we will check if there is a remainder left with the division of the length of the array by 2.

> If it's `0`, we will return the element in the table using `mid` as index.

> If it's something else, we'll add the values ​​in the array corresponding to the index `mid-1` and `mid`, and divide that by `2`.

Then we will return the value.

```javascript
return arr.length % 2 !== 0 ? arr[mid] : (arr[mid - 1] + arr[mid]) / 2;
```

## Final Result

```javascript
const findMedianSortedArrays => (nums1, nums2) {
  const arr = nums1.concat(nums2).sort((a, b) => a - b);
  if (arr.length == 1) return arr[0];

  const mid = Math.floor(arr.length / 2);
  return arr.length % 2 !== 0 ? arr[mid] : (arr[mid - 1] + arr[mid]) / 2;
};
```

## For further information

- [Info about Math.floor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
