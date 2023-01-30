# 第一篇文章

# Debian安装dwm
**配置用户使用sudo**
```
apt install sudo
usermod -aG sudo hxm
```


## 安装需要的环境

**安装需要的环境**

`sudo apt install xorg --install-suggests`
`sudo apt install libx11-dev libxft-dev libxinerama-dev`

xrandr -s //调整分辨率

## 装的软件有
**装的软件有**

Thunar
Konsole 命令行终端
Apper 包管理器
feh

vim
h -option-list
配色

"Dracula,#282a3浅黑,#ffeedb肉色,#bd93f9紫色,#ffb86c黄色,#6272a4灰紫,#50fa7b荧绿,#ff5555红色"

picom

cloc

Chromium

xfce4-panel不用下什么了

补丁

cflow -d 3 wget.c | tree2dotx -e 1 -r 1 | awk '!a[$0]++' > out.dot

barpadding（我觉得不好看）

**picom使用**

字体：Hack
``````
fc-cache -v -f
fc-list | grep "Hack"

``````

