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

Next operation: multiplication. There's a very good case that you should be able to define multiplication productively: the fundamental idea behind prods is multiplying primes so that's kind of what they're all about. There's even some quite good evidence for this. Take a look at the trees of $4,3,12$ and remember that $12 = 4 \times 3$:


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

## Productive operations

