---
layout: post
title: Some properties of normal distribution
mathjax: true
tikz: yes
comments: true  
categories: methods, statistics, proofs, normal distribution, distribution
---
$\require{\AMSmath}$ 
<div style="display:none">
\( \newtheorem{theorem}{Theorem} \)
<\div>

# Notation
This section mainly focuses on defining formal notations that will be used in the later sections.


A normal distribution function can be written as, 

\begin{equation} \label{eq:normpdf}
	f(x) = \frac{1}{\sqrt{2\pi} \sigma} e^{-\frac{1}{2} \big(\frac{x-\mu}{\sigma}\big)^2}
\end{equation}

where $f(x)$ represents the probability density function, in short this tells us how the probability is distributed for different values of x. $\mu$ represents the mean value of the distribution and $\sigma^2$ is the variance which tells how the narrow or broad the distribution is.

In short we can represent a variable which has possible values following normal distribution as,

\begin{equation}
	X \sim \mathcal{N} (\mu, \sigma^2)
\end{equation}

The above equation tells that the value of $X$ follows a normal distribution with mean $\mu$ and variance $\sigma^2$.

# Moment generating function

Moment generating functions are used to calculate the expected value of random variables. WE define moment generating function as,

\begin{equation} \label{eq:mgf}
	M_X (t) = \mathbb{E}[e^{Xt}]
\end{equation}
Where $\mathbb{E}$ known as expectation which represents the average value of variable inside the square bracket.


So for normal distribution we have, 
\begin{equation}
	M_X (t) = \mathbb{E}[e^{Xt}] = \int_{-\infty}^{+\infty} e^{xt} f_X(x) dx  = \int_{-\infty}^{+\infty} e^{xt} \frac{1}{\sqrt{2\pi} \sigma} e^{-\frac{1}{2} \big(\frac{x-\mu}{\sigma}\big)^2} dx  
\end{equation}


Let's define $z = \frac{x-\mu}{\sigma}$, we have $dx =  \sigma dz $

\begin{equation}
	M_X (t) =  \int_{-\infty}^{+\infty} e^{(z \sigma + \mu)t} \frac{1}{\sqrt{2\pi} \sigma} e^{-\frac{1}{2} z^2} \sigma dz = \int_{-\infty}^{+\infty} e^{z \sigma t} e^{\mu t} \frac{1}{\sqrt{2\pi} } e^{-\frac{1}{2} z^2}  dz
\end{equation}

\begin{equation}
	M_X (t) =   e^{\mu t} \int_{-\infty}^{+\infty} e^{z \sigma t} \frac{1}{\sqrt{2\pi} } e^{-\frac{1}{2} z^2} dz = e^{\mu t}  \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi} } e^{z \sigma t -\frac{1}{2} z^2 } dz 
\end{equation}

We can write the above equation as, 

\begin{equation}
	e^{z \sigma t -\frac{1}{2} z^2 } = e^{z \sigma t -\frac{1}{2} z^2 -\frac{1}{2}t^2\sigma^2 + \frac{1}{2}t^2 \sigma^2} = e^{z \sigma t -\frac{1}{2} z^2 + \frac{1}{2}t^2\sigma^2} e^{-t^2 \sigma^2} = e^{z \sigma t -\frac{1}{2} z^2 - \frac{1}{2}t^2 \sigma^2} e^{+\frac{1}{2}t^2 \sigma^2}
\end{equation}


\begin{equation}
	\Rightarrow e^{-\frac{1}{2}(-z\sigma t + z^2 + t^2\sigma^2)} e^{\frac{1}{2}t^2\sigma^2 } = e^{-\frac{1}{2}(z- t\sigma)^2} e^{\frac{1}{2}t^2\sigma^2 } 
\end{equation}
Thus we write moment generating function as, 

\begin{equation}
	M_X (t) =   e^{\mu t} \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi} } e^{-\frac{1}{2}(z- t\sigma)^2} e^{\frac{1}{2}t^2\sigma^2 }  dz = e^{\mu t} e^{-\frac{1}{2}t^2\sigma^2 } \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi} } e^{\frac{1}{2}(z- t\sigma)^2} dz
\end{equation}

In the above equation we have, 

\begin{equation}
	\int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi} } e^{-\frac{1}{2}(z- t\sigma)^2} dz = \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi} } e^{-\frac{1}{2}(z- u)^2} dz = 1
\end{equation}
since it is a normal distribution, where $u = t\sigma$ 


