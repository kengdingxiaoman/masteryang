# markdown一些功能的使用

## 插入图片

```
![说明](链接)
```

例如：

使用图片链接：
```
![hmsmock](http://ouruoqnrh.bkt.clouddn.com/hmsmock%E6%B5%81%E7%A8%8B.png)
```

## 表格

```
| 数据类型 | 含义 |
| - | - |
| tinyint(m) | 1个字节&nbsp; 范围(-128~127)|
| smallint(m) | 2个字节&nbsp; 范围(-32768~32767) |
| mediumint(m) | 3个字节&nbsp; 范围(-8388608~8388607) |
```

第一列是标题<br/>
第二列是对齐，|-| 表示默认左对齐, |:-| 表示左对齐, |-:| 表示右对齐, |:-:| 表示居中<br/>
第三列开始是表格的内容了

## 代码高亮
hexo markdown 使用了 highlight.js，所以代码高亮很简单

如果要使用java，这样：

\`\`\` java

{这里放具体的代码}

\`\`\`

就可以了，支持多种语言，包括常用的 xml, yml, sql, java等，足够用了
