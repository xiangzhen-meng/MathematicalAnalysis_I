# Stolz 定理

## 概述

stolz 定理是高中时期常用的 L'Hopital 法则的离散版本，而且有着比较强的限制
通常适用于处理分式极限的问题

注意，stolz 定理对于序列的限制都是限制在分母上，要求分母严格单调

### $\frac{*}{\infty}$ 型的 Stolz 定理

若 $\{x_n\}, \{y_n\}$ 为实数列，且 $\{x_n\}$ 为严格单调数列，极限为无穷。若：
$$
\exists\lim\limits_{n\to\infty} \frac{y_{n+1}-y_n}{x_{n+1}-x_n}=a \ (其中 a为有穷极限)
$$则有：
$$
\lim\limits_{n\to\infty} \frac{y_n}{x_n} = a
$$
### $\frac{0}{0}$ 型的 Stolz 定理

若 $\{a_n\}$ 和 $\{b_n\}$ 均为无穷小序列，其中 $\{a_n\}$ 为严格单调递减序列，且存在：
$$
\lim_{ n \to \infty } \frac{b_{n+1}-b_n}{a_{n+1}-a_n}=l\ (其中 l 为有限或者 \infty)
$$
则有: 
$$
\lim_{ n \to \infty } \frac{b_n}{a_n}=l
$$

## 证明

### 对于 $\frac{*}{\infty}$ 型的 Stolz 定理的证明

首先方便起见，扩充定义，令 $x_0 = 0, y_0 = 0$

则可以将目标形式凑成条件形式
$$
\frac{y_n}{x_n} = \frac{1}{x_n} \sum\limits_{k=1}^n (y_k - y_{k-1}) = \sum\limits_{k=1}^n \frac{x_k - x_{k-1}}{x_n} \cdot \frac{y_k - y_{k-1}}{x_k - x_{k-1}}
$$
进一步的，将常数也凑成类似形式
$$
\begin{align}
\frac{y_n}{x_n} - a &= \sum\limits_{k=1}^n \frac{x_k - x_{k-1}}{x_n} \cdot \frac{y_k - y_{k-1}}{x_k - x_{k-1}} - a \cdot \sum\limits_{k=1}^n \frac{x_k - x_{k-1}}{x_n}  \\
&= \sum\limits_{k=1}^n \frac{x_k - x_{k-1}}{x_n} \left( \frac{y_k - y_{k-1}}{x_k - x_{k-1}} - a \right)
\end{align}
$$

记 $\alpha_k = \frac{y_k - y_{k-1}}{x_k - x_{k-1}} - a$，$\beta_{k,n} = \frac{x_k - x_{k-1}}{x_n}$，$\gamma_n = \frac{y_n}{x_n} - a = \sum\limits_{k=1}^n \beta_{k,n} \alpha_k$
则 $\{\alpha_k\}$ 为无穷小数列$\forall n\in\mathbb{N}, \sum\limits_{k=1}^n \beta_{k,n} = 1$；$\forall k\in\mathbb{N}, \lim\limits_{n\to\infty} \beta_{k,n} = 0$；$\beta_{k,n} > 0$ 

要证原式，其实也就是证明 $\gamma _n$ 为无穷小序列即可

**注**：这里其实是构造出了 [[Toeplitz 定理]] 的形式

以下使用到了经典的 [[an epsilon of room]] 的思想

考虑**前有限项**数列，可以通过取最大值的方式放缩掉：

由于 $\{\alpha_k\}$ 为无穷小数列，故 $\forall \varepsilon > 0$，$\exists N_0 \in \mathbb{N}$，s.t. $\forall k > N_0$，$|\alpha_k| < \frac{\varepsilon}{2}$
令 $M = \max\{1, |\alpha_1|, |\alpha_2|, \cdots, |\alpha_{N_0}|\}$ ，可以将所有的 $\{\alpha_k\}$ 放缩为 M 

考虑**后无穷多项**数列，可以通过取 $\varepsilon$ 的方式放缩掉：

