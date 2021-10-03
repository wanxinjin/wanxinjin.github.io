---
layout: post
title: Safe Pontryagin Differentiable Programming
date: 2021-10-20 11:12:00-0400
description: an example of a blog post with some math
---




# Motivation
Safety is usually a  priority in the deployment of a learning and control algorithm to real-world systems. For a physical system (agent), safety is normally given in various states and inputs constraints, which must not be violated by the algorithm at _any stage_ of the learning and control process, otherwise will cause irrevocable or unacceptable failure/damage/loss. Those systems are  referred to as _safety-critical_. The constraints in  a safety-critical system can  include the _immediate_ ones, which are directly  imposed on  the system state and input  at certain/all time instances, and the _long-term_ ones, which are defined on the   trajectory of system states and inputs over a long time period. 
Compared to the abundant results that  focus on   system optimality,   systematic and principled treatments for safety-critical learning and control problems  seem largely insufficient, particularly in the following  gaps (see the related work section in the paper. First, existing safety strategies are either too conservative, which may restrict the  task performance, or violation-tolerable, which only pursues the near-constraint guarantee and thus are not strictly  constraint-respecting. Second, a generic safety paradigm capable  of handling different types of constraints, including system state and input (or mixed), immediate, or/and long-term constraints, is still lacked. Third,  some  existing safety strategies suffer from huge computational- and data- complexity,  difficult to be integrated into any differentiable programming frameworks to solve  large-scale  learning and continuous control tasks.




To address the above research gaps, this paper aims to develop a new theoretical and algorithmic framework for safe learning and control with the following  key  abilities.  

- First, the framework provides a systematic treatment for **different types of  constraints** in a safety-critical problem;
- second, it attains **provable safety- and optimality- guarantees** throughout the  learning and control process;
- third, it is flexible   to perform **safe learning of any unknown aspects of a safety-critical system**, including  policy, dynamics, state and input constraints, and control cost function;
- finally, it can be integrated into any **differentiable programming framework** to efficiently solve large-scale safe learning and control tasks.

-----







This theme supports rendering beautiful math in inline and display modes using [MathJax 3](https://www.mathjax.org/){:target="\_blank"} engine. You just need to surround your math expression with `$$`, like `$$ E = mc^2 $$`. If you leave it inside a paragraph, it will produce an inline expression, just like $$ E = mc^2 $$.

To use display mode, again surround your expression with `$$` and place it as a separate paragraph. Here is an example:

$$
\sum_{k=1}^\infty |\langle x, e_k \rangle|^2 \leq \|x\|^2
$$

You can also use `\begin{equation}...\end{equation}` instead of `$$` for display mode math.
MathJax will automatically number equations:

\begin{equation}
\label{eq:caushy-shwarz}
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
\end{equation}

and by adding `\label{...}` inside the equation environment, we can now refer to the equation using `\eqref`.

Note that MathJax 3 is [a major re-write of MathJax](https://docs.mathjax.org/en/latest/upgrading/whats-new-3.0.html){:target="\_blank"} that brought a significant improvement to the loading and rendering speed, which is now [on par with KaTeX](http://www.intmath.com/cg5/katex-mathjax-comparison.php){:target="\_blank"}.
