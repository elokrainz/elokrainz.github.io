---
title: 一道网易面试题--英雄升级
date: 2014-11-11 22:00
layout: post
category: Mathematics
tags: interview probability
description: "Welcome to my new website!."
excerpt: "英雄升级,
          从0级升到1级,概率100%.
          从1级升到2级,有1/3的可能成功;1/3的可能停留原级;1/3的可能下降到0级;
          从2级升到3级,有1/9的可能成功;4/9的可能停留原级;4/9的可能下降到1级.
          每次升级要花费一个宝石,不管成功还是停留还是降级.
"
---
英雄升级,

&#8194;&#8194;从0级升到1级,概率100%.

&#8194;&#8194;从1级升到2级,有$$\frac{1}{3}$$的可能成功;$$\frac{1}{3}$$的可能停留原级;$$\frac{1}{3}$$的可能下降到0级;

&#8194;&#8194;从2级升到3级,有$$\frac{1}{9}$$的可能成功;$$\frac{4}{9}$$的可能停留原级;$$\frac{4}{9}$$的可能下降到1级.

&#8194;&#8194;每次升级要花费一个宝石,不管成功还是停留还是降级.

&#8194;&#8194;求英雄从0级升到3级平均花费的宝石数目.

看完题目后,大脑就自动脑补状态转移方程了…果然码农的属性已然根深蒂固…

一开始想正面求解,于是,就出现了…

$$
E(1) = 1 \times 1
$$
$$
E(2) = \frac{1}{3} \times 1 + \frac{1}{3} \times \big( 1 + \frac{1}{3} \times 1 + \frac{1}{3} \times ( 1 + \frac{1}{3} \times 1 + \frac{1}{3} + \cdots ) + \frac{1}{3} \times ( 1 + 1 \times 1 + \cdots) \big)
       + \frac{1}{3} \times big( 1 + 1 \times 1 + \frac{1}{3} \times 1 + \frac{1}{3} \times ( 1 + \frac{1}{3} \times 1 + \frac{1}{3} \times ( 1 + \frac{1}{3} \times 1 + \frac{1}{3} + \cdots ))\big) \\
$$
$$
E(3) =  \frac{1}{9} \times 1 +  \frac{4}{9} \times \big( 1 + \frac{1}{9} \times 1 +  \cdots\big) + \ldots \\

其中, E(x) 表示英雄从x-1级升到x级所需宝石的期望数.
$$

这...要不要拆括号求和呢???

(ˇ_ˇ)....

$$
E(2) = \frac{1}{3} \times 1 + \frac{1}{3} \times \big( 1 + \underbrace{\frac{1}{3} \times 1 + \frac{1}{3} \times ( 1 + \frac{1}{3} \times 1 + \frac{1}{3} + \cdots ) + \frac{1}{3} \times ( 1 + 1 \times 1 + \cdots)}_{这货不就是...} \big) + \cdots \\
$$

好吧...

$$
\begin{align}
E(1) = 1 \times 1  &\\
E(2) = \frac{1}{3} \times 1 + \frac{1}{3} \times ( 1 + E(2) ) +  \frac{1}{3} \times ( 1 + E(1) + E(2) ) &\\
E(3) = \frac{1}{9} \times 1 + \frac{4}{9} \times ( 1 + E(3) ) +  \frac{4}{9} \times ( 1 + E(2) + E(3) ) &\\
\end{align}
$$

于是乎... 从0级升到3级平均需要$$E(1)+E(2)+E(3) = 30$$个宝石.

最后,我想说......

还可以写个程序模拟一下嘛~~~



