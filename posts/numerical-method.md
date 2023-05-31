---
title: '数值方法'
date: '2023-05-31'
---

牛顿法的迭代公式为
$$
x_{n+1}=x_n-\frac{f(x_n)}{f^\prime(x_n)}
$$
其中根 $r$ 满足 $f(r)=0$. 利用迭代公式减去两边，我们有
$$
r - x_{n+1}=r - x_n+\frac{f(x_n)}{f^\prime(x_n)}
$$
或
$$
\varepsilon_{n+1}=\varepsilon_n+\frac{f(x_n)}{f^\prime(x_n)}
$$
用泰勒级数来展开关于根 $r$ 的函数 $f(x_n)$ 和 $f^\prime(x_n)$，使用 $f(r)=0$，有
$$
\begin{align*}
f(x_n)&=f(r)+(x_n-r)f^\prime(r)+\frac{1}{2}(x_n-r)^2f^{\prime\prime}(r)+\dots\\
&=-\varepsilon_nf^\prime(r)+\frac{1}{2}\varepsilon_n^2f^{\prime\prime}(r)+\dots;\\
f^\prime(x_n)&=f^\prime(r)+(x_n-r)f^{\prime\prime}(r)+\frac{1}{2}(x_n-r)^2f^{\prime\prime\prime}(r)+\dots\\
&=f^\prime(r)-\varepsilon_nf^{\prime\prime}(r)+\frac{1}{2}\varepsilon_n^2f^{\prime\prime\prime}(r)+\dots
\end{align*}
$$
利用以下标准泰勒级数：
$$
\frac{1}{1-\varepsilon}=1+\varepsilon+\varepsilon^2+\dots
$$
它对于 $|\varepsilon|<1$ 收敛. 将这些泰勒展开式代入上面的误差式子，得到
$$
\begin{align*}
\varepsilon_{n+1}&=\varepsilon_n+\frac{f(x_n)}{f^\prime(x_n)}\\
&=\varepsilon_n+\frac{-\varepsilon_nf^\prime(r)+\frac{1}{2}\varepsilon_n^2f^{\prime\prime}(r)+\dots}{f^\prime(r)-\varepsilon_nf^{\prime\prime}(r)+\frac{1}{2}\varepsilon_n^2f^{\prime\prime\prime}(r)+\dots}\\
&=\varepsilon_n+\frac{-\varepsilon_n+\frac{1}{2}\varepsilon_n^2\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\dots}{1-\varepsilon_n\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\dots}\\
&=\varepsilon_n+\left(-\varepsilon_n+\frac{1}{2}\varepsilon_n^2\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\dots\right)\left(1+\varepsilon_n\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\dots\right)\\
&=\varepsilon_n+\left(-\varepsilon_n-\varepsilon_n^2\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\frac{1}{2}\varepsilon_n^2\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}+\dots\right)\\
&=-\frac{1}{2}\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}\varepsilon_n^2+\dots
\end{align*}
$$
因此，证明了随着 $n\to\infty$，
$$
|\varepsilon_{n+1}|=k|\varepsilon_n|^2
$$
只要 $f^\prime(r)\ne 0$，$k$ 满足
$$
k=\frac{1}{2}\left|\frac{f^{\prime\prime}(r)}{f^{\prime}(r)}\right|
$$
因此，牛顿方法在单根上是 2 阶的.