---
title: "WebFront_JavaScript"
date: 2021-06-29T14:00:00+08:00
draft: false
tags:
  [
    "Web Front",
    "Web",
    "HTML",
    "HTML5",
    "CSS",
    "CSS3",
    "JavaScript",
    "ECMAScript",
  ]
catagories: ["WebFront"]
---

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

## 初识 JavaScript

### 前端三层

- 结构层 HTML 搭建结构、放置部件、描述语义
- 样式层 CSS 美化页面、实现布局
- 行为层 JavaScript 实现交互效果、数据收发、表单验证等

### 什么是前端语言和后端语言

### ECMAScript 是 JavaScript 的标准

- 1997 年，欧洲计算机制造商协会（ECMA）设置了 JavaScript 的标准，命名为 ECMAScript
- JavaScript 实现了 ECMAScript ECMAScript 规范了 JavaScript
- JavaScript 体系
  - 语言核心包括：ECMAScript5 和 ECMAScript6、7、8、9
  - DOM
  - BOM
- JavaScript 的语言风格和特性
  - 类 C 语言的风格，简单好学
  - 弱类型，使用方便
  - 丰富效果，易产生兴趣
	
### JavaScript 的书写位置

- 在<body>中<script>标签，在内部书写 JavaScript 代码
- 将代码单独保存为.js 格式文件，然后 HTML 文件中使用<script src=""></script>
- Notes:JavaScript 不能脱离 HTML 网页运行(NodeJS 可以成为 JavaScript 的独立运行平台)

### 认识输出语句

- alert()语句 -弹出警告框 alter('xxx')是内置函数，函数就是功能的“封装”，调用函数需要使用圆括号 'xxx'三个字是函数的参数，因为它是字符串，我们需要将它用引号包裹，语句的末尾最好书写分号，对文件压缩与维持文件可读性非常重要
- console.log()语句 -控制台输出 console 是 JS 的内置对象，通过“打点”可以调用它内置 log“方法”。所谓“方法”就是对象能够调用的函数。

### 学会处理报错

- Uncaught SyntaxError: Invalid or unexpected token 未捕获的语法错误： 不合法或错误的符合 发生错误的行号可能有 1 行的误差（`alert('xxxx')；`分号用了中文分号）
- Uncaught ReferenceError: xxxx is not defined.未捕获引用错误：xxxx 没有被定义（`alert(xxxx);` 忘记用引号包裹）
- Uncaught ReferenceError: alert is not defined (`alert('xxxx');`拼写错误)
- REPL 环境 控制台也是一个 REPL 环境，可以使用它临时测试表达式的值 `read读`-->`eval执行`-->`print打印`-->`loop循环`-->`read读`
- 遇到错误不要怕，10 年经验的老程序员每天仍有一半时间在寻找并解决 bug
- 遇见错误先尝试自己解决，因为这是工作中必备的技能，如果实在找不到错误，再找人请教并解决

### 变量

- 变量是计算机语言中能存储计算机结果或能表示值抽象概念
- 变量不是数值本身，他们仅仅是一个用于存储数值的容器
- 定义变量
  - 要想使用变量，第一步就是声明它，并给它赋值 使用 var 关键字定义变量
- 变量的使用
  - 当变量被赋值后，就可以使用它了
- 改变变量的值
  - 变量的值可以被改变，改变变量的值不再需要书写 var 了
- 标识符的命名规则（变量的合法命名） 函数、类名、对象的属性等也都要遵守这个命名规则
  - 只能由字母、数字、下划线、$组成，但不能以数字开头；
  - 不能关键字或保留字
  - 变量名大小写敏感，a 和 A 两个不同的变量
- 优秀的变量命名法
  - 驼峰命名法：mathTestScore
  - c 风格：math_test_score
  - 匈牙利命名法：iMathTestScore 首字母 i---提示变量类型
- 变量的默认值
  - 一个变量只定义，但没有赋初值，默认值是 undefined
  - 一个变量只有被 var 定义，并赋初值之后，才算正式初始化完成
- 变量的常见错误
  - 不用 var 定义，而直接将值赋予它，虽不引发报错，但会产生作用域问题
  - 尝试使用一个既没有被 var 定义过，也没有赋过值的字符，就会产生引用错误
  - 等号表示赋值
  - 同时声明多个变量 使用逗号同时声明和初始化两个变量

### 变量声明提升

- 变量声明的提升：你可以提前使用一个稍后才声明的变量，而不会引发异常
- 在执行所有代码前，JS 有预编译阶段，会预先读取所有变量的定义
- 变量声明提升只提升定义不提升值
- 注意事项：
  - 变量声明的提升是 JavaScript 的特性，所以经常会出面试题
  - 在实际开发时，不要刻意是哟和变量声明提升特性。一定要先定义并给变量赋初值，然后再使用变量

### 重点内容是

1. 前端开发主要有哪些层？语言和功能是什么？

1. JavaScript 的书写位置是哪里？

1. JavaScript 有哪些输出语句？

1. 变量是什么？如何定义变量？变量的合法命名规则有哪些？

1. 只用 var 定义一个变量，但是没有赋初值，这个变量的值是？

1. 什么是变量声明的提升？

1. JavaScript 中，等号的作用是什么？

## JavaScript 基础数据类型

### 数据类型简介和检测

1. JavaScript 中两大类数据类型

   - 基本数据类型
     - Number 数字类型
       - 所有数字不分大小、不分整浮、不分正负，都是数字类型
       - 在表示零点几小数的时候，小数中的零可以省略 e.g. `.5 // 0.5`
       - 科学计数法：较大数或较小数（绝对值较小）可以写成科学计数法 e.g. `3e8 // 300,000,000` `3e-4 // 0.0003`
       - 不同进制的数字： 二进制数值以 0b 开头 八进制数字以 0 开头 十六进制数字以 0x 开头
       - 一个特殊的数字型值 NaN: NaN 是英语“not a number”的意思，即“不是一个数”，但它是一个数字类型的值
       - 0 除于 0 的结果是 NaN，事实上，在数学运算中，若结果不能得到数字，其结果往往都是 NaN
       - NaN 有一个“奇怪”的性质：不自等
     - String 字符串类型
     - Boolean 布尔类型
     - Undefined undefined 类型
     - Null null 类型
   - 复杂数据类型
     - Object
     - Array
     - Function
     - RegExp
     - Date
     - Map
     - Set
     - Symbol

1. `typeof` 运算符
   - 使用 `typeof` 运算符可以检测值或者变量的类型 `typeof <值或者变量>`
   - 5 种基本数据类型的 `typeof` 检测结果
     3-01 完
