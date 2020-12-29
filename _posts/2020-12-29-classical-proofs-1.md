---
layout: post
mathjax: true
tikz: yes
comments: true
title:  "Classical proofs"
date:   2020-12-29 13:08:00 +0000
categories: github jekyll
---

Proofs of some classical statistical tests
======



#### **DEFINITION 1** 

*If $Z \sim \mathcal{N}(0,1)$, then $Z^2\sim \chi^2_1$ where $\chi^2_1$ is $\chi^2$ distribution with $1$ degree of freedom.*



#### **DEFINITION 2**

*If $Z \sim \mathcal{N}(0,1)$ and $U \sim \chi^2_n$, then* $$\frac{Z}{\sqrt{\frac{U}{n}}} \sim t_n$$ *where, $t_n$ is a $t$ distribution with $n$ degrees of freedom.*



#### **DEFINITION 3**

*If $U \sim \chi^2_m$ and $V \sim \chi^2_n$, then* $$\frac{\frac{U}{m}}{\frac{V}{n}} \sim F_{m,n}$$ *where, $F_{m,n}$ is a $F$ distribution with $m$ and $n$ degrees of freedom.*



#### **Theorem 1**

*If $X \sim \mathcal{N}(\mu, \sigma^2)$, then $Z = \frac{X-\mu}{\sigma} \sim \mathcal{N}(0,1)$*



*Proof*

As we know $X \sim \mathcal{N}(\mu, \sigma^2)$, thus, $X - \mu \sim \mathcal{N}(\mu, \sigma^2) - \mu = \mathcal{N}(0, \sigma^2)$, and finally, $\frac{X - \mu}{\sigma^2} \sim \mathcal{N}(0, 1)$



#### **Theorem 2**

*If $X_1, X_2, ... $ are the normally distributed random variables, with $\mu$ mean and $\sigma^2$ variance, then, $$\frac{\bar{X}-\mu}{\sigma/\sqrt{n}} \sim \mathcal{N}(0,1)$$*



*Proof*

As we know $\bar{X} \sim \mathcal{N}(\mu, \sigma^2/n)$, thus $\bar{X} - \mu \sim \mathcal{N}(\mu, \sigma^2/n) - \mu = \mathcal{N}(0, \sigma^2/n)$, and finally,
$\frac{\bar{X} - \mu}{\sigma/\sqrt{n}} \sim \mathcal{N}(0, 1)$



#### **Corollary 1**

*If $X_1, X2, X3,...$ are the normally distributed random variables, then, $Z = \frac{\bar{X}-\mu_0}{\frac{\sigma}{\sqrt{n}}}$ follows standard
normal distribution where $\mu_0$ is hypothesized mean under null hypothesis.*



*Proof*

The above corollary is known as one sample $Z$-test, which calculated the probability of a sample mean to occur for a hypothesized population mean $\mu_0$ and given population variance $\sigma^2$.



#### **Theorem 3**

*If $X$ is a normally distributed random variable, with $\mu_X$ mean and $\sigma_X^2$ variance, and $Y$ is another normally distributed random variables, with $\mu_Y$ mean and $\sigma_Y^2$ variance then,*

$$\frac{\bar{D}-\delta}{\sigma_D/\sqrt{n}} \sim \mathcal{N}(0,1)$$

*where $\bar{D} = \sum_{i=1}^n\frac{D_i}{n}$, $D_i = X_i - Y_i$ , and $\sigma_D^2$ is the variance population of pairwise difference $(D_i)$, and 
$\delta = \mu_X - \mu_Y $.*



*Proof*

As we know $X_i \sim \mathcal{N}(\mu_X, \sigma_X^2)$ and $Y_i \sim \mathcal{N}(\mu_Y, \sigma_Y^2)$, and $X_i-Y_i \sim \mathcal{N}(\mu_X-\mu_Y, (\sigma_X^2+\sigma_Y^2))$.
Further, if $D_i = X_i - Y_i$ and $\bar{D} = \sum_{i=1}^{n}\frac{D_i}{n}$, then $\bar{D} \sim \mathcal{N}(\mu_X-\mu_Y, (\sigma_X^2+\sigma_Y^2)/n) = \mathcal{N}(\delta, \sigma_D^2/n) $.

With a little manipulation we have,
$ \frac{\bar{D} - \delta}{\sigma_D/\sqrt{n}} \sim \mathcal{N}(0,1) $





#### **Corollary 2**

*If $X_1, X_2, ..., X_n$ is a normally distributed random variable, and $Y_1, Y_2, ..., Y_n$ is another normally distributed random variables, then,*

$$\frac{\bar{D}-\delta}{\sigma_D/\sqrt{n}} \sim \mathcal{N}(0,1)$$

*where $\bar{D} = \sum_{i=1}^n\frac{D_i}{n}$, $D_i = X_i - Y_i$ , and $\sigma_D^2$ is the variance population of pairwise difference $(D_i)$. $\delta $ is the hypothesized mean under null hypothesis.*



*Proof*

The above corollary is known as *Paired-sample $Z$-test*, which calculates the probability of samples difference  to occur for a hypothesized population difference $\delta$ and given population difference variance $\sigma_D^2$.





#### **Theorem 4**

