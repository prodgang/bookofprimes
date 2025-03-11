(sections:lattice)=
# Lattices

One day, I was sitting on a roof top practicing some ... breathing excercises ... and it occured to me that maybe graft and prune form a lattice. I didn't really know what a lattice was, so I went downstairs, pulled up the [wikipedia definition](https://en.wikipedia.org/wiki/Lattice_(order)#As_algebraic_structure) and coded up some python to check which conditions were satisfied. It went pretty well.

It turns out there's a whole family of different type of lattices that form a kind of poset:
```{figure} ../../imgs/Lattice_v4.png
---
align: center
height: 400px
---
[source](https://en.wikipedia.org/wiki/Map_of_lattices)
```

Almost immediately, I realized I had accidentally discovered a distributive lattice. A week later, I had proven it. After a few more months, I finally worked out how to produce Boolean algebras. The following sections detail this journey but with hindsight's gift of clarity.

## Order

As you can see from the image above, a lattice is at the very least a partial order. So how do we make a productive partial order?

First of all, it makes sense to require that $0$ is less than everything else:
```{math}
:label: PLEQ0
   0 \sqsubseteq x \text{ , for any } x \in \mathbb{\Pi}
```

I've chosen the $\sqsubseteq$ symbol to maintain the square vibes.

The other natural requirements are for the primes to be incomparable and that if $x \sqsubseteq y$, then $[x] \sqsubseteq [y]$. This second part generalizes to:
```{math}
:label: PLEQ1
   x_1 \sqsubseteq y_1, ..., x_n \sqsubseteq y_n \implies [x_1, ..., x_n] \sqsubseteq [y_1, ..., y_n]
```

And that's it[^leqref]. Let's try a couple of examples:

1. $[] \sqsubseteq []$. Remember that $[] = [0]$ by {eq}`PRODPAD`. Since $0 \sqsubseteq 0$ by {eq}`PLEQ0`, then $[0] \sqsubseteq [0]$ by {eq}`PLEQ1`.
2. $[] \sqsubseteq x$, for any $x \neq 0$. Expand $[]$ to $[0, ..., 0]$ and $x$ to $[x_1, ..., x_n]$. Apply {eq}`PLEQ0` to every component and then {eq}`PLEQ1` on the whole thing.
3. $[[]] \sqsubseteq [[], []]$. Firstly, pad $[[]]$ to $[[], 0]$. We just saw that $[] \sqsubseteq []$. Meanwhile, $0 \sqsubseteq []$ by {eq}`PLEQ0`. So by {eq}`PLEQ1`, $[[], 0] \subseteq [[], []]$.
4. $[[], 0] \not \sqsubseteq [0, []]$. $0 \sqsubseteq []$ so both sides are part greater and part less than the other. Since neither is uniformly greater, we cannot use {eq}`PLEQ1`, so different primes are incomparable.
5. $[[[]]] \not \sqsubseteq [[0, []]]$. We just saw that $[[]] \not \sqsubseteq [0, []]$, so of course wrapping each side in another bracket doesn't change anything. But this is example is important because the corresponding numbers divide: $4 | 8$. Therefore $\sqsubseteq$ is different to divisibility.

Here's a snapshot of the Hasse diagram:
```{image} ../../tikz/plat.svg
        :alt: productive lattice
        :height: 250px
        :align: center
```

Once again, its much easier to interpret things with trees. The general pattern is that $x \sqsubseteq y$ if the you can place $y$ on top of $x$ and completely cover it. Practice a few for yourself if you want.

We'd better check that this does actually define a partial order! I'll go through the reflexivity proof in detail and you can check out the other parts if you want. They're all not-particularly-insightful inductions.

```{prf:theorem} 
:label: pleqrefl
$x \sqsubseteq x$
```


```{prf:proof} 

Base case ($x=0$): $0 \sqsubseteq 0$ by {eq}`PLEQ0`

Inductive step ($x = [x_1, ..., x_n]$). Assume for inductive hypothesis $x_i \sqsubseteq x_i$. Then by {eq}`PLEQ1`, $[x_1, ..., x_n] \sqsubseteq [x_1, ..., x_n]$, so $x \sqsubseteq x$. Done.

```


````{dropdown} Click me for proofs of transitivity and anti-symmetry

We'll go with anti-symmetry first because its merely a double induction.

```{prf:theorem}
:label: pleqasymm
$x \sqsubseteq y \land y \sqsubseteq x \implies x = y$
```

```{prf:proof} 
Base case ($x = 0$): If $y \sqsubseteq 0$, then $y = 0 = x$.

Inductive step ($x = [x_1, ..., x_n])$. $x \sqsubseteq y$, so $y \neq 0$ and we can expand to $[y_1, ..., y_n]$. Assume for inductive hypothesis that $x_i \sqsubseteq y_i \land y_i \sqsubseteq x_i \implies x_i = y_i$. 

Since $x \sqsubseteq y$, then $x_i \sqsubseteq y_i$ for every $i$ by {eq}`PLEQ1`. Similarly, $y \sqsubseteq x$ implies $y_i \sqsubseteq x_i$. 

Now apply inductive hypothesis to get $x_i = y_i$. So $[x_1, ..., x_n] = [y_1, ..., y_n]$ and $x = y$. Done
```
Transitivity triple induction time!

