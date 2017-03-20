---
title: 6、注解篇@SessionAttributes
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,SessionAttributes
---
# @SessionAttributes 该注解使用在类注解上
**该注解使用再与将request中存在的值共享到session中**
## 1、value值 
**实际中存入到request中的键值**
## 2、types 
**除了可以传键值以外还可以指定类型当值的类型为String时传入String.class**
```
@SessionAttributes(value={"user"}, types={String.class})
@RequestMapping("/springmvc")
@Controller
public class SpringMVCTest {

    /**
	 * @SessionAttributes 除了可以通过属性名指定需要放到会话中的属性外(实际上使用的是 value 属性值),
	 * 还可以通过模型属性的对象类型指定哪些模型属性需要放到会话中(实际上使用的是 types 属性值)
	 * 
	 * 注意: 该注解只能放在类的上面. 而不能修饰放方法. 
	 */
	@RequestMapping("/testSessionAttributes")
	public String testSessionAttributes(Map<String, Object> map){
		User user = new User("Tom", "123456", "tom@atguigu.com", 15);
		map.put("user", user);
		map.put("school", "atguigu");
		return SUCCESS;
	}
}
```
**上方实例将会存入user到session中与school的值**