If $X \sim \mathcal{N}(\mu_X, \sigma_X^2)$ and $Y \sim \mathcal{N}(\mu_Y, \sigma_Y^2)$ then, $$\frac{(\bar{X} - \bar{Y}) - (\mu_X - \mu_Y)}{\sqrt{\frac{\sigma_X^2}{n} + \frac{\sigma_Y^2}{m}}} \sim \mathcal{N}(0,1)$$

*Proof*

Proved previously.





#### **Theorem 5**

*If $X$ is a normally distributed variable, then $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2_{n-1}$, where $S^2$ is the sample variance, and $n$ is the number of measurements in a sample, $\sigma^2$ is the variance of normal distribution.* 



*Proof*

Let $X\sim \mathcal{(\mu, \sigma^2)}$, and the sample variance statistic be $S^2 = \frac{\sum_{i=1}^n (X_i - \bar{X})}{n-1} $. Then we write the population variance as, 
$$
\begin{eqnarray}
        \sum_{i=1}^{n}\frac{(X_i - \mu)^2}{\sigma^2} &=& \sum_{i=1}^{n}\frac{(X_i - \bar{X} + \bar{X} - \mu)^2}{\sigma^2} \\
        &=& \sum_{i=1}^{n}\frac{(X_i - \bar{X})^2 + (\bar{X} - \mu)^2 + 2 (X_i - \bar{X}) (\bar{X} - \mu)}{\sigma^2} \\
        &=& \sum_{i=1}^{n}\frac{(X_i - \bar{X})^2}{\sigma^2} + \sum_{i=1}^{n}\frac{(\bar{X} - \mu)^2}{\sigma^2} + 2 (\bar{X} - \mu)  \sum_{i=1}^{n}\frac{(X_i - \bar{X}) }{\sigma^2} \\
        &=& \sum_{i=1}^{n}\frac{(X_i - \bar{X})^2}{\sigma^2} + \sum_{i=1}^{n}\frac{(\bar{X} - \mu)^2}{\sigma^2} \\\end{eqnarray}
$$


With a little manipulation we have,

$$
\begin{eqnarray}
    \sum_{i=1}^{n}\frac{(X_i - \bar{X})^2}{\sigma^2} &=& \sum_{i=1}^{n}\frac{(X_i - \mu)^2}{\sigma^2} - \sum_{i=1}^{n}\frac{(\bar{X} - \mu)^2}{\sigma^2} \\
    \Rightarrow \frac{n-1}{\sigma^2}\sum_{i=1}^{n}\frac{(X_i - \bar{X})^2}{n-1} &=& \sum_{i=1}^{n}\frac{(X_i - \mu)^2}{\sigma^2} - \sum_{i=1}^{n}\frac{(\bar{X} - \mu)^2}{\sigma^2} \\
    \Rightarrow \frac{n-1}{\sigma^2}S^2 &=&  \sum_{i=1}^{n}\frac{(X_i - \mu)^2}{\sigma^2} - \frac{1}{n}\sum_{i=1}^{n}\frac{(\bar{X} - \mu)^2}{\sigma^2/n} \\\end{eqnarray}
$$


As we know $\frac{(X_i - \mu)}{\sigma} = Z \sim \mathcal{N}(0,1)$, and $\frac{(\bar{X} - \mu)^2}{\sigma^2/n} = Z \sim \mathcal{N}(0,1)$. Thus we can write,
$$
\begin{aligned}
\frac{n-1}{\sigma^2}S^2 &=  \sum_{i=1}^{n}Z^2 + \frac{1}{n}\sum_{i=1}^{n}Z^2\\  
&=  nZ^2 - \frac{1}{n}nZ^2 \\
    &=  nZ^2 - Z^2 \\
    &=  (n-1)Z^2 \sim \chi^2_{n-1} \\\end{aligned}
$$
Thus,
$$
\frac{n-1}{\sigma^2}S^2 \sim \chi^2_{n-1}
$$






#### **Corollary 3**

*If $X_1, X_2, ...,X_n$ are the independent random variables such that $X_i \sim \mathcal{N}(\mu,\sigma^2)$ then, $$\frac{\bar{X} - \mu}{S/\sqrt{n}} \sim t_{n-1}$$ where, $n$ is number of data points, $\bar{X}$ is the mean of all data points, and $t_{n-1}$ is Student's t-distribution $n-1$ degrees of freedom*


$$
\begin{aligned}
        \frac{\bar{X}-\mu}{S/\sqrt{n}} &= \frac{1}{S}\frac{\bar{X}-\mu}{1/\sqrt{n}} \sqrt{\frac{\sigma^2}{\sigma^2}}  \\
        &= \sqrt{\frac{\sigma^2}{S^2}}\frac{\bar{X}-\mu}{\sigma/\sqrt{n}}   \\
        &= \sqrt{\frac{(n-1)\sigma^2}{(n-1)S^2}}\frac{\bar{X}-\mu}{\sigma/\sqrt{n}}   \\
        &= \frac{\frac{\bar{X}-\mu}{\sigma/\sqrt{n}}}{\sqrt{\frac{(n-1)S^2}{\frac{\sigma^2}{(n-1)}}}}    \\
        &= \frac{Z}{\sqrt{\frac{U}{n-1}}}    \sim t_{n-1}    \\
    \end{aligned}
$$
In the above equation, we use *Definition 2* 
