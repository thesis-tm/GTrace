---
layout: post
title: Normal distribution
mathjax: true
tikz: yes
comments: true  
categories: methods, normal distribution, derivation, proof
---

<div style="display:none">
\(
  \def\<#1>{\left<#1\right>}
  \newcommand{\ddx}[2]{\frac{#1}{#2}}
  \newcommand{\CC}{\mathbf{C}}
  \newcommand{\bld}[1]{\boldsymbol{#1}}
  \newcommand{\hbld}[1]{\hat{\boldsymbol{#1}}}
  \newcommand{\textbf}[1]{\mathbf{#1}}
  \newcommand{\textit}[1]{\mathit{#1}}
\)
</div>


# Introduction
Normal distribution function or normal probability distribution function (PDF) is probably the most common distribution used in statistics. It is a function of two parameters, known as mean $(\mu)$ and standard deviation $ (\sigma) $ or variance $(\sigma^2)$. Normal PDF is represented by $\mathcal{N}(\mu, \sigma^2)$.  Figure \ref{typical_normal_distribution} shows example of normal PDF for varying parameters. 


<script type="text/tikz">
\begin{tikzpicture}
\draw[-](-3.5,0)--(3.5,0);
\draw[-](0,0)--(0,0.5*10);
\foreach \x in {0.1,0.2,0.3,0.4}{
\draw[-](-0.1,\x*10)-- (0.1,\x*10) node[label=right:{\x}]{};
}
\foreach \x in {-3,-2,...,3}{
\draw[-](\x, -0.1)--(\x, 0.1)node[label=below:{\x}]{};
}
\draw[samples=70, color=red]plot(\x, {10*(1/(sqrt(2*pi*1))*exp(-(\x-0)^2/(2*1)))});
\end{tikzpicture}
</script>


![subcaption here](){typical_normal_distribution width=50%}

{% include image.html url="./dot.jpg" description="My cat, Robert Downey Jr." %}



# The concept of probability

Probability, in general, defines the possibility or chances of something to happen. For example, what is the probability that it will rain on a particular day in future. Probability varies between $0$ and $1$, where $0$ implies that there is perfectly no chances of something to happen and $1$ implies that something will happen definitely. And a probability between $0$ and $1$ tells the changes of something to happen.

Imagine that we are playing a game of darts. The aim is to throw the dart that lands on the centre of the board, which is represented by $x-y$ coordinate $(0,0)$. As we are not expert in throwing the dart, after many tries, we got trained to throw the dart which lands near to the centre of the board. Here, near implies that sometimes the dart lands on left and sometimes right of the centre. Similarly sometimes the darts falls on below the centre position and sometimes above of the centre position. Of course, in few cases, we are able to hit the bull's eye i.e. the centre point.

Now as the dart can land on any arbitrary position, we represent the arbitrary position $(x,y)$ by polar coordinates $(r,\theta)$, measured from  origin $(0,0)$, where $r$ defines the distance of the centre points, and $\theta$ defines the angle that line connecting points $(0,0)$ and $(x,y)$ from horizontal direction.\\ 
If we assume that coordinates $x$ and $y$ are independent and probability is depending only on radial distance $r$, then we can write probability distribution function (PDF) as,

\begin{equation}\label{eq_1}
\phi(r) = f(x)f(y)
\end{equation}
where, $\phi(r)$ defines the probability that the dart lands on distance $r$ from the centre, irrespective of angle $\theta$. Similarly, $f(x)$ define the probability that the point is located at horizontal distance $x$ from $x-axis$ and $f(y)$ define the probability that the point is located at horizontal distance $y$.\\
Since we know that $r^2=x^2+y^2$, so we can write Eq. \ref{eq_1} as follows, 

\begin{equation}
\phi(\sqrt{x^2+y^2})=f(x)f(y)
\end{equation}

Suppose $y=0$, we have,
\begin{equation}
\begin{split}
\phi(\sqrt{x^2}) &= f(x)f(0)\\
\Rightarrow \phi(x) &= \lambda f(x)
\end{split}
\end{equation}

where $\lambda$ is a constant. $\lambda$ can be understood as what is the probability that the dart lends on $0$ distance from horizontal or vertical axis. 
Further we can write the above equation as,

\begin{equation}
\begin{split}
\lambda f(\sqrt{x^2+y^2}) &= f(x)f(y)

\Rightarrow \frac{\lambda f(\sqrt{x^2+y^2})}{\lambda^2} &= \frac{f(x)}{\lambda} \frac{f(y)}{\lambda}
\end{split}
\end{equation}

Further we can write it as,

\begin{equation}
\frac{\lambda f(\sqrt{x^2+y^2})}{\lambda^2} = \frac{f(x)}{\lambda} \frac{f(y)}{\lambda}
\end{equation}

Lets define $g(a) = \frac{f(a)}{\lambda}$, then we can write the above equation as,\\ 
\begin{equation}\label{eq_2}
g(x)g(y) = g(\sqrt{x^2+y^2})
\end{equation}

Now here the question is, what should be the function $g$ that satisfies the condition given in Eq. \ref{eq_2}.

For a moment, let's consider that the function $g$ is an exponential function, i.e. $g(a) = \exp(A a^2)$, where $A$ is a constant. 

Using $g$ as exponential function, we have the following equation, 

\begin{equation}
\begin{split}
g(x)g(y) &= \exp(A x^2)\exp(A y^2)\\
\Rightarrow g(x)g(y) &= \exp(A (x^2 + y^2))\\
\Rightarrow g(x)g(y) &= g(\sqrt{x^2+y^2})
\end{split}
\end{equation}

Hence, we have,

\begin{equation}\label{eq_3}
\begin{split}
f(x) &= \lambda g(x) \\
\Rightarrow f(x) &= \lambda \exp(Ax^2) 
\end{split}
\end{equation}

So far, we do not know the parameters $\lambda$ and $A$. These parameters are having important aspects that we will discuss in the future sections. 
 
# Distribution 
As mentioned previously, the distributions represent the probability of something to happen for given parameters. The area under the curve of distribution should be unity as that would represent the total probability.
Let's first find the area under the curve for the function derived in Eq. \ref{eq_3}. We integrate the function from $-\infty$ to $+\infty$ to calculate all area, as follows, 

\begin{equation}
\begin{split}
\int_{-\infty}^{+\infty} f(x)dx &= 1\\
\int_{-\infty}^{+\infty} \lambda \exp(Ax^2)dx &= 1
\end{split}
\end{equation}

For the sake of computational easing, let's replace $A$ by $-h^2$, where $h$ is another parameter, and we will calculate this later. 


\begin{equation}
\int_{-\infty}^{+\infty} \lambda \exp(-h^2x^2)dx = 1
\end{equation}

Let's consider $hx = u$, we have $du = h dx$,\\

\begin{equation}
\begin{split}
\int_{-\infty}^{+\infty} \frac{\lambda}{h} \exp(-u^2)du &= 1\\
\Rightarrow \frac{\lambda}{h} \sqrt{\pi} &= 1\\
\Rightarrow h &= \lambda \sqrt{\pi}\\
\end{split}
\end{equation}
where, $\int_{-\infty}^{+\infty} \exp(-u^2)du = \sqrt{\pi}$.\\
Further, 
\begin{equation}
h^2 = \lambda^2 \pi 
\end{equation}
so we can write Eq. \ref{eq_3} as follows, 
\begin{equation} \label{eq_3a}
f(x) = \lambda \exp(-\pi \lambda^2 x^2)
\end{equation}

So far, the distribution represented by $f(x)$ has area unity. \\

Now we will calculate the variance of the distribution, as follows, 

\begin{equation}\label{eq_4}
\begin{split}
Var(x) = \sigma^2 &= \int_{-\infty}^{+\infty} x^2 \exp(-\pi \lambda^2 x^2) dx\\
\Rightarrow Var(x) &= \sigma^2 = \lambda \int_{-\infty}^{+\infty} x.x \exp(-\pi \lambda^2 x^2) dx
\end{split}
\end{equation}
 

As we know from calculus that $\int udv  = uv - \int v du$. We can compare this identity with Eq. \ref{eq_4} as $u = x$, so $du = dx$, and $v = x \exp(-\pi h^2x^2)$, so $dv = x \exp(-\pi \lambda^2 x^2) dx$ and $v = -\frac{1}{2\pi \lambda^2} \exp(-\pi \lambda^2 x^2)$

So we can write Eq. \ref{eq_4} as follows, 

\begin{equation}
\begin{split}
Var(x) = \sigma^2 = \lambda \Big( x \Big( -\frac{1}{2\pi \lambda^2} &\exp(-\pi \lambda^2 x^2) \biggr\rvert_{-\infty}^{+\infty} \Big) \\
&- \int_{-\infty}^{+\infty}  -\frac{1}{2\pi \lambda^2} \exp(-\pi \lambda^2 x^2  \Big)
\end{split}
\end{equation}


\begin{equation}\label{eq_4a}
\begin{split}
Var(x) = \sigma^2 &= \lambda \Big( x \Big( 0 \Big) - \int_{-\infty}^{+\infty}  -\frac{1}{2\pi \lambda^2} \exp(-\pi \lambda^2 x^2) \Big)\\
&= \frac{1}{2\pi \lambda^2} \Big(  \int_{-\infty}^{+\infty} \lambda  \exp(-\pi \lambda^2 x^2) \Big)\\
&= \frac{1}{2\pi \lambda^2} \Big( \int_{-\infty}^{+\infty} \lambda  \exp(-\pi \lambda^2 x^2 \Big)\\
\end{split}
\end{equation}



Since we know from Eq. \ref{eq_3a} that $\int_{-\infty}^{+\infty} \lambda  \exp(-\pi \lambda^2 x^2 = 1$
Hence we can write Eq. \ref{eq_4a} as given below,

\begin{equation}
\begin{split}
\sigma^2 &= \frac{1}{2\pi \lambda^2}\\
\end{split}
\end{equation}

\begin{equation}\label{eq_5}
\begin{split}
\lambda^2 &= \frac{1}{2\pi \sigma^2 }\\
\Rightarrow \lambda &= \frac{1}{\sigma \sqrt{2\pi }}
\end{split}
\end{equation}


So we finally have from Eq. \ref{eq_3a} and Eq. \ref{eq_5}, 
\begin{equation}\label{eq_6}
f(x) = \frac{1}{\sigma \sqrt{2\pi }} \exp\Big(-\frac{x^2}{2\sigma^2}\Big) 
\end{equation}

We should remember here that the we assumed $(0,0)$ as centre. However, to adept the distribution in Eq. \ref{eq_6} to any centre represented by $\mu$ can be done in the following way. 

\begin{equation}\label{eq_7}
f(x) = \frac{1}{\sigma \sqrt{2\pi }} \exp\Big(-\frac{(x-\mu)^2}{2\sigma^2}\Big) 
\end{equation}

Eq. \ref{eq_7} is known as $\textbf{normal distribution function}$, and also represented by $\mathcal{N}(\mu, \sigma^2)$
