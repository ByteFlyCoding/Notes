---
title: "WebFront"
date: 2021-06-18T21:34:00+08:00
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

# Web 前端

## HTML5 语法与基础标签

### 互联网基本原理

- 在本地开发 在服务器共享

- HTTP 协议

  1. HTTP 协议(Hypertext Transfer Protocol, 超文本传输协议)是互联网数据传输的常见协议
  1. 一次 HTTP 事务由“HTTP 请求”和“HTTP 响应”构成
  1. 网址前的 http:// 就表示用 http 协议请求页面
  1. 什么是前端、后端？

### HTML5 基本入门

1. 创建第一个网页

   - 创建新文件夹，并打开
   - 新建文件`.html`

2. 浏览网页的方法

3. 认识 HTML5 骨架

   - <!DOCTYPE html> : 文档类型声明DTD，HTML文件第一行必须是DTD(Document Type Definition, 文档类型声明)；不写DTD会引发浏览器的一些兼容问题，不同版本的HTML有不同的DTD写法
   - <html lang="en"></html> : lang属性表示网页的语言，zh表示中文，不改也行
   - <head></head> : 网页的配置，不要认为是网页的头部
   - <body></body> : 书写网页的内容，包括网页的头部、主要内容、页脚等各个部分

4. 字符集
   - <meta charset="UTF-8"> 元标签，表示网页的基础配置 charset:字符集 文件字符集要与该标签上设置的一样，否则会出错
   - <meta name="viewport" content="......"> 视口是设置，在移动开发中会用到
5. title 关键字及页面描述

   - <title></title> 网页的title
       - title标签用来设置网页的标题，文字会显示在浏览器的标签栏上
       - title也是搜索引擎收录网站时显示的标题，为了吸引用户的点击，合理设置title是必要的
   - SEO(Search Engine Optimization, 搜索引擎优化)利用搜索引擎的规则提高在有关搜索引擎内的自然排名，让网站在搜索引擎的结果内占据领先地位，获取品牌收益
     - 合理设置网页的关键词和页面描述，也是 SEO 的重要手段
     - 使用 meta 标签设置网页关键词和描述，name 属性非常关键，用来设置 meta 的具体功能
     - <meta name="Keywords" content=""> Keywords首字母要大写，content里面添加的内容能够提升搜索引擎对这些重点词的抓取
     - <meta name="Description" content=""> Description首字母要大写，页面描述也是搜索引擎显示的简介词语

6. 认识标签

### HTML5 的基本标签

HTML: 超文本标记语言(Hyper Text Markup Language)

- 标签通常是成对存在的
- 不同的标签有不同的功能
- 有的标签不是成对的，而是只有起始标签，称为单标签
- 在 HTML4 代，单标签必须写一个结尾的反斜杠，HTML5 不用写

1. 标题与段落标签
   - 标题标签---h 系列标签表示“标题”语义，h 是 headliine 的意思
     - h1 : 一级标签
     - h2 : 二级标签
     - h3 : 三级标签
     - h4 : 四级标签
     - h5 : 五级标签
     - h6 : 六级标签
     - 搜索引擎非常看重<h1></h1>标签的内容，应该将重点放到<h1></h1>中，比如网页的 logo 等
     - <h1></h1>标签一般只能放置一个，否则会被搜索引擎视为作弊
   - 段落标签
     - <p></p>标签表示段落标签，p是英语paragraph的意思
     - 任何段落都要放到<p></p>标签中，因为 HTML 中即使代码换行了，页面显示效果也不会换行，必须写到<p></p>中
     - <p></p>标签中不能嵌套h系列标签和其他p标签
2. div 标签
   - div 是英文 division “分割”的缩写。<div></div>标签对用来将相关的内容组合到一起，以和其他内容分割，使文档结构更清晰。
   - 比如，网页的头部要放到一个<div></div>标签对中，轮播图也要放到一个<div></div>标签对中，文章内容也要放到一个<div></div>
   - <div></div>是最常见的HTML标签，因为它可以结合CSS使用，实现网页的布局，这种布局形式叫做“DIV+CSS”。
   - <div></div>像是一个容器，什么都可以容纳，因此工程师也习惯称呼<div></div>为“盒子”。
3. 空白折叠现象

   - 文字和文字之间的多个空格、换行会被折叠成一个空格
   - 标签“内壁”和文字之间的空格会被忽略

4. 转义字符

   - 常见转义字符（字符实体）
     - &lt; 小于号
     - &gt; 大于号
     - &nbsp; 空格（不会被折叠）
     - &copy; 版权符号@

5. HTML 注释
   - 为代码书写清晰的注释是非常的重要的,可以使日后再阅读代码或者他人阅读代码提供提示
   - HTML 的注释语法如下：<!-- ...... -->

