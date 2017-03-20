---
title: 8、注解篇@DateTimeFormat
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,DateTimeFormat
---
# @DateTimeFormat 注解可对
## java.util.Date、java.util.Calendar、java.long.Long 时间类型进行标注：
**– pattern 属性：类型为字符串。指定解析/格式化字段数据的模式，
如：”yyyy-MM-dd hh:mm:ss”**

**– iso 属性：类型为 DateTimeFormat.ISO。指定解析/格式化字段数据
的ISO模式，包括四种：ISO.NONE（不使用） -- 默
认、ISO.DATE(yyyy-MM-dd) 、ISO.TIME(hh:mm:ss.SSSZ)、
ISO.DATE_TIME(yyyy-MM-dd hh:mm:ss.SSSZ)**

**– style 属性：字符串类型。通过样式指定日期时间的格式，由两位字
符组成，第一位表示日期的格式，第二位表示时间的格式：S：短日
期/时间格式、M：中日期/时间格式、L：长日期/时间格式、F：完整
日期/时间格式、-：忽略日期或时间格式**
```
@DateTimeFormat(pattern="yyyy-MM-dd")
	private Date birth;
```