# 用VSCode搭建NodeJs开发环境

## 1.安装vs code

官方下载地址：[下载地址](https://code.visualstudio.com/)
windows下安装勾选“ *将“通过Code打开”操作添加到Windows资源管理器目录上下文菜单*”
右键目录用vs code打开项目文件夹已提升操作快捷度。
Mac用户可参照以下操作：
先运行Automator，选择“服务”：
![](P4-Node.js/_media/002/P4-002-001.png)
然后，执行以下操作：
![](P4-Node.js/_media/002/P4-002-002.png)
1.在右侧面板选择“服务”收到选定的“文件夹”，位于“Finder.app“，该选项是为了从Finder中接收一个文件夹；
2.在左侧面板选择”实用工具“，然后找到”运行Shell脚本“，把它拽到右侧面板里；
3.在右侧”运行Shell脚本“的面板里，选择Shell”/bin/bash“，传递输入“作为自变量”，然后修改Shell脚本如下：
```shell
for f in "$@"
do
    open -a "Visual Studio Code" "$f"
done
```
保存为“Open With VSCode”后，打开Finder，选中一个文件夹，点击右键，“服务”，就可以看到“Open With VSCode”菜单：
![](P4-Node.js/_media/002/P4-002-003.png)


## 2.安装node.js

nvm安装指定版本node参照之前的文章《Mac下安装nvm及node》 -->[查看地址](http://m.dinghui.me/?p=245 "Mac下安装nvm及node")

windows下快速安装参照之前的文章《Node.js初探》 -->[查看地址](http://m.dinghui.me/?p=69 "Node.js初探")

## 3.运行和调试JavaScript
使用debug快速创建.vscode文件夹和调试脚本launch.json
![](P4-Node.js/_media/002/P4-002-004.png)


