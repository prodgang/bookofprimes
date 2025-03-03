(sections:prod:ops)=
# Operate

The [previous section](sections:prod:iso) showed we can write any number uniquely as a prod. That's great. But what can we do with prods? 

In this section, we'll take a look at some extremely simple operations that do some extremely cool things. But first, let's take a look at some bad operations.

## Counter-productive operations

My criteria for a bad operation is that it cannot be defined in a similar manner to productive numbers themselves. We'll see that counting is a bad operation - hence counter-productive. Haha.

### Addition

Recall that [Peano arithmetic](sections:numbers:peano) kicks off by defining addition. How do you think we can define addition in productive arithmetic? 

The quick answer is that you can't. Just adding one to a number will change its factorization properties in very unpredictable ways. Basically all you can guarantee is that its factors will be completely different. So its not gonna happen. I don't know how to formally prove this, so if you don't believe me just try it yourself.

### Multiplication

Next operation: multiplication. There's a very good case that you should be able to define multiplication productively: the fundamental idea behind prods is multiplying primes so that's kind of what they're all about. We can even see this happen with an example. Take a look at the trees of $4,3,12$ and remember that $12 = 4 \times 3$:


```{image} ../../tikz/p4.svg
:alt: 4 as tree
:align: left
```
```{image} ../../tikz/p3.svg
:alt: 3 as tree
:align: center
```
```{image} ../../tikz/p12.svg
:alt: 12 as tree
:align: right
```

You can literally see how four and three are just attached to each other side by side to give $12$! Indeed, any time $x,y$ don't share any factors (i.e. are coprime), you can multiply them side-by-side like this. However, when they *do* share factors, then we're back to the classic equation: $a^b \times a^c = a^{b+c}$. So multiplication reduces to addition. So multiplication is counter-productive.

### Expontentiation

There's a similar story for exponentiation. While you can get away with writing $2^x$ as $[x]$ and even $6^x = [x, x]$, as soon as you have nested powers you have to eventually use the fact that $(x^y)^z = x^{y \times z}$. So expontentiation reduces to multiplication. So expontention is counter-productive. And so on.

It's kind of interesting that none of the usual arithmetic operations work. Even though these counter-examples were not hard to find, it would have been reasonable to expect that defining prods based on taking the product of prime powers would at least allow you to do products and powers. But you can't. So we need to think more carefully. 

### List operations

A fun way to test the rapidly developing abilities of language models is to try to get them to recreate prod arithmetic from scratch. Its a useful test case because there's been no trace of prods on the internet (until now) and so they really are required to work things out from scratch, as opposed to memorizing the thousands of training examples they've seen. In the past few years, they've gone from being incapable of consistently writing numbers productively to proving {prf:ref}`ftpa` given only the axioms.

However, even the newest models continue to suck at coming up with productive operations. What usually happens is they propose some additive operation, I repeat the argument from above to show its not productive and then they switch to list based operations. 

For example, given two lists you can *concantenate* them which just means stick one on the end of the other one. So $[a, b, c] ++ [d, e] = [a, b, c, d, e]$. But this is not a productive operation because it does not respect the padding axiom {eq}`PRODPAD`: you can pad then concatenate to get $[0] ++ [[]] = [0, []]$ or you can concatenate then pad to get $[] ++ [[]] = [[]] = [[], 0]$, which is very different. 

So operations that are natural for lists are not necessarily productive.

## Productive operations

Let's take a step back. Rather than trying to reinvent the wheel, let's just find the simplest possible productive operation and see what it ends up doing. 

The simplest prod is $0$ and the simplest thing to do with $0$ is nothing. So let's define an operation that does nothing with zero:

```{math}
:label: CUP0
   0 \sqcup x = x = x \sqcup 0
```

I've chosen the $\sqcup$ symbol to suggestively look like the set union symbol, but square because prod has square vibes. But {eq}`CUP0` isn't enough for a fully fledged operation, because what happens to nonzero prods? What about the simplest possible thing:

```{math}
:label: CUP1
   [x_1, ..., x_n] \sqcup [y_1, ..., y_n] = [x_1 \sqcup y_1, ..., x_n \sqcup y_n]
```
On trees this looks like:
```{image} ../../tikz/cup1.svg
   :alt: cup tree
   :align: center
   :width: 500px
```

So it's recursive! All {eq}`CUP1` does is the pass the work down one level. But that's enough because all prods eventually with zeros and then {eq}`CUP0` kicks in. By the way, you can safely assume that $x$ and $y$ are both the same length in {eq}`CUP1` by padding with zeros. 

Let's see it in action! Here's a detailed walkthrough for how to compute $4 \sqcup 3$:
```{image} ../../tikz/egcup1.svg
   :alt: cup tree
   :align: center
   :width: 500px
````


Here's a more complicated example: $40 \sqcup 18$ (remember that $40 = 2^3 \times 5$ and $18 = 2 \times 3^2$):
```{image} ../../tikz/egcup2.svg
   :alt: cup tree
   :align: center
   :width: 750px
````

The trick is to start off with everything padded so that they have roughly the same shape, then work bottom-up.


```{list-table}
:align: center 
:header-rows: 1
:widths: auto
* - $x$
  - $y$
  - $x \sqcup y$
  - as a number
* - $2$
  - $3$
  - $5$
  - TODO
```