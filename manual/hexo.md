# hexo 常用命令

## 生成
hexo g

## 本地启动
hexo s

## 部署上传
hexo d

## 清空
hexo clean

有时因为修改了文件名等造成一些异常的页面产生，这时可以使用 hexo clean 先清空后，再使用 hexo g 生成新的页面

## tags
hexo 写的文章时，起始的文件说明格式如下

```
---
title: Spring Boot + HikariCP 多数据源配置
category: 技术
tags: [Spring Boot, HikariCP]
date: 2017-12-07 09:20:57
---
```

title： 标题 <br/>
category: 归档<br/>
tags: tags<br/>
date：日期<br/>
