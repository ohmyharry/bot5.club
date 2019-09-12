---
title: "搞定一个对话平台"
author: qhduan
categories: talks
tags:
  - dialog system
  - chatbot
---

搞定一个对话平台

## 最好别用对话

- 对话系统还没有统一的规范。思考一下wit.ai，dialogflow，botframework，rasa这几个产品哪个产品有统治地位？没有，他们的设计规范一样吗？不同。
- 没有很好的平台。没人有统治地位，维护都有风险
- 消费者还没习惯。消费者刚刚习惯app，刚刚尝试习惯智能音箱，现在是好时候吗？
- 有太多很好的替代品。网页HTML5、小程序、命令式而不是自然语言等等都是可能的替代品。
- 对话总是会错的，能接受吗？如果你或你的客户必须要你保证正确，还是别对话了，人和人交流都不太容易，真的。

## 能不能不用对话？

- 你能接受自然语言不准确吗？其实命令式很好，到现在所有股票交易软件都保持着用各种指令、简写或数字就能下单的良好习俗，说明专业人士能学习，愿意学习。
- 用户其实也在学习。只要你的功能真的有用，用户是真的会学习的，他们对觉得有用的产品是不会说：“请给我买一杯咖啡”，其实真正用的时候他们只会说：“1杯咖啡”
- 命令其实很好。真的，用户会去掌握的，slack也证明了。
- 按钮或许更好。其实用app和小程序在很多时候能解决问题，最差也是按钮、命令和自然语言的相互配合，而不能仅仅靠自然语言。
- 抛弃幻想，肯定不准的。在现在，自然语言肯定不准的，未来？那大概率也不一定，现在人和人交流依然困难

## 是否真的需要对话

- 是否真的有无法改变的场景？
- 是否客户真的只能习惯对话，如果真的客户只能接受自然语言对话而不是命令式方法，这个场景是真实的吗？
- 对话技术是否只作为辅助，如果你用命令式其似乎也可以用类似自然语言和对话系统的技术的。

## 用什么对话

- 程序员和产品经理谁更便宜？
- 犯错了的时候，如何快速处理？谁处理？

产品经理可以决定数据、标注、对话流。
程序员设计、实现对话流。

如果前者便宜，那可以试试类似rasa的平台，如果后者便宜，尽量还是用botframework这样规则逻辑的平台。

## 问答与知识问答

- FAQ
- Factoid
- Non-factoid

这些如何分别实现，是否实现

## NLU是很重要的

- 它的意图识别其实比较准，如果你知道什么是意图的话。
- 槽值提取不够准的，如何修正？

### NLU的意图是什么

意图是什么？一个最常见的错误是这样的：

- 我要买一张火车票？

大部分人会认为这个意图是“买票”或者“买火车票”，这个问题不大

那假设我们说：

- 一张

这句话的意图是什么？
大部分人的回答是：我怎么知道，它没意图啊。
这就说明这个人没懂NLU在做什么。

NLU的本质就是解析“一句话”的意图，
一句话的意思是没有上下文，所以这句话自然也应该有意图，那它的意图是什么呢？

在绝大多数解决方案（学术研究）中，第二句话的意图是“inform”，
也就是说只是机器人提供一个信息给人而已，这个信息是“一”“张”。

至于这是一张火车票？电影票？这些是要由后续的机制，如对话管理来根据上下文判断并给出结果的。

### 槽值怎么准？

- 词表
- 更多例句和模板
- 用各种规则修正

## 对话选择

- RASA尝试通过定义对话流程并准备很多数据制作机器人
- BotFramework用规则制作机器人
- 程序员便宜还是产品经理便宜？
  - 找一个很懂对话的产品经理并能带领团队制造很多对话训练数据便宜？
  - 还是找一个很会写规则机器人的程序员便宜？
- 错了谁修正？是由产品经理修正对话流还是程序员修正逻辑？
- 是否选择安全的？规则永远比统计“安全”
- 容忍错误吗？容忍什么类型的错误？

## 对话设计

- 解决什么问题
- 怎么解决问题，即解决问题需要什么

- 客服
  - 一般问答 FAQ 店在哪？（常用问答）
  - 商品问答 KBQA 半岛咖啡有咖啡因吗？（基于“半岛咖啡”这个实体的问答）
  - 下单 Task-oriented DS （收集下单需要的信息，然后下单）
- 咖啡
  - 第一次买咖啡 Task-oriented DS
  - 其他买咖啡 某种Guess & Good luck 策略

## 解决问题的要素是最重要的

- FAQ
  - 往往要素就是一句话
- KBQA
  - 要素往往是一个实体和一个关系
- Task-oriented DS
  - 要素是所有要完成这个任务的上下文、元素、用户选择等等

## 如何收集要素

- NLU
- NLU + 词表
- NLU + 词表 + 规则
- NLU + 词表 + 规则 + 各种修正用的子程序
- NLU + 词表 + 规则 + 各种修正用的子程序 + BotFramework / Rasa
- NLU + 词表 + 规则 + 各种修正用的子程序 + BotFramework / Rasa + 各种修正用的子程序

## 用20%的时间解决80%的问题，然后用剩下的80%的时间解决剩下的20%的问题

- 很容易达成Happy Path
- 然后选择是否处理Bad Path