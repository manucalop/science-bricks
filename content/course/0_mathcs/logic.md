---
title: Logic
date: '2022-08-06'
type: book
weight: 20
---


## WIP

Propositional Logic is the basic language upon which all modern Mathematics can be built. Its key notion is a proposition.

_A __proposition__ is a statement that can only be true or false._

Examples:

- "If I can read this, I am alive"
    - Always __True__. Also known as a __tautology__.
- "All cars are red". 
    - Always __False__. Also known as a __contradiction__.
- "I am hungry".
   - __True__ or __False__. Now it is __True__, but pizza is coming. Soon it will be __False__.

<!-- The goal of propositional logic is not to determine whether a proposition is true or false, but to provide the tools to operate with propositions. -->
Just as a computer, which operates with variables that are either 0 or 1, propositional logic provide the tools to operate with statements that are either True or False. 

One can build propositions from given ones by means of __logical operators__:

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

In python the NOT operator is already implemented. Play with this code:

```python
p = True
print(not(p))
```

<iframe 
    src="https://trinket.io/embed/python3" 
    width="100%" 
    height="356" 
    frameborder="0" 
    marginwidth="0" 
    marginheight="0" 
    allowfullscreen
    input="foo"
    >
</iframe>


One can quickly check that, if $p$ can only be true or false, these operators cover all the possibilities to define a unary operator. The next step is to consider binary operators, i.e. operators that take two propositions and return a new one. We have 16 binary operators in total, but we draw some interesting ones in the following table:

{{< math >}}
$$
\small
\begin{array}{c|c||c|c|c|c|c}
  p & q & p\land q & p\lor q & p\veebar q & p \Rightarrow q & p \Leftrightarrow q \\
  \hline
    \rule{0pt}{12pt} F & F & F & F & F & T & T\\
                     F & T & F & T & T & T & F\\
                     T & F & F & T & T & F & F\\
                     T & T & T & T & F & T & T
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

From the implication operator, one can conclude anything based on false assumptions, also known as ''ex falso quodlibet''.

Let $p$, $q$ be propositions. Then $(p \Rightarrow q) \Leftrightarrow ((\neg q)\Rightarrow (\neg p))$.

We need only to construct the truth table and see that the two last propositions are identical:

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

We can prove assertions by way of contradiction. E.g. assume that $p$ is true and we want to prove that $q$ is true. Then, what we can do instead, and is fully equivalent, is to assume that what we want to prove is not true, and then prove that the assumption is not true. Then we say we have a contradiction and $q$ must have been true.

## Predicate Logic



## Quiz

{{< spoiler text="What is the difference between lists and tuples?" >}}
Lists

- Lists are mutable - they can be changed
- Slower than tuples
- Syntax: `a_list = [1, 2.0, 'Hello world']`

Tuples

- Tuples are immutable - they can't be changed
- Tuples are faster than lists
- Syntax: `a_tuple = (1, 2.0, 'Hello world')`
  {{< /spoiler >}}

{{< spoiler text="Is Python case-sensitive?" >}}
Yes
{{< /spoiler >}}
