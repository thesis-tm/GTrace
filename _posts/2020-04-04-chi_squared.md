---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Adding MathJax to a GitHub Pages Jekyll Blog"
date:   2016-08-21 23:41:54 +0000
categories: github jekyll
---

<link rel="stylesheet" type="text/css" href="https://tikzjax.com/v1/fonts.css">
<script src="https://tikzjax.com/v1/tikzjax.js"></script>

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

<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (1in);
  \end{tikzpicture}
</script>

\tikzset{declare function = {
cosf(\x) = cos(\x r);%
gamma(\x) =  array({1.772453851, 1, 0.886226925, 1, 1.329340388, 2, 3.32335097, 6, 11.6317284, 24, 52.34277778, 120, 287.8852778, 720, 1871.254306, 5040, 14034.40729, 40320}, \x-1);%
normf(\x,\m,\s) = (exp(-0.5*((\x-\m)/\s)^2))/(\s*sqrt(2*pi));%
chif(\x,\m) = ((\x^((\m/2)-1))*exp(-(\x/2)))/((2^(\m/2))*(gamma(\m)));% gamma is for \m/2
}
}


\title{Pearson's Chi-squared test}
\author{
Vijay Kumar \\
\href{mailto:vijay.kumar@hb.se}{vijay.kumar@hb.se}
}

\begin{document}
\maketitle
\linenumbers



\section{Pre-requisite}
We have learned previously that a variable $X_i$ following normal distribution with mean $\mu$ and variance $\sigma^2$ can be converted into standard normal distribution i.e. normal distribution with mean $0$ and variance $1$, using the following transformation, 

\begin{equation}
\frac{X_i-\mu}{\sigma} \sim \mathcal{N}(0,1)
\end{equation} 

As we know that all variables are not normally distributed. One of the interesting statistical result is that, a variable $X_i$ following any distribution (and we don't dare to know that, because we have many other things to do!), the distribution of the sample means of $Y_i$ always follow normal distribution. The sample means implies here that we observe some numbers for variable $X_i$, let's say, we observe the output of $X_i$ for 100 times and we we say that one sample contains $10$ numbers. Thus making $100$ observations of variables $X_i$, we create $10$ samples. So the distribution of the sample means (or averages) always follow some normal distribution. Nonetheless, there exists a relation among the parameters of the sample mean distribution original distribution as, the means of both distribution remain same, while the variance of the sample mean distribution gets scaled by a factor of $1/n$. This implies that if we have the population mean as $\mu$ and population variance as $\sigma^2$, then the mean of sample averages would $\mu$ while the variance would be $\sigma^2/n$.\\
Further, the sample mean distribution can be converted into standard normal distribution as,\\ 
\begin{equation}\label{eq:st_normal}
\frac{\bar{x}-\mu}{\sigma/\sqrt{n}} \sim \mathcal{N}(0,1)
\end{equation} 

Figure \ref{fig:normal_curves}(b) shows the distributions of means for varying number of sample size collected from a distribution $\mathcal{N}(3,4)$ shown in Figure \ref{fig:normal_curves}(a). Further Figure \ref{fig:normal_curves}(c) shows the conversion of curves shown in Figure \ref{fig:normal_curves}(b) into the standard normal distribution using Eq. \ref{eq:st_normal}. 

The curves presented Figure \ref{fig:normal_curves} shows us the probability distribution. For example, what is the probability that the number generated 

\begin{figure}
\centering
\subfigure[]{
\begin{tikzpicture}
\def\XMIN{-10}
\def\XMAX{10}
\def\NSAMP{100}
\datavisualization
[scientific axes=clean, visualize as smooth line, 
x axis={length=6cm, ticks=few},
y axis={length=4cm, ticks=few},
visualize as line/.list={norm1, norm2, norm3},
legend=right,
norm1={label in legend={text={$\mathcal{N}(0,1)$}}},
norm2={label in legend={text={$\mathcal{N}(0,4)$}}},
norm3={label in legend={text={$\mathcal{N}(3,4)$}}},
style sheet=vary hue
]
data [set=norm1, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 0, 1);
}
data [set=norm2, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 0, 2);
}
data [set=norm3, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 3, 2);
};
\end{tikzpicture}
}
\subfigure[]{
\begin{tikzpicture}
\def\XMIN{-10}
\def\XMAX{10}
\def\NSAMP{100}
\datavisualization
[scientific axes=clean, visualize as smooth line, 
x axis={length=6cm, ticks=few},
y axis={length=4cm, ticks=few},
visualize as line/.list={norm31, norm32, norm33},
legend=right,
norm31={label in legend={text={$\bar{x}$ for $n=5$}}},
norm32={label in legend={text={$\bar{x}$ for $n=10$}}},
norm33={label in legend={text={$\bar{x}$ for $n=20$}}},
style sheet=vary hue
]
data [set=norm31, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 3, 3/sqrt(5));
}
data [set=norm32, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 3, 3/sqrt(10));
}
data [set=norm33, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 3, 3/sqrt(20));
};
\end{tikzpicture}
}
\subfigure[]{
\begin{tikzpicture}
\def\XMIN{-10}
\def\XMAX{10}
\def\NSAMP{100}
\datavisualization
[scientific axes=clean, visualize as smooth line, 
x axis={length=6cm, ticks=few},
y axis={length=4cm, ticks=few},
visualize as line/.list={norm01},
legend=right,
norm01={label in legend={text={$\mathcal{N}(0,1)$}}},
style sheet=vary hue
]
data [set=norm01, format=function] {
var x : interval [\XMIN:\XMAX] samples \NSAMP;
func y = normf(\value x, 0, 1);
};
\end{tikzpicture}
}
\caption{(a) Normal distribution with varying mean and variance, (b) sampling distribution for $\mathcal{N}(3,4)$ for varying sample-size ($n$) and (c) standard normal distribution calculated using Eq. \ref{eq:st_normal}}
\label{fig:normal_curves}
\end{figure}


