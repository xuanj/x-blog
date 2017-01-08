---
title: mysql 主键与外键
date: 2016-06-30 23:42:00
categories: mysql
tags:
- mysql 
- database
---

> mysql 主键与外键

先建一个t1表，主键如果是UNSIGNED，那么外键关联的字段要也要是UNSIGNED，反正就是要一样。

{% codeblock lang:sql %}
CREATE TABLE `x-dorwins`.`t1` (
  `id` BIGINT(16) NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`),
  UNIQUE INDEX `id_UNIQUE` (`id` ASC))
AUTO_INCREMENT = 10000;
{% endcodeblock %}

<!-- more -->
外键名不能用id1，即： CONSTRAINT `id1`会报错， 不知道为什么！！！
{% codeblock lang:sql %}
CREATE TABLE `x-dorwins`.`t2` (
  `id` BIGINT(16) NOT NULL AUTO_INCREMENT COMMENT 'id',
  `user_id` BIGINT(16) NOT NULL COMMENT '外键 basic表用户id',
  PRIMARY KEY (`id`),
  INDEX `id_idx` (`user_id` ASC),
  CONSTRAINT `user_id`
    FOREIGN KEY (`user_id`)
    REFERENCES `x-dorwins`.`t1` (`id`))
    AUTO_INCREMENT = 10000;
{% endcodeblock %}


想一次在mysqlworkbench上运行，要设置运行出错继续运行。因为，初次运行没有这两张表就会报错。在菜单Query下设置。
{% codeblock lang:sql %}
DROP TABLE `x-dorwins`.`t2`,`x-dorwins`.`t1`;
CREATE TABLE `x-dorwins`.`t1` (
  `id` BIGINT(16) NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`),
  UNIQUE INDEX `id_UNIQUE` (`id` ASC))
AUTO_INCREMENT = 10000;

CREATE TABLE `x-dorwins`.`t2` (
  `id` BIGINT(16) NOT NULL AUTO_INCREMENT COMMENT 'id',
  `user_id` BIGINT(16) NOT NULL,
  PRIMARY KEY (`id`),
  INDEX `id_idx` (`user_id` ASC),
  CONSTRAINT `user_id`
    FOREIGN KEY (`user_id`)
    REFERENCES `x-dorwins`.`t1` (`id`))
    AUTO_INCREMENT = 10000;
{% endcodeblock %}