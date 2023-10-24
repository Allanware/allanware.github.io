---
title: "My Leetcode Journey"
date: 2023-10-22T11:42:45-05:00
author: Wenxuan Zhao
tags: ['']
mathjax: true
summary: This post documents my journey wading through leetcode. 
cover:
    image: 
    alt: 
    relative: true
---

# [1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)

## Approach 1: Double pointers

i, j points to word1 and word2. A while loop that does the traversing and  appending. To traverse two lists throughly, we check for `i < len(words1)` **or** `j < len(words2)`. 

Inside while loop, result list appends words1[i] if i < len(words1) and words2[j] if j < len(words2). 

Note: in Python, strings are immutable, we used the list `result` to append letters and later joined the list with an empty string to return it as a string object. The `join` operation takes linear time equal to the length of `results` to merge `results` with empty string.

### Time

$O(m+n)$: m is the length of word1, n is the length of word2.

### Space 

$O(n)$: we use a temp list `result` to store the final string.  

## Approach 2: One pointer

To traverse two lists throughly, we could also check for `i < max(len(word1), len(word2))`. 

Inside while/for loop, result list appends words1[i] `if i < len(words1)` and words2[j] `if j < len(words2)`. 

# [1071. Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/)

## Approach 1: Analgous to math GCD

Denote len(str1) = m, len(str1) = n.

if m > n, gcdString = gcd(str1 - str2, str2), and vice versa. str1 - str2 means deleting str2 from the start of str1. If there is any mismatch, then there is no gcd string (return "" as gcdString).

Base case: if str1 == "", return str2; vice versa

### Time

We need to scan the longest string of str1 and str2 once: $O(max(m+n))$

### Space

$O(1)$ if we can modify string in place. 

# [605. Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)

## Approach

Greedy algorithm + padding the front and the end of the array. If a spot is plantable, then +2 to find the next via spot. 

If the array is not allowed to change, we could create a new array with paddings, or we could handle the front and end very carefully.

We could return True early if n is already 0 (assuming each time we find a spot we decrement n by 1).

### Time

We need to scan the array once: $O(n)$.

### Space

$O(1)$

# [345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

## Approach

1. Python string is immutable. First convert input string to a list to enable in-place swap. After that, use `"".join(stringList)` to convert the list back to string.
2. Use a dictionary to store the vowels. 
3. Use double pointers, one pointing at the front, and another pointing at the back. Use a while loop to make sure they do not cross. 
4. Inside the while loop: use two while loops for i and j to find vowels, and make sure they do not touch. If they haven't touched after the two while loops, then they must find a pair of vowels => we do the swap.

### Time

We need to scan the string once: $O(n)$.

### Space

$O(n)$

# [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

## Approach

1. Similar to the above problem. Use `.split()` split a string into a list of words. The default delimiter to `split`  is any number of white spaces. 
2. Use double pointers to swap. 

### Time
$O(n)$ 

### Space
$O(n)$

# [1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)

## Approach

To solve it and not use recursion, which is of exponential complexity, we use a dynamic programming technique: 

- use an array of size n+1 to store the partial results along computing $T_n$
- initialize $T_0, T_1, T_2$
- use for loop to compute $T_n$

### Time:

$O(n)$

### Space

$O(n)$

# [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

## Approach 

For each number in the array, to get the product of everything besides it, we can divide the problem into two halves: multiply the numbers on the left and store the result, then multiply the numbers on the right. 

The key point is to store the partial result in an variable, and update the slots in the output array with the corresponding partial result. 

### Time:

$O(n)$

### Space

$O(1)$

# [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

## Approach 1

This problem is under the section *Two Pointers*. I approach this problem by setting the one pointer to keep track of the first 0 on the left (the first swap position), and the other pointer to the next non-zero number (use a while loop). 

## Approach 2: Fast and Slow pointer

The fast pointer iterates faster than the slower one. But they should end at about the same time. So I use a for loop to iterates the fast pointer over the whole array, and only updates the slow pointer if it points to a non-zero. Like the previous approach, essentially the fast will keep track of the non-zero, the slow keeps track of the first zero. But the structure of a for loop to update the fast, and inside the loop an if to conditionally update slow is much cleaner than approach 1. 