Finally we have the moment generating function of a normal distribution of mean $\mu$ and variance $\sigma^2$ as, 
\begin{equation} \label{eq:mgf}
	M_X (t) = e^{\mu t} e^{\frac{1}{2}t^2\sigma^2 } 
\end{equation}



Further we can expand Eq. \ref{eq:mgf} as,


\begin{eqnarray} 
	M_X (t) = \mathbb{E}[e^{Xt}] &=& \mathbb{E} \bigg[1 + \frac{Xt}{1!} + \frac{X^2t^2}{2!} + \frac{X^3t^2}{3!}+ ...\bigg] \nonumber \\
	&=& \mathbb{E}\bigg[\Sigma_0^\infty \frac{X^kt^k}{k!} \bigg] \nonumber \\
	&=& \mathbb{E}[X^k] \Sigma_0^\infty \frac{t^k}{k!} 
\end{eqnarray}

Further taking $k$th derivative of the above equation as, 

\begin{eqnarray} 
	 \mathbb{E}[X^k] \frac{d^k}{dt^k} \Sigma_0^\infty \frac{t^k}{k!} = \frac{d^k}{dt^k} M_X (t) 
\end{eqnarray}

Since we know that $ \frac{d^k}{dt^k} \Sigma_0^\infty \frac{t^k}{k!} = 1$. 
So we calculate the $k$th moment of the variable by , 

\begin{eqnarray} \label{eq:expect}
	\mathbb{E}[X^k]  = \frac{d^k}{dt^k} M_X (t) |_{t=0}
\end{eqnarray}



## First moment
We can calculate the first moment by placing $k=1$ in Eq. \ref{eq:expect}, as shown bellow, 

\begin{eqnarray} 
	\mathbb{E}[X]  &=& \frac{d^1}{dt^1} e^{\mu t} e^{\frac{1}{2}t^2\sigma^2 } |_{t=0} = e^{\frac{1}{2}t^2\sigma^2} \frac{d^1}{dt^1} e^{\mu t}|_{t=0} + e^{\mu t}  \frac{d^1}{dt^1} e^{\frac{1}{2}t^2\sigma^2} |_{t=0} 
	\label{eq:first_moment_equation} \\
	&=& e^{\frac{1}{2}t^2\sigma^2}  e^{\mu t} \mu t  \mu|_{t=0} +  e^{\mu t}  e^{\frac{1}{2}t^2\sigma^2} \frac{1}{2}t^2\sigma^2 t\sigma^2 |_{t=0} \nonumber \\
	&=& e^{-\frac{1}{2}t^2\sigma^2}  e^{\mu t} \mu|_{t=0} -  e^{\mu t}  e^{-\frac{1}{2}t^2\sigma^2} t\sigma^2 |_{t=0} \nonumber \\
	&=& \mu \label{eq:mean}
\end{eqnarray}


Thus the first moment is nothing but the mean value of distribution.


## Second moment
We can calculate the second moment by placing $k=2$ in Eq. \ref{eq:expect}, as shown bellow, 


\begin{eqnarray} 
	\mathbb{E}[X^2] &=& \frac{d^2}{dt^2} M_X (t) |_{t=0} \nonumber \\
	&=& \frac{d}{dt} \big(\frac{d}{dt} e^{\mu t} e^{\frac{1}{2}t^2\sigma^2 }\big) |_{t=0} \nonumber \\
	&=& \frac{d}{dt} \big( e^{\frac{1}{2}t^2\sigma^2} \frac{d}{dt} e^{\mu t} + e^{\mu t} \frac{d}{dt} e^{\frac{1}{2}t^2\sigma^2} \big) |_{t=0} \nonumber \\
	&=& \frac{d}{dt} \big( e^{\frac{1}{2}t^2\sigma^2}  e^{\mu t} \mu +  e^{\mu t}  e^{\frac{1}{2}t^2\sigma^2} t\sigma^2 \big) |_{t=0}
\end{eqnarray}

We solve it in parts as, 

\begin{eqnarray}
	\frac{d}{dt} \big( e^{\frac{1}{2}t^2\sigma^2}  e^{\mu t} \mu \big)|_{t=0} = \big( e^{\frac{1}{2}t^2\sigma^2} e^{\mu t} \mu^2 + e^{\mu t} \mu t \sigma^2 e^{\frac{1}{2}t^2\sigma^2} \big) |_{t=0} = \mu^2
\end{eqnarray}

