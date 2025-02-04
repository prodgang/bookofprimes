# Numbers


Everyone knows what numbers are. County things. But what does that really mean?

## Peano Arithmetic 

A lot of maths is about taking a very obvious concept and giving it a meticulous definition. This process is called \textit{axiomitazation}. Naturally, mathematicians have spent quite a lot of time axiomiatizing numbers. 

Numbers are so fundamental that you can't really define them in terms of anything else. So you basically have to start from nothing. Conveniently, nothing is itself a number: \textit{zero}. So the first stage of axiomitazing numbers is to simply demand that zero is a number. Symbolically,

\begin{equation}
    0 \in \NN \tag{PA0}
\end{equation} 	

OK great. We have our first number. The next stage of axiomiatizing numbers is to come up with a way of making old numbers from new numbers. The idea is to have a function that takes a number $n$ to the ``next'' number. This is called the successor function, written $S(n)$. You can think of the successor function as adding one, but technically we are yet to define what one is and so aren't allowed to call it that yet. Instead, we can now say that $S(0)$ is number and that this is the \textit{definition} of one. Then we can get $S(S(0))$ and call it two. And so on and so on and so on. In summary, if $n$ is a number, then so is $S(n)$. Symbolically, this is:

\begin{equation}
    n \in \NN \implies S(n) \in \NN \tag{PA1}
\end{equation}



Intuively, we think of numbers arranging themselves on a line that stretches out foreover. We know this line continues forever because we know we can always just add one more to it. We need to make sure that $S$ behaves in the same way so that it never produces an old number and makes numbers go in circles. A concise way of expressing this is that different numbers have different successors. Symbollically,

\begin{equation}
    n \neq m \implies S(n) \neq S(m) \tag{PA2}
\end{equation}

That just about completes our definition of numbers. All we need now is something to do with them. Let's try addition. Take a moment to think about what adding really means and try to find a way of expressing it using only $0$ and $S$. Once upon a time, some dude called Peano did exactly this and ended up coming up with following two conditions. Actually, there's some disagreement about whether it was Peano or some other dude called Dedekin. But who cares - they're both dead now anyway. What lives on are the following two equations:

\begin{equation}\label{eq:PA3}
    0 + m = m \tag{PA3}
\end{equation}

\begin{equation}\label{eq:PA4}
    S(n) + m = S(n+m) \tag{PA4}
\end{equation}

The equation \ref{eq:PA3} shouldn't come as much of a surprise. The second equation \ref{eq:PA4}, is a little weirder. Doesn't using $+$ on both sides of the equals sign mean we're defining addition in terms of itself? Well yes, but also no. We are defining addition in terms of itself, but also in such a way that if you keep applying \ref{eq:PA4}, you'll eventually hit rock bottom. That's where \eqref{eq:PA3} comes in. Such symbolic witchcraft is called \textit{recursion}. Let's see it in action as we prove our first theorem!

\begin{theorem}
    $1 + 1 = 2$
\end{theorem} 

\begin{proof}
    
    Remember that we defined $1$ as $S(0)$. So we start with $$S(0) + S(0)$$
    
    Now set $n = 0$ and $m = S(0)$, so that we can apply \eqref{eq:PA4} and get: $$S(0) + S(0) \stackrel{\eqref{eq:PA4}}{=} S(0 + S(0))$$
    
    Now we can apply \eqref{eq:PA3} to get: $$S(0 + S(0)) \stackrel{\eqref{eq:PA3}}{=} S(S(0))$$
    
    But $S(S(0))$ is the definition of $2$, so we're done!

    
\end{proof}


You'll have to trust me that wasn't as much a waste of time as it may have felt. While proving things directly with these axioms is rather tedious, the important thing is that we are able to do so having started with effectively nothing. The logic game is all about maximizing the bang for your axiomatic buck, and there really is quite a lot of bang with Peano arithmetic. Not only can you do any sum you like, but you can also go on to define multiplication with just two equations (one for zero, one for everything else just like before) and much more. 

To be able to prove slightly more interesting facts about numbers, we do need one last axiom called \textit{induction}. Actually, its a placeholder for infinitely many different axioms but don't worry too much about that. The idea behind induction is that if every number inherits some property from its predecessor, then every number will posess that property. Imagine there was some family curse that couldn't be cured and was eternally passed down by the sucessor function. Then every number would be cursed. Symbolically, this is written as 

\begin{equation}
    \phi(0) \land (\forall x, \phi(x) \implies \phi(S(x))) \implies \forall n, \phi(n) \tag{PA5}
\end{equation}

$\phi(n)$ is a placeholder for the curse/property we're interested in. Let's see induction in action with another quick theorem, $n + 0 = n$. Don't be fooled into thinking this could be immediately proven with \eqref{eq:PA3} because doing so would assume $n + m = m + n$, which we are yet to prove (but could also be done with induction in case you want to try).

\begin{theorem}
    $n + 0 = n$
\end{theorem}

\begin{proof}
    We are setting $\phi(n)$ to be the statement $n + 0 = n$. To use induction, we need to prove it seperately for $0$ and then for everything else. The $0$ case really is just \eqref{eq:PA3}: $0 + 0 = 0$.
    
    The remaining case is more interesting. We can assume that $x + 0 = x$. Now we must show $S(x) + 0$.  By \eqref{eq:PA4}, $S(x) + 0 = S(x+0)$. Now using our assumption $S(x + 0) = S(x)$, so we are done.
    
\end{proof}

If you want to learn more about Peano Arithmetic, I recommend playing the natural numbers game. It's where I learnt about all this and enjoyed it a lot. 

Before ending on too positive of a note, I want to trash talk the Peano axioms a bit. From a logical point of view, its great news that we have condensed so many numbers into so few rules. But don't you feel a small nagging sense of sadness to watch the weird and wonderful world of numbers being so coldly reduced into an endless sucession of symbolic successors? Well, I certainly do. That's why I present to you my solution: a slightly more complicated set of mechanical manipulations that take numbers back to their roots. But you'll have to be patient. We're not even halfway through this rambling introduction.


    


		
		
	
### Number Bases