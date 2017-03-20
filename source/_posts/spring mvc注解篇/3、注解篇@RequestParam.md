---
title: 3、注解篇@RequestParam
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,RequestParam
---
# @RequestParam 参数标识注解存在三个参数
## 1、value值 
**对应url提交的?id=xx中的id，参数名**
## 2、defaultValue 该参数的默认值
**当url中id值没有传输时将使用这个参数进行赋值**
## 3、required
**是否必须。默认为 true, 表示请求参数中必须包含对应
的参数，若不存在，将抛出异常**
```
    /**
	 * @RequestParam 来映射请求参数. value 值即请求参数的参数名 required 该参数是否必须. 默认为 true
	 *               defaultValue 请求参数的默认值
	 */
	@RequestMapping(value = "/testRequestParam")
	public String testRequestParam(
			@RequestParam(value = "username") String un,
			@RequestParam(value = "age", required = false, defaultValue = "0") int age) {
		System.out.println("testRequestParam, username: " + un + ", age: "
				+ age);
		return SUCCESS;
	}
```