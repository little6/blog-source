title: "设计模式学习 - Strategy Pattern"
date: 2013-02-27
tags: 设计模式
categories: 技术
---

Strategy Pattern （策略模式）是对一系列可以替换的策略（算法）进行抽象，具体算法继承与抽象，在不同的场景下可以选择不同的算法，这样的好处就是将策略的使用者与具体的策略解耦。 <!--more-->

对于一系列不同的策略（算法），选择哪个策略（算法）要根据不同的场景。比如在一个国际支付系统中，各个国家/地区的税收政策并不相同，于是计算税收成为系统中的“变化的部分”，策略模式正好适合此场景，抽象税收计算行为，各个地区的税收分别独立实现。于是选择哪个税收算法，应该根据用户所处的国家/地区来确定。画出结构图如下所示：

![](/images/strategy-pay.jpg)

在此系统中，支付逻辑依赖于上下文，由上下文决定采用哪种计算税率的方法。这样支付逻辑就和具体的计算税率逻辑解耦了。

这个实现也是符合“开闭原则” 的，当你支持新的税率算法时，只需要增加一个TaxCalculator的实现就可以了。

剩下的重点就是 上下文 TaxContext了，他是策略选择中的一个重要角色。从我们以前的经验来看，这个角色的职责倒是和工厂的职责相当类似的，这里我们就用工厂实现就可以了。由此我们看出，工厂真是无处不在（这篇介绍了工厂模式的一些实现：[](/factory-pattern.html)）。