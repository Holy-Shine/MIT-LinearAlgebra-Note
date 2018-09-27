# MIT线性代数笔记
- [第1课-方程组的几何解释](#第1课-方程组的几何解释)  
- [第2课-矩阵消元](#第2课-矩阵消元)  
- [第3课-矩阵乘法和可逆矩阵](#第3课-矩阵乘法和可逆矩阵)  




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