\section{$\chi^2$ or Chi-squared distribution}
Let's consider $Z_i \sim \mathcal{N}(0,1)$. $\chi^2$ distribution is nothing but the distribution of $Z_i^2$. A normal distribution can be calculated for a negative number, but since $\chi^2$ is calculated by squaring, it always take positive number. 
In general form, we write, \\
\begin{equation}
Z_1^2 + Z_2^2+...+Z_n^2  \sim \chi^2_n 
\end{equation}


<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (1in);
  \end{tikzpicture}
</script>

where $n$ is known as the degree of freedom. 

In simple words, $\chi^2$ distribution is the distribution followed by a square of variable which follows the normal distribution. Further, how many such variables are added tells how much is the degree of freedom of a $\chi^2$ distribution.



\begin{figure}
\begin{tikzpicture}[scale=2]
\def\XMIN{0}, \def\XMAX{10}, \def\NSAMP{50},
\datavisualization
[scientific axes=clean, 
visualize as line/.list={df1, df2, df4, df8},
legend=above,
df1=	{label in legend={text=$1$}},
df2=	{label in legend={text=$2$}},
df4=	{label in legend={text=$4$}},
df8=	{label in legend={text=$8$}},
style sheet=vary hue,
x axis={label=$x$},
y axis={label=$f(x)$, max value=0.5}
]
data [set=df1, format=function] {
var x : interval[0.4:10] samples \NSAMP;
func y = chif(\value x, 1);
}
data [set=df2, format=function] {
var x : interval[\XMIN:\XMAX] samples \NSAMP;
func y = chif(\value x, 2);
}
data [set=df4, format=function] {
var x : interval[\XMIN:\XMAX] samples \NSAMP;
func y = chif(\value x, 4);
}
data [set=df8, format=function] {
var x : interval[\XMIN:\XMAX] samples \NSAMP;
func y = chif(\value x, 8) ;
};
\end{tikzpicture}
\caption{$\chi^2$ distribution for different degrees-of-freedom.}
\label{fig:chi2f}
\end{figure}





