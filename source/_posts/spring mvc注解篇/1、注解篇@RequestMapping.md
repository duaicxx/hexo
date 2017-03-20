---
title: 1、注解篇@RequestMapping
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,RequestMapping
---
# 1、@RequestMapping 请求url注解该注解有四个参数
## 1）、value

**对应的url值，当类与方法都存在该注解是 将是拼接结果类在前方法在后。**

## 2）、method

**请求方法存在PUT、DELETE、POST、GET等常见的rest风格方式。**
```
	/**
	 * 常用: 使用 method 属性来指定请求方式
	 */
	@RequestMapping(value = "/testMethod", method = RequestMethod.POST)
	public String testMethod() {
		System.out.println("testMethod");
		return SUCCESS;
	}
```
## 3）、params使用其约定url规则：

**①、param 代表必须存在param这个参数**

**②、!param 不能包含这个参数**

**③、 param!=value param的值不能等于value**

**④、param=value param的值必须等于value**

**params是复数所以以数组方式传递规则：{"param=value","param != 1","param","!param"}**

## 4）、headers 请求头约束
**可以使用 params 和 headers 来更加精确的映射请求. params 和 headers 支持简单的表达式.使用方式与params相同**
```
	/**
	 * 了解: 可以使用 params 和 headers 来更加精确的映射请求. params 和 headers 支持简单的表达式.
	 * 
	 * @return
	 */
	@RequestMapping(value = "testParamsAndHeaders", params = { "username",
			"age!=10" }, headers = { "Accept-Language=en-US,zh;q=0.8" })
	public String testParamsAndHeaders() {
		System.out.println("testParamsAndHeaders");
		return SUCCESS;
	}
```
# 2、@RequestMapping 该注解的ant 风格请求
## 1）、支持三种通配符
**①、?匹配url中任意一个字符**

**②、\*匹配url中任意多个字符**

**③、\*\*:**匹配多层路劲任意多个字符**

```
@RequestMapping("/testAntPath/*/abc")
	public String testAntPath() {
		System.out.println("testAntPath");
		return SUCCESS;
	}
```