由于 $\forall k \in \mathbb{N}$，$\lim\limits_{n\to\infty} \beta_{k,n} = 0$ 
故对于：
$k = 1$，$\exists N_1 \in \mathbb{N}$，s.t. $\forall n > N_1$，$|\beta_{1,n}| < \frac{\varepsilon}{2MN_0}$ 
$k = 2$，$\exists N_2 \in \mathbb{N}$，s.t. $\forall n > N_2$，$|\beta_{2,n}| < \frac{\varepsilon}{2MN_0}$ 
$\cdots$
$k = N_0$，$\exists N_{N_0} \in \mathbb{N}$，s.t. $\forall n > N_{N_0}$，$|\beta_{N_0,n}| < \frac{\varepsilon}{2MN_0}$
令 $N = \max\{N_0, N_1, N_2, \cdots, N_{N_0}\}$
则 $\forall n > N$，
$$
\begin{align}
|\gamma_n| &= \left| \sum\limits_{k=1}^{N_0} \beta_{k,n} \alpha_k + \sum\limits_{k=N_0+1}^n \beta_{k,n} \alpha_k \right| \\
&\leq \sum\limits_{k=1}^{N_0} \beta_{k,n} |\alpha_k| + \sum\limits_{k=N_0+1}^n \beta_{k,n} |\alpha_k| \\
&\leq \sum\limits_{k=1}^{N_0} \beta_{k,n} \cdot M + \left( \sum\limits_{k=N_0+1}^n \beta_{k,n} \right) \frac{\varepsilon}{2} \\
&<\frac{\varepsilon}{2MN_0} \cdot N_0 \cdot M + \frac{\varepsilon}{2} = \varepsilon
\end{align}
$$

即 $\lim\limits_{n\to\infty} \gamma_n = 0$ ，即 $\lim\limits_{n\to\infty} \frac{y_n}{x_n} = a$ ，证毕

## 例题

### 问题 1：根式相关

>[!note] 问题 1 根式相关
>设 $a_{1}>0$，$a_{n+1}=a_n+\frac{1}{a_n}$，求证：$$
>\lim_{ n \to \infty } \frac{a_n}{\sqrt{ 2n }}=1 $$

估计极限：画出蛛网图，显然 $a_n$ 是严格单调递增正无界（无穷）序列

首先尝试直接对根式形式使用 Stolz 定理：
$$
\begin{align}
\lim_{ n \to \infty } \frac{a_n}{\sqrt{ 2n }}&=\lim_{ n \to \infty } \frac{a_{n}-a_{n-1}}{\sqrt{ 2 }(\sqrt{ n }-\sqrt{ n-1 })} \\
&=\lim_{ n \to \infty } \frac{\frac{1}{a_{n-1}}}{\sqrt{ 2 }(\sqrt{ n }-\sqrt{ n-1 })} \\
&=\lim_{ n \to \infty } \frac{(\sqrt{ n }+\sqrt{ n-1 })}{\sqrt{ 2 }a_{n-1}}
\end{align}
$$
 他妈的洛回去了，~~抄错题继续给我洛~~ 
 
将根式平方，之后即可简单地洛出来

$$
\lim_{ n \to \infty } \frac{a_n^2}{2n}=\lim_{ n \to \infty } \frac{a_{n+1}^2-a_n^2}{2n+2-2n}= \frac{1}{2}\lim_{ n \to \infty } \left( 2+\frac{1}{a_n^2} \right) =1
$$
### 问题 2：无穷大乘以无穷小

>[!note]  问题 2：无穷大乘以无穷小
>序列 $\{a_n\}$ 满足：$$0<a_{1}<1, a_{n+1}=a_n(1-a_n)$$求证：$$\lim_{ n \to \infty } na_n=1$$

#### 分析

显然本题属于无穷大乘以无穷小。通常可以将其化为 $\frac{\infty}{\infty}$ 或者 $\frac{0}{0}$ 形式，但是这两个形式需要二选一，不一定都走得通

#### 证明

显然有序列单调递减，且有下界 0，故极限存在，对递推式两边同时取极限得到：
$$
\lim_{ n \to \infty } a_n=0
$$
尝试 1：将 n 扔到分母上，构造 0/0 形式。失败了
尝试 2：将 $a_n$ 扔到分母上，走通了：
$$
\begin{align}
\lim_{ n \to \infty } na_n&=\lim_{ n \to \infty } \frac{n}{\frac{1}{a_n}}=\lim_{ n \to \infty } \frac{n-(n-1)}{\frac{1}{a_n}-\frac{1}{a_{n-1}}} \\
&=\lim_{ n \to \infty } \frac{a_na_{n-1}}{a_{n-1}-a_n}=\lim_{ n \to \infty } \frac{a_n}{a_{n-1}}=\lim_{ n \to \infty } (1-a_{n-1})=1
\end{align}
$$
因此 Stolz 定理的使用不一定要一条路走到黑，这样的时候需要换个思路重走