(sections:post:next)=
# Next Steps

Here's a bunch of stuff I've come across that seems vaguely related to prods, along with some unfinished thoughts about topics that are mostly beyond my paygrade. 


## Other Number Systems

* $p$-adics is a [number system](https://en.wikipedia.org/wiki/P-adic_number) that makes no sense but makes pretty pictures. If mathematicians can get away with studying this nonsense, surely they can do something with prods...
* [Surreal numbers](https://en.wikipedia.org/wiki/Surreal_number) is pretty fun: you literally define numbers as games! This was a very inspiring example for me. I'm also very envious because not only does surreal numbers recover rational and real numbers, it goes beyond and produces new numbers (hence the name). My biggest disappointment is that prods can, so far, only deal with natural numbers.


## Infinite Prod

As mentioned above, I'm sad that prods are merely countable. So how to make them infinite? 

In set theory, you get infinite sets by taking the limit of an increasing sequence of sets. So what if you took the limit of the following increasing sequence?
```{image} ../../tikz/seq1.svg
        :alt: sequence of prods
        :height: 100px
        :align: center
```


If that's allowed, then take an arbitrary function $f: \mathbb{N} \to \mathbb{N}$ and encode it like so:
```{image} ../../tikz/seq2.svg
        :alt: sequence of f values
        :height: 100px
        :align: center
```


Then there's uncountably many infinite prods. They seem well-defined, but I don't know how to work with them because I can't just code them up in python any more. But maybe there's some fun stuff here.


## Logic

* One of the most important insights in defining prods was to make them recursive. This was directly inspired by reading about Godel numbering, which recursively represents logical formulae as numbers through exponentiation. Godel numbering is the key ingredient to the incompleteness theorems, so can they also be proven for productive arithmetic?

* We've seen that productive Heyting algebras are subtly different from the divisibility lattices. Does this give rise to meaningful differences in the internal logics?

## Indepedence

I've claimed that addition can't be defined productively. I have a hunch that $\sqcup$ can't be defined additively. Would be nice to prove those claims. More generally, I reckon a model theoretic analysis on the productive axioms (plus induction schema of course) would be useful. 

## Number Theory

Do prods simplify the proof of Fermat's Last Theorem? I wrote down a version of this once, but can't remember where I put it. What about the Riemmann hypothesis? I wouldn't be much of a crackpot internet number theorist if I didn't claim to have solved it, would I?

But seriously, what can prods do for number theory?

## You

One of the wonderful things about math is how often unexpected connections pop up between things that really have no right to be similar. I don't know where the next connection might be, but maybe you do. So why not try? 

That is all, my friends. Go forth and productivize. 