Similarly we have,
\begin{eqnarray}
	\frac{d}{dt} \big( e^{\mu t}  e^{\frac{1}{2}t^2\sigma^2} t\sigma^2 \big) |_{t=0} = \sigma^2
\end{eqnarray}

Thus we write second moment as, 

\begin{eqnarray} 
	\mathbb{E}[X^2] &=&  \mu^2 + \sigma^2
\end{eqnarray}

Also, we can write variance or $\sigma^2$ as, 

\begin{eqnarray} \label{eq:sig_sq}
	\sigma^2 = \mathbb{E}[X^2] - \mu^2=  \mathbb{E}[X^2] - \mathbb{E}[X]^2
\end{eqnarray}


\begin{eqnarray} 
	\mathbb{E}[X^2] = \frac{d}{dt} \big(\frac{d}{dt} e^{\mu t} e^{-\frac{1}{2}t^2\sigma^2 }\big) |_{t=0}\\
\end{eqnarray}

Further, we can create calculate the $n$th moment of the distribution by $n$th differentiate of the moment generating function at $t=0$, 
\begin{equation}
	\mathbb{E}[X^n] = \frac{d^n}{dt^n} M_X (t) |_{t=0}  =\frac{d^n}{dt^n} e^{\mu t} e^{-\frac{1}{2}t^2\sigma^2 } |_{t=0}
\end{equation}


# Propositions

\begin{theorem}
If $X \sim \mathcal{N}(\mu_1, \sigma^2_X)$ and $Y \sim \mathcal{N}(\mu_2, \sigma^2_Y)$, then	$Z = X + Y \sim \mathcal{N}(\mu_X + \mu_X, \sigma^2_Y+ \sigma^2_Y)$, where $\mu_X$ and $\mu_X$ are the means and $\sigma^2_X$ and $\sigma^2_Y$ are the variance. 
\end{theorem}

\begin{proof}
	We write the moment generating functions variables $Z$ as in form of summation of $X$ and $Y$ in the following form.
	
	\begin{eqnarray}
		M_Z (t) = \mathbb{E}[e^{Zt}] = \mathbb{E}[e^{(X+Y)t}] = \mathbb{E}[e^{Xt}] \mathbb{E}[e^{Yt}]
	\end{eqnarray}
	
	
	Putting the value of respective moment generating function we have, 
	
	
	\begin{eqnarray}
		M_Z (t) = e^{\mu_X t} e^{-\frac{1}{2}t^2\sigma_X^2 } e^{\mu_Y t} e^{-\frac{1}{2}t^2\sigma_Y^2 } = e^{(\mu_X+\mu_Y)t} e^{-\frac{1}{2}t^2(\sigma_X^2+\sigma_Y^2) }
	\end{eqnarray}
	
	
	Thus comparing the above equation with Eq. \ref{eq:mgf} and Eq. \ref{eq:normpdf} we have the resulting distribution as (alternately mean and variance from the above moment function can be calculated to write the following normal distribution), 
	
	\begin{eqnarray}
		f_Z(x) = \frac{1}{\sqrt{2\pi (\sigma_X^2 + \sigma_Y^2)}} e^{-\frac{1}{2} \big(\frac{x-(\mu_X +\mu_Y)}{\sqrt{\sigma_X^2 + \sigma_Y^2}}\big)^2} 
	\end{eqnarray}
	
	
	Or we can write it as, 
	\begin{eqnarray}
		Z \sim \mathcal{N}(\mu_X + \mu_Y, \sigma_X^2 + \sigma_Y^2)
	\end{eqnarray}
\end{proof}
 






\begin{theorem}
If $a$ is a constant and $X$ follows a normal distribution i.e. $X \sim \mathcal{N}(\mu_X, \sigma_X^2)$, then $aX \sim \mathcal{N}(a\mu_X, a^2\sigma_X^2)$
\end{theorem}


\begin{proof}
For variable $Z$ which is $aX$ we have the moment generating function as, 
\begin{equation}
	\mathbb{E}[e^{Zt}] = \mathbb{E}[e^{aXt}]= \mathbb{E}[e^{X(at)}] = e^{\mu_X (at)} e^{-\frac{1}{2} (at)^2 \sigma_X^2} = e^{(a\mu_X)t} e^{-\frac{1}{2} t^2 (a\sigma_X)^2}
\end{equation}

Thus comparing the above equation with Eq. \ref{eq:mgf} and Eq. \ref{eq:normpdf} we have the resulting distribution as, 

