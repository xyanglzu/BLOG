---
title: 机器学习模型对比.md
toc: true
date: 2018-08-12 17:38:04
tags: 机器学习
categories: 机器学习
---

# 朴素贝叶斯法

风险函数为最大后验概率：
$$
f(x) = \text{argmax}_{c_k} P(c_k | X = x)
$$
即：
$$
f(x) = \text{argmax}_{c_k} \frac{P(Y=c_k)\Pi_j P(X^{(j)} = x^{(j)} | Y = c_k)} {\sum_k{P(Y=c_k)\Pi_j P(X^{(j)} = x^{(j)} | Y = c_k)}}
$$
最大似然估计不考虑先验概率，将其作为1；

最大后验概率考虑先验概率，即$P(Y=c_k)$。