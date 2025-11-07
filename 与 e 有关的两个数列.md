# 与 e 有关的两个数列

## 一、下界数列

#### 问题 1 单调性

>[!note] 问题 1 单调性
>$$
>求证：a_n = (1 + \frac{1}{n})^{n} \ 单调递增
>$$

##### 方法一：使用均值不等式

仿照上界数列单调性的证明，有：
$$
\sqrt[n+1]{(1+\frac{1}{n})^n \cdot 1} \leq \frac{n(1+\frac{1}{n}) + 1}{n+1} = 1 + \frac{1}{n+1}
$$
这里使用了 [[均值不等式#AM-GM 不等式]] 

##### 方法二：邻项比较法使用伯努利不等式

[[伯努利不等式]] 

将两个邻项作比（显然为正），考察与 1 的关系
$$
\begin{align}
\frac{a_{n+1}}{a_n}&=\frac{n+2}{n+1}\cdot \left(\frac{n+2}{n+1}\right)^n\cdot \left( \frac{n}{n+1} \right)^n \\
&=\left( 1-\frac{1}{(n+1)^2} \right)^n\cdot \frac{n+2}{n+1} \\
&\geq\left( 1-\frac{n}{(n+1)^2} \right)\cdot \frac{n+2}{n+1}\ \ (Bernoulli 不等式) \\
&=\frac{n^3+3n^2+3n+2}{n^3+3n^2+3n+1}>1
\end{align}
$$
注意不等号方向，我们要证明此数列为单调递增，故希望式子 > 1
因此直接用伯努利不等式就是对的

但是再下面的上界数列单调性就需要一些技巧

#### 问题 2 上界

>[!note] 问题 2 上界
>求证：
>$$x_n=(1+\frac{1}{n})^n 有上界
>$$

这里使用了 [[二项展开#例子 1]] 

## 二、上界数列

#### 问题 1 单调性

>[!note] 问题 1 单调性
>$$
>求证：a_n = (1 + \frac{1}{n})^{n + 1} \ 单调递减
>$$

##### 方法一：使用均值不等式

（很难）注意到：通分后分子与指数次幂相同，通过多元调和均值可以消去，故有：

$$\sqrt[n+2]{\left(1+\frac{1}{n}\right)^{n+1}} = \sqrt[n+2]{1\cdot\left(1+\frac{1}{n}\right)^{n+1}} \geqslant \frac{n+2}{1+(n+1)\frac{1}{1+\frac{1}{n}}} = 1+\frac{1}{n+1}$$
这里使用了 [[均值不等式#GM-HM 不等式]] 

##### 方法二：邻项比较法使用伯努利不等式

[[伯努利不等式]]

仿照下界数列单调性的证明，使用邻项比较法
$$
\begin{align}
\frac{a_{n+1}}{a_n}&= \frac{n+2}{n+1}\cdot \left(\frac{n(n+2)}{(n+1)^2}\right)^{n+1} \\ 
&=\frac{n+2}{n+1}\cdot \left( 1-\frac{1}{(n+1)^2} \right)^{n+1}
\end{align}
$$
写到这里发现 **不等号方向不对**！要证明递减的，故希望找到这个数列的一个上界数列，要将这个东西放大，但是伯努利给出的是下界数列

于是有技巧：构造 **倒数**：
$$
\begin{align}
RHS&=\frac{\frac{n+2}{n+1}}{\left(\frac{(n+1)^2}{n(n+2)}\right)^{n+1}} \\
&=\frac{\frac{n+2}{n+1}}{\left(1+\frac{1}{n(n+2)}\right)^{n+1}} \\
&\leq \frac{\frac{n+2}{n+1}}{1+\frac{n+1}{n(n+2)}} \\
&=\frac{n^3+4n^2+4n}{n^3+4n^2+4n+1}<1
\end{align}
$$
我们可以 **将本来要放缩的符号不对的那项取倒数扔到分母上**，之后使用不等式，不等号方向就对了，因为分母带来了不等号反号一次

## 三、e 的构造

注意到：上界序列单调递减有下界，下界序列单调递增有上界，并且显然有: 
$$
\left( 1+\frac{1}{n} \right)^n <\left( 1+\frac{1}{n} \right)^{n+1}
$$

对两边同时取极限，即有：
$$
RHS= \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{n+1}=\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n \cdot \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)=LHS
$$
得到两个数列的极限相同，定义：
$$
\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n =\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{n+1} := e
$$

## 四、第二个重要极限

>[!note] 第二个重要极限
>$$
>\lim_{ x \to \infty } \left( 1+ \frac{1}{x} \right)^x=e
>$$

### 证明

#### 当 $x\to +\infty$ 时

使用夹逼准则：
$$
[x]\leq x\leq [x] + 1
$$
将其分别扔进序列的形式里面，得到：
$$
\left( 1 + \frac{1}{[x] + 1} \right)^{[x]+1}\left( 1 + \frac{1}{[x] + 1} \right)^{-1}<\left( 1+ \frac{1}{x} \right)^x<\left( 1+ \frac{1}{[x]} \right)^{[x]}\left( 1+ \frac{1}{[x]} \right)
$$
取极限夹逼即可

#### 当 $x\to -\infty$ 时

令 y = -x ，换元即可

## 五、经典不等式的构造

>[!note] 经典不等式
>$$\frac{1}{n+1}<\ln\left( 1+ \frac{1}{n} \right)< \frac{1}{n}$$

这完全是由第二个重要极限推出的

由 e 的定义，显然有：
$$
\left( 1+ \frac{1}{n} \right)^n < e <\left( 1+\frac{1}{n} \right)^{n+1}
$$
两边同时取对数，得到：
$$
n\ln\left( 1+\frac{1}{n} \right)<1<(n+1)\ln\left( 1+ \frac{1}{n} \right)
$$
此也即要证明的式子