\begin{equation}
	f_{Z}(x) = f_{aX}(x) = \frac{1}{\sqrt{2\pi} a\sigma_X} e^{-\frac{1}{2} \big(\frac{x-(a\mu_X)}{a\sigma_X}\big)^2}
\end{equation}

Thus, 
\begin{equation}
	Z = aX \sim \mathcal{N}(a\mu_X, a^2 \sigma_X^2) \nonumber
\end{equation}

\end{proof}


\begin{theorem}
If $a$ is a constant and $X$ follows a normal distribution i.e. $X \sim \mathcal{N}(\mu_X, \sigma_X^2)$, then $a+X \sim \mathcal{N}(a+\mu_X, \sigma_X^2)$
\end{theorem}


\begin{proof}
	
For variable $Z$ which is $a+X$, we have the moment generating function as, 
\begin{equation}
	\mathbb{E}[e^{Zt}] = \mathbb{E}[e^{(a+X)t}] =  \mathbb{E}[e^{at}] \mathbb{E}[e^{Xt}]= e^{at}\mathbb{E}[e^{Xt}] = e^{at} e^{\mu_X t} e^{-\frac{1}{2} t^2 \sigma_X^2} = e^{(a+\mu_X) t} e^{-\frac{1}{2} t^2 \sigma_X^2}
\end{equation}

Thus comparing the above equation with Eq. \ref{eq:mgf} and Eq. \ref{eq:normpdf} we have the resulting distribution as, 

\begin{equation}
	f_{Z}(x) = f_{a+X}(x) = \frac{1}{\sqrt{2\pi \sigma_X^2} } e^{-\frac{1}{2} \big(\frac{x-(a+\mu_X)}{\sigma_X}\big)^2}
\end{equation}

Thus, 
\begin{equation}
	Z = a+X \sim \mathcal{N}(a+\mu_X, \sigma_X^2)
\end{equation}

\end{proof}


\begin{theorem}
If $X$ follows normal distributions i.e. $X \sim \mathcal{N}(\mu_X, \sigma_X^2)$ then $\frac{X-\mu_X}{\sigma_X} \sim \mathcal{N}(0,1)$
\end{theorem}

\begin{proof}
	Let $Z = \frac{X-\mu_X}{\sigma_X} $, then, 
	\begin{eqnarray}
		M_Z(t) &=& \mathbb{E}[e^{Zt}] \nonumber \\ 
		&=& \mathbb{E}\bigg[e^{\frac{X-\mu_X}{\sigma_X}t} \bigg] \nonumber \\ 
		&=& \mathbb{E}\bigg[e^{\frac{X-\mu_X}{\sigma_X}t} \bigg] \nonumber \\
		&=& \mathbb{E}\bigg[e^{\frac{X}{\sigma_X}t} \bigg] \mathbb{E}\bigg[e^{\frac{-\mu_X}{\sigma_X}t} \bigg] \nonumber \\
		&=& e^{\frac{-\mu_X}{\sigma_X}t} \mathbb{E}\bigg[e^{\frac{X}{\sigma_X}t} \bigg]  \nonumber \\
		&=& e^{\frac{-\mu_X}{\sigma_X}t} \mathbb{E}\bigg[e^{\frac{X}{\sigma_X}t} \bigg]  \nonumber \\
	\end{eqnarray}


As we know that, if $k=\frac{1}{\sigma_X}$, then $kX \sim \mathcal{N}(k\mu_X, \sigma_X^2 k^2) = \mathcal{N}(\mu_X/\sigma_X, \sigma_X^2/\sigma_X^2) = \mathcal{N}(\mu_X/\sigma_X, 1) $

Thus we can write the above equation as, 

\begin{eqnarray}
	M_Z(t) &=& e^{\frac{-\mu_X}{\sigma_X}t} e^{\frac{\mu}{\sigma_X}t} e^{\frac{1}{2}t^2} \nonumber \\
	&=& e^{\frac{\mu}{\sigma_X}t - \frac{-\mu_X}{\sigma_X}t} e^{\frac{1}{2}t^2} \nonumber \\
	&=& e^{0t} e^{\frac{1}{2}t^2}
\end{eqnarray}

Thus comparing the above equation with Eq. \ref{eq:mgf} and Eq. \ref{eq:normpdf} we have the resulting distribution as, 

\begin{eqnarray}
	Z = \frac{X-\mu_X}{\sigma_X} \sim \mathcal{N} (0,1)
\end{eqnarray}


\end{proof}	

\end{document}