```{prf:theorem}
:label: pleqtrans
$x \sqsubseteq y \land y \sqsubseteq z \implies x \sqsubseteq z$
```

```{prf:proof} 
Base case split on $x,y,z$:
- $x=0$ immediately implies $x \sqsubseteq z$ by {eq}`PLEQ0`
- $y=0$ and $x \sqsubseteq y$ implies $x = 0$ and so $x \sqsubseteq z$
- $z=0$ and $y \sqsubseteq z$ implies $y=0$ which implies $x=0$ and so $x \subseteq z$.

Inductive step ($x = [x_1, ..., x_n], y=[y_1, ..., y_n], z=[z_1, ..., z_n]$): assume for inductive hypothesis that $x_i \sqsubseteq y_i \land y_i \sqsubseteq z_i \implies x_i \sqsubseteq z_i$, for every $i$. 

Then $x \sqsubseteq y$ implies $x_i \sqsubseteq y_i$ by {eq}`PLEQ1`. Similarly, $y \sqsubseteq z$ implies $y_i \sqsubseteq z_i$.

Applying inductive hypothesis, $x_i \sqsubseteq z_i$ for every $i$. So $[x_1, ..., x_n] \sqsubseteq [z_1, ..., z_n]$ which means $x \sqsubseteq z$ by {eq}`PLEQ1`. Done
```

These proofs are so mechanical and uninteresting I don't really see the point in reading them. Most of my intuition for $\sqsubsteq$ comes from its semantic similarities to $\subseteq$ and $|$. But if that's too informal you, symbol shunt away!

````




That trick I mentioned about fitting $y$ on top of $x$ to check whether its bigger segues nicely into the next observation. If you've read the wikipedia article on lattices closely (or just know enough about them already), you'll know that there's two different ways to different a lattice: either starting with a poset and looking for greatest/least upper/lower bounds or starting with two operations $\land, \lor$ and using them to define a poset. Conveniently, these are identical in our case.

````{prf:theorem} 
:label: pleqeqlatt
$x \sqsubseteq y \iff x = x \sqcap y$
````

````{dropdown} Click me for proof of equivalence

You'd never have guessed - its more inductions!

```{prf:proof} 

   Forwards direction: $x \sqsubseteq y \implies x = x \sqcap y$

   Base case ($x = 0$): $0 \sqcap y = 0$ by {eq}`PRUNE0`.

   Inductive step ($x = [x_1, ..., x_n]$): suppose $x \sqsubseteq y$. Then $y \neq 0$, so let $y = [y_1, ..., y_n]$. 
   
   By {eq}`PLEQ1`, we have $x_i \sqsubseteq y_i$. By inductive hypothesis, $x_i = x_i \sqcap y_i$. 
   
   Therefore, $x \sqcap y = [x_1, ..., x_n] \sqcap [y_1, ..., y_n] = [x_1 \sqcap y_1, ..., x_n \sqcap y_n] = [y_1, ..., y_n] = y$. Done.

   Backwards direction: $x = x \sqcap y \implies x \sqsubseteq y$. 

   Base case ($x = 0$): $0 \sqsubseteq y$ by {eq}`PLEQ0`.

   Inductive step ($x = [x_1, ..., x_n]$): suppose $x = x \sqcap y$. Then $y \neq 0$, so let $y = [y_1, ..., y_n]$. 
   
   By {eq}`PRUNE1`, $x_i = x_i \sqcap y_i$. By inductive hypothesis, $x_i \sqsubseteq y_i$. Therefore, $x \sqsubseteq y$ by {eq}`PLEQ1`. Done.
```

````


```{admonition} Historical Tangent
This equivalence was pretty exciting for me when I first noticed it because I had written down the definitions of $\sqsubseteq$ and $\sqcap$ completely independently, years apart, and they ended up working together in the nicest possible way, forming some structure I had barely even heard of. The only link between their definitions was that both times, I had tried to write down the simplest thing I could imagine. This gave the same sense of eery excitement as realizing the way you butter your toast is the same as the way you brush your teeth, and these similiarities could help you solve a rubik's cube. 

The fact that both definitions had split into a $0$ case and a $[x_1, ..., x_n]$ case is what led me to write down {eq}`PROD0` and {eq}`PROD1`, where your journey began. Only then did I realize I could prove things by induction at which point the proofs wrote themselves and I could write this book. The point is that the structure of this book is not chronological but pedagogical. 
```


Remember to prove:
- $x \sqsubseteq y \implies x | y$ (and also $x \subseteq y$ when interpetred properly)

[^leqref]: Technically, the definition should be written as $x \sqsubseteq y \iff x = 0 \lor$ {eq}`PLEQ1` but you get the idea.