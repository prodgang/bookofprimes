(sections:algebra)=
# Algebra


For unrelated reasons, I once came across this thing called group theory. A group is kind of like a set with some cool powers. Groups are part of abstract algebra, which basically studies the idea of combining the doing of one thing with the doing of another thing. Hence the abstract. The algebra part means shunting meaningless symbols around, just like the one that scarred you in highschool. 

A group is a set where the cool power gives you the ability to (a) do nothing, (b) undo everything that you can do and (c) something boring called associativity (which I call *chalkboard grease* because it just makes the symbol shunting easier). Wow so cool! But seriously, whenever you find yourself a set that can do those three things, you'd better get excited because it means that your set posseses some incredibly intricate and elegant structure.

$\mathbb{N}$ is nearly a group, but not quite. You can do nothing with it (add zero or times by one), but you can't undo (subtract or divide) because that would take you out of $\mathbb{N}$ (into $\mathbb{Z}$ or $\\mathbb{Q}^+$).  But that's OK because $\mathbb{Z}$ and $\mathbb{Q}^+$ both are groups, with the powers of addition and multiplication respectively. 

Equipping a set with an operation makes it possible to view that set in many different lights.  Algebra is really fun because it teaches you to see how things are shaped by their possible interactions (if you choose to accept some abstraction).  Anyway, the upshot of all this is that a set looks extremely different depending on what powers you're studying within it. Since numbers is sets, then numbers look differently depending on whether you're adding them or multiplying them. Let's take a closer look that.

(sections:algebra:additive)=
## Additive Numbers

Let's play a game. You get given a calculator that only adds and a starting number $s$. If you type in $a$ and $b$, you get back $a+b$. You can only use the starting number $s$ or a number that you got out in a previous go. But you can re-use every number as much as you want. 

My goal is to ask you a number that you cannot write on your calculator. So if your starting number is $0$, you're screwed because I can just ask for $3$ and you'll be stuck doing $0+0=0$ forever. But if you start on $1$, then can do $1+1=2$ and then $1+2=3$. Trying again, starting on $2$ would only get you even numbers. 

Play it here!

Clearly, $1$ is a great number to start with because by doing $1+1+1+...$ you can get to all the numbers. The jargon for this is that $1$ generates $\mathbb{N}$ under addition which just means adding $1$ gives you everything. On the one hand, that's great news because it means you can always win the calculator game. But on the other hand, its almost disappointgly boring. Like if you imagine playing the number line like a musical instrument, then addition is like ambsent-mindedly dragging your hand across an infinite Piano forever. 

## Multiplicative Numbers

Let's play the calculator game again but this time with multiplication. So starting with $0$ still sucks because you're doing $0\times0=0$ forever. $1$ also sucks because $1\times1=1$. $2$ is a bit more useful because you get $4$ and then $8$ and so on. Notice how we missed $6$, meaning $2$ was actually more useful additively. In fact, there's no number that's more useful multiplicatively than it is additively. Nor is there any single number that can multiplicatively get you to every other number. 

The next thing to try is getting several numbers together to start with. Because if you start with $2$ and $3$ you still get $\{4,8,...\} \cup \{3, 9, ...\}$ but now you also get $\{6, 12, ...\}$. Better but youre still missing $\{5, 7, 10, ...\}$. You could try choosing a new bunch of starting numbers from the pile you're missing. But no matter what you pick next, there will always be more numbers you can't reach multiplicatively. Technically, you can get away with it by choosing an infinite number of starting numbers. Not in the boring/cheating sense of just choosing the whole of $\mathbb{N}$ for you starting numbers. But in the super-cool/maybe-kind-of-still-cheating sense of choosing $\{2, 3, 5, 7, 11, ...\}$: the *primes* [^primeref]. The primes is the bedrock of multiplicative numbers. You can tell primes is important because its been given a name with less than five syllables. 

You might recognise primes from drawing those diagrams in elementary school where you divided a number down like a tree until you couldn't continue. That game ends at the primes and is kind of like the calculator game backwards. I'm not going to draw any such diagrams because they look misleadingly similar to the way I'll be drawing productive numbers later on, even though their meaning is completely different so I don't want to confuse the person lazily skimming this section. 

The fact that addition only needed to add $1$, whilst multiplication requires an intricate tapestry of infinite primes to get anywhere may feel like an irritating complication. But as the sudden appearence of a visual metaphor may have suggested, there's also a very compelling aesthetic attraction towards towards it.

## Addiplicative Numbers

Last version of the game. I promise. 

Now you're allowed to use both addition, subtraction and multiplication. 

...

euclid ... gcd


[^primeref]: The reason for the primes being infinite is pretty much everyone's first favourite theorem. The idea is multiplying all your candidate primes then adding $1$ gives you a number you couldn't have added before.