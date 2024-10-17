## <div style="text-align:center;"> Analysis of Algorithms </div>

#### **Scientific Method:**

The very same approach that scientists use to understand the natural world is effective for studying the running time of programs:
- **Observe** some feature of the natural world, generally with precise measurements.
- **Hypothesize** a model that is consistent with the observations.
- **Predict** events using the hypothesis.
- **Verify** the predictions by making further observations.
- **Validate** by repeating until the hypothesis and observations agree.

---

#### How to do it?
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For many programs, developing a mathematical model of running time reduces to the following steps:
- **Develop** an input model, including a deﬁnition of the problem size.
- **Identify** the inner loop.
- **Deﬁne** a cost model that includes operations in the inner loop.
- **Determine** the frequency of execution of those operations for the given input.

---
#### Reasons to Analyse an Algorithm

**Predict Performance**
**Compare Algorithms**
**Provide Guarantees**
**Understand Theoretical Basis**
**Primary Practical Reason:** avoid Performance bugs

```text
Client gets poor performance becauser programmer
did not understand performance characteristics
```

