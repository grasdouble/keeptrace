---
layout: default
title: 002 Add Two Numbers [Medium]
parent: Medium
nav_order: 2
---

# Scenario

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Examples

### Example 1:

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

### Example 2:

```
Input: l1 = [0], l2 = [0]
Output: [0]
```

### Example 3:

```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

## Constraints

```
The number of nodes in each linked list is in the range [1, 100].
0 <= Node.val <= 9
It is guaranteed that the list represents a number that does not have leading zeros.
*/
```

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
```

# How to proceed

## Create a function to transform ListNode to String

we will create a method who will take as parameter a ListNode (`node`) and a string (`arr`).

Example:

this ListNode

```javascript
{
  val: 1,
  next: {
    val: 2,
    next: {
      val:3
    }
  }
}
```

after transformation will become

```
321
```

First of all, we will check if the ListNode has a next value.

### If YES

we will do another call to the same function with as parameter `node.next` and `arr`.
Next to the call, we will assign the result to `arr` concat it with the `node.val`.

### If NO

if `node.val` is greater than `0` we will concat `arr` with `node.val`.

As result we will have retrieve the content of the ListNode as a String.

```javascript
const transformNode = (node, arr) => {
  if (node.next) {
    arr = transformNode(node.next, arr);
    arr = arr.concat(node.val);
  } else if (node.val > 0) {
    arr = arr.concat(node.val);
  }
  return arr;
};
```

## Create a function to transform String to node

As requested, at the end we need to return a ListNode.
We will do a function to transfom a String to ListNode and for that we will supposed that char (`value`) will be send as first parameter and a ListNode (`next`) as second paramter.

First step will be to create a new ListNode with as value the first parameter

```javascript
const node = new ListNode(value);
```

Next, we will set the next value in the new ListNode with the second parameter

```javascript
node.next = next;
```

Then, we will return the ListNode.

```javascript
const transformToNode = (value, next) => {
  const node = new ListNode(value);
  node.next = next;
  return node;
};
```

## Transform, Calculate and Transform a second time

Now we have all the functions needed to proceed.

First action will be to transform the two ListNode (`l1` and `l2`) passed as parameter as String and right after to BigInt.

For that we will call the first function created before: `transformNode`

```javascript
const l1Value = BigInt(transformNode(l1, "") || 0);
const l2Value = BigInt(transformNode(l2, "") || 0);
```

Next, we will do the calculation and convert it as String

```javascript
const calcResult = BigInt(l1Value + l2Value).toString();
```

Then, we will transform the result to a ListNode to return it at the end.

For that, we will convert the String as an Array and iterate on it.

For each element in the Array, we will call the second function created before: `transformToNode`

And finish by returning the result

```javascript
let finalResult = null;
calcResult.split("").forEach((elm) => {
  finalResult = transformToNode(elm, finalResult);
});
return finalResult;
```

# Final Result

```javascript
const transformNode = (node, arr) => {
  if (node.next) {
    arr = transformNode(node.next, arr);
    arr = arr.concat(node.val);
  } else if (node.val > 0) {
    arr = arr.concat(node.val);
  }
  return arr;
};

const transformToNode = (value, next) => {
  const node = new ListNode(value);
  node.next = next;
  return node;
};

/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
const addTwoNumbers = function (l1, l2) {
  const l1Value = BigInt(transformNode(l1, "") || 0);
  const l2Value = BigInt(transformNode(l2, "") || 0);
  const calcResult = BigInt(l1Value + l2Value).toString();
  let finalResult = null;
  calcResult.split("").forEach((elm) => {
    finalResult = transformToNode(elm, finalResult);
  });
  return finalResult;
};
```
