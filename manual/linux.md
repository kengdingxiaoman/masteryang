## linux命令积累

### 修改文件所有者
chown <font color="red">${用户}</font> <font color=red>${文件路径}</font>

例子： chown mag /app/mag/jboss/test.war
将/app/mag/jboss/test.war文件的所有者修改为mag

-R 如果是文件夹，那么对该目录下的所有子目录和文件递归进行修改。
