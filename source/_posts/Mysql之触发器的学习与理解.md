---
title: Mysql之触发器的学习与理解
date: 2017-02-23 11:31:38
tags: Mysql,触发器
---
# Mysql触发器
先上代码：
```sql
DROP TRIGGER control_log_trigger;
CREATE TRIGGER control_log_trigger AFTER INSERT ON control_log.termail
  FOR EACH ROW BEGIN
    INSERT INTO temp_control_log.termail SELECT * FROM control_log.termail where id = NEW.id;
  END;
```
解释：

---
    1、DROP TRIGGER control_log_trigger;第一行是删除同名触发器
    2、CREATE TRIGGER control_log_trigger;创建触发器
    3、AFTER INSERT ON control_log.termail;设置触发器,触发时间:1、AFTER 在commit之后2、befoer在commit之前,指定触发操作为INSERT、UPDATE、DELETE，最后部分指定表。
    4、FOR EACH ROW BEGIN;固定代码。
    5、需要进行的操作,操作结束后必须使用分好结尾';'。
    6、END,结尾。
---
个人理解：触发相当于后端的拦截器。