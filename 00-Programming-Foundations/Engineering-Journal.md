# Phase 1 — While Loop Practice & Learning Journal

## Today's Objective

Today, I focused on building the mental model required to solve loop problems instead of simply memorizing loop syntax.

My goal was to understand how I can break a problem into:

```text
Initial State
     ↓
Condition
     ↓
Repeated Work
     ↓
Progress / State Change
     ↺
```

I also started practicing how to dry-run an algorithm mentally before writing the code.

---

# Problems I Attempted

## Q1. Print all numbers from 1 to 10

### My Solution

```python
num = 1

while num <= 10:
    print(num)
    num += 1
```

### My Logic

```text
Initial state : num = 1
Condition     : num <= 10
Work          : print(num)
Progress      : num += 1
```

### My Dry Run

```text
1 → print → 2
2 → print → 3
...
10 → print → 11
11 <= 10 → False → stop
```

### Complexity

* **Time:** O(n) for the generalized problem of printing `1` to `n`
* **Space:** O(1)

### What I Learned

I learned that I need to define where my variable starts, when my loop should continue, what work happens during each iteration, and how the variable moves toward termination.

---

## Q2. Print numbers from 10 down to 1

### My Solution

```python
num = 10

while num >= 1:
    print(num)
    num -= 1
```

### My Logic

```text
Initial state : num = 10
Condition     : num >= 1
Work          : print(num)
Progress      : num -= 1
```

### My Dry Run

```text
10 → print → 9
9  → print → 8
...
1  → print → 0
0 >= 1 → False → stop
```

### Complexity

* **Time:** O(n) for the generalized problem of printing `n` down to `1`
* **Space:** O(1)

### What I Learned

I understood that changing the direction of a loop simply means changing the initial state, termination condition, and state transition.

---

# Q3. Print all even numbers between 1 and 100

I explored two approaches.

## Approach A — Check every number

### My Solution

```python
num = 1

while num <= 100:
    if num % 2 == 0:
        print(num)

    num += 1
```

### My Logic

```text
Initial state : num = 1
Condition     : num <= 100
Work          : check whether num is even and print it
Progress      : num += 1
```

### Complexity

* **Time:** O(n)
* **Space:** O(1)

---

## Approach B — Skip odd numbers

### My Solution

```python
num = 2

while num <= 100:
    print(num)
    num += 2
```

### My Logic

```text
Initial state : num = 2
Condition     : num <= 100
Work          : print(num)
Progress      : num += 2
```

### Complexity

* The loop performs approximately `n/2` iterations.
* **Time:** O(n)
* **Space:** O(1)

### My Understanding

I learned that even though Approach B performs fewer actual operations, it is still O(n), because:

```text
O(n/2) = O(n)
```

Big O describes the growth pattern, not the exact number of operations.

I also learned that I can sometimes make an algorithm better by skipping states that I already know are irrelevant.

---

# Q4. Print all odd numbers between 1 and 100

I again considered two approaches.

## Approach A — Check every number

### My Solution

```python
num = 1

while num <= 100:
    if num % 2 != 0:
        print(num)

    num += 1
```

### My Logic

```text
Initial state : num = 1
Condition     : num <= 100
Work          : check whether num is odd and print it
Progress      : num += 1
```

### Complexity

* **Time:** O(n)
* **Space:** O(1)

### Mistake I Discovered

I initially placed:

```python
num += 1
```

inside the `if` statement.

That was wrong because when `num` became even, the condition became false and `num` stopped changing. This created an infinite loop.

I learned:

> My progress/state-update step must happen whenever the algorithm needs to move toward termination, not only when a particular condition is true.

---

## Approach B — Skip even numbers

### My Solution

```python
num = 1

while num <= 100:
    print(num)
    num += 2
```

### My Logic

```text
Initial state : num = 1
Condition     : num <= 100
Work          : print(num)
Progress      : num += 2
```

### Complexity

* Approximately `n/2` iterations
* **Time:** O(n)
* **Space:** O(1)

### My Understanding

I learned that I can use knowledge about the problem to avoid unnecessary checks.

Instead of checking:

```text
1, 2, 3, 4, 5, 6...
```

I can directly move through:

```text
1, 3, 5, 7, 9...
```

---

# Q5. Print the multiplication table of a given number from n × 1 to n × 10

### My Solution

```python
n = int(input("Enter the number: "))

i = 1

while i <= 10:
    print(n * i)
    i += 1
```

### My Logic

```text
Input         : n
State         : i
Initial state : i = 1
Condition     : i <= 10
Work          : n × i
Progress      : i += 1
```

### My Understanding

I learned to distinguish between:

```text
n → fixed input
i → changing algorithmic state
```

For example, if `n = 7`:

```text
7 × 1
7 × 2
7 × 3
...
7 × 10
```

The number `n` stays fixed while `i` represents my current position in the multiplication table.

### Complexity

For this exact problem:

* **Time:** O(1), because the loop always runs exactly 10 times.
* **Space:** O(1)

If the problem were generalized to printing a table from `1` to `n`, then the time complexity would become O(n).

---

# What I Learned Today

## 1. I learned the basic structure of a loop

I now think about a loop as:

```text
Initial State
     ↓
Condition
     ↓
Repeated Work
     ↓
Progress
     ↺
```

---

## 2. I learned the difference between `while` and `if`

The `while` condition asks:

> **Should I continue the process?**

The `if` condition asks:

> **Should I perform this particular action?**

I should not confuse these two roles.

---

## 3. I learned that every loop needs progress

I need to know:

> **What changes after every iteration?**

I also need to know why that change will eventually make my condition false.

---

## 4. I learned that correctness comes before optimization

An algorithm that executes very quickly but doesn't solve the problem is not a good algorithm.

I should first ask:

> **Does my solution produce the correct result?**

Only then should I optimize it.

---

## 5. I learned that fewer operations do not necessarily mean a different Big O

For example:

```text
n iterations
```

and:

```text
n/2 iterations
```

are both:

```text
O(n)
```

The second can still be practically better because it performs less actual work.

---

## 6. I learned to separate input from algorithmic state

For example:

```text
n = input
i = state
```

The input can remain fixed while my state variable changes throughout the algorithm.

---

# My Current Problem-Solving Framework

For every new problem, I want to ask myself:

```text
INPUT:
What am I given?

OUTPUT:
What must I produce?

STATE:
What information do I need to keep track of?

INITIAL STATE:
Where does the process start?

CONDITION:
When should I continue?

REPEATED WORK:
What happens once per iteration?

PROGRESS:
How does my state change?

TERMINATION:
Why will my loop eventually stop?

DRY RUN:
Can I manually simulate my solution?

TIME:
How does the amount of work grow?

SPACE:
How much additional memory do I use?
```

---

# My Biggest Takeaway

Today I started moving away from thinking:

> "How do I write a `while` loop?"

and toward thinking:

> **"What process am I trying to model, what state am I tracking, what happens repeatedly, and how does that state move toward termination?"**

I understand that the code is only the final expression of the algorithm.

The real work happens before I write the code:

```text
Problem
   ↓
Understand input/output
   ↓
Identify state
   ↓
Find repeated action
   ↓
Define condition
   ↓
Define progress
   ↓
Dry-run
   ↓
Write code
   ↓
Analyze complexity



My goal is **not to maximize the number of questions I finish**. My goal is to make the problem-solving process itself more natural.

Tomorrow, I can continue with the remaining loop problems and also continue with my Python learning.
