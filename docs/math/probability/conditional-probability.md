## 概述

当某事件已经发生时，一些随机事件的概率会因为已知信息的增加发生变化。例如在手游抽卡时，我们可能会认为单次抽卡出六星与不出六星是等概率的，但随着我们连抽 $50$ 发一个六星都没有，再固执地认为「出六星与不出六星等概率」就显得不是那么明智。

总之，研究在某些已知条件下事件发生的概率是必要的。

## 条件概率

### 定义

若已知事件 $A$ 发生，在此条件下事件 $B$ 发生的概率称为 **条件概率**，记作 $P(B|A)$。

在概率空间 $(\Omega, \mathcal{F}, P)$ 中，若事件 $A \in \mathcal{F}$ 满足 $P(A) > 0$，则条件概率 $P(\cdot|A)$ 定义为

$$
P(B|A) = \frac{P(AB)}{P(A)} \quad \forall B \in \mathcal{F}
$$

可以验证根据上式定义出的 $P(\cdot|A)$ 是 $(\Omega, \mathcal{F})$ 上的概率函数。

根据条件概率的定义可以直接推出下面两个等式：

-   **概率乘法公式**：在概率空间 $(\Omega, \mathcal{F}, P)$ 中，若 $P(A) > 0$，则对任意事件 $B$ 都有

$$
P(AB) = P(A)P(B|A)
$$

-   **全概率公式**：在概率空间 $(\Omega, \mathcal{F}, P)$ 中，若一组事件 $A_1, \cdots, A_n$ 两两不交且和为 $\Omega$，则对任意事件 $B$ 都有

$$
P(B) = \sum_{i=1}^{n} P(A_i)P(B|A_i)
$$

### Bayes 公式

一般来说，设可能导致事件 $B$ 发生的原因为 $A_1, A_2, \cdots, A_n$，则在 $P(A_i)$ 和 $P(B|A_i)$ 已知时可以通过全概率公式计算事件 $B$ 发生的概率。但在很多情况下，我们需要根据「事件 $B$ 发生」这一结果反推其各个原因事件的发生概率。于是有

$$
P(A_i|B) = \frac{P(A_iB)}{P(B)} = \frac{P(A_i)P(B|A_i)}{\sum_{j=1}^{n} P(A_j)P(B|A_j)}
$$

上式即 Bayes 公式。

## 事件的独立性

在研究条件概率的过程中，可能会出现 $P(B|A) = P(B)$ 的情况。从直观上讲就是事件 $B$ 是否发生并不会告诉我们关于事件 $A$ 的任何信息，即事件 $B$ 与事件 $A$「无关」。于是我们就有了下面的定义

### 定义

若同一概率空间中的事件 $A$,$B$ 满足

$$
P(AB) = P(A)P(B)
$$

则称 $A$,$B$  **独立**。对于多个事件 $A_1, A_2, \cdots, A_n$，我们称其独立，当且仅当对任意一组事件 $\{ A_{i_k} : 1 \leq i_1 < i_2 < \cdots < i_k \leq n \}$ 都有

$$
P( A_{i_1}A_{i_2} \cdots A_{i_r} ) = \prod_{k=1}^{r} P(A_{i_k})
$$

### 多个事件的独立性

对于多个事件，一般不能从两两独立推出这些事件独立。考虑以下反例：

有一个正四面体骰子，其中三面被分别涂成红色、绿色、蓝色，另一面则三色皆有。现在扔一次该骰子，令事件 $A$,$B$,$C$ 分别表示与桌面接触的一面包含红色、绿色、蓝色。

不难计算 $P(A) = P(B) = P(C) = \frac{1}{2}$，而 $P(AB) = P(BC) = P(CA) = P(ABC) = \frac{1}{4}$。

显然 $A, B, C$ 两两独立，但由于 $P(ABC) \neq P(A)P(B)P(C)$，故 $A, B, C$ 不独立。