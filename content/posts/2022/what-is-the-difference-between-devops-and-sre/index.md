+++ 
draft = false
date = 2022-04-17T16:46:43+08:00
title = "What is the Difference Between DevOps and SRE"
description = ""
slug = ""
authors = ["jiasir"]
tags = ["SRE", "DevOps"]
categories = ["2022"]
externalLink = ""
series = ["SRE"]
+++

# DevOps分解的5个关键领域
* Reduce Organization Silos：减少组织沉默。打破团队之间的障碍，增加协作。
* Accept failure as Normal：接受正常的失败。计算机本质上是不可靠的，所以我们不能期望完美。
* Implement Gradual Change：实施渐进式变更。小的变更更容易审查，渐进式变更能减少平均恢复时间，使回滚更简单。
* Leverage Tooling & Automation：利用工具和自动化。
* Measure Everything：衡量一切。衡量是成功的标准，如果没发衡量，那么我们就无法知道前四个支柱是否成功。

# DevOps VS SRE
* 如果DevOps被看作是一种哲学，那么SRE是实现该哲学的一种规范方式
* 如果DevOps是编程语言中的一个接口，那么SRE是一个实现DevOps的具体类
```java
class SRE implements DevOps
```

# SRE的具体实现
* Reduce Organization Silos
    * Share ownership：与开发人员共享生产所有权，通过相同的工具确保每个人都有相同的观点和相同的方法来处理生产，降低对于生产的模糊。
* Accept failure as Normal
    * SLOs & Blameless PMs：我们有没有可指责的事后分析，确保相同问题不会再次发生。
* Implement Gradual Change
    * Reduce costs of failure：在完全发布到生产之前，做大量的灰度发布。
* Leverage Tooling & Automation
    * Automate this year’s job away：尽可能的消除手工工作，衡量我们最近一年有多少手工工作，将今年的工作自动化
* Measure Everything
    * Measure toil and reliability：衡量我们自己的工作量以及系统的可靠性和健康状况的衡量标准