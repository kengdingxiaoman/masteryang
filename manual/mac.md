
### 在 Finder 中显示隐藏文件夹

使用命令：
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder

### 跳转到行首或行尾

command + <- 跳转到行首

command + -> 跳转到行尾

### 剪切
默认的 command + c ， command + v 只是复制一份
要想剪切，需要使用 command + option + v

### 在 Finder 中显示当前目录的完整地址

使用命令：
defaults write com.apple.finder \_FXShowPosixPathInTitle -bool YES

### 查看端口占用情况
使用命令：
sudo lsof -i:<font color="red">${具体端口}</font>

kill -9 <font color="red">{对应进程号}</font>
