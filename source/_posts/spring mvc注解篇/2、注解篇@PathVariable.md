---
title: 2、注解篇@PathVariable
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,PathVariable
---
# @PathVariable url传参注解改注解有一个参数
## value指定url中的参数对应的变量名
**例如：requestMapping值为/index/{id}**

**此处PathVariable值应该为：id**
```
	/**
	 * @PathVariable 可以来映射 URL 中的占位符到目标方法的参数中.
	 * @param id
	 * @return
	 */
	@RequestMapping("/testPathVariable/{id}")
	public String testPathVariable(@PathVariable("id") Integer id) {
		System.out.println("testPathVariable: " + id);
		return SUCCESS;
	}
```