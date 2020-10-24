---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Poisson's distribution derivation"
date:   2020-10-25 23:41:54 +0000
categories: github jekyll
---

\documentclass[12pt]{article}
\usepackage{textcomp}
\usepackage{amsmath, amssymb}
\usepackage{rotating} 
\usepackage{hyperref}
\usepackage{tcolorbox}
\usepackage{pgfplots}
\usetikzlibrary{calc}
\usetikzlibrary{arrows.meta}
\usepackage{float}
\usepackage{subfigure}
\setlength\parindent{0pt}
\usetikzlibrary{positioning}
\usetikzlibrary{mindmap,trees}
\usetikzlibrary{calendar}
\usetikzlibrary{datavisualization}
\usetikzlibrary{datavisualization.formats.functions}
\usepackage{pgfmath}
\usepackage{lineno}
\usepackage{xargs}
\pgfplotsset{compat=1.16}


<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (1in);
  \end{tikzpicture}
</script>

\title{Poisson's distribution}
\author{
Vijay Kumar \\
\href{mailto:vijay.kumar@hb.se}{vijay.kumar@hb.se}
}


\begin{document}
	\maketitle
	\linenumbers
	
	
Poisson's distribution is a probability distribution used to simulate the probability (or possibility) of happening some (discrete) events. For example, probability of $x$ number of accidents in a city. It is important to understand that the event are discrete $i.e.$ either they happen or do not happen, there is no middle state. Thus the events are counted in discrete numbers like $1, 2,..., n$. 


\section{Preliminaries}
Before start introducing the Poisson's distribution, we understand binomial distribution first, which is a probability distribution calculating successes of an event when it is tried for given number of times. For example, if we flip a coin ($n=$) 20 times, what is the probability that it will be head for let's say ($x$) 5 times. 

The standard expression for binomial distribution is, 
\begin{equation}
	P(X=x) = \frac{n!}{x!(n-x)!} p^{x} (1-p)^{n-x}
\end{equation}

where, $n$ is the total number of events and $p$ is the probability of success and automatically $1-p$ becomes the probability of failure (e.g. tails). 

So the above equation tells what would be the probability if there are total $n$ tossesit will be heads for $x$ times (and $n-x$ times would be tails).  


\begin{figure}
	\begin{tikzpicture}
		\pgfmathsetmacro{\n}{10}
		\pgfmathsetmacro{\p}{0.5}
		\begin{axis}
			[
			xlabel={$x$},
			ylabel={$P(X=x)$},
			xmin=-0.5, xmax=10,
			ymin = 0
			]
			\addplot[ycomb, domain=0:10, samples at={0,1,...,10}, blue, mark=*]{factorial(\n) * (\p^x)*((1-\p)^(\n-x))/(factorial(x)*factorial(\n-x))};
		\end{axis}
	\end{tikzpicture}
\caption{Probability distribution of $x$ times an event-one to happen which has a probability of $0.1$, when total $20$ events happen.}
\label{Fig1}
\end{figure}

Figure \ref{Fig1} shows the probability distribution of heads (i.e. success) when it has an overall probability of $0.5$ (i.e. we know that randomly it will be half times heads and half times tails), and total $20$ events happen.


\section{Derivation}
Now we come to the main part here. Poisson's distribution function is a probability distribution function which tells us the probability of successes when $n \rightarrow \infty$, while $p$ is relatively small.
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


Let's take an example traffic light violation. Imagine we have a data for one year for a traffic light violation in a city. There are total $(n=) 1000$ light crossings in a city and there were total $(\lambda=)5.6$ violations daily or $560 \times 365$ violations in a year on all crossings. So we can calculate the probability distribution for traffic light violations from Poisson's distribution, as shown in Figure \ref{Fig:2}


\begin{figure}
<script type="text/tikz">
	\begin{tikzpicture}
		\pgfmathsetmacro{\p}{5.6}
		\begin{axis}
			[
			xlabel={$x$},
			ylabel={$P(X=x)$},
			xmin=-0.5, xmax=20,
			ymin = 0
			]
			\addplot[ycomb, domain=0:10, samples at={0,1,...,19}, blue, mark=*]{exp(-\p) * (\p^x)/(factorial(x)};
		\end{axis}
	\end{tikzpicture}
</script>
	\caption{Probability distribution for traffic light violations.}
	\label{Fig:2}
\end{figure}

\end{document}