### 小慕医生项目开发(贯穿 HTML5 与 CSS 的学习)

1. 工作开发流程
   - Step1: 产品经理：提出需求 画原型图
   - Step2: 设计师(UI/UE)：画设计图
   - Step3: 前端开发工程师：编码
   - 原型图： 就是用一些非常简单的线条简明扼要的描述出这个网页大致的栏目与功能区划，对样式和字体没有作出描述
   - 设计图: 能够一比一的网页呈现形式
   - 现在测量原型图非常先进，设计师使用 Axure 或者 Sketch 等软件，可以给我们“直观标注”的原型图/设计图。
2. 项目起步
   - 创建文件夹结构，主要文件夹如下：
     - images: 存放图片
     - css: 存放样式表
     - js: 存放 js 文件
   - 网页首页 index.html
     - 绝大多数服务器默认的网站首页 index.html
3. div 常见的类名
   - <div>标签可以添加class属性表示“类名”，类名服务于CSS
       - 页头:header
       - logo:logo
       - 导航栏:nav
       - 横幅:banner
       - 内容区域:content
       - 页脚:footer
4. 重点内容
   - HTML 是什么？如何创建网页？如何流量网页？
   - HTML5 骨架是什么结构？什么是 DTD?
   - 标题和段落标签、div 标签要如何使用？
5. 难点内容
   - 网页的字符集有什么区别？
   - 常见的 SEO 配置项和应该遵守的规则有哪些？
   - HTTP 是什么？我们做好的网页如何被要用户看见？

### 列表标签

注意代码正确缩进：

- 当 HTML 形成嵌套，必须注意代码的缩进

1. <ul></ul> 无序列表(unordered list)
   * 无序列表<ul></ul>标签，每个列表项都是<li></li>标签
   * 无序列表是一个父子组合标签，不能单独出现
   * <ul></ul>的子标签只能是<li></li>, HTML规定，<ul>的子标签只能是<li>,绝对不能出现其他任何标签
   * <ol>标签的type属性 用来设置编号的类型
       * a 表示小写英文字母编号
       * A 表示大写英文字母编号
       * i 表示小写罗马数字编号
       * I 表示大写罗马数字编号
       * 1 表示数字编号（默认）

1. <ol></ol> 有序列表(order list)
   * 每个列表项都是<li></li>
   * <li></li>标签不能散着放，它必须是<ol></ol>标签或者<ul></ul>标签的子标签
   * 无序列表的 type 属性
      _ 无序列表有 type 属性，可以定义前导符号的样式，但是在 HTNL5 中已经被废弃，建议使用 CSS 替代
      _ disc 默认值，实心圆
      _ circle 空心圆
      _ square 实心方块
   * <ol></ol>标签的start属性
      - start属性值必须是一个整数，指定了列表编号的起始值
      - 此属性的值应为阿拉伯数字，尽管列表条目的编号类型type属性可能指定为罗马数字编号等其他类型编号
      - <ol>标签的reversed属性
             * reversed属性指定列表中的条目是否倒序排列
             * reversed属性不需要值，只需要写reversed单词即可，这是HTML5的全新特性
   * <ul></ul>的子标签只能是<li></li>标签
   * <li>标签中可以放任何东西

1. <dl></dl>定义列表
   * 需要逐条给出定义描述的列表，就是定义列表
   * <dl></dl>是定义列表标签，内容交替出现<dt>、<dd>标签
   * 也允许dt和dd不交替出现，而是分别处于不同的定义列表中
   * 哪里应该使用定义列表
        - 使用什么标签，不应该看样式，应该看语义
        - 只要语义上有“解释说明”含义的文字，且为列表形态，应该使用定义列表

1. <li></li>标签(list item)
   * 不能单独使用 它必须放到<ul>或者<ol>中使用
   * <li></li>标签是容器，内部可以放任何其他标签
   * Notes: <li></li>不能散着放，<ul></ul>的子标签只能是<li></li>，<li></li>可以放任何东西

### 图片标签

1. <img>标签
   * <img> 标签用来在网页中插入图片 <img src="images/xxxxx.jpg">
   * 一定要注意，图片必须要复制到项目文件夹中，一般将图片保存到项目文件夹的images子文件夹中
   * 图片路径必须写正确
   * 图片本质上没有被插入到网页中，只是被引用到了网页中，所以将来要将图片也一起上传到服务器上，将图片复制到项目文件中，即可整体上传
   * <img>标签的alt属性是alternate“替代品”的缩写，它是对图像的文本描述，不是强制性的
   * 如果由于某种原因无法加载图像，浏览器会在页面上显示alt中的备用文本
   * <img>标签的width、height属性 width、height属性分别设置宽度和高度，单位是像素，但是不需要写单位
   * 如果省略其中一个属性，则表示按原始比例缩放图片