### Time:

$O(n)$

### Space

$O(1)$

# [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)

## Approach: fast and slow pointer

To check if s is a substring of t, the fast pointer iterates over t, and the slow pointer iterates over s. If the iterator of s points to beyond the end of s, then we know s is a substring of t. We also use a similair structure to the above problem: a for loop for t; inside for loop, use a if to iterate s if we find a characet match. 

### Time:

$O(n)$

### Space

$O(1)$

# [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)

## Approach: Sliding window

If we were to average every window, the complexity is $O(k*n)$. To make it linearly dependent on n, we observe that for each window, we only need to keep track of the changes between each window: subtract the left, add the right. My first thought was if we can find an i such that `nums[i] < nums[i+k]`, then we update `maxI` to this new `i`. However, this only work locally, namely, if we compare two contiguous windows. It doesn't word between two non-neighbors since they do not share the middle two elements. Thus, we also need to track the `sum` and `maxSum`.

### Time:

$O(n)$

### Space

$O(1)$

# [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)

## Approach: Sliding window

Use `leftSum` and `rightSum` to store the sum of left and right elements of the potential pivot. If `leftSum == rightSum`, we find the pivot.

We use the sliding window approach to update `leftSum` and `rightSum`. Init `leftSum` to 0 and `rightSum` to `sum(nums)-nums[0]` for `i=0` . 

### Time:

$O(n)$

### Space

$O(1)$

# [2215. Find the Difference of Two Arrays](https://leetcode.com/problems/find-the-difference-of-two-arrays/)

## Approach: set difference

`answer[0] = set(nums1) - set(nums2)`

`answer[1] = set(nums2) - set(nums1)`

### Time:

$O(n)$

### Space

$O(n)$

# [1207. Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences/)

## Approach 

Create a dictionary; Loop through the array, and insert the element into the dictionary or increment the counter for the existing key; If the size of the dictionary (number of keys) is the same as the unique values of the counters of those keys, then we know each key (each unique element in array) has a unique number of appearances. 

### Time:

$O(n)$

### Space

$O(n)$

# [2390. Removing Stars From a String](https://leetcode.com/problems/removing-stars-from-a-string/)

## Approach 

To "Remove the closest **non-star** character to its **left**, as well as remove the star itself", we can use a stack to simulate this process: read the string from left to right (start to end), when we see a non star, we push it to the stack. When we see a star, we pop the last element we pushed (LIFO). 

In Python, we can use `deque` in `collections`, because it offers $O(1)$ insertion at both the right end  (`append`) and the left enb (`appendleft`) and $O(1)$ pop (`pop`) at the right and the left end (`popleft`). 

### Time:

$O(n)$

### Space

$O(1)$

# [735. Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)

## Approach

Use `deque` to simulate stack in python. Make sure the element to be pushed on top of the stack is compatible with elements inside the stack before pushing it. 

Invariants: 

1. If the stack is empty, push the next element in the array.
2. If the top element in the stack is negative, push the next element in array no matter it is negative or positive.
3. If the next element is positive, just push it. 
4. Else (top is positive, next element is negative): crush whatever can be crushed by the next element in the stack: a while loop 

### Time:

$O(n^2)$

### Space

$O(1)$

# [933. Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)

## Approach

t is in strictly increasing order. If some ping falls outside of the range, it must be in the start of the ping array. This behavior can be simulated using queue (FIFO). 

In python, we can use `deque` to implement a queue: `append` to push, `popleft` to pop. 

### Time:

$O(n)$

### Space

$O(1)$

# [2095. Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

## Approach

To fid the middle node, we could use the "fast" and "slow" double pointer method. Inside the while loop, by updating the "fast" pointer twice and the "slow" pointer once, we can locate the mid node at the "slow" pointer. 

To delete it, we can use another pointer to point to the prev of the "slow" pointer, and update `prev.next` to its `next.next`. 

### Time:

$O(n)$

### Space

$O(1)$

# [328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)

## Appraoch

The intuition is to maintain a double-pointer structure to this linked-list: the `oddNode` pointer that first points to the `head` and the `evenNode` pointer that first points to `head.next` . 

