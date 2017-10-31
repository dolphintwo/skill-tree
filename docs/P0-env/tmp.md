# 源代码对接

## App内嵌h5页面 activity.yaoqian.com
- 借款协议
- 借款流程
- 大转盘
- 邀请好友
- 注册页面
    - src\2017\register

#### 安装node依赖
该项目基于nodejs开发使用gulp完成自动化构建，首先使用npm安装gulp依赖，依赖文件存放于package.json文件中：
```
npm install
```
#### 安装运行服务
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
该工程使用zepto的精简库作为js库，页面文件为index.html

## 功能实现 app.yaoqian.com

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

> 相关帮助页面存放在 `src/help`下，

> 帮助信息以json格式存放在`src/json/help.json.js`里

#### 安装node依赖
该项目基于nodejs开发使用gulp完成自动化构建，首先使用npm安装gulp依赖，依赖文件存放于package.json文件中：
```
npm install
```
#### 安装运行服务
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

## 后台管理系统 control.yaoqian.com & manage.yaoqian.com
这两套系统的前端框架都是使用vue，用webpack打包在服务器中直接运行，ui利用基于vue2.0的组件库element，ele官网有一整套api组件库，在开发时直接调用组件。
#### Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

## 官网 www.yaoqian.com
- 官网（四个页面）
    - 首页    -index.html
    - 帮助中心  -help.html
    - 关于我们  -about.html
    - 隐私协议  -yinsi.html
> 无后台，纯展示



