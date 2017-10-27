# 源代码对接

## activity.yaoqian.com

### 安装node依赖
该项目基于nodejs开发使用gulp完成自动化构建，首先使用npm安装gulp依赖，依赖文件存放于package.json文件中：
```
npm install
```
### 安装运行服务
安装完gulp依赖，查看gulpfile.js中的任务情况：
```
# 该指令用于构建项目
gulp build

# 该指令用于清理构建
gulp clean

# 该指令用于构建完成后运行服务
gulp server

# 该指令指向build，default可以不写
gulp default
```
该工程使用zepto的精简库作为js库，页面文件为index.html实现以下内容：
- 大转盘

## app.yaoqian.com

### 安装node依赖
该项目基于nodejs开发使用gulp完成自动化构建，首先使用npm安装gulp依赖，依赖文件存放于package.json文件中：
```
npm install
```
### 安装运行服务
安装完gulp依赖，查看gulpfile.js中的任务情况：
```
# 该指令用于构建项目
gulp build

# 该指令用于清理构建
gulp clean

# 该指令用于构建完成后运行服务
gulp server

# 该指令指向build，default可以不写
gulp default
```
该工程使用zepto的精简库作为js库，页面文件为index.html实现以下内容：
- 协议
    - 借款协议
        - src\doc\loan_protocol
        - src\doc\loan_protocol_for360
    - 服务协议
        - src\doc\services_protocol
- 公告
    - src\doc\notice
- 审核不通过
    - src\doc\refuse


## control.yaoqian.com


## manage.yaoqian.com


## www.yaoqian.com




