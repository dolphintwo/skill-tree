# shell
## 1.zsh
### 1.1.安装zsh和oh-my-zsh
```shell
yum install -y zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
or
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```
### 1.2.修改主题和插件信息
配置存放在`~/.zshrc`中
```shell
# 修改主题
ZSH_THEME="wedisagree"

# 修改插件
plugins=(git wd zsh-syntax-highlighting)

# alias
alias zshconfig="mate ~/.zshrc"
```

## 2.常用包lib
```shell
yum install -y wget vim gcc net-tools git lrzsz
```

