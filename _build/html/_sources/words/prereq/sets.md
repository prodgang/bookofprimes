# Sets


Never briefly, a *set* is collection of things (called elements) that share some property. We write sets between $\{$ and $\}$. For example, $\{a, b, c, ..., z\}$ is the set of lowercase letters. Some more important examples:


```{math}  \mathbb{N} = \{0, 1, 2, ...\}

\mathbb{Z}= \{..., -2, -1, 0, 1, 2, ...\}

 \mathbb{Q}^+ = \{1/2, 1/3, ...\} 

 ```

And so on. If $a$ is an element of a set $A$, we write $a \in A$. Sometimes, sets share elements. For example, $\mathbb{N}$ and $\mathbb{Z}$ both contain $0$. If $A$ and $B$ are sets, then $A \cap B$ is the set of all the shared elements of $A$ and $B$, called the *intersection*. For example, $\mathbb{Z} \cap \mathbb{Q}^+ = \mathbb{N}$. 


Intersection has a dual operation called *union* and written $A \cup B$ which gives you the set of elements that are either in $A$ or $B$ (as opposed to both). So if $EVEN$ is the set of even integers and $ODD$ is the set of odd integers, then $EVEN \cup ODD = \mathbb{Z}$. 



Finally, if all the elements of one set are also in another set, we write $A \subseteq B$ and say $A$ is a *subset* of $B$. If there's some $a \in A$ that's *not* in $B$, then $A \not\subseteq B$. For example, $\mathbb{N} \subseteq \mathbb{Z}$ but $\\mathbb{Z} \not\subseteq \mathbb{Q}^+$. Try and work out whether its true that $A \cap B \subseteq A \subseteq A \cup B$ (or vice-versa).



A trick for remembering the difference between $\cap$ and $\cup$ is that $\cap$ sort of looks like an N and you can sort of think of the elements of $A \cap B$ as the elements of "A aNd B", meanwhile $\cup$ sort of looks like a U and you can sort of read $A \cup B$ as "A Uor B"...

Functions?
