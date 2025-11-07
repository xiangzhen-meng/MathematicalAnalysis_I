# 柯西收敛准则 (Cauchy's convergence test)

## 定义与概述

### 柯西列（基本列）

对于数列 $\{x_n\}$：
$$
\forall \varepsilon>0,\exists N\in \mathbb{N},\forall n,m>N,|x_n-x_m|<\varepsilon
$$
则称这个数列为 柯西列（或名：基本列）

### 柯西收敛准则

数列收敛 $\iff$ 数列是柯西列

### 理解

这是一个非常强的定理，因为这个定理给出了一种 **不必猜出数列极限**，即可证明该数列收敛的方法。该定理也可以理解成：自数列的某一项后，任意两项之间的距离都足够小

另外注意到，柯西收敛原理给出了序列收敛的 **充分必要条件**，也即不仅可以在判定收敛的时候使用，还可以在判定不收敛的时候使用

柯西收敛准则是 [[实数的完备性定理]] 中的一个，他说明了实数的完备性

### 等价叙述

$$
\forall \varepsilon>0,\exists N\in \mathbb{N},\forall n>N,\forall p\in \mathbb{N},|x_{n+p}-x_n|<\varepsilon
$$
也即将 m 换成了 n+p，这是一种差分手法

### 否定叙述：证明序列发散的手法

数列不是柯西列 $\iff$
$$
\exists \varepsilon>0,\forall N\in \mathbb{N},\exists n,m>N,s.t.|x_m-x_n|>\varepsilon
$$
也即：数列某一项之后，**某**两项之间的距离并不充分小
也即：总能找到某个数，使得在某一项之后，**某**两项的距离都大于那个数

### 不等价的一种叙述

可能有这种 **错误** 理解：
$$
\forall p,\lim_{ n \to \infty } (x_n-x_{n+p}) =0
$$
这错在：对于每一个不同的 p，可能存在 **不同的 n**，也即没有要求 **一致性**

这种叙述柯西序列的必要条件，而不充分

反例可以取 **调和数列** 

### 有误的理解：相邻两项之差趋近于零不能保证收敛

#### 例子

