

### **Problem Recap:**
We are tasked to show that the recurrence \( T(n) = 2 + T(\lfloor n/2 \rfloor) \), where \( T(1) = 1 \), grows approximately like \( 2 \lg n \). Here, \( \lg n \) means \( \log_2 n \), the logarithm base 2.

This recurrence describes the number of comparisons an algorithm performs when searching through a sorted list of size \( n \).

---

### **Step 1: Understand the Recurrence**

#### 1.1 Base Case:
- When the list size is \( n = 1 \), \( T(1) = 1 \). This means:
  - If there's only one element, the algorithm performs just one comparison.

#### 1.2 Recursive Case:
- When \( n \geq 2 \), \( T(n) = 2 + T(\lfloor n/2 \rfloor) \).
  - The \( 2 \) comes from the two comparisons made at each step:
    - One to check if \( x < am \) (too small).
    - Another to check if \( am < x \) (too large).
  - After making these comparisons, the algorithm reduces the problem to half the size (\( \lfloor n/2 \rfloor \)) and repeats the process.

---

### **Step 2: Expand the Recurrence**

Let’s break the recurrence down step by step by repeatedly substituting \( T(\lfloor n/2 \rfloor) \):

1. Start with \( T(n) = 2 + T(\lfloor n/2 \rfloor) \).

2. Replace \( T(\lfloor n/2 \rfloor) \) with \( 2 + T(\lfloor n/4 \rfloor) \):
   \[
   T(n) = 2 + \left(2 + T(\lfloor n/4 \rfloor)\right) = 2 + 2 + T(\lfloor n/4 \rfloor).
   \]

3. Replace \( T(\lfloor n/4 \rfloor) \) with \( 2 + T(\lfloor n/8 \rfloor) \):
   \[
   T(n) = 2 + 2 + 2 + T(\lfloor n/8 \rfloor).
   \]

4. Continue unrolling:
   \[
   T(n) = 2 + 2 + 2 + \dots + T(1).
   \]

---

### **Step 3: Count the Terms**

Each \( 2 \) in the recurrence corresponds to one step where the size of the problem is halved. The process stops when the size of the problem becomes \( 1 \).

#### How many steps does it take to reach 1?

- At each step, the size of the problem reduces by half:
  - Start: \( n \).
  - After 1 step: \( \lfloor n/2 \rfloor \).
  - After 2 steps: \( \lfloor n/4 \rfloor \).
  - After 3 steps: \( \lfloor n/8 \rfloor \).
  - ...
  - After \( k \) steps: \( \lfloor n/2^k \rfloor \).

- The process stops when \( n/2^k = 1 \). Solving for \( k \):
  \[
  2^k = n \quad \implies \quad k = \lg n.
  \]

Thus, the algorithm takes \( \lfloor \lg n \rfloor \) steps.

---

### **Step 4: Total Comparisons**

Since each step adds \( 2 \) comparisons, and there are \( \lg n \) steps, the total number of comparisons is approximately:
\[
T(n) \sim 2 \lg n.
\]

---

### **Step 5: Add the Base Case**

The recurrence starts with \( T(1) = 1 \), but this is just one comparison at the very last step. For large \( n \), the effect of this \( +1 \) becomes negligible compared to the \( 2 \lg n \) term.

---

### **Step 6: Intuition Behind the Solution**

Why does the recurrence grow like \( \lg n \)?

- The \( \lg n \) comes from the **halving process**:
  - Every time we halve the problem size, we perform 2 comparisons.
  - Halving repeatedly leads to a logarithmic growth because \( n \) halves \( \lg n \) times before reaching 1.

- The factor of \( 2 \) comes from the **2 comparisons per step**:
  - Each halving step involves checking whether \( x < am \) and \( am < x \).

---

### **Final Answer:**
The recurrence \( T(n) \) grows asymptotically like:
\[
T(n) \sim 2 \lg n.
\]
