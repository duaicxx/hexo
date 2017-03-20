---
title: 9、注解篇@NumberFormat
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,NumberFormat
---
# @NumberFormat 可对类似数字类型的属性进行标
## 注，它拥有两个互斥的属性：
**– style：类型为 NumberFormat.Style。用于指定样式类
型，包括三种：Style.NUMBER（正常数字类型）、
Style.CURRENCY（货币类型）、 Style.PERCENT（
百分数类型）**

**– pattern：类型为 String，自定义样式，
如patter="#,###"**
```
@NumberFormat(pattern="#,###,###.#")
	private Float salary;
```