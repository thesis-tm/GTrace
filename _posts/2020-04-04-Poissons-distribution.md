---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Poisson's distribution derivation"
date:   2020-10-25 23:41:54 +0000
categories: basic statistics
---
$\require{\AMSmath}$
$\require{\tikz}$

Poisson's distribution is a probability distribution used to simulate the probability (or possibility) of happening some (discrete) events. For example, probability of $x$ number of accidents in a city. It is important to understand that the event are discrete $i.e.$ either they happen or do not happen, there is no middle state. Thus, the events are counted in discrete numbers like $1, 2,..., n$. 


# Preliminaries
Before start introducing Poisson's distribution, we understand binomial distribution first, which is a probability distribution calculating successes of an event when it is tried for given number of times. For example, if we flip a coin ($n=$) 20 times, what is the probability that it will be head for let's say ($x$) 5 times. 

The standard expression for binomial distribution is, 
\begin{equation}
	P(X=x) = \frac{n!}{x!(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

where, $n$ is the total number of events and $p$ is the probability of success and $1-p$ automatically becomes the probability of failure (e.g. tails). 

So the above equation tells what would be the probability if there are total $n$ tosses, it will be head for $x$ times (and $n-x$ times would be tails).  


 
# Derivation of expression for Poisson's distriution
Now we come to the main part here. Poisson's distribution function is a probability distribution function which tells us the probability of successes when $n \rightarrow \infty$, while $p$ is relatively small. It is, in fact, a special case of Binomial distribution when total number of events are very very large.

What happens to the probability distribution when we have $n$ which is very large i.e. infinite and $p$ is very small ?

In other words we have,

\begin{equation}\label{Eq:1}
	P(X=x) = \lim_{n \to \infty}\frac{n!}{(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

We can calculate $p$ as,
\begin{equation\*}
	p = \frac{\lambda}{n}
\end{equation\*}

i.e. if we observe $n$ events (where $n$ is very large) and $\lambda$ are total successes, then probability of success is $\lambda/n$.

Hence we can rewrite Eq. \ref{Eq:1} as, 

\begin{equation}
	P(X=x) = \lim_{n \to \infty}\frac{n!}{x!(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}
\end{equation}

A little modification leads to,
\begin{equation\*}
	\begin{split}
		P(X=x) &= \bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{n!}{(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\
		&= \bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{n \times (n-1) \times...\times (n-x+1) \times (n-x)!}{(n-x)!} \bigg(\frac{\lambda}{n}\bigg)^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\
		&=\bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{(n-x)!}{n^k} \lambda^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
		&=\bigg(\frac{1}{x!}\bigg) \lim_{n \to \infty}\frac{(n-x)}{n} \frac{(n-x-1)}{n} \frac{(n-x-2)}{n} ... \frac{(n-x-x)}{n} \lambda^{x} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
		&=\bigg(\frac{\lambda^{x}}{x!}\bigg) \lim_{n \to \infty} \bigg(1-\frac{\lambda}{n}\bigg)^{n-x}\\	
	\end{split}
\end{equation\*}


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

The above equation is known as *Poisson*'s probability distribution function.


# Application
Let's take an example traffic light violations. Imagine we have data for one year for traffic light violations in a city. There are total $(n=) 1000$ light crossings in the city and there were total $(\lambda=)5.6$ violations daily or $560 \times 365$ violations for a year across all crossings. So we can calculate the probability distribution for violations at a given traffic light using Poisson's distribution, as shown in Figure \ref{Fig:2}. Alternately, we can also calculate the distribution of violations across the traffic lights in the city as shown in \ref{Fig:3}, by simply multiplying the probability by total number of traffic lights.

\begin{figure}
	\centering
<script type="text/tikz">
\begin{tikzpicture}
{% raw %}
\def\DimScale#1{\pgfmathparse{#1}\pgfmathprintnumberto[precision=2]{\pgfmathresult}{\roundednumber} \roundednumber}
\draw [->, ultra thick] (0,0) -- (15,0);
\draw [->, ultra thick] (0,0) -- (0,5);
\foreach \y [count=\x from 1] in {0.004,
 0.021,
 0.058,
 0.108,
 0.152,
 0.17,
 0.158,
 0.127,
 0.089,
 0.055,
 0.031,
 0.016,
 0.007,
 0.003,
 0.001} {
\fill[](\x,\y*10) circle (1mm);
\draw[-](\x,0) -- (\x,\y*10)node[label=\y]{};
}
\foreach \x in {0,1,...,15}{
\draw[-] (\x, -0.1) -- (\x, 0.1) node[label=below:\x]{};
}
\foreach \y in {0,0.1,...,0.5}{
\draw[-] (-0.1, \y\*10) -- (+0.1, \y\*10) node[label=left:\DimScale{\y}]{};
}
{% endraw %}
\end{tikzpicture}
</script>
\caption{Distribution of number of traffic light violations}
\label{Fig:3}
\end{figure}
