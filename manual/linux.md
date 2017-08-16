## linux命令积累

### 修改文件所有者
chown <font color="red">${用户}</font> <font color=red>${文件路径}</font>

例子： chown mag /app/mag/jboss/test.war<br/>
将/app/mag/jboss/test.war文件的所有者修改为mag

-R 如果是文件夹，那么对该目录下的所有子目录和文件递归进行修改。

### 修改文件所属组
chgrp <font color="red">${组}</font> <font color="red">${文件路径}</font>

例子：chgrp dba /app/mag/jboss/test.war<br/>
将/app/mag/jboss/test.war文件的所属组修改为dba

-R 如果是文件夹，那么对该目录下的所有子目录和文件递归进行修改。

### 查询一批文件中的内容
find <font color="red">${文件路径}</font> -type f -name <font color="red">${匹配文件名}</font> | xargs grep <font color="red">${要查找的内容}</font>

例子：find /app/test/logs -type f -name "test.log*" | xargs grep '异常'
查询/app/test/logs/目录下所有文件名匹配test.log*的文件中查询异常两个字

### 解压和压缩文件
tar -zcvf <font color="red">${需要后的文件}</font> <font color="red">${需要压缩的文件或者目录路径}</font>

例子：tar -zcvf test.tar /app/test <br/>
将/app/下的test目录压缩为当前目录下的test.tar文件

tar -zxvf <font color="red">${需要解压的文件}</font>

例子：tar -zxvf test.tar<br/>
将当前目录下的test.tar文件解压到当前目录

### 创建用户
useradd -u <font color="red">${用户号}</font> -g <font color="red">${所属用户组}</font> -G <font color="red">${用户所属的附加组}</font> -d <font color="red">${用户主目录}</font> <font color="red">${用户名}</font>

echo <font color="red">${密码}</font>|passwd --stdin <font color="red">${用户名}</font>

例子：
useradd -u 2024 -g appgrp -G dba -d /app/coder coder
echo coder2014|passwd --stdin coder

创建用户coder, 用户号为2024，coder所属组为appgrp，所属附加组为dba，
用户的主目录为/app/coder
coder用户的密码为coder2014

useradd只是建立用户，需要与passwd一起使用。
-u 是给用户分配用户号，值要尽量大于500，以免冲突。因为Linux安装后会建立一些特殊用户，一般0到499之间的值留给bin、mail这样的系统账号

### 修改用户密码
修改当前用户的密码只需要输入：passwd，如果是修改其他用户的密码，输入：passwd <font color="red">${用户名}</font>

随后确认当前旧密码，再输入两次新的密码就可以了

例如：

![linux_passwd](http://ouruoqnrh.bkt.clouddn.com/linux_passwd.png)

例子：<br/>
passwd abssv<br/>
修改用户abssv的密码

### 建立用户组
groupadd <font color="red">${用户组名称}</font>

例子：<br/>
groupadd dba<br/>
创建用户组：dba