\section{Persson's $\chi^2$ test of independence}
The Persson's $\chi^2$ test of independence (or simply $\chi^2$ test)is conducted quite often to compare the categorical sets of data and check if they belong to the same population. 

The person's $\chi^2$ test states that, 

\begin{equation}\label{eq:1}
\sum_{i=1}^k \frac{(O_i-E_i)^2}{E_i} \sim \chi^2_{k-a}
\end{equation}

where $O_i$ is the observed frequency and $E_i$ is the expected frequency. \\
if the observed values and expected values belong to the same population, then the operation mentioned in Eq. \ref{eq:1} convert those observed and expected frequencies into a $\chi^2$ distribution with $k-1$ degree-of-freedom. 

Maybe the above-mentioned is not that easy to grasp.\\ 


Let's understand the $\chi^2$ test with an example. Let's consider that there is an e-commerce website which sells kids clothing. On a regular day, the website receives $10 000$ unique visitors on an average, among which, $30\%$ make atleast one purchase. Now the website implemented a new payment system, which is considered more secure. Now the website manager wants to check if the the new payment system has an impact on purchasing. \\
The very next day, the website receives $9024$ unique visitors and, out of that, $3125$ visitor i.e. $34.54\%$ make purchase of atleast one product. Now the question remains, is $34.54\%$ different from $30\%$ ?  \\

In this case, we take know that historical average $30\%$, if there is no impact of new payment system, the expected number of people making purchase would be $0.30\times9024 = 2707$, while people not making purchase would be $5899$. \\


We summarize the above-mentioned information in Table \ref{table:1}.

\begin{table}
\centering
\begin{tabular}{|r|r|r|}
\hline
 	& purchased (1)	& not purchased (2)\\
\hline
$E_i$	& $0.30\times9024 = 2707$	& $9024-2707 = 6317$ \\
\hline
$O_i$	& $3125$	& $5899$\\
\hline
\end{tabular}
\caption{Contingency table}
\label{table:1}
\end{table}

As we know that if the expected and observed frequencies are coming from same population, they must follow the $\chi^2$ distribution. Therefore, using Eq. \ref{eq:1}, we calculate the $\chi^2$ statistic and then using the $\chi^2$-distribution, we check how probable is that the gather data belong (i.e. observed data) to same population (i.e. expected data). In this context, we fist calculate the $\chi^2$ statistic from Table \ref{table:1} using Eq. \ref{eq:1} as shown below, 

\begin{equation}
\chi^2 = \frac{(3125-2707)^2}{2707} + \frac{(5899-6317)^2}{6317} = 92.20
\end{equation}

Now we calculate that what is the probability that the data (i.e. observed and expected both) belong to the same population using the $\chi^2$ distribution. To confirm the calculated $\chi^2$ statistic belongs to what significance level for given degree-of-freedom of $df$ (i.e. $df= k-1$  and in the above case $k=2$ so $df = 1$), we need to do some reverse calculations. 


Now we check the $\chi^2_1$ statistic against the critical $\chi^2_1$ value for a given statistical significance level (or p-value, which is 1-significance level). In general the  

\subsection{General procedure}
Let's imagine we have k-categories with given probability distribution and observed values for each class. 


 

\section{Derivation}
\subsection{Distribution}
The categorical data, in general, can be produced by multinomial distribution function. Multinomial distribution function can be understood as a function which tells the probability of how the categorical data. For example, imaging we have a bag of infinite number (a very large number) of red, blue and black coloured balls. Overall, 50\% of all balls are red, 30\% are green and 20\% are blue. Now if you are given a chance to grab 7 balls, what is the probability that it will be 2 black balls, 1 red balls and 4 green balls?

This type of probability is calculated by the multinomial distribution, which is expressed below, \\
\begin{equation}\label{eq:multinomail}
P(X_1=x_1, X_2=x_2,...,X_k=x_k) = \frac{n!}{x_1!x_2!...x_k!}p_1^{x_1}p_2^{x_2}...p_k^{x_k}
\end{equation} 


where, $X_i$ is the $i$th category, $x_i$ is the number of items in category $X_i$, and $p_i$ is the probability or proportion of the $i$th category in the population, $k$ is the number of categories.

When $k=2$ and $n=1$, this is called Bernoulli distribution. When $k=2$ and $n>1$, this is called Binomial distribution. When $k>2$ and $n>1$, this is called Multinomial distribution.  

So going back to the example, we have three colours in our population i.e. three categories namely red, green, and black which are in proportion (i.e. 
$p_i$) of $0.5$, $0.3$ and $0.2$ respectively. 
Now we can to calculate the probability that when $n=7$ i.e. when 7 balls were drawn from the population, what is the probability that $X_1=1, X_2=4, x_3=2$. 
Therefore using Eq. \ref{eq:multinomail} we have the following,\\
\begin{equation}
\begin{split}
P(X_1=1, X_2=4,X_3=2) &= \frac{7!}{1!4!2!}\times 0.5^{1}0.3^{4}0.2^{2} \\
&=\frac{720}{1\times 24 \times 2} \times 0.5 \times 0.0081 \times 0.04 \\
&= 0.00243
\end{split}
\end{equation}

\subsection{Derivation}

Let's take an example of Binomial distribution i.e. $k=2$ and $n>1$. In this case, we have the formulation as, 

\begin{equation}
P(X_1=x_1, X_2=x_2) = \frac{n!}{x_1!x_2!}p_1^{x_1}p_2^{x_2}
\end{equation} 
We can simply write it as, $x_1=x$, $x_2=n-x_1$, $p_1=p$, $p_2=1-p$.

\begin{equation}
P(X_1=x, X_2=n-x)=P(x) = \frac{n!}{x!(n-x)!}p^{x}(1-p)^{n-x}
\end{equation} 


For such distribution, we can easily calculate the mean as 
\begin{equation}
\mathbb{E}(X)=\mu=np
\end{equation}

Similarly the variance can be calculated as, 

\begin{equation}
\begin{split}
\text{Var}(X) &= \mathbb{E}(X-\mathbb{E}(X))^2\\
&= \mathbb{E}(X^2)+\mathbb{E}(\mathbb{E}(X))^2 - 2\mathbb{E}(X)\mathbb{E}(X)\\
&=\mathbb{E}(X^2)+ \mu^2-2\mu\mu \\
&=\mathbb{E}(X^2)- \mu^2 \\
&= np(1-p)
\end{split}
\end{equation}

We can convert the binomial distribution into standard normal distribution using Eq. \ref{eq:st_normal},\\

\begin{equation}
\chi = \frac{(X-np)}{\sqrt{np(1-p)}}
\end{equation}

\begin{equation}
\chi^2 = \frac{(X-np)^2}{np(1-p)}
\end{equation}
Since $n = np + n(1-p)$, and $n = \mu+n-\mu$

\begin{equation}
\begin{split}
\chi^2 &= \frac{(X-np)^2}{np} + \frac{(n-X-n(1-p))^2}{n(1-p)}\\
&=  \frac{(X-np)^2}{np} + \frac{((n-X)-n(1-p))^2}{n(1-p)}
\end{split}
\end{equation}

\begin{equation}
\chi^2 = \sum_{i=1}^2\frac{(O_i-E_i)^2}{E_i}
\end{equation}

where $O_1$ observed values in class $1$, $O_2$ is the observed values in  class $2$. $E_i$ is the expected values for class $1$ and $E_2$ is the observed value for class $2$.

\end{document}