1. 网页上支持的图片格式
   * .bmp windows画图软件默认保存的格式，位图
   * .gif 支持动画(比如表情包)
   * .jpeg(.jpg) 有损压缩图片，用于照片
   * .png 便携式网络图像，用于logo、背景图形等，支持透明和半透明
   * .svg 矢量图片
   * .webp 最新的压缩算法非常优秀的图片格式

1. 相对路径

1. 绝对路径

1. 超级链接 超级链接是将网页和网页联结在一起的方法，是互联网“成网”的原因。

   - <a>标签 使用<a>标签制作超级链接 <a href="xxx.html">xxxxxx</a>
       * href属性支持相对路径和绝对路径
       * <a>标签的title属性 <a>标签的title属性用于设置鼠标的悬停文本
       * 将<a>标签的target属性设置为blank,即可在新标签中打开网页
       * HTML4代，blank之前有一个下划线 `_blank`
       * 图片也可以设置超级链接，只需要用<a>标签包裹img标签即可

   - 页面内锚点
       * 较长的页面，可以适当的给h系列标签添加id属性，它将成为页面的“锚点” <h1 id="">xxxxx</h1>
       * 当网址后面添加#时，页面将自动滚动到锚点所在位置
       * 其他页面的超级链接，可以链接到指定指定锚点

   - 下载链接
       * 指向exe、zip、rar等文件格式的链接，将自动成为下载链接

   - 邮件链接、电话链接
       * 有`mailto:` 前缀的链接是邮件链接，系统将自动打开Email相关软件
       * 有`tel:` 前缀的链接是电话链接，系统将自动打开拨号盘

1. 音频和视频
   - 曾经在网页中插入音视频需要借助Flash，现在，Flash技术基本要被淘汰了，HTML5可以在网页中插入音视频
   - 音频
       * 在浏览器中插入音频需要使用<audio>标签，兼容到IE9
       * <audio controls src="音频地址">抱歉，您的浏览器不支持audio标签，请升级浏览器</audio> controls：显示播放控件 标签对中是对不兼容audio标签的浏览器的显示文字
       * 常用的音频格式是mp3和ogg格式
       * autoplay属性，声明autoplay属性，音频会自动播放
       * loop属性 声明loop属性，将循环播放音频
   - 视频
       * 在浏览器中插入视频需要使用<video>标签，兼容到IE9
       * <video control src="视频地址" loop autoplay>抱歉，您的浏览器不支持video标签，请升级浏览器</video> controls：显示播放控件 标签对中是对不兼容video标签的浏览器的显示文字
       * 常见音频格式是mp4、ogv、webm等格式

1. 大纲标签
    * div标签实现文档区块分隔 曾经div标签是文档区块分隔的唯一手段，为了区分每个div的功能，程序会借助div标签的class属性
    * HTML5区块标签 HTML5推出了众多新的区块标签
        - <section> 文档的区域，语义比div大
        - <article> 文档的核心文章内容，会被搜索引擎主要抓取
        - <aside> 文档的非必要相关内容，比如广告等
        - <nav> 导航条
        - <header> 页头
        - <main> 网页核心部分
        - <footer> 页脚
        - <adress>

1. <span>标签
   * <span>标签是文本中的“区块”标签，本身没有任何特殊的显示效果，可以结合CSS来丰富样式

1. <b>、<u>、<i>标签充满浓浓的“样式”，已经被CSS替代，但是在网页中也可以表示需要强调的文本
    * <b> 被加粗的文字，CSS已经替代了它的功能
    * <u> 加下划线的文字，CSS已经替代了它的功能
    * <i> 倾斜的文字，CSS已经替代了它的功能

1. <strong>、<em>、<mark>标签
    * <strong>、<em>、<mark>标签均表示强调语义
    * <strong> 代表特别重要的文字
    * <em> 代表强调文字
    * <mark> 代表一段需要被高亮的文字

1. <figure>、<figcaption> 标签
    * <figure>元素代表一段独立性的内容，与说明<figcaption>配合使用，它是一个独立的引用单元，比如建议读者拓展视野的图片等，当这部分转移到附录中或者其他页面时不会影响到主体

