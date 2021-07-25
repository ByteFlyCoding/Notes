---
title: "Ubuntu_20.04_LTS_Configure"
date: 2021-03-31T19:45:02+08:00
draft: false
tags: ["Linux"]
categories: ["Linux"]
---

# Ubuntu 20.04 安装记录以及配置与美化

## 换源

1. 在安装界面就可以在设置里换源了

1. settings->about->Software Update

## 卸载 snap

```bash
# 列出已经安装的 snap 包
sudo snap list
# 卸载 snap 中安装的包
sudo snap remove <package-name>
# 卸载 snap-core
sudo apt autoremove --purge snapd
```

## Ubuntu 20.04 ssr 安装（太坑了，被坑了两三天）

[下载地址](https://github.com/qingshuisiyuan/electron-ssr-backup/releases/)

1. 安装依赖
   ```bash
   sudo apt install libcanberra-gtk-module libcanberra-gtk3-module gconf2 gconf-service libappindicator1
   ```
2. 可选依赖（如果软件报错，请安装可选依赖）
   ```bash
   sudo apt install libssl-dev
   sudo apt install libsodium-dev
   ```
3. Ubuntu 20.04 与 Electron-SSR Bug：Electron-SSR 默认调用 python 而不是 python3（并不需要下载 python2.7）
   解决方法：

   1.手动创建 symlink

   ```bash
   sudo ln -s /usr/bin/python3 /usr/bin/python
   ```

   2.检查是否成功

   ```bash
   whereis python
   ```

4. 运行软件
   ```bash
   electron-ssr
   ```
   [Bug 处理参考链接](https://github.com/shadowsocksrr/electron-ssr/issues/86)

## 设置输入法

[搜狗拼音官方安装指南](https://pinyin.sogou.com/linux/help.php)

[下载链接](https://pinyin.sogou.com/linux/?r=pinyin)

1. 安装 fcitx,并把键盘输入法系统切换成 fcitx(iBus 不支持 Sougou 拼音,切换方法参考[搜狗拼音官方安装指南](https://pinyin.sogou.com/linux/help.php))
   ```bash
   sudo apt update -y
   sudo apt install fcitx
   ```
2. 在 Terminal 下安装搜狗输入法
   ```bash
   sudo apt -f intall sogoupinyin_版本号_amd64.deb
   ```
3. 注销或重启计算机即可正常使用搜狗输入法

## 安装 Google Chrome 并同步

## 安装 Golang 并配置环境变量

## 安装 vscode 并同步

[官方安装指南](https://code.visualstudio.com/docs/setup/linux)

注：Snap 版的 vscode 有个 bug, 不能用 Sougou 拼音输入法

## Ubuntu20.04-LTS 安装NVM NodeJS npm yarn

### Install NVM NodeJS npm yarn

[NodeJs Official Website](https://nodejs.org/zh-cn/)

1. Install NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash

vim ~/.bashrc
## Add by myself
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

[Install Reference](https://github.com/nvm-sh/nvm#manual-install)

1. NVM Change Resource.

```bash
cd ~/.nvm/nvm.sh
# Press `/` in order to search `NVM_NODEJS_ORG_MIRROR` and press `enter`, then, change its url to `https://npm.taobao.org/mirrors/node/`.
```

[Reference](https://blog.csdn.net/qq_14815199/article/details/104610163)

1. Install NodeJS

```bash
nvm install node
```

1. NPM Change Resource And Upgrade

```bash
npm config set registry https://registry.npm.taobao.org/
npm install npm -g
```

[Reference](https://zhuanlan.zhihu.com/p/108370177)

1. Install yarn And Change Resource

```bash
npm install -g yarn
yarn config set registry https://registry.npm.taobao.org
```

[Reference](https://zhuanlan.zhihu.com/p/108370177)

### Install @vue/cli

```bash
npm install -g @vue/cli
```

[Vue official Website](https://v3.cn.vuejs.org/)

[@vue/cli Official Website](https://cli.vuejs.org/)

### Install create-react-app

```bash
npm install -g create-react-app
```

[React Official Website](https://zh-hans.reactjs.org/)

[create-react-app Official Website](https://create-react-app.dev/)

### Install xgplayer

```bash
npm install -g xgplayer
```

[xgplayer Official Website](https://v2.h5player.bytedance.com/)

### Install BootStrap

```bash
npm install -g bootstrap
```

[BootStrap Official Website](https://v5.bootcss.com/)

### Install handlebars

```bash
npm install handlebars
```

[handlebarsjs Official Website](https://handlebarsjs.com/)

### Install Electron

[Electron Official Website](https://www.electronjs.org/)

[Suggest install Electron Release directly](https://github.com/electron/electron)

[Domestic Resource](http://npm.taobao.org/mirrors/electron/)

```bash
# Use Domestic Resource
npm config set ELECTRON_MIRROR http://npm.taobao.org/mirrors/electron/
```

## 安装 Jetbrains

安装 toolbox，用 toolbox 安装

## 美化

感觉自己的下载的文件有问题，找个时间重新下一遍并且写一下文档

[Ubuntu 20.04 安装记录以及配置与美化参考链接](http://www.ahutcloud.cn/212/#toc-head-13)

[Ubuntu 清理系统日志](https://blog.csdn.net/yyinhai/article/details/52944897)

[清理 Ubuntu 系统的缓存、垃圾、多余内核](https://my.oschina.net/zhangqingcai/blog/23994)

## ubuntu 彻底卸载软件

```bash
sudo apt autoremove --purge + SoftwareName
```

## ubuntu 安装 git

[安装 git 参考](https://git-scm.com/download/linux)

## ubuntu 安装 typora

[安装 typora 查看](https://www.typora.io/#linux)

## apt 的使用

- apt 列出可以升级的包

  ```bash
  apt list --upgradeable
  ```

- List the versions available in your repo:

  ```bash
  apt-cache madison <packagename>
  ```

- 查询包的依赖关系

  ```bash
  # 查询包的依赖
  apt-cache depends mysql
  ```

- 查询包的反向依赖关系

  ```bash
  # 查询包的反向依赖
  apt-cache rdepends mysql
  ```

  ## 查看 Ubuntu 的连接过的 Wi-Fi 的密码

  ```bash
  cd /etc/NetworkManager/system-connections && ll
  cat + <Wi-Fi_Name>
  ```

## 根分区扩容

[参考链接](https://zhuanlan.zhihu.com/p/146554549)

## Linux 清除日志文件

```bash
journalctl --disk-usage	# 检查日志的大小
sudo journalctl --vacuum-time=<n>d	# 清除早于<n>天的日志
sudo find /var/log/ -type f -mtime +<n> -exec rm -f {} \;	# 删除<n天前的旧>
```

## 安装 Postman

[参考](https://blog.csdn.net/gymaisyl/article/details/86573247)

[参考](https://blog.csdn.net/baifengqing/article/details/80303250)

- Step1: Download Postman

- Step2: 解压到`/opt`目录下

  ```bash
  sudo tar -xzvf Postman-linux-x64-X.X.X.tar.gz -C /opt
  sudo ln -s /opt/Postman/app/Postman /usr/bin/postman
  ```

- Step3: 创建启动项(该步骤失败了，有空的时候再研究一下)

## 安装 Apache Jmeter

- Step1: [Download Jmeter](https://mirrors.bfsu.edu.cn/apache//jmeter/binaries/apache-jmeter-5.2.1.tgz)

- Step2: 解压到`/opt`目录下

  ```bash
  sudo tar -xzvf apache-jmeter-x.x.x.tgz -C /opt
  sudo ln -s /opt/apache-jmeter-x.x.x/bin/jmeter /usr/bin/jmeter
  ```

- Step3: 创建启动项文件(该步骤失败了，有空的时候再研究一下)
