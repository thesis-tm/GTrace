---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Poisson's distribution derivation"
date:   2020-10-25 23:41:54 +0000
categories: github jekyll
---

Poisson's distribution is a probability distribution used to simulate the probability (or possibility) of happening some (discrete) events. For example, probability of $x$ number of accidents in a city. It is important to understand that the event are discrete $i.e.$ either they happen or do not happen, there is no middle state. Thus, the events are counted in discrete numbers like $1, 2,..., n$. 


\section{Preliminaries}
Before start introducing Poisson's distribution, we understand binomial distribution first, which is a probability distribution calculating successes of an event when it is tried for given number of times. For example, if we flip a coin ($n=$) 20 times, what is the probability that it will be head for let's say ($x$) 5 times. 

The standard expression for binomial distribution is, 
\begin{equation}
	P(X=x) = \frac{n!}{x!(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

where, $n$ is the total number of events and $p$ is the probability of success and automatically $1-p$ becomes the probability of failure (e.g. tails). 

So the above equation tells what would be the probability if there are total $n$ tosses, it will be heads for $x$ times (and $n-x$ times would be tails).  