1. 表单是什么
    * 表单用来收集信息，比如注册、登录、发送评论反馈、购买商品等等
    * 表单的创建
        - 所有HTML表单都以一个<form>元素开始 <form action="xxxxx" method="post"></form> action属性表示表单要提交的后台程序的网址 method属性表示表单提交的方式，有get或post
    * 基本控件
        - 单行文本框 使用`type`属性值被设置为`text`的<input>元素可以创建单行文本框，它是一个单标签 <input type="text">
        - `value`属性表示已经填好的值
        - `placeholder`值表示提示文本，将以浅色文字写在文本框中，并不是文本框中的值 <input type="text" placeholder="请输入姓名">
        - `disable`属性表示用户不能与元素交互，即“锁死”
    * 单选按钮
        - 使用`type`属性的值被设置为`radio`的<input>元素可以创建单选按钮
        - 互斥的单选按钮应该设置它们的`name`为相同的值
        - 单选按钮要有`value`属性值，向服务器提交的就是value值
        - 单选按钮如果加上了`checked`属性，表示默认被选中
    * `label`标签用来将文字和单选按钮进行绑定，用户单击文字的时候也视为点击了单选按钮 <label><input type="radio">xxx</label>
        - 在HTML4时代，label标签是通过for属性和单选按钮的id属性进行绑定的 <input type="radio" id="num1"><label for="num1"></label>
    * 复选框
        - 使用type属性值被设置为`checkbox`的<input>元素可以创建复选框 <input type="checkbox">
        - 同组复选框应该设置它们的`name`为相同值
        - 复选框要有`value`属性值，向服务器提交的就是`value`值
    * 密码框
        - 使用type属性值被设置为`password`的<input>元素可以创建密码框
    * 下拉菜单
        - <select>标签表示下拉菜单，<option>是它内部的选项
            ```html
                  <select>
                     <option value="alipay">支付宝</option>
                     <option value="wx">微信</option>
                     <option value="bank">网银</option>
                  </select>
            ```
        - <option> 元素中设置一个 `selected` 属性可以将其设置为页面加载完成时默认选中的元素
        - <textarea></textarea>表示多行文本框 rows和cols属性，用于定义多行文本框的行数和列数
            ```html
                  <textarea name="" id="" cols="xx" rows="xx"></textarea>
            ```
    * 三种按钮
        - 表单中常见的三种按钮，它们也都是input标签，type属性值不同
        - button 普通按钮 <input type="button" value="">在HTML5中被<button name="xxx">xxxx</button>取代
        - submit 提交按钮 <input type="submit" value="xxxx">
        - reset 重置按钮

1. input类型总结
    * text 单行文本框
    * radio 单选按钮
    * checkbox 多选按钮
    * password 密码框
    * button 普通按钮
    * reset 重置按钮
    * submit 提交按钮

1. HTML5中新增的表单控件
    * color 颜色选择控件    <input type="color">
    * date time 日期、时间选择控件    <input type="date"> <input type="time">
    * email 电子邮件输入控件    <input type="email">
    * number 数字输入控件    <input type="number">
    * range 拖拽条    <input type="range" min="xx" max="xx">
    * search 搜索框    <input type="search">
    * url 网址输入控件    <input type="url">

1. <datalist>控件
    * <datalist>控件可以为输入框提供一些备选项，当用户输入的内容与备选项文字相同时，将会显示智能感应
        ```html
            <input type="text" list="listName">
            <datalist id="listName">
                <option value="xxx">
                <option value="xxx">
                <option value="xxx">
                <option value="xxx">
                <option value="xxx">
                <option value="xxx">
            </datalist>
        ```

1. <input>标签required属性 表示必须填写了该标签才可以提交

1. 表格标签 <table> <tr> <td>标签
    * table是表格的意思
    * table row 表格行
    * table data 表格数据
    ```html
       <table>
             <tr>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
             </tr>
             <tr>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
             </tr>
             <tr>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
             </tr>
       </table>
    ```
    * <table>的border属性 <table>标签的border属性能够显示边框
        ```html
            <!-- <num>表示边框的像素 -->
            <table border="<num>">
                ......
                ......
            </table>
        ```
    * <table>的caption属性 <caption>是表格的标题，它常常作为<table>的第一个子元素出现
   ```html
      <table>
            <caption>我是表格的标题</caption>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
      </table>
   ```
    * <th>标签 <th>是“标题小格”，可以替代<td>的作用，表示标题小格
   ```html
      <table>
            <caption>我是表格的标题</caption>
            <tr>
               <th>xxxx</th>
               <th>xxxx</th>
               <th>xxxx</th>
               <th>xxxx</th>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
      </table>
   ```

1. 单元格合并
    * colspan属性用来设置td或者th的列跨度
    * rowspan属性用来设置td或者th的行跨度
   ```html
      <table border="1">
            <caption>我是表格的标题</caption>
            <tr>
               <th>xxxx</th>
               <th>xxxx</th>
               <th>xxxx</th>
               <th>xxxx</th>
            </tr>
            <tr>
               <td colspan="<num>" colspan="<num>">xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
            <tr>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
               <td>xx</td>
            </tr>
      </table>
   ```