
# Two Pointers Technique Guide

In this guide, we will focus on the two pointers technique, which involves using two pointers to keep track of indices, simplify logic, and save time and space.

We will talk about five variations of two pointers. For each type, we will learn about it through two steps:

1. Describing the concept using an algorithm template and flow chart
2. Providing typical examples to help you understand application scenarios and how to use it

---
## Two Pointers

The pointer is a very important concept in C/C++, as well as in algorithms. Applied to an algorithm, the pointer can be used to represent the current element in a sequence (such as an array or string). We can combine two pointers in different traversal ways to express complex algorithm logic.

The two pointers technique is widely used in many algorithm scenarios. According to the mechanism and usage, I have roughly classified them into five categories:

1. **Old and new state:** old, new = new, cur_result
2. **Slow and fast runner:** slow-> fast->->
3. **Left and right boundary:** |left-> ... <-right|
4. **Pointer-1 and pointer-2 from two sequences:** p1-> p2->
5. **Start and end of sliding window:** |start-> ... end->|

The above list and the following overview diagram show the core idea of each type in a brief, not rigorous way, just to give you an overview.

In the following sections, we will further discuss each type with a code template, diagram, and examples in detail.

---
## Slow and Fast Runner

### Template

The first idea is to use two pointers as slow runner and fast runner. Each of them flags a key point during traversal. In general, fast runner grows each iteration and slow runner grows with some restrictions. By that, we can process logic based on these two runners.

```python
# slow & fast runner: slow-> fast->->
def slow_fast_runner(self, seq):
    # initialize slow runner
    slow = seq[0]   # for index: slow = 0
    # fast-runner grows each iteration generally
    for fast in range(seq):     # for index: range(len(seq))
        #slow-runner grows with some restrictions
        if self.slow_condition(slow):
            slow = slow.next    # for index: slow += 1
        # process logic before or after pointers movement
        self.process_logic(slow, fast)
```
It should be noted that this template is only for the most common process, and it should be reformed for a more complex scenario, such as the fastrunner also growing with some restrictions. It is most important to understand the idea of the algorithm. In this way, we can draw inferences and expand to a more complex algorithm scenario.

---
#### Examples

A classic example is to remove duplicates from a sorted array. We can use the fast runner to represent the current element and use the slow runner to flag the end of the new, non-duplicate array.

`Given a sorted array nums, remove the duplicates in place such that each element appear only once and return the new length`

```c++
int removeDuplicates(vector<int>& nums) {
        int slow = 0, fast = 0;
        for(; fast < nums.size(); fast++) {
            if(nums[slow] != nums[fast]) {
                slow++;
                nums[slow] = nums[fast];
            }
        }
        return slow + 1;
    }
```
---
Let's take another example. Unlike the normal process, the fast runner moves a distance before the slow runner.

`Given a linked list, remove the n-th node from the end of the list and return its head.`

```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        if(head->next == nullptr)     
            return NULL;
        
        ListNode *fast = head, *slow = head;
        
        for(int i = 0; i < n; i++) fast = fast->next;
        
        if(fast == nullptr) return head->next;

        while(fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next;
        }
        
        slow->next = slow->next->next;
        
        return head;
    }
```
---
## Old and New State

### Template

Another idea is to use two pointers as variables. In the whole algorithm process, variables store intermediate states and participate in the calculation to generate new states.

```python
# old & new state: old, new = new, cur_result
def old_new_state(self, seq):
    # initialize state
    old, new = default_val1, default_val2
    for element in seq:
        # process current element with old state
        old, new = new, self.process_logic(element, old)
```
---
#### Examples

`A simple and classic example is calculating a Fibonacci number.`

Each number is the sum of the two preceding ones, starting from 0 and 1.

```cpp
int fib(int n) {
        int a = 0, b = 1, c = 0;
        for(int i = 2; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return c;
    }
```

---

An example with the current element involved:

`Determine the maximum amount of money you can steal tonight without robbing adjacent houses.`

```cpp
    int rob(vector<int> &v) {
        int temp = 0, last = 0, now = 0;
        for(int i : v) {
            temp = now; //sotring the prev val of now
            now = max(l + i, now); // finding the max val upto this home
            last = temp;
        }
        return now;
    }
```
j