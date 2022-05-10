---
title: 023 Merge k sorted lists
permalink: /leetcode/023_merge_k_sorted_lists__Hard__/
---

## Description

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

#### Example 1:

```
Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
```

#### Example 2:

```
Input: lists = []
Output: []
```

#### Example 3:

```
Input: lists = [[]]
Output: []
```

#### Constraints:

```
k == lists.length
0 <= k <= 10^4
0 <= lists[i].length <= 500
-10^4 <= lists[i][j] <= 10^4
lists[i] is sorted in ascending order.
The sum of lists[i].length won't exceed 10^4.
```

```javascript
/**
 * Definition for singly-linked list.
 **/
function ListNode(val, next) {
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}
```

## How to proceed

The main idea with this problem is to regroup all ListNode in one.

### One to regroup and one for the result

We will start by create to variable `arr` and `result`.

The first one will be used to regroup all values in an array and the second one will be use to construct the ListNode to return.

```javascript
const arr = [];
let result = null;
```

### Iteration and navigation

Like the parameter is an array of ListNode, we will iterate on it and navigate on each ListNode to add all values in our array `arr`.

```javascript
lists.forEach((elm) => {
  let node = elm;
  while (node) {
    arr.push(node.val);
    node = node.next;
  }
});
```

As you can see, to navigate in each ListNode, we use a `while` and we use the value of node to know if we need to continue.

Like that, once the value of node.next is empty we will stop with the current value in the table and take the next one.

### Order and construct the result

Now we have an array with all values and before to create the result we need to order the content.

```javascript
arr.sort((a, b) => b - a);
```

And then, we can create a new ListNode in `result` and return it.

```javascript
arr.forEach((elm) => {
  result = new ListNode(elm, result);
});
return result;
```

## Final Result

```javascript
const mergeKLists = (lists) => {
  const arr = [];
  let result = null;
  lists.forEach((elm) => {
    let node = elm;
    while (node) {
      arr.push(node.val);
      node = node.next;
    }
  });
  arr.sort((a, b) => b - a);
  arr.forEach((elm) => {
    result = new ListNode(elm, result);
  });
  return result;
};
```

## For further information

- [Info about Array.forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [Info about While](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)
