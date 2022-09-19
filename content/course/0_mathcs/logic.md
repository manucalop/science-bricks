---
title: Propositional Logic
date: "2022-08-06"
type: book
weight: 20
---

**Propositional Logic** is the basic language upon which all modern Mathematics and Computer Science can be built. Its key notion is a proposition.

## Proposition

_A **proposition** is a statement that can only be True or False._

<!-- Its equivalent in Computer Science, is a binary digit (bit), which can only be 0 or 1. -->

Examples:

- "If I can read this, I am alive"
  - Always **True**. Also known as a **tautology**.
- "All cars are red".
  - Always **False**. Also known as a **contradiction**.
- "I am hungry".
  - **True** or **False**. Now it is **True**, but pizza is coming. Soon it will be **False**.

<!-- The goal of propositional logic is not to determine whether a proposition is true or false, but to provide the tools to operate with propositions. -->

Just as a computer, which operates with variables that are either 0 or 1, propositional logic provide the tools to operate with statements that are either True or False.

## Logical Operators

One can build propositions from given ones by means of **logical operators**.

### Unary operators

_**Unary operators** take **one** proposition and return a new proposition_.

These are all possible unary operators:

{{< math >}}

$$
\small
\begin{array}{c||c|c|c}
p & \neg p & \mathrm{id}(p) & \top p & \bot p \\
\hline
\rule{0pt}{12pt}
F & T & F & T & F\\
T & F & T & T & F
\end{array}\qquad
\begin{array}{ll}
  \neg & NOT\\
  id   & Identity\\
  \top & Tautology\\
  \bot & Contradiction
\end{array}
$$

{{< /math >}}

In python, these operators could be defined as follows:

<!-- Not {{{ -->

{{< spoiler text="NOT" >}}

```python
def NOT(p):
    if p is True:
        return False
    else:
        return True

proposition = True
NOT(proposition) #out: False
proposition = False
NOT(proposition) #out: True
```

{{< /spoiler >}}

<!-- }}} -->
<!-- Identity {{{-->

{{< spoiler text="Identity" >}}

```python
def identity(p):
    return p


proposition = True
identity(proposition) #out: True
proposition = False
identity(proposition) #out: False
```

{{< /spoiler >}}

<!--}}}-->
<!-- Tautology {{{-->

{{< spoiler text="Tautology" >}}

```python
def tautology(p):
    return True

proposition = True
tautology(proposition) #out: True
proposition = False
tautology(proposition) #out: True
```

{{< /spoiler >}}

<!--}}}-->
<!-- Contradiction {{{-->

{{< spoiler text="Contradiction" >}}

```python
def contradiction(p):
    return False

proposition = True
contradiction(proposition) #out: False
proposition = False
contradiction(proposition) #out: False
```

{{< /spoiler >}}

<!--}}}-->

### Binary operators

_**Binary operators** take **two** propositions and return a new proposition_.

There are 16 binary operators in total, but we show some interesting ones in the following table:

{{< math >}}

$$
\small
\begin{array}{c|c||c|c|c|c|c}
  p & q & p\land q & p\lor q & p\veebar q & p \uparrow  q& p \Rightarrow q & p \Leftrightarrow q \\
  \hline
    \rule{0pt}{12pt} F & F & F & F & F & T & T & T\\
                     F & T & F & T & T & T & T & F\\
                     T & F & F & T & T & T & F & F\\
                     T & T & T & T & F & F & T & T
\end{array}\qquad
\begin{array}{ll}
  \land           & AND\\
  \lor            & OR\\
  \veebar         & \text{EX-OR}\\
  \uparrow        & \text{NAND (not AND)}\\
  \Rightarrow     & Implication\\
  \Leftrightarrow & Equivalence
\end{array}
$$

{{< /math >}}

Some of them written in python:

<!-- AND {{{ -->

{{< spoiler text="AND" >}}

```python
def AND(p, q):
    if p is True:
        if q is True:
            return True
    return False

p = True
q = False
out = AND(p,q) #out: False
q = True
out = AND(p,q) #out: True
```

{{< /spoiler >}}

<!-- }}} -->
<!-- OR {{{ -->

{{< spoiler text="OR" >}}

```python
def OR(p, q):
    if p is True:
        return True
    elif q is True:
        return True
    return False

p = True
q = False
out = OR(p,q) #out: True
p = False
out = OR(p,q) #out: False
```

{{< /spoiler >}}

<!-- }}} -->
<!-- EX-OR {{{ -->

{{< spoiler text="EX-OR" >}}

```python
def EXCLUSIVE_OR(p, q):
    if p is True:
        if q is True:
            return False
        return True
    elif q is True:
        return True
    return False

p = True
q = False
out = OR(p,q) #out: True
q = True
out = OR(p,q) #out: False
```

{{< /spoiler >}}

<!-- }}} -->
<!-- NAND {{{ -->

{{< spoiler text="NAND" >}}

```python
def NAND(p, q):
    return NOT(AND(p, q))

p = True
q = False
out = OR(p,q) #out: True
q = True
out = OR(p,q) #out: False
```

{{< /spoiler >}}

<!-- }}} -->

The NAND operator is **functional complete**, which allows
**any operator** to be constructed from NAND operators. A crucial fact in Digital Electronics.

## Proofs by Contradiction

<!-- From the implication operator $(\Rightarrow)$, one can conclude anything based on false assumptions, also known as ''ex falso quodlibet''. -->

An immediate consequence of the implication operator $(\Rightarrow)$ is that **assertions can be proven by contradiction**.

Let's assume that we want to prove that the proposition $q$ is True from the assumption that $p$ is True. Then, we can equivalently assume that $q$ is false and prove that $p$ must be False, which contradicts the original assumption that $p$ is True. Mathematically:

$$
(p \Rightarrow q) \Leftrightarrow ((\neg q)\Rightarrow (\neg p))
$$

We can prove it by constructing the truth table and see that the two last propositions are identical:

{{<math>}}

$$
\begin{array}{c|c||c|c|c|c}
  p & q & \neg p &  \neg q & p \Rightarrow q & (\neg q) \Rightarrow (\neg p) \\
  \hline
    \rule{0pt}{12pt} F & F & T & T & T & T\\
                     F & T & T & F & T & T\\
                     T & F & F & T & F & F\\
                     T & T & F & F & T & T
\end{array}
$$

{{</math>}}

## Predicate Logic

_A **predicate** is a "function" that takes proposition(s) and returns True or False._

_A **relation** is a predicate of **two** propositions._

TODO

<!-- ## Quiz -->

<!-- {{< spoiler text="What is the difference between lists and tuples?" >}} -->
<!-- Lists -->

<!-- - Lists are mutable - they can be changed -->
<!-- - Slower than tuples -->
<!-- - Syntax: `a_list = [1, 2.0, 'Hello world']` -->

<!-- Tuples -->

<!-- - Tuples are immutable - they can't be changed -->
<!-- - Tuples are faster than lists -->
<!-- - Syntax: `a_tuple = (1, 2.0, 'Hello world')` -->
<!--   {{< /spoiler >}} -->

<!-- {{< spoiler text="Is Python case-sensitive?" >}} -->
<!-- Yes -->
<!-- {{< /spoiler >}} -->
