---
title: 用机器学习方法预测硬盘使用数据
tags:
- lstm
- machine learning
- keras
---

## 主要内容
1. 准备工作
    1. data explore
    2. 如何为LSTM准备输入
    3. 如何划分验证集, 测试集
    4. 误差metric选取
        1. `r2_score for keras`
2. 模型训练
    - DNN / AR / LSTM
3. 结果分析

<!--more-->


...TODO: 观察数据
**经过上述对数据的观察, 我认为服务器硬盘使用量对于时间已经有了明显的规律性, 所以当成一个单变量的时序问题是可行的.**

### 1.2 如何为LSTM准备数据

