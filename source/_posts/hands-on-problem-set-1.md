---
title: Hands-On ML 第一章 Notes & Exercises
tags:
  - Hands On Machine Learning
date: 2019-02-18 14:12:31
updated: 2019-02-28 15:12:00
---


## 摘要

回答整理 {%link "Hands On Machine Learning & Tensorflow" https://www.amazon.com/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1491962291 true %}, {% link 中文版 https://item.jd.com/12429306.html true %} 第一章练习题.
以及一些零散笔记.
<!--more-->

## 正文

**Warning: 标准答案见附录, 本文仅为整理学习, 和所学知识的再表述, 与标准答案存在一定偏差.**

1.  How would you define Machine Learning? (你如何定义机器学习?)
    - 机器学习是一种科学(和艺术), 让计算机编程变为**从数据中学习(learn from data)**.
    - 不用**显式地编程**就能学习(出一个 Model, 用于完成目标任务)
    - 形式化的定义: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.

2. Can you name four types of problems where it shines? (机器学习在哪些问题上表现突出?)

| Task                 | 传统方法                                 | 机器学习                                                                       | 总结                                  |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------- |
| 垃圾邮件过滤器, 编写 | 一长串规则, 难以覆盖所有 case            | 数据进, 模型出, 再评估模型                                                     | 避免复杂手工规则                      |
| 垃圾邮件过滤器, 更新 | 出现一种就要添加规则, 并保证和原有不冲突 | 带着新数据再训练一次                                                           | 高可维护性                            |
| 语音识别             | 没有好用的传统算法                       | 数据进, 模型出, 并且具备更好的**可扩展性**                                     | 可扩展性 + 解决传统方法难以处理的问题 |
| 数据挖掘             | /                                        | 可以试试多个 Model, 根据模型的解释, 找到初步数据 data explore 时难以发现的模式 | 帮助人们发现未发现的数据特征          |

4. What are the two most common supervised tasks? (请举出二种常见的监督式学习任务)
5. Can you name four common unsupervised tasks? (请举出四种常见的非监督式学习任务)

| 监督式 | 非监督式                                                                    |
| ------ | --------------------------------------------------------------------------- |
| 分类   | 聚类(k-Means, 分层聚类(HCA), 最大期望)                                      |
| 回归   | 可视化和降维(PCA, kernel PCA, 局部线性嵌入(LLE), t-分布随机近似嵌入(t-SNE)) |
| /      | 关联规则学习(Apriori, Eclat)                                                |

Note:
关联规则学习: 目的是挖掘大量数据, 发现属性之间的有趣联系.

6. What type of Machine Learning algorithm would you use to allow a robot to walk in various unknown terrains? (如果要让一个机器人在各种未知的地形中行走, 你会使用什么类型的机器学习算法?)
  
    - 用强化学习.  An agent(智能体), can observe the environment, select and perform actions, and get rewards or penalties in return.

7. 要将顾客分成多个组, 你会使用什么类型的算法?
  
    - 当分组不明确时, 可以采用聚类算法生成分组类别. 当分组明确后, 就可以采用监督式学习方法, 对新用户分组到现有类别中.

9. 什么是在线学习系统?

    - 批量学习(Batch leaning): 必须在全数据集上训练的的学习系统, 占用计算资源多, 通常情形下只能离线完成, 又名离线学习(offline learning). 
    - 在线学习(Online Learning): In online learning, you train the system incrementally by feeding it data instances sequentially, either **individually** or by small groups called **mini-batches**. Each learning step is fast and cheap, so the system can learn about new data on the fly.

    Note: 训练, 评估, 启动学习系统是可以轻易地自动化的, 所以只要计算资源充足, 成本/时间代价可接受, 批量学习也不是不可取的.

10. 什么是核外学习? (What is out-of-core learning?)
    - Page 23
    ONLINE learning algorithms can also be used to train systems on huge datasets 
    that cannot fit in one machine’s main memory (this is called out-of-core learning). 
    THE algorithm loads part of the data, runs a training step on that data, 
    and repeats the process until it has run on all of the data


11. What type of learning algorithm relies on a similarity measure to make predictions?
    - 基于实例的学习(Instance-Based Learning). 比如垃圾邮件分类, 做一个相似度度量算法, 然后对新data, 计算所有既有labeled data的相似度, 根据最相似的那个labeled data来判断是否是垃圾邮件.


12. **模型参数** vs 学习算法的**超参数**(hyperparameter)

    - 模型参数: 决定模型对数据会怎样预测
    - 学习算法: 优化模型参数至模型参数能最好地泛化到训练集
    - 超参数: 学习算法的参数


13. 基于模型的学习算法搜索的是什么? 他们最常用的策略是什么? 他们如何做出预测?

    - 搜索目标: 最佳的组合参数让模型具有最好的泛化性能.
    - 策略: 构造成本函数, 成本函数用来衡量系统有多坏, 如果模型有正则化(regularization, `to make model simpler and reduce the risk of overfitting`), 则再加上一个对模型复杂度的惩罚. 策略即搜索成本函数的最小值.


14. 机器学习中的四个主要挑战:
    - 书P29 - P35
    - 训练数据数量不足  
        - 扩展阅读: 数据的不合理有效性 {% link "The Unreasonable Effectiveness of Data" http://static.googleusercontent.com/media/research.google.com/fr//pubs/archive/35179.pdf true %}
    - 训练数据不具代表性
        - 采样集太小, 将会出现采样噪声(即非代表性数据进入数据集)
        - 采样集非常大, 很可能(因为采样方法欠妥), 导致得到非代表性数据, 例子见P31(兰登vs罗斯福的选举民意调研).
    - 质量差的数据
        - 丢弃异常情况, 或者对齐进行修复
        - 记录缺失部分特征: 忽略该特征/忽略该实例/(基于某些假设)填充缺失值
    - 无关特征
        - **一个成功的机器学习项目, 关键部分是提取出一组好的用来训练的特征集, 即特征工程**
            - 特征选择
            - 特征提取(整合现有特征, 产生更有用特征)
            - 通过收集新数据创造特征
    - 模型太简单: 欠拟合
    - 模型太复杂: 过拟合


15. 如果你的模型在训练数据上表现很好, 但是应用到新的实例上的泛化结果却很糟糕, 是怎么回事? 能提出三种可能的解决方案吗?
    - 模型在训练数据上过拟合了.
    - 解决方法:
        - 引入更多数据.
        - 对模型进行化简(对模型进行正则化, 选择更简单模型, 减少输入特征)
        - 减少训练数据中的噪声


16. 什么是测试集, 为什么要使用测试集
    - 测试集: 用于**评估**模型在新实例的泛化误差, 用于模型上线前的测试评估.
    - **不用于模型选择**, 最后才能去看测试集.

17. 验证集的目的是什么?
    - 用于比较不同的模型, 来选择最佳的模型和调整超参数.


18. 如何使用测试集调整超参数会出现什么问题?
    - 出现模型在训练+测试集上的过拟合, 导致测试集误差过于乐观, 上线后性能GG. 


19. 什么是交叉验证? 它为什么比验证集更好?
    - 交叉验证: 将训练集分成若干个互补子集, 然后每个模型都通过这些子集的不同组合来训练, 之后用剩余的子集进行验证.
        - *模型和超参数确定后, 再对整个训练集进行一次训练, 得到用于到测试集上评估的模型.*
    - 不需要单独划分一块验证集, 节省了宝贵的训练数据.
