---
title: 13、注解篇@ControllerAdvice
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,ControllerAdvice
---
# @ControllerAdvice全局处理方式
**上一个注解ExceptionHandler只能处理当前类中的并不全局所以使用@ControllerAdvice注解的类中使用ExceptionHandler被注解的方法，将会被任意类中的异常使用**
```
@ControllerAdvice
public class SpringMVCTestExceptionHandler {

	@ExceptionHandler({ArithmeticException.class})
	public ModelAndView handleArithmeticException(Exception ex){
		System.out.println("----> 出异常了: " + ex);
		ModelAndView mv = new ModelAndView("error");
		mv.addObject("exception", ex);
		return mv;
	}
	
}
```
**如果需要传值到界面时需要使用ModelAndView对象返回**