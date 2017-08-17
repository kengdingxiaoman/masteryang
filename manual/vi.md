## vi命令积累

### 在文件末尾
先在命令模式下使用：<font color="red">shift + g</font>跳转到文件末行的行尾；随后在命令模式下使用"<font color="red">o</font>"(英文字母小写的o)<br/>
这样做的效果就是在文件的最后一行的下一行进入编辑模式

### 光标停留在行首
在命令模式下使用：<font color="red">0</font> (阿拉伯数字0)

### 跳转到行尾
在命令模式下输入：<font color="red">shift + $</font>

### 跳转到文件的最后一行
有两种方法：
1. 在命令模式下使用：<font color="red">shift + g</font>
2. 在命令模式下输入： '<font color="red">:</font>'， 输入字符：'<font color="red">$</font>'回车

这两种方法都可以，但还是使用shift + g比较方便吧

### 复制N行
有时候有一些在xml的配置，我们可能需要配置多次，例如jndi的配置，如果有多个jndi，那么很多配置是重复的，相同的。但是在vi里不能像windows下用鼠标选中N行，然后在需要的地方粘贴就好了。vi是很强大的，自然也提供了这样的方法。

首先在命令模式下，在需要拷贝的段落的首行输入<font color="red">nyy</font>，n代表需要复制多少行，例如如果要复制17行，那么就输入17yy，在最下方会有提示：

![vi_nyy](http://ouruoqnrh.bkt.clouddn.com/nyy.jpg)

最后在需要复制的地方，在命令模式下点击按键 p<br/>
这样就会将这复制的N行粘贴到该处

### 删除N行
在命令模式下，在需要删除的段落首行输入<font color="red">ndd</font>，n代表需要删除多少行，例如如果需要删除17行，那么就输入：17dd，就可以了

### 查询
在命令模式下输入 "/${待搜索字符串}"，按照当前光标向下搜索匹配的内容，例如  /content<br/>
在命令模式下输入 ":${待搜索字符串}",  按照当前贯标向上搜索匹配的内容，例如 :content

需要注意的是按照当前光标，而不是从文件的头部或者尾部

### 编辑二进制文件
使用命令 <font color="red">vi -b</font> ${filename} 就可以用二进制的形式编辑文件

例如我遇到一个文件，里面是自己的一个命令，但怎么都提示一行的末尾有 '\\r' 存在，导致命令失败，这时就可以使用vi -b 来编辑文件，可以看到文件末尾有 ^M 的存在，删除后就可以了。

### 替换字符串
:s/vivian/sky/    替换当前行第一个 vivian 为 sky<br/>
:s/vivian/sky/g  替换当前行所有 vivian 为 sky

:n,$s/vivian/sky/ 替换第 n 行开始到最后一行中每一行的第一个 vivian 为 sky<br/>
:n,$s/vivian/sky/g 替换第 n 行开始到最后一行中每一行所有 vivian 为 sky<br/>
(n 为数字，若 n 为 .，表示从当前行开始到最后一行)

:%s/vivian/sky/（等同于 :g/vivian/s//sky/） 替换每一行的第一个 vivian 为 sky<br/>
:%s/vivian/sky/g（等同于 :g/vivian/s//sky/g） 替换每一行中所有 vivian 为 sky
