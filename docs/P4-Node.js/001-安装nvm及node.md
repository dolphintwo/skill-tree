# 安装

## 1.Mac下安装nvm及node
GitHub：
[creationix/nvm](https://github.com/creationix/nvm "creationix/nvm")

### 安装脚本

To install or update nvm, you can use the install script using cURL:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.5/install.sh | bash
```
根据图示完成安装
![图示](P4-Node.js/_media/001/P4-001-001.jpeg)

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm

source ~/.bashrc
```

### 确认安装
```
command -v nvm
nvm
```

### 安装使用node指定版本
查看nvm使用帮助
```
Example:
  nvm install 8.0.0                     Install a specific version number
  nvm use 8.0                           Use the latest available 8.0.x release
  nvm run 6.10.3 app.js                 Run app.js using node 6.10.3
  nvm exec 4.8.3 node app.js            Run `node app.js` with the PATH pointing to node 4.8.3
  nvm alias default 8.1.0               Set default node version on a shell
  nvm alias default node                Always default to the latest available node version on a shell
```

