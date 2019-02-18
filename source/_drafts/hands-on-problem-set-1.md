---
title: hands-on-problem-set-1
tags:
---

## 摘要

回答 {%link "Hands On Machine Learning & Tensorflow" https://www.amazon.com/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1491962291 true %} 第一章练习题.
以及一些零散笔记.
<!--more-->

## 正文

1.  How would you define Machine Learning?

**答:**  机器学习是一种科学(和艺术), 让计算机编程变为**从数据中学习(learn from data)**.
- 不用**显式地编程**就能学习(出一个 Model, 用于完成目标任务)
- 形式化的定义: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.

2. Can you name four types of problems where it shines?
**答:**

| Task                 | 传统方法                                 | 机器学习                                                                       | 总结                                  |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------- |
| 垃圾邮件过滤器, 编写 | 一长串规则, 难以覆盖所有 case            | 数据进, 模型出, 再评估模型                                                     | 避免复杂手工规则                      |
| 垃圾邮件过滤器, 更新 | 出现一种就要添加规则, 并保证和原有不冲突 | 带着新数据再训练一次                                                           | 高可维护性                            |
| 语音识别             | 没有好用的传统算法                       | 数据进, 模型出, 并且具备更好的**可扩展性**                                     | 可扩展性 + 解决传统方法难以处理的问题 |
| 数据挖掘             | /                                        | 可以试试多个 Model, 根据模型的解释, 找到初步数据 data explore 时难以发现的模式 | 帮助人们发现未发现的数据特征          |

4. What are the two most common supervised tasks?
5. Can you name four common unsupervised tasks?
**答:**

| 监督式 | 非监督式                                                                    |
| ------ | --------------------------------------------------------------------------- |
| 分类   | 聚类(k-Means, 分层聚类(HCA), 最大期望)                                      |
| 回归   | 可视化和降维(PCA, kernel PCA, 局部线性嵌入(LLE), t-分布随机近似嵌入(t-SNE)) |
| /      | 关联规则学习(Apriori, Eclat)                                                |

Note:
关联规则学习: 目的是挖掘大量数据, 发现属性之间的有趣联系.

6. What type of Machine Learning algorithm would you use to allow a robot to walk in various unknown terrains?
**答:** 用强化学习.  An agent(智能体), can observe the environment, select and perform actions, and get rewards or penalties in return.