一个例子是 [[伯努利不等式#例子 1 证明小于 1 的幂次增长速率会衰减到 0]] 

比如 $f(x)=\sqrt{ x }$ 在无穷远处相邻两项的增速趋于零，但是这个函数趋于正无穷

#### 错因

错误理解的原因是这样的。首先看柯西收敛准则的定义
$$
\forall \varepsilon>0,\exists N\in \mathbb{N},\forall n>N,\forall p\in \mathbb{N},|x_{n+p}-x_n|<\varepsilon
$$
其中要求先确定 $N$，后确定 $p$，而非根据 $p$ 确定 $N$ 

这样的话，对于前述的 N，即便两项之差足够小，只要 p 足够大，仍然不能保证误差的累积是足够小的。也可以说，上述错误理解类似于 [[柯西收敛准则 (Cauchy's convergence test)#不等价的一种叙述|上面不等价的叙述]] ，也即把命题的条件换了顺序，这是不可以的

## 证明

### 必要性证明

数列收敛 $\implies$ 数列是柯西列
这个证明是 trivial 的

$$
\forall \varepsilon>0, \exists N\in \mathbb{N},\forall n>N,|x_n-a|< \frac{\varepsilon}{2}
$$
因此，借由 [[绝对值不等式]] 搭桥，可以有：
$$
\forall m,n>N,|x_m-x_n|<|x_m-a|+|x_n-a|< \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
### 充分性证明

使用 [[B-W 定理 (Bolzano-Weierstrass theorem)]] 证明

先证柯西列是 **有界数列**：

这里使用了 [[an epsilon of room]] 的思想

对于后无穷多项，我们可以将其限制在一个有限值的附近，因为后无穷多项中，任意两项之间的距离都充分小

不妨取：$\varepsilon=1$，则可以取一个有限的 $N_{0}$，使得：$\forall m,n>N_{0},|x_m-x_n|<1$
因此有：
$$
\forall n\geq N_{0}+2,|x_n|=|x_n-x_{N_{0}+1} + x_{N_{0}+1}|\leq |x_n-x_{N_{0}+1}|+|x_{N_{0}+1}|<1+|x_{N_{0}+1}|
$$
右侧显然是一个有限值

对于前有限项，取最大值即可

下证柯西列是 **收敛数列**：

由 B-W 定理，有界无穷数列必有收敛子列 $\{x_{n_k}\} \to a$

一方面，取定一个 N1，使得子列收敛
$$
\forall \varepsilon>0,\exists N_{1},s.t.\forall k>N_{1},|x_{n_k}-a|< \frac{\varepsilon}{2}
$$
另一方面，取定一个 N2，使得该数列满足柯西列在无穷多项时的性质
$$
\exists N_{2},s.t.\forall m,n>N_{2},|x_n-x_m|< \frac{\varepsilon}{2}
$$
综合这两个条件，取定 $N=max(N_{1},N_{2})$ 有：
$$
\forall n>N,|x_n-a|\leq |x_n-x_{n_k}| + |x_{n_k}-a| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
故收敛于 a，证毕

## 应用

### 证明闭区间套定理

[[闭区间套定理]] 

先证 **存在性**：

考察闭区间套 $\sigma_n=[a_n,b_n]$ ，必定有 $\varepsilon>0$，使得区间长度小于 $\varepsilon$
因此考察其中的子闭区间：$\sigma_{n+p}=[a_{n+p},b_{n+p}]$，因为其属于上述区间，所以必定有：
$$
|a_{n+p}-a_n|<\varepsilon,|b_{n+p}-b_n|<\varepsilon
$$

因此由柯西收敛准则，我们证明了上述两个数列为柯西列，即为收敛序列，故
$$
\exists \lim_{ n \to \infty } a_n,\exists \lim_{ n \to \infty } b_n
$$
由闭区间套的条件，我们知道：
$$
\lim_{ n \to \infty } (a_n-b_n)=0
$$
所以，取得 c，使得：
$$
c:=\lim_{ n \to \infty } a_n=\lim_{ n \to \infty } b_n
$$
下面证明 c 是符合要求的，即证 
$$
\forall n,a_n\leq c\leq b_n
$$
由柯西列，可以知道：
$$
\forall n,p\in \mathbb{N},a_n \leq a_{n+p} \leq b_{n+p}\leq b_n
$$
对于取定的 n，对 p 取极限趋于正无穷，得到：
$$
a_n\leq \lim_{ k \to \infty }a_k=c=\lim_{ k \to \infty } b_k\leq b_n
$$
因此成立

再证 **唯一性**：

假设有异于 c 的 c'满足上述条件，夹逼之即可

证毕

### 压缩映射定理

[[迭代生成数列#压缩映射定理]] 

## 函数的柯西收敛准则

### 概述

>[!note] 函数的柯西收敛准则
>$$
>\lim_{ x \to x_{0} } =A \iff \forall \varepsilon >0,\exists \delta>0,s.t.\forall x',x''\in O^-(x_{0},\delta),|f(x')-f(x'')|<\varepsilon
>$$

#### 理解

这给出了函数狭义收敛的等价说法。也即，任找一个 $x_{0}$ 的去心邻域，在这个去心邻域里的任意两个值的函数值都能够充分接近

### 证明

#### 必要性

由定义可知：
$$
\forall \varepsilon>0,\exists \delta>0,s.t.\forall x'\in O(x_{0},\delta),|f(x')-A|< \frac{\varepsilon}{2}
$$
类似地：
$$
\forall \varepsilon>0,\exists \delta>0,s.t.\forall x''\in O(x_{0},\delta),|f(x')-A|< \frac{\varepsilon}{2}
$$
两个东西对着加起来，使用绝对值不等式即可

#### 充分性

可以看出，所谓 **任找两个函数值** 的操作，与 **任找数列中两项** 的操作非常类似。我们于是可以使用序列版本的柯西收敛准则配合 [[序列极限与函数极限的关系（海涅归结原理）]] 证明上述定理

由序列极限与函数极限的关系，只要证明：
$$
\forall \{x_n\} \subset O^-(x_{0},\delta),\lim_{ n \to \infty } x_n=x_{0} ,\lim_{ n \to \infty } f(x_n)\exists
$$
将 x' 和 x'' 认为成某个数列中的两项，则对于任意取定的某个序列 $\{x_n\}$ 有：
$$
\lim_{ n \to \infty } x_n=x_{0} \iff \forall \delta >0,\exists N\in \mathbb{N},\forall n > N,|x_n-x_{0}|<\delta
$$
因此可以取得这样的 x' 和 x'' 使得：
$$
|f(x')-f(x'')|<\varepsilon
$$
这说明了 $\{f(x_n)\}$ 是基本列，也即说明 $\{f(x_n)\}$ 的极限存在，证毕