My first try was to update `oddNode.next = oddNode.next.next` in a while loop, which essentially gets the oddNode list ready. Then I update the evenNode list similarly. But this did not work, because `evenNode.next` is the updated oddNode not the original oddNode, and `evenNode.next.next` is not a evenNode. 

To account for that, we need to carefully update oddNode and evenNode *in turn*. Another thing is that we need to store the head.next in a special variable `evenListStart` so that the last oddNode knows where it should point to. The last evenNode should point to `None`. 

### Time:

$O(n)$

### Space

$O(1)$

# [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

## Approach 

We traverse the linked list and do this: 

1. Store `currentNode.next` to  `nextNode`. 
2. Set `currentNode.next` to `prevNode`
3. Update `prevNode` to `currentNode`
4. Update `currentNode` to `nextNode`
5. We need to handle the head and the end of the list a little differently:
   1. head of the list does not have `prevNode`: therefore in step 2, set it to `None`.
   2. End of the list does not have `nextNode` (equals `None`), if we know it is `None`, we know it is the end and we set it to be the new `head`.

### Time:

$O(n)$

### Space

$O(1)$

# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

## Background: Tree traversal 

Unlike linear data structures (Array, Linked List, Queues, Stacks, etc) which have only one logical way to traverse them, trees can be traversed in different ways. 

### Traversal using DFS

#### Inorder Traversal (left, root, right)

Inorder traversal gives nodes in non-decreasing order. 

##### Implementation: 

- Iterative: 
  - Keep appending left nodes to the stack until hitting None
  - Pop the stack to get the node and print it. Go to its right. Goes back to the above step. 
- Recursive: 
  - InorderTravese(root.left)
  - Print (root)
  - InorderTravese(root.right)

##### Time and Space

Time: $O(n)$

Space: $O(h)$, $h$ is the height of the tree. In the iterative case, $h = len(stack)$. In the recursive case: $h = len(functionStack)$

#### Preorder Traversal (root, left, right)

Preorder traversal is used to create a copy of the tree. 

##### Implementation: 

- Iterative: *The right child is pushed before the left child to make sure that the left subtree is processed first.*
  - Pop an item from the stack and print it. 
  - Push right child of a popped item to stack 
  - Push left child of a popped item to stack

- Recursive: 
  - Print (root)
  - PreorderTravese(root.left)
  - PreorderTravese(root.right)

##### Time and Space

The same as InorderTraverse. 

#### Postorder Traversal (left, right, root)

Postorder traversal is used to delete the tree.

### Level Order Traversal (BFS Traversal)

Traverse all the nodes of a lower level before moving to any of the nodes of a higher level.

##### Implementation

- Iterative: 
  - Visit the root and push all its children to the queue. 
  - Pop the queue and visit the popped node and push all its children to queue. Repeat until queue is empty. 

## Approach 

### Recursively

Using DFS. If the node is None, return 0. Otherwise, return `max(maxDepth(node.left), maxDepth(node.right)) + 1`

### Time:

$O(n)$

### Space

$O(h)$:  h = Max height of the tree.

# [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

## Approach

To do it in linear time, the intuition is to use dynamic programming: reuse the result in smaller `i`s (i from 1 to n) to compute big `i`s.  

One way to do this is to divide `i` by 2 by using `i>>1` and access `output[i>>1]` to get the number of 1s besides the last digit. If the last digit is 1, then we add 1 to the above number; otherwise, add 0. To check if the last digit is 1 or not, we can use `i&1`. 

### Time:

$O(n)$

### Space

$O(1)$

# [136. Single Number](https://leetcode.com/problems/single-number/)

Since besides the singled number the list contains numbers all in pair. To cancel themselves out, we can use xor (`^` in python). We can xor the whole list together and what remains is the single number. 

### Time:

$O(n)$

### Space

$O(1)$

# [1. Two Sum](https://leetcode.com/problems/two-sum/)

## Approach

I did not figure it out myself. The most obvious solution is to use a $O(n^2)$ brute-force method. I then try to reduce it to $O(n\log{n})$  by first sorting it, and then use binary search to search for each element's complement in the list. That is another $O(n\log{n})$. This doesn't work becasue the numbers could be negative and the target sum could be acheived by summing 

