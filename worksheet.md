# A3 Worksheet: Design Document for the Linked List

**Name: Kien Le**
**Onyen: kientrle**

Six sections, 15 points. Fill this in **before** you write any code. It is a design document, so it says what your methods must do and what must stay true, not how you will write them. Everything you need is in `README.md`. Keep it short: the whole document should fit on about one page. Write your answers directly under each prompt.

---

## 1. The problem in your own words (2 points)

In two or three sentences, describe the problem this assignment asks you to solve. Say what the six new methods let a program do with a list of whole numbers, and whether they build new lists or change the ones they are given.

```
This assignment asks me to implement 6 specific methods for linked lists. These methods can merge two lists, remove an
element at a specific index, check for equality, remove nodes with duplicate values, reverse a list and intertwine two
lists. These methods all change the one they were given without building new lists.
```

---

## 2. Operations (3 points)

For each method you will write, describe in a few words what it is responsible for. Then say which of the list's **first node**, **last node**, and **size** the method can change, and in what situation. If it can change none of them, write "none". For the two merge methods, also say what state `list2` is left in.

| Method | What it is responsible for                                                                        | Which of first node / last node / size it can change, and when                                        |
|---|---------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| `simpleMerge` | Merge two lists together by connecting the head of one to the tail of the other                   | First node changes to the head of list 2 and size increases, assuming list 2 is non-empty             |
| `removeAtIndex` | Remove a node at a given index                                                                    | The first/ last node might change if the node to be removed is the head/ tail. Size decreases by 1.   |
| `isEqual` | Check if two lists have the same length and each node contains the same value                     | No modification is made. First node, last node and size all do not change.                            |
| `removeRepeats` | Check for nodes with the same values, remove duplicates, and retain only one node with that value | Last node might change if duplicates occur in the last nodes. Size decreases if duplicates are found. |
| `reverse` | Invert the connection between every two node                                                      | Last node becomes first. First node becomes last. Size does not change.                               |
| `merge` | Interleave list 2's nodes into this list, starting with list 2's head                             | The head changes when list2 is nonempty. Size increases by list2’s size when list2 is nonempty.       |

---

## 3. Data structure and justification (2 points)

This assignment uses a singly linked list that keeps a reference to both its first node and its last node. In one sentence, justify a linked list over an array-backed list (like the dynamic array from L11) for the work in Tasks 1 and 6. In a second sentence, explain what keeping a reference to the **last** node gives the class, and name one method, either provided or one of yours, that would have to do more work without it.

```
A linked list is more efficient than array-backed lists when it comes to memory use, using just enough memory to hold every node. Keeping a reference to the last node lets the class access or append at the end in constant time; for example, addLast would need to traverse the list without it.
```

---

## 4. Class invariant (3 points)

State the invariant the `LinkedList` class must maintain: what is always true about `_head`, `_tail`, and `_size` whenever no method is in the middle of running. Your answer should cover an empty list and a non-empty list, and it should say how `_size` relates to the nodes actually in the list.

```
When no method is running, _size is equal to all nodes in the list. If _size == 0 (empty linked list), both _head and _tail are null. If _size > 0 (non-empty linked list), both are non-null. _tail must always have null as its next node.
```

---

## 5. Three edge cases (3 points)

List three edge cases where a first attempt at one of your methods is likely to go wrong. Use at least two different methods, and don't reuse the main examples from the README. For each one, give the exact input (the list, plus `list2` or the index where one applies) and the correct result, including anything that must change about the first node, the last node, or the size.

| Method | Input                  | Correct result                                                                                          |
|---|------------------------|---------------------------------------------------------------------------------------------------------|
| removeAtIndex(0) | [5]                    | The list becomes empty: _head = null, _tail = null, _size = 0.                                          |
| removeRepeats() | [1,2,2]                | The list becomes [1, 2]; _head stays at the first 1, _tail becomes the remaining 2, and _size becomes 2 |
| merge() | [1,2,3] and list2 = [] | The list stays the same. _head, _tail, _size stay the same.                                             |

---

## 6. Test strategy (2 points)

In two or three sentences, describe how you will check each method before you submit to the autograder. Say what you will look at after each call besides the printed contents of the list, and where your edge cases from section 5 come in.

```
I will test each method on normal inputs and edge cases in section 5, checking _head, _tail, and _size as well as the printed elements afterwards. I will also verify that removed or merged lists have the expected _size, _head and _tail, and that empty and single-node cases preserve the class invariant.
```

---

## Submitting

Turn this in with your answers as a `.md` file on Gradescope. The code goes to Gradescope separately; see `README.md`.
