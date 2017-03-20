---
title: 10、注解篇@Valid
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,Valid
---
# 需要引用hibernate-validator相应的jar
```
    @NotEmpty
	private String lastName;

	@Email
	private String email;
```
```
@RequestMapping(value="/emp", method=RequestMethod.POST)
	public String save(@Valid Employee employee, BindingResult result, 
			Map<String, Object> map){
		System.out.println("save: " + employee);
		
		if(result.getErrorCount() > 0){
			System.out.println("出错了!");
			
			for(FieldError error:result.getFieldErrors()){
				System.out.println(error.getField() + ":" + error.getDefaultMessage());
			}
			
			//若验证出错, 则转向定制的页面
			map.put("departments", departmentDao.getDepartments());
			return "input";
		}
		
		employeeDao.save(employee);
		return "redirect:/emps";
	}
	
```
**因为BindingResult继承ERRORS 所以使用该类也可**
# 界面显示时使用<form:errors path=""></form:errors>标签
**使用方式打印所有时使用\*打印所有如果打印指定字段时使用字段name**

**还需要注意一点就是：检测的实体与结果必须紧挨着，中间不能隔其他参数。**
# 国际化输出i18n.properties
```
NotEmpty.employee.lastName=^^LastName\u4E0D\u80FD\u4E3A\u7A7A.
Email.employee.email=Email\u5730\u5740\u4E0D\u5408\u6CD5
Past.employee.birth=Birth\u4E0D\u80FD\u662F\u4E00\u4E2A\u5C06\u6765\u7684\u65F6\u95F4. 
typeMismatch.employee.birth=Birth\u4E0D\u662F\u4E00\u4E2A\u65E5\u671F. 
```
**格式：注解类型.实体类变量名.属性名**
**typeMismatch代表着前面使用类型转换注解异常，需要使用typeMismatch定义提示语**
```
<!-- 配置国际化资源文件 -->
	<bean id="messageSource"
		class="org.springframework.context.support.ResourceBundleMessageSource">
		<property name="basename" value="i18n"></property>
	</bean>
```