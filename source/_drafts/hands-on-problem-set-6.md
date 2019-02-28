---
title: Hands-On ML 第六章 Notes & Exercises
tags:
  - Hands On Machine Learning
  - 决策树
---

## 摘要

回答整理 {%link "Hands On Machine Learning & Tensorflow" https://www.amazon.com/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1491962291 true %}, {% link 中文版 https://item.jd.com/12429306.html true %} 第六章练习题.
以及一些零散笔记.
<!--more-->

## 正文

#### 决策树可视化
- graphviz {%link "Windows package" https://graphviz.gitlab.io/_pages/Download/Download_windows.html true%}
- `from sklearn.tree import export_graphviz`
- `$ dot -Tpng iris_tree.dot -o iris_tree.png`

#### 基尼不纯度 还是 信息熵
基尼不纯度倾向于从树枝中分裂出最常见的类别, 而信息熵则倾向于生产更平衡的树.

**Warning: 标准答案见附录, 本文仅为整理学习, 和所学知识的再表述, 与标准答案存在一定偏差.**

1. 如果训练集有100万个实例, 训练决策树在无约束情况下大致的深度是多少?
最好情况下, 生成了平衡二叉树, 需要 math.log2(1_000_000) ≈ 20 的深度.

2. 通常来说, 子节点的基尼不纯度是高于还是低于其父节点? 是通常(更高)还是(永远)更高?
考虑叶节点和其父节点, 一般叶节点能确认一个类型(比如A), 它和另一个叶节点(用于确认B) 的样本集合构成了父节点(A U B). 因此父节点一般比子节点更加不纯.
通常更高. 考虑有A, B, C样本80, 10, 10构成100个. 根节点的判断能把A完全分出去, 左叶为A 100%, 右儿子是 B 50% / C 50%. 这种情况下 B / C 共同组成的节点的基尼不纯度高于根节点的基尼不纯度.


