---
title: 4、注解篇@RequestHeader
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,RequestHeader
---
# @RequestHeader 获取请求头文件的信息
## 1、value值 
**对应头文件中的键**
## 2、defaultValue 该参数的默认值
**当键值没有传输时将使用这个参数进行赋值**
## 3、required
**是否必须。默认为 true, 表示请求参数中必须包含对应
的参数，若不存在，将抛出异常**
```
	/**
	 * 了解: 映射请求头信息 用法同 @RequestParam
	 */
	@RequestMapping("/testRequestHeader")
	public String testRequestHeader(
			@RequestHeader(value = "Accept-Language") String al) {
		System.out.println("testRequestHeader, Accept-Language: " + al);
		return SUCCESS;
	}
```