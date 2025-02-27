(sections:prod:defs)=
# Define

We [left off](sections:prod) suggesting $8 = [3]$. Here's the problem: what the hell is $3$?! 


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
    x \neq 0 \implies [x_1, ..., x_n] = [x_1, ..., x_n, 0]
```

That's it. The rest is commentary.


The first equation {eq}`PROD0` is not a surprise. The second {eq}`PROD1` is where all the action happens. The third {eq}`PRODPAD` just says you can pad a prod with zeros without changing it[^padref].

Let's see how these axioms interact. So we must start with $0$. Then by {eq}`PROD1`, $[0, 0]$ is a prod. By {eq}`PRODPAD` and our earlier convention $[0, 0] = [0] = []$. So $[[]]$ is a prod, and so is $[0, []]$ and $[[0, []]]$ and so on.

(sections:prod:iso)=
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

As an example, let's work out $I([[[]], 0, []])$. Remember that $[]$ is just shorthand for $[0]$ so $I([]) = 2^0 = 1$. So: 
\begin{align*}
I([[[]], 0, []]) &= 2^{I([[]])} \times 3^{I(0)} \times 5^{I([])} \\
&= 2^{2^{I([])}} \times 3^{I(0)} \times 5^{I([])} \\
 &= 2^{2^1} \times 3^0 \times 5^1 \\
 &= 2^2 \times 1 \times 5 = 20.
\end{align*}

That was a little bit tedious but hopefully you can see how it works. In fact, $I$ works very well indeed. Behold the Fundamental Theorem of Productive Arithmetic:
````{prf:theorem} 
:label: ftpa
$I$ is bijective, i.e. $\mathbb{\Pi} \simeq \mathbb{N}$
````

Pretentious names aside, this is not a huge surprise. Notice how the definition of $I$ in equation {eq}`INT1` is pretty much the same as {prf:ref}`fta`. In any case, you can look at the proof below if you want.


````{dropdown} Click me for proof

Hope you're ready for some [inductions](sections:numbers:induction)!

```{prf:proof}

Prove by strong induction the following statement: $\forall n \in \mathbb{N}, \exists ! p \in \mathbb{\Pi}, I(p) = n$

*Base cases*: 

By {eq}`INT0`, $I(0) = 0$. This is unique, since $I(x) \geq 1$ for any $x \neq 0$ by {eq}`INT1`.


For $n=1$, $I([0]) = 2^0 = 1$. This is unique since $[] = [0, ..., 0] = [0]$ by {eq}`PRODPAD`.

*Inductive step* ($n > 1$): Assume for inductive hypothesis (IH) $\forall m < n, \exists ! p, I(p) = m$.

By {prf:ref}`fta`, $n$ factors uniquely into exponents $e_1, ..., e_k$. Since every $e_i < n$ (because x $n \geq p_i^{e_i}$ for each $i$), apply IH to find unique $x_i$ such that $I(x_i) = e_i$ for every $i$. Then by {eq}`INT1`, $I([x_1, ..., x_k]) = 2^{I(x_1)} \times ... \times p_k^{I(x_k)} = 2^{e_1} \times ... \times p_k^{e_k} = n$. Done.

```
That's all. You'd
````


## Examples

Here's a table of some numbers, their factorization and their productive representation. Enjoy!

| $n$ | factorization of $n$ | prod of $n$ |
| :--- | :----: | :----: |
| $0$    | $0$      | $0$     |
| $1$    | $1$      | $[]$     |
| $2$    | $2^1$      | $[[]]$     |
| $3$    | $3^1$      | $[0, []]$     |
| $4$    | $2^2$      | $[[[]]]$     |
| $5$    | $5^1$      | $[0, 0, []]$     |
| $6$    | $2^1 \times 3^1$      | $[[], []]$     |
| $7$    | $7^1$      | $[0, 0, 0, []]$     |
| $8$    | $2^3$      | $[[0, []]]$     |
| $9$    | $3^2$      | $[0, [[]]]$     |
| $10$    | $2^1 \times 5^1$      | $[[], 0, []]$     |

As you can see already, it gets quite fiddly to parse these nested brackets. Luckily, a friend pointed out to me a much more human-readable way of writing prods: trees! All you have to do is substitute $0$ to $\circ$, $[]$ to $\bullet$ and $[x_1, ..., x_n]$ to a root node connected to $x_1, ..., x_n$. Here's the same table but with trees:

```{list-table}
:align: center -- doesnt seem to work
:header-rows: 1
:widths: auto
* - $n$
  - factorization of $n$
  - tree of $n$
* - $0$
  - $0$
  - $\circ$
* - $1$
  - $1$
  - $\bullet$
* - $2$
  - $2^1$
  - ```{image} ../../tikz/p2.svg
        :alt: 2 as tree
        :height: 50px
    ```
* - $3$
  - $3^1$
  - ```{image} ../../tikz/p3.svg
        :alt: 3 as tree
        :height: 50px
    ```
* - $4$
  - $2^2$
  - ```{image} ../../tikz/p4.svg
        :alt: 4 as tree
        :height: 100px
    ```
* - $5$
  - $5^1$
  - ```{image} ../../tikz/p5.svg
        :alt: 5 as tree
        :height: 50px
    ```
* - $6$
  - $2^1 \times 3^1$
  - ```{image} ../../tikz/p6.svg
        :alt: 6 as tree
        :height: 50px
    ```
* - $7$
  - $7^1$
  - ```{image} ../../tikz/p7.svg
        :alt: 7 as tree
        :height: 50px
    ```
* - $8$
  - $2^3$
  - ```{image} ../../tikz/p8.svg
        :alt: 8 as tree
        :height: 100px
    ```
* - $9$
  - $3^2$
  - ```{image} ../../tikz/p9.svg
        :alt: 9 as tree
        :height: 100px
    ```
* - $10$
  - $2^1 \times 5^1$
  - ```{image} ../../tikz/p10.svg
        :alt: 10 as tree
        :height: 50px
    ```
```

If you want to see more examples, check out [this page](sections:draw) which allows you to draw any prod you want!

That's all for now. In the next section, we'll take a look at the what you can do with prods.

[^padref]: The padding axiom is kind of inelegant and I wish it didn't need to be there. Technically, you could define the underlying lists as implicitly having an infinite number of trailing zeros. Alternatively, you could bite the bullet and point the finger at decimal notation for also having redundant padding: ever noticed that $2 = 02 = 002 = 002.000$?


