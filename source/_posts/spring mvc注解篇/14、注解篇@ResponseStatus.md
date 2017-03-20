---
title: 14、注解篇@ResponseStatus
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,ResponseStatus
---
# @ResponseStatus有两个参数
## 1、value
**对应枚举HttpStatus的值，此值对应相应404,403,500**
## 2、reason
**界面提示文字**
## 3、使用案例
```
@ResponseStatus(value=HttpStatus.FORBIDDEN, reason="用户名和密码不匹配!")
public class UserNameNotMatchPasswordException extends RuntimeException{
}
```
**当抛出这个异常的时候界面所要修改的值**
```
@ResponseStatus(reason="测试",value=HttpStatus.NOT_FOUND)
	@RequestMapping("/testResponseStatusExceptionResolver")
	public String testResponseStatusExceptionResolver(@RequestParam("i") int i){
		if(i == 13){
			throw new UserNameNotMatchPasswordException();
		}
		System.out.println("testResponseStatusExceptionResolver...");
		return "success";
	}
```
**方法修饰，当访问该方法时返回的状态信息**
**使用：如果需要修改tomcat的异常页面时使用，建议使用在异常类上而不是方法上--自我总结**