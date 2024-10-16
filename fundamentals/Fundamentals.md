# <p style="text-align:center;">Fundamentals </p>

---
#### Arrays

An array stores a sequence of values that are all of the same type. We want not only to store values but also to access each individual value. The method that we use to refer to individual values in an array is numbering and then indexing them. If we have N values, we think of them as being numbered from 0 to N-1. Then, we can unambiguously specify one of them in code by using the notation a[i] to refer to the i-th value for any value of i from 0 to N-1. This construct is known as a *one-dimensional* array

---
#### Recursion.
A method that calls itself until some condition (Base Condition) is met.

#### Properties of Recursion

- The recursion has a base case we always include a conditional statement as the ﬁrst statement in the program that has a return.

- Recursive calls must address subproblems that are smaller in some sense, so that recursive calls converge to the base case. In the code below, the difference between the values of the fourth and the third arguments always decreases.

- Recursive calls should not address subproblems that overlap. In the code below, the portions of the array referenced by the two subproblems are disjoint.

**Example**
```cpp
int ranker(vector<int> &arr, int key, int lo, int hi) {
    if(lo > hi) {
        return -1;
    }
    int mid = lo + (hi - lo) / 2;
    if(key < arr[mid]) {
        return ranker(arr, key, lo, mid - 1);
    } else if(key > arr[mid]){
        return ranker(arr, key, mid + 1, hi);
    } else {
        return arr[mid];
    }
    return -1;
}

int binarySearch(vector<int> &arr, int key) {
    return ranker(arr, key, 0, arr.size() - 1);
}
```
---
**Modular programming** Of critical importance in this model is that libraries of static methods enable modular programming where we build libraries of static methods (modules) and a static method in one library can call static methods deﬁned in other libraries. This approach has many important advantages. It allows us to

- Work with modules of reasonable size, even in program involving a large amount of code.
- Share and reuse code without having to reimplement it.
- Easily substitute improved implementations.
- Develop appropriate abstract models for addressing programming problems.
- Localize debugging (see the paragraph below on unit testing).

**Your own libraries** It is worthwhile to consider every program that you write as a library implementation, for possible reuse in the future.

- Write code for the client, a top-level implementation that breaks the computation up into manageable parts.
- Articulate an API for a library (or multiple APIs for multiple libraries) of static methods that can address each part.
- Develop an implementation of the API, with a main() that tests the methods independent of the client.

Not only does this approach provide you with valuable software that you can later reuse, but also taking advantage of modular programming in this way is a key to successfully addressing a complex programming task.

---
## <p style="text-align:center;">API</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The purpose of an API is to separate the client from the implementation: the client should know nothing about the implementation other than information given in the API, and the implementation should not take properties of any particular client into account. APIs enable us to separately develop code for various purposes, then reuse it widely. No Java library can contain all the methods that we might need for a given computation, so this ability is a crucial step in addressing complex programming applications. Accordingly, programmers normally think of the API as a contract between the client and the implementation that is a clear speciﬁcation of what each method is to do. Our goal when developing an implementation is to honor the terms of the contract. Often, there are many ways to do so, and separating client code from implementation code gives us the freedom to substitute new and improved implementations. In the study of algorithms, this ability is an important ingredient in our ability to understand the impact of algorithmic improvements that we develop.

---
#### String

A String is a sequence of characters (char values). A literal String is a sequence of characters within double quotes, such as "Hello, World". The data type String is a Java data type but it is not a primitive type. We consider String now because it is a fundamental data type that almost every Java program uses.