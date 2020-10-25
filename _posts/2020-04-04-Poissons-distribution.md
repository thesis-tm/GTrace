---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Poisson's distribution derivation"
date:   2020-10-25 23:41:54 +0000
categories: basic statistics
---

Poisson's distribution is a probability distribution used to simulate the probability (or possibility) of happening some (discrete) events. For example, probability of $x$ number of accidents in a city. It is important to understand that the event are discrete $i.e.$ either they happen or do not happen, there is no middle state. Thus, the events are counted in discrete numbers like $1, 2,..., n$. 


# Preliminaries
Before start introducing Poisson's distribution, we understand binomial distribution first, which is a probability distribution calculating successes of an event when it is tried for given number of times. For example, if we flip a coin ($n=$) 20 times, what is the probability that it will be head for let's say ($x$) 5 times. 

The standard expression for binomial distribution is, 
\begin{equation}
	P(X=x) = \frac{n!}{x!(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

where, $n$ is the total number of events and $p$ is the probability of success and automatically $1-p$ becomes the probability of failure (e.g. tails). 

So the above equation tells what would be the probability if there are total $n$ tosses, it will be heads for $x$ times (and $n-x$ times would be tails).  


 
# Derivation of expression for Poisson's distriution
Now we come to the main part here. Poisson's distribution function is a probability distribution function which tells us the probability of successes when $n \rightarrow \infty$, while $p$ is relatively small. It is, in fact, a special case of Binomial distribution when total number of events are very very large.

What happens to the probability distribution when we have $n$ which is very large i.e. infinite and $p$ is very small ?

In other words we have,

\begin{equation}\label{Eq:1}
	P(X=x) = \lim_{n \to \infty}\frac{n!}{(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

We can calculate $p$ as,
\begin{equation*}
	p = \frac{\lambda}{n}
\end{equation*}

i.e. if we observe $n$ events (where $n$ is very large) and $\lambda$ are total successes, then probability of success is $\lambda/n$.

Hence we can rewrite Eq. \ref{Eq:1} as, 

\begin{equation}
	P(X=x) = \lim_{n \to \infty}\frac{n!}{x!(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}
\end{equation}

A little modification leads to,
\begin{equation*}
	\begin{split}
		P(X=x) &= \bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{n!}{(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\
		&= \bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{n \times (n-1) \times...\times (n-x+1) \times (n-x)!}{(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\
		&=\bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{(n-x)!}{n^k} \lambda^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
		&=\bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{(n-x)}{n} \frac{(n-x-1)}{n} \frac{(n-x-2)}{n} ... \frac{(n-x-x)}{n} \lambda^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
		&=\bigg(\frac{\lambda^{x}}{x!}\bigg) \lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
	\end{split}
\end{equation*}


In the above equation $\frac{(n-x)}{n}=\frac{(n-x-1)}{n}=\frac{(n-x-2)}{n} =...=\frac{(n-x-x)}{n} = 1$ when $n \rightarrow \infty$ or $n>>x$.

Further we have, 
$$\lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x} = \lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n} \bigg(1-\frac{\lambda}{n}\bigg)^{-x} = \lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n} $$

In the above equation we have, $\lim_{n \to \infty}  \bigg(1-\frac{\lambda}{n}\bigg)^{-x} = 1$ because $\frac{\lambda}{n} <<1$ when $n \rightarrow \infty$. 

Further, $\lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n} = \lim_{n \to \infty} \bigg(1-\frac{1}{z}\bigg)^{-z\lambda} = e^{-\lambda}$, where $z=\frac{n}{\lambda}$, and $\bigg(1-\frac{1}{z}\bigg)^{z} = e$.

Thus, finally we have, 
\begin{equation}
	\begin{split}
		P(X=x) &=\frac{e^{-\lambda}\lambda^{x}}{x!}
	\end{split}
\end{equation}

The above equation is known as \textit{Poisson}'s probability distribution function.



