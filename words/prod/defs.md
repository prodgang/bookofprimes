(sections:prod:defs)=
# Definitions

We left off suggesting $8 = [3]$. Here's the problem: what the hell is $3$?! 


## Fixing the Problem


Having made a commitment to represent every number as a list of its exponents, we then immediately reverted to describing those exponents using nothing other than an additive representation.

Since $3 = [0, 1]$, we really should have written $[[0, 1]]$. But wait - what is $1$? Technically, it would be $[0] = [0, 0] = ...$, but let's just call it $[]$. So at last, $8$ becomes $[[0, []]]$. 

More generally, in order to productively write a number as a list of its exponents, we must first write the exponents as a list of their exponents, but that means we need to write those exponents etc etc. In short, we must make productive numbers *recursive*!

Rather than working from additive to productive, its a little easier to define productive numbers from scratch and then see later how they can be related to additive numbers. Also, productive numbers is a mouthful so I'll call them *prods*.

So here it is. The formal definition of the set of prods $\mathbb{\Pi}$:

```{math}
:label: PROD0 
    0 \in \mathbb{\Pi}
```



```{math}
:label: PROD1
    x_1 \in \mathbb{\Pi}, x_2 \in \mathbb{\Pi}, ..., x_n \in \mathbb{\Pi} \implies [x_1, x_2, ..., x_n] \in \mathbb{\Pi}
```



```{math}
:label: PRODPAD
    [x_1, ..., x_n] = [x_1, ..., x_n, 0]
```

The first equation {eq}`PROD0` is not a surprise. The second {eq}`PROD1` is where all the action happens. The third {eq}`PRODPAD` just says you can pad a prod with zeros without changing it[^padref].

That's it. The rest is commentary.

## Isomorphism

The interpretation of a productive number (i.e. what number it corresponds to) is given by the following recursive function $I: \mathbb{\Pi} \to \mathbb{N}$:

```{math}
:label: INT0
    I(0) = 0
```


```{math}
:label: INT1
    I([x_1, x_2, ..., x_n]) = 2^{I(x_1)} \times 3^{I(x_2)} \times ... \times p_n^{I(x_n)}
```
(where $p_n$ is the nth prime)

As an example, let's work out $I([[[]], 0, []])$. Remember that $[]$ is just shorthand for $[0]$ so $I([]) = 2^0 = 1$. So we can rewrite to $[[1], 0, 1]$. 

[^padref]: The padding axiom is kind of inelegant and I wish it wasn't there. Technically, you could define the underlying lists as implicitly having an infinite number of trailing zeros. Alternatively, you could bite the bullet and point the finger at decimal notation for also having redundant padding: ever noticed that $2 = 02 = 002 = 002.000$?


