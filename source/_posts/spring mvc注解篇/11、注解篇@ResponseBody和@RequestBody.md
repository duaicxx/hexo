---
title: 11、注解篇@ResponseBody and @RequestBody
date: 2017-03-20 17:15:00
tags: spring,spring mvc,注解,ResponseBody,RequestBody
---
```
@RequestMapping("/testResponseEntity")
	public ResponseEntity<byte[]> testResponseEntity(HttpSession session) throws IOException{
		byte [] body = null;
		ServletContext servletContext = session.getServletContext();
		InputStream in = servletContext.getResourceAsStream("/files/abc.txt");
		body = new byte[in.available()];
		in.read(body);
		
		HttpHeaders headers = new HttpHeaders();
		headers.add("Content-Disposition", "attachment;filename=abc.txt");
		
		HttpStatus statusCode = HttpStatus.OK;
		
		ResponseEntity<byte[]> response = new ResponseEntity<byte[]>(body, headers, statusCode);
		return response;
	}
	
	@ResponseBody
	@RequestMapping("/testHttpMessageConverter")
	public String testHttpMessageConverter(@RequestBody String body){
		System.out.println(body);
		return "helloworld! " + new Date();
	}
```
**spring mvc请求和相应都会使用到HttpMessageConverter进行处理对象**
**对应注解为@ResponseBody和@RequestBody**
**注解又对应两个对象HttpEntity<T> / ResponseEntity<T>**