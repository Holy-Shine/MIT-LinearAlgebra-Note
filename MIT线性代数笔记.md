# MIT线性代数笔记
- [第1课-方程组的几何解释](#第1课-方程组的几何解释)  
- [第2课-矩阵消元](#第2课-矩阵消元)  
- [第3课-矩阵乘法和可逆矩阵](#第3课-矩阵乘法和可逆矩阵)
- [第4课-LU分解](#第4课-LU分解)
- [第5课-转置置换和向量空间](#第5课-转置置换和向量空间)
- [第6课-列空间和零空间](#第6课-列空间和零空间)
- [第7课-求解Ax=0:主变量&特解](#第7课-求解Ax=0:主变量&特解)
- [第8课-可解性和解的结构](#第8课-可解性和解的结构)
- [第9课-线性相关性,基和维数](#第9课-线性相关性,基和维数)
- [第10课-4个基本的子空间](#第10课-4个基本的子空间)




# 第1课-方程组的几何解释

有如下方程组
$$
\tag 1
\left \{ \begin{array}
2x-y&=0\\
-x +2y&=3
\end{array}
\right.
$$
用矩阵的形式描述其行图像(row picture)和列图像(col picture)

- **行图像**
  $$
  \label 2
  \begin{bmatrix}-2 & -1 \\ -1 & 2 \end{bmatrix}\begin{bmatrix}x \\ y \end{bmatrix}=\begin{bmatrix}0  \\ 3 \end{bmatrix}
  $$
  可以看做$Ax=b$ 即:

  <img src='https://markdownfoto-1252952266.cos.ap-guangzhou.myqcloud.com/wizNote/figure_1.svg' width=60%>

  看到其本质即在二维空间中两条直线，而它们的交点 $(1,2)$ 即方程组的解。

- **列图像**

  看成列向量的线性组合：
  $$
  \label 3
  x\begin{bmatrix}2\\ -1\end{bmatrix}+y\begin{bmatrix}-1\\ 2\end{bmatrix}=\begin{bmatrix}0\\ 3\end{bmatrix}
  $$
  用图来解释

  <img src='https://markdownfoto-1252952266.cos.ap-guangzhou.myqcloud.com/wizNote/figure_2.svg' width=70%>

  其中，$\begin{bmatrix}2\\ -1\end{bmatrix}$ 即 col1, $\begin{bmatrix}-1\\ 2\end{bmatrix}$ 即 col2，而 两个向量的线性组合，得到了最终的目标向量


来看下3D的情况，假设有方程组：  
$$
\label 4
\left\{\begin{array}{}
11-4x+2y-z&=0\\
(16-2x+4y)/2-z&=0\\
(17-x+2y)/4-z&=0
\end{array}

\right.
$$
同样来看下它的行图像和列图像。

- **行图像**：

  二维空间中是直线相交，那么三维空间中即平面相交。

  <img src='https://markdownfoto-1252952266.cos.ap-guangzhou.myqcloud.com/wizNote/figure_3.svg' width=50%>



- **列图像**：

  列图像即三维空间中，三维列向量的线性组合。

于是对于这么一个问题：对于 $\forall b$ 是否一定能找到一个 $x$， 使得 $Ax=b$?

这个问题可以转化为：$A$ 矩阵列向量的线性组合能否覆盖整个向量空间，显然当 $A$ 的某两个列向量共线，则会使得矩阵退化，而不能覆盖整个空间，从而无法得到一些目标向量。



# 第2课-矩阵消元

来看下这个方程组：
$$
\tag 1
\left \{ 
\begin{array}{}
x+2y+z&=2\\
3x+8y+z&=12\\
4y+z &=6

\end{array}
\right.
$$
看成 $Ax=b$ 的形式, $A=\begin{bmatrix}1&2&1\\3&8&1\\0&4&1\end{bmatrix}$ 

消元过程如下：
$$
\tag 2
\begin{bmatrix}1&2&1\\3&8&1\\0&4&1\end{bmatrix}\Rightarrow^1 \begin{bmatrix}1&2&1\\0&2&-2\\0&4&1\end{bmatrix}\Rightarrow^2 \begin{bmatrix}1&2&1\\0&2&-2\\0&0&5\end{bmatrix}
$$
即是一个确定 **主元** 的过程：先以 $(1,1)$ 位置元素，即 1 为主元，再是 $(2,2)$ 为主元，最后的主元即 $(3,3)$ 位置的5。  

主元不能为0，则会出现不能找到主元的情况，可以进行适当的行变换，无论如何都找不到主元，则说明矩阵奇异

这个消元过程可以用 **左乘初等矩阵** 来表示 ，在介绍这个过程前，先引入概念：

$$
\notag
\begin{array}{}
matrix &\times column &= column\\
row &\times matrix &= row
\end{array}
$$

即：矩阵右乘列向量=列向量，矩阵左乘行向量=行向量，于是：
$$
\tag 3
\begin{bmatrix}-A-\\-B-\\-C-\end{bmatrix}\times M = \begin{bmatrix}AM\\BM\\CM\end{bmatrix}
$$

- **过程1**: 

  1，3行矩阵都不需要改变，因此初等矩阵$E_{2,1}$的1，3行分别是 $[1,0,0] 和 [0,0,1]$，而第二行需要1个第二行与3个第一行相减，则 $E_{2,1}$ 的第二行是$[-3,1,0]$ 则：
  $$
  \notag
  E_{2,1}=\begin{bmatrix}1&0&0\\-3&1&0\\0&0&1\end{bmatrix}, E_{2,1}\times \begin{bmatrix}1&2&1\\3&8&1\\0&4&1\end{bmatrix}=\begin{bmatrix}1&2&1\\0&2&-2\\0&4&1\end{bmatrix}
  $$



















- **过程2**:

  1，2 行不动，第3行为第3行减去两倍的第二行，则：
  $$
  \notag
  E_{3,2}=\begin{bmatrix}1&0&0\\0&1&0\\0&-2&1\end{bmatrix}, E_{2,1}\times \begin{bmatrix}1&2&1\\0&2&-2\\0&4&1\end{bmatrix}=\begin{bmatrix}1&2&1\\0&2&-2\\0&0&5\end{bmatrix}=U
  $$



















由于矩阵乘法满足结合律，则：
$$
\notag
E_{3,2}(E_{2,1}A)=U\Rightarrow (E_{3,2}E_{2,1})A=U
$$

>置换矩阵：
>
>左乘：行变换
>右乘：列变换
>$$
>\notag
>\begin{array}{}
>\begin{bmatrix}0&1\\1&0\end{bmatrix}\begin{bmatrix}a&b\\c&d\end{bmatrix}=\begin{bmatrix}c&d\\a&b\end{bmatrix}\\
>\begin{bmatrix}a&b\\c&d\end{bmatrix}\begin{bmatrix}0&1\\1&0\end{bmatrix}=\begin{bmatrix}b&a\\d&c\end{bmatrix}
>\end{array}
>$$
>

则可逆的一种直观的理解是，当某个矩阵(比如$E_{2,1}$)进行操作后，其可逆矩阵能将其还原，显然：
$$
\notag
E_{2,1}^{-1}=\begin{bmatrix}1&0&0\\3&1&0\\0&0&1\end{bmatrix}
$$



 # 第3课-矩阵乘法和可逆矩阵

## 3.1 矩阵乘法的5种描述

假设有如下矩阵乘法：
$$
A\cdot B = C
$$

- **一般描述**

  对于矩阵 $C$ 的每个 entry  $C_{ij}$： 第 $i$ 行 第 $j$ 列的元素，有: 
  $$
  C_{ij}=\sum_{k=1}^n A_{ik}\cdot B_{kj}
  $$
  直观地来讲，矩阵 $C$ 的 $(i,j)$ 位置上的元素等于 $A$ 矩阵的第 $i$ 行 行向量与 $B$ 矩阵的第 $j$ 列列向量的点积

- **矩阵x列向量描述**

  考虑 $A^{m\times n}$, $B^{n\times p}$ , 则 $C^{m\times p}$:
  $$
  [A]\begin{bmatrix}| & | &| \\ \text{col}_1 & \text{col}_2&\text{col}_3\\| & | &| \end{bmatrix}=\begin{bmatrix}| & | &| \\ A\text{col}_1 & A\text{col}_2&A\text{col}_3\\| & | &| \end{bmatrix}
  $$
  $C$ 中的每一列等于矩阵 $A$ 去乘上对应的 $B$ 中的每一列，即：**$C$ 中的每一列等于 $A$ 中列向量的线性组合**

  $A$ 有 $n$ 个列向量， $B$ 有 $p$ 个列向量，就有 $p$  组组合，所以 $C$ 有 $p$ 列，其中每个组合是这 $n$ 个列向量的线性组合

- **行向量x矩阵描述**

  同样考虑 $A^{m\times n}$, $B^{n\times p}$ , 则 $C^{m\times p}$:
  $$
  \begin{bmatrix}\text{row}_1 \\ \text{row}_2\\ \text{row}_3\end{bmatrix}[B]=\begin{bmatrix}\text{row}_1B \\ \text{row}_2B\\ \text{row}_3B\end{bmatrix}
  $$
  $C$ 中的每一行等于矩阵 $A$ 中每一行去乘上 $B$ ，即：**$C$ 中的每一行等于 $B$ 中行向量的线性组合**

- **列x行描述**

  一般的矩阵求解是左矩阵行向量与右矩阵列向量点积得到对应位置的值，那么**列向量x行向量**会怎样？

  考虑如下等式：
  $$
  \begin{bmatrix}2 & 7\\ 3 & 8\\ 4 & 9 \end{bmatrix}\begin{bmatrix}1 & 6 \\0 & 0 \end{bmatrix}=\begin{bmatrix}2  \\3 \\4 \end{bmatrix}\begin{bmatrix}1 &6\end{bmatrix}+\begin{bmatrix}7  \\8 \\9 \end{bmatrix}\begin{bmatrix}0 &0\end{bmatrix}
  $$
  即：$AB=sum(cols\ of\ A)\times (row\ of\ B)$

- **切块描述**
  $$
  \begin{bmatrix}A_1 & A_2 \\A_3 & A_4 \end{bmatrix}\begin{bmatrix}B_1 & B_2 \\B_3 & B_4 \end{bmatrix}=\begin{bmatrix}A_1B_1+A_2B_3 &..  \\ ..& .. \end{bmatrix}
  $$

















## 3.2 逆

先来讨论方阵的情况。

对于方阵 $A$, 若有 ：
$$
A^{-1}A=AA^{-1}=I
$$


则方阵 $A$ 可逆(非奇异)。

### 奇异的情况

考虑矩阵 $A$:
$$
A=\begin{bmatrix}1&3\\2&6\end{bmatrix}
$$
显然不可逆。 

- **用可逆的定义来解释这个问题**，矩阵 $A$ 右乘一个任意一个矩阵 $B$ , 等于 $A$ 中列向量的线性组合， 而 $A$ 的列空间是一条直线，则肯定不能构成单位阵所描述的空间，故 $B$ 不存在。
- **反证法**。 取列向量 $x=\begin{bmatrix}-3 \\1 \end{bmatrix}$, 则 $Ax=\begin{bmatrix}0 \\0 \end{bmatrix}$, 假设 $A$ 存在逆$A^{-1}$, 则 $A^{-1}Ax=Ix=x=\begin{bmatrix}0 \\0 \end{bmatrix}$, 矛盾。则$A$ 不可逆。

### 可逆的情况

考虑矩阵 $A$:
$$
A=\begin{bmatrix}1 & 3 \\2 & 7 \end{bmatrix}，\text{assume }A^{-1}=\begin{bmatrix}a & c \\b & d \end{bmatrix}
$$
则根据可逆定义，构成两个方程组:
$$
\left \{\begin{array}{}
\begin{bmatrix}1 & 3 \\2 & 7 \end{bmatrix}\begin{bmatrix}a  \\b \end{bmatrix}&=\begin{bmatrix}1 \\0 \end{bmatrix}\\
\begin{bmatrix}1 & 3 \\2 & 7 \end{bmatrix}\begin{bmatrix}c  \\d \end{bmatrix}&=\begin{bmatrix}0 \\1 \end{bmatrix}
\end{array}
\right.
$$
利用**高斯若尔当消元**，求解逆阵过程如下：
$$
\begin{bmatrix}1 & 3 & 1 &0\\2 & 7 & 0 &1\end{bmatrix}\Rightarrow \begin{bmatrix}1 & 3 & 1 &0\\0 & 1 & -2 &1\end{bmatrix}\Rightarrow \begin{bmatrix}1 & 0 & 7 &-3\\0 & 1 & -2 &1\end{bmatrix}
$$
则 $\begin{bmatrix}a & c \\b & d \end{bmatrix}=\begin{bmatrix}7 & -2 \\-3& 1 \end{bmatrix}$

上述过程实际上是一个多次**初等行变换** 的过程，即可以用**左乘初等矩阵** 表示,。

**证明：**

假设对于增广矩阵 $[A, I]$ 进行了一系列初等行变换，即用一系列的初等矩阵 E'=$(\cdots E\cdots)$ 左乘 增广阵：
$$
E'[A,I]=[I,E']
$$
$E'A=I\Rightarrow E'=A^{-1}$



# 第4课-LU分解

LU分解：（Lower and Upper）即将一个矩阵分解为上三角和下三角矩阵的乘积

## 4.1 低维的情况

- **二维的情况**

  简单起见，先考虑2维的情况。考虑矩阵 $A$ 的变换，目标是获得一个上三角阵，即需要确定2个主元，$E_{21}A=U$ (2,1)表示对该位置元素的变换
  $$
  \begin{bmatrix}1&0\\-4 & 1\end{bmatrix}\begin{bmatrix}2&1\\8 & 7\end{bmatrix}=\begin{bmatrix}2&1\\0 & 3\end{bmatrix}
  $$
  转化为 $A=LU$ 的形式：
  $$
  \begin{bmatrix}2&1\\8 & 7\end{bmatrix}=\begin{bmatrix}1&0\\4 & 1\end{bmatrix}\begin{bmatrix}2&1\\0 & 3\end{bmatrix}
  $$
  事实上，还可以进一步转换为 $A=LDU$ 的形式，$D$ 是一个对角阵：
  $$
  \begin{bmatrix}2&1\\8 & 7\end{bmatrix}=\begin{bmatrix}1&0\\4 & 1\end{bmatrix}\begin{bmatrix}2&\\ & 3\end{bmatrix}\begin{bmatrix}1&\frac{1}{2}\\ 0& 1\end{bmatrix}
  $$

- **三维的情况**

  对于三维的情况，矩阵$A$ 需要确定3个主元，则需要左乘初等矩阵达到目的。假设没有行变换，并且：
  $$
  E_{32}E_{31}E_{21}A=U
  $$
  显然 $A=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}U=LU$


## 4.2 置换矩阵

考虑三维的情况，所有的置换阵罗列如下：
$$
\underbrace{\begin{bmatrix}1&0&0\\0&1&0\\0&0&1\end{bmatrix}}_{\text{不交换}},\underbrace{\begin{bmatrix}0&1&0\\1&0&0\\0&0&1\end{bmatrix},\begin{bmatrix}0&0&1\\0&1&0\\1&0&0\end{bmatrix},\begin{bmatrix}1&0&0\\0&0&1\\0&1&0\end{bmatrix}}_{交换两行},\underbrace{\begin{bmatrix}0&0&1\\1&0&0\\0&1&0\end{bmatrix},\begin{bmatrix}0&1&0\\0&0&1\\1&0&0\end{bmatrix}}_{交换3行}
$$
这些矩阵组成的群中，任意两个相乘的结果任然在群中(连续两次行变换组合肯定还是行变换)，且群大小为 $n!$

对于置换阵，有$P^{-1}=P^T$



# 第5课-转置置换和向量空间

## 5.1 置换

置换矩阵 $P$ 执行换行操作，在上一课中已经讨论过低维($dim=n$) 的情况下，置换矩阵的总个数为 $n!$。

在矩阵的 LU分解中，若没有出现主元为0的情况，则 $A=LU$, 而若出现主元为0的情况，则 $PA=LU$， 即需要对 $A$ 进行相应的换行操作，使得主元不为0

## 5.2 转置

transpose($A$)=$A^T$:  $A^T_{ij}=A_{ji}$，即转置矩阵行列互换。

**对称矩阵**： $R^T=R$  的矩阵被称为对称阵，对任意矩阵 $A$, $A^TA$ 一定是对称矩阵

证明：$(A^TA)^T=A^TA$, 证明完毕

## 5.3 向量空间

一个向量空间要满足：向量的数乘和相加操作得到的向量仍然要在该空间中。

则对于 $R^2$ 空间，其有子空间

- $R^2$ 本身
- 经过$(0,0)$ 的直线（注意该直线和$R^1$空间不一样，因为该空间内的向量都有两个分量）
- $Z=\{(0,0)\}$ ，即只包含原点

推广到$R^3$:

- $R^3$ 本身
- 经过 $R^3$ 原点的直线
- 经过$R^3$ 原点的平面
- $Z=\{(0,0,0)\}$

**列空间**：

来看看矩阵是如何构建列空间的，以 $A=\begin{bmatrix}1&3\\2&3\\4&1\end{bmatrix}$ 其两个列向量$(1,2,4)^T, (3,3,1)^T$ 通过线性组合构成了矩阵的列空间 $C(A)$



# 第6课-列空间和零空间

## 6.1 列空间

先回顾一下向量空间和子空间的定义：

- **列空间**： 向量的加法和数乘封闭的空间
- **子空间**： 例如 $R^3$ 中一个过原点的平面

假设有两个子空间， $P$ 和 $L$ ，有：

- $P\cup L$ 不是子空间
- $P\cap L$ 是子空间

**证明：**

任取向量 $v,w\in P\cap L$ ，则 $v+w\in P, v+w\in L\Rightarrow v+w \in P\cap L$ ，同理，数乘也满足，则 $P\cap L$ 仍然是子空间。

假定矩阵 $A$:
$$
A=\begin{bmatrix}1&1&2\\2&1&3\\3&1&4\\4&1&5\end{bmatrix}
$$
$A$ 的列空间由其三个列向量描述，记作 $C(A)$, 显然 $C(A)\in R^4$ 。

事实上， **$A$ 的列空间由 $A$ 的所有列线性组合构成**，且$\neq R^4$ 。（3个列向量线性组合不可能充满整个$R^4$，可以联想$B=\begin{bmatrix}1&2\\2&3\\3&4\end{bmatrix}, C(B)\in R^3$,而$B$ 的列向量只能描述一个平面 ）。

根据列空间这个思路，我们看看$Ax=b$ 是否一定有解。即：
$$
\begin{bmatrix}1&1&2\\2&1&3\\3&1&4\\4&1&5\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}b_1\\b_2\\b_3\\b_4\end{bmatrix}
$$
是否有解。

由于 **$A​$ 的列空间由 $A​$ 的所有列线性组合构成**， 则 $A​$ 的列空间最多充满 $R^4​$ 中的一个 $R^3​$ 的空间，那么上述方程组(4个方程，3个未知数)不总是有解。

问题来了，**什么 $b$ 可以让方程有解？**

**当且仅当 $b$ 在 $A$ 的列空间中**，方程组有解(可以看到如果 $b=0$, 则$x=0$ 必然是方程组的解)

>$A$ 的列是否线性无关。 可以看到，对于 $A$, $col_1+col_2=col_3$，故 $A$ 的列空间是 $R^4$ 中的 $R^2$ 空间



## 6.2 零空间

考察列空间是，我们关注的是什么 $b$ 能让 方程组有解，而对于零空间，则是由 $Ax=0$ 的解构成的向量空间。我们把$A$的零空间记作 $N(A)$

显然 $x=0$ 是一个特解，则零向量在该零空间中。

形如 $\begin{bmatrix}c\\c\\-c\end{bmatrix}$ 的向量，都是方程组的解。即 $N(A)$ 是 $R^3$ 空间中的一条直线。

> 向量空间必须包含零点，离开零点则不构成向量空间。根据定义，对于空间中的任意向量 $v$， $-v+v$ 一定在该空间中，则必然包含零点

# 第7课-求解Ax=0:主变量&特解

本节来讲如何求解 $Ax=0$， 即 矩阵$A$ 的零空间。一般过程为消元(**消元不改变方程解，即不改变矩阵零空间**)

假定矩阵 $A$:
$$
A=\begin{bmatrix}1&2&2&2\\2&4&6&8\\3&6&8&10\end{bmatrix}
$$
首先可以看到矩阵 $A$ 的第三行可以由1，2两行相加得到，$A$ 的有效行为2，因此在消元过程中会出现主元缺失的情况。

## 7.1 Step1-消元

$A$ 的消元过程如下：
$$
\begin{bmatrix}1&2&2&2\\2&4&6&8\\3&6&8&10\end{bmatrix}\Rightarrow^1\begin{bmatrix}\textbf{1}&2&2&2\\0&0&\textbf{2}&4\\0&0&2&4\end{bmatrix}\Rightarrow^2\begin{bmatrix}\textbf{1}&2&2&2\\0&0&\textbf{2}&4\\0&0&0&0\end{bmatrix}=U
$$
加粗的为矩阵主元。

> 在求解第二个主元的时候，发现第二列主元位置为0，用行交换也无法获得非零主元，则可知道**第2列是前面列的线性组合**(待证明)。

我们发现矩阵 $A$ 的主元数为2，即矩阵 $A$ 的秩(Rank) $r(A)=2$

## 7.2 Step2-主列和自由列

主元所在列称为主列，其余的为自由列，对于自由列的变量，我们可以自由赋值，即对于消元后的方程组：
$$
\left\{ 
\begin{array}{}
x_1+2x_2+&2x_3+2x_4&=0\\
&2x_3+4x_4&=0
\end{array}\right.
$$
同过取$\left\{ 
\begin{array}{}
x_2&=1\\
x_4&=0
\end{array}\right.$和$\left\{ 
\begin{array}{}
x_2&=0\\
x_4&=1
\end{array}\right.$ 我们可以得到方程的两个特解：
$$
\textbf{x}_1=\begin{bmatrix}2\\1\\0\\0\end{bmatrix},\textbf{x}_2=\begin{bmatrix}2\\0\\-2\\1\end{bmatrix}
$$
两个特解都在矩阵 $A$ 的零空间中，则 $A$ 的解集(零空间)为：
$$
N(A)=c\begin{bmatrix}2\\1\\0\\0\end{bmatrix}+d\begin{bmatrix}2\\0\\-2\\1\end{bmatrix}
$$
其中 $c,d$ 为任意实数。

> 我们看到，对于 $m\times n$ 的秩为 $r$ 的 矩阵，自由变量的个数为 $n-r​$ 

## 7.3 简化行阶梯形式

$A$ 的最终化简结果$U$为行阶梯形式，事实上可以进一步化简，使得：

- 主元都是1
- 主元上下方为0

化简的最终形式我们称之为简化行阶梯形式，记作为 $R$

化简过程如下：
$$
U=\begin{bmatrix}\textbf{1}&2&2&2\\0&0&\textbf{2}&4\\0&0&0&0\end{bmatrix}\Rightarrow^1\begin{bmatrix}\textbf{1}&2&0&-2\\0&0&\textbf{2}&4\\0&0&2&4\end{bmatrix}\Rightarrow^2\begin{bmatrix}\textbf{1}&2&0&-2\\0&0&\textbf{1}&2\\0&0&0&0\end{bmatrix}=R
$$
此时矩阵 $R$ 的主列即单位矩阵 $I$ , 而自由列我们记为 $F​$（Free）。

原方程的形式$ Ux=0$ 转化为了 $Rx=0$， 即：
$$
R=\begin{bmatrix}I&F\\0&0\end{bmatrix}, RN(A)=0\Rightarrow N(A)=\begin{bmatrix}-F\\I\end{bmatrix}
$$



# 第8课-可解性和解的结构

## 8.1 可解性

考虑方程和对应的增广矩阵：
$$
\left \{
\begin{array}{}
x_1+2x_2+2x_3+2x_4 &=b_1\\
2x_1+4x_2+6x_3+8x_4 &=b_2\\
3x_1+6x_2+8x_3+10x_4 &=b_3\\
\end{array}
\right.\Rightarrow^{\text{augmented matrix}}
\begin{bmatrix}
1&2&2&2&b_1\\
2&4&6&8&b_2\\
3&6&8&10&b_3\\
\end{bmatrix}
$$
其中：
$$
A=\begin{bmatrix}
1&2&2&2\\
2&4&6&8\\
3&6&8&10\\
\end{bmatrix},
x=\begin{bmatrix}
x_1\\
x_2\\
x_3\\
x_4\\
\end{bmatrix}
b=\begin{bmatrix}
b_1\\
b_2\\
b_3\\
\end{bmatrix}
$$


为了求解 $Ax=b$ 我们需要对增广阵进行消元。

消元结果如下(加粗为矩阵主元)：
$$
\begin{bmatrix}
\textbf{1}&2&2&2&b_1\\
0&0&\textbf{2}&4&b_2-2b_1\\
0&0&0&0&b_3-b_2-b_1\\
\end{bmatrix}
$$
若希望方程有解，则显然需要满足 $b_3-b_2-b_1=0$

又有：全0行表示消元前第三行可以由其他行线性组合得到，所以可知：

**若$A$的其他行线性组合得到0，则相应位置的 $b$ 进行相应的线性组合也要等于0**

> 我们同样可以用列空间的概率来讨论可解性的问题：
>
> **仅当 $b$ 在 $A$ 的列空间内($b\in C(A)$)** 才有解

## 8.2 全解的形式

全解的求解步骤：

- 找一个特解$x_p$
  - 置所有自由变量(所在列无主元)为0
  - 解出 $Ax=b$ 中的主变量
- 求出$A$的零空间$N(A)$,事实上，这个就是齐次线性方程组的**基础解系**。

则方程的全解为特解+零空间的任意向量，即： $x_p+N(A)$

> **证明：**
>
> $Ax_p=b, Ax_n = 0\Rightarrow A(x_p+x_n)=b$

运用上述步骤，我们求解章节初的方程。

**① 找一个特解**

令 $x_2=x_4=0$ 得到 $\left \{
\begin{array}{}
x_1+&2x_3 &=1\\
&2x_3&=3\\
\end{array}
\right.$，解得 $x_p=\begin{bmatrix}-2\\0\\3/2\\0\end{bmatrix}$

**② 零空间**

对于自由变量，分别取0，1和1，0（上一节讲过），得到零空间一组基向量，得到：
$$
N(A)=c_1\begin{bmatrix}-2\\1\\0\\0\end{bmatrix}+c_2\begin{bmatrix}-2\\0\\-2\\1\end{bmatrix}
$$
则全解：
$$
x_{\text{complete}}=\begin{bmatrix}-2\\0\\3/2\\0\end{bmatrix}+c_1\begin{bmatrix}-2\\1\\0\\0\end{bmatrix}+c_2\begin{bmatrix}-2\\0\\-2\\1\end{bmatrix}
$$
零空间为 $R^4$ 中一个二维平面，则全解也是一个二维平面(但不是子空间，因为不过原点)



## 8.3 秩对解的影响

总共有4种情况。

考虑$A^{m\times n}$，$A$的秩为 $\text{rank}(A)=r$。

**① $r=n<m$**

即每一列都有主元，此时自由变量个数为0，即零空间(基础解系)只有一个零点，根据全解构成，直到此时有一个或0个解。

例如：$A=\begin{bmatrix}1&3\\3&1\\6&1\\5&1\end{bmatrix}$， 其简化行阶梯(rref)形式为$R=\begin{bmatrix}1&0\\0&1\\0&0\\0&0\end{bmatrix}=\begin{bmatrix}I\\F\end{bmatrix}$

当3，4列的 $b$ 不为 0 的时候，方程无解，若均为0，则必有解。

**② $r=m<n$**

即每一行都有主元，此时自由变量个数为 $n-r=n-m$，此时方程必有无穷个解

例如：$A=\begin{bmatrix}1&2&6&5\\3&1&1&1\end{bmatrix}$，简化行阶梯形式为$R=\begin{bmatrix}1&0&F\\0&1&F\end{bmatrix}$，无论 $b$ 为何值，都能通过自由变量的取值得到相应的解。

**③ $r=m=n$**

满秩，则矩阵可逆，显然有 $x=A^{-1}b$ 有唯一解。同时其简化行阶梯形式即为单位矩阵 $I$, 表明其零空间为0

**④ $r<m,r<n$**

此时$R=\begin{bmatrix}I&F\\0&0\end{bmatrix}$

若满足全0行，则有无穷个解，否则无解。



# 第9课-线性相关性,基和维数

## 9.1 背景

对于矩阵 $A^{m\times n}, m<n$ 描述的齐次线性方程组，$Ax=0$ 必有非零解。

$m<n$， 则必有$n-m$ 个自由变量



## 9.2 线性无关性

**定义**：

对于向量组：$v_1, v_2,..., v_n$ ，对于任意非0向量 $c$，总有：
$$
c_1v_1+c_2v_2+\cdots+c_nv_n\neq 0
$$
则利用刚才的背景知识，**平面内三个向量一定线性相关**。

取 $A=\begin{bmatrix}v_1,v_2,v_3\end{bmatrix}=\begin{bmatrix}2&1&2.5\\1&2&-1\end{bmatrix}$，三个平面向量构成了 $A$ 的列向量，根据线性无关定义，即证明：

$\begin{bmatrix}2&1&2.5\\1&2&-1\end{bmatrix}\begin{bmatrix}c_1\\c_2\\c_3\end{bmatrix}=0$ 有非零解，显然成立，即矩阵 $A$ 的零空间不仅包含原点

>  $v_1, v_2,...,v_n$ 是 $A^{m\times n}$ 的列向量：
>
>  - 若这组向量线性无关，则 $N(A)=\{0\}$, 即$A$ 的零空间只包含原点，同时 $rank(A)=n$
>  - 若这组向量线性相关，则 $Ac=0$ 对于非零向量$c$ 成立，同时，$rank(A)<n$



## 9.3 基和维数

再讲基之前，我们先讲生成空间。

我们知道一组向量 $v_1, v_2,\cdots, v_n$ 可以生成一个空间，该空间包含这些向量的所有线性组合。  

我们关注 **这样的向量组**：向量的个数不多不少，刚好可以构成空间：

- 个数太少则无法构成空间
- 个数太多则会有线性相关

这里的向量组就是生成空间的一组 **基**, 基要满足下列条件：

- 线性无关
- 可以构成向量空间

观察一下 $\R^3$ 的两组基(矩阵的列向量)：
$$
\begin{bmatrix}0&0&1\\0&1&0\\1&0&0\end{bmatrix},\begin{bmatrix}1&2&3\\1&2&3\\2&5&8\end{bmatrix}
$$
可以知道基不只有一组，只要其构成的矩阵可逆，即可构成一组基。

虽然基有多组，但是他们有一个共同点：**基向量的个数相同**， 比如上面两组基向量的个数都是3，都等于空间的**维数**。于是有：

$rank(A)=$主列个数$=A$的列空间的维数



# 第10课-4个基本的子空间

对于矩阵 $A^{m\times n}$, 其4个基本子空间分别为：

- 列空间 $C(A)$
- 零空间 $N(A)$
- 行空间 $C(A^T)$
- 左零空间 $N(A^T)$

行空间、左零空间分别是**矩阵转置**后的列空间和零空间。

讨论一下四个子空间各自所处的空间，显然有：
$$
C(A), N(A)\in \R^n; C(A^T),N(A^T)\in \R^m
$$

## 10.1 子空间的基

在讨论这4个子空间的基前，我们要知道它们各自的维数。

假设矩阵$A$ 的秩为 $\text{rank}(A)=r$，代表矩阵主列有 $r$ 列，有

**① $\text{dim}(C(A))=r$ 且 $A$ 的主列即 $C(A)$ 的一组基**

**② $\text{dim}(N(A))=n-r$且$Ax=0$ 的特解们即 $N(A)$的一组基(自由变量个数为 $n-r$则特解个数相应为$n-r$)**

**③ $\text{dim}(C(A^T))=\text{dim}(C(A))=r$**

**④ $\text{dim}(N(A^T))=m-r$**

这里再说明下行空间和左零空间的基，方便讨论，假设$A$ 矩阵的行最简形式变换如下：
$$
A=\begin{bmatrix}1&2&3&1\\1&1&2&1\\1&2&3&1\end{bmatrix}\rightarrow \begin{bmatrix}1&0&1&1\\0&1&1&0\\0&0&0&0\end{bmatrix}=R
$$
显然$A$ 的列空间发生了变化($[1,1,1]^T$在 $C(A)$ 中而不在 $C(R)$ 中)，即 $C(A)\neq C(R)$，可见：**行初等变换改变了列空间，而不改变行空间**，因为本质上，行初等变换是行向量的线性组合，必然不改变行空间。

于是，**行空间的基可以由 $R$ 的前 $r$ 行行向量构成**

至于左零空间，首先来说明为啥叫左零空间。

对于做左零空间，即使求 $A^Ty=0$ 的解，$A$ 的左零空间包含这些解向量，于是 $y^T A = 0^T$ ，如何求这个 $y^T$ ？

事实上，这个求解过程隐藏在了上述消元过程中，回顾下高斯若尔当消元。
$$
[A^{m\times n}, I^{m\times m}]\rightarrow [R^{m\times n}, E^{m\times m}]
$$
矩阵 $E$ 记录了$A$ 的所有消元操作(行操作)。而行操作是一个左乘矩阵的操作，即:
$$
E[A^{m\times n}, I^{m\times m}]=[R^{m\times n}, E^{m\times m}]
$$
这里$E=\begin{bmatrix}-1&2&0\\1&-1&0\\-1&0&1\end{bmatrix}$：
$$
\begin{bmatrix}-1&2&0\\1&-1&0\\\textbf{-1}&\textbf{0}&\textbf{1}\end{bmatrix}\begin{bmatrix}1&2&3&1\\1&1&2&1\\1&2&3&1\end{bmatrix}=\begin{bmatrix}1&0&1&1\\0&1&1&0\\0&0&0&0\end{bmatrix}=R
$$
上式说明了零空间维数和基向量：

- 维数：$R$ 的零行行数
- 基向量：对应 $R$ 的零行的 $E$ 的行向量(那几行可以使得 $A$ 行向量组合为0)