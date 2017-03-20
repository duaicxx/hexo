---
title: 5、注解篇@CookieValue
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,CookieValue
---
# @CookieValue 获取指定cookie的值
## 1、value值 
**对应cookie的key**
## 2、defaultValue 该参数的默认值
**当key值没有传输时将使用这个参数进行赋值**
## 3、required
**是否必须。默认为 true, 表示请求参数中必须包含对应
的参数，若不存在，将抛出异常**
```
/**
	 * 了解:
	 * 
	 * @CookieValue: 映射一个 Cookie 值. 属性同 @RequestParam
	 */
	@RequestMapping("/testCookieValue")
	public String testCookieValue(@CookieValue("JSESSIONID") String sessionId) {
		System.out.println("testCookieValue: sessionId: " + sessionId);
		return SUCCESS;
	}
```