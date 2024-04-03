# TalkMatev2

chat as a real human

## 训练日记

### 数据切分

* 统计群聊中发言数目最多的N个人（前10%）进行训练，切分思路如下：
1. 对于用户i来说找到最近一次发言的位置，将前一次发言结束和这一次发言开始的之间的作为聊天context；
2. 将之前不规则且可能有符号干扰的用户名映射到统一命名的空间；将引用某人的地方有名字出现时也用新命名替代；
3. 连续发言（中间无其他人发言时）进行合并

### 训练思路

* 直接按传统多轮对话数据及进行训练
**缺点：** 在群聊的场景下，发言较短，可学的部分太少，训练效率太低，而输入上下文太长

* 其他大模型整理成ReAct模板进行回复
**优点：** 回答有理有据，可学习部分很多
**缺点：** 非常消耗token来标注；很依赖标注模型的能力

* 参考斯坦福小镇中的智能体设计

