# GeekPark 前端代码规范 v1.1  
![GeekPark](http://www.geekpark.net/public/img/icons/logo-black.png "极客公园 | 发现产品的价值") 
![BusinessValue](http://businessvalue.com.cn/css/images/logo.gif "商业价值 | 科技改变商业 创新赢得未来")
![ITvalue](http://www.itvalue.com.cn/public/images/forward/itvalue-logo.png "ITvalue | 基于知识分享的CIO人际网络")

[GeekPark] & [BusinessValue] & [ITvalue] 前端开发团队遵循和约定的代码书写规范，意在提高代码的规范性和可维护性。

## 索引
* [规范内容](#规范梗概)
    * [规范说明](#规范说明)
    * [结构说明](#结构说明)
* [书写规范](#书写规范)
    * [样式与内容分离](#样式与内容分离)
        * [项目结构](#项目结构)
        * [重构步骤约定](#重构步骤约定)
        * [命名规范](#命名规范)
        * [格式&编码](#格式编码)
    * [CSS 细化规范](#css-细化规范)
        * [CSS(含Less)文件结构](#CSS含less文件结构)
        * [CSS各属性](#css各属性的排列顺序：不做硬性要求)
        * [CSS嵌套规则](#css嵌套规则)
        * [CSS格式化](#css格式化)
    * [XHTML 细化规范](#xhtml-细化规范)
        * [HTML 注释格式](#html-注释格式约定)
        * [HTML嵌套规则](#html嵌套规则)
    * [JS 细化规范](#js-细化规范)
        * [JS 文件结构](#js-文件结构)
        * [jQuery Call](#jquery-call)
        * [jQuery Plugin](#jquery-plugin)
        * [JSON格式规范](#json格式规范)
* [Newletter制作规范](#newletter-制作规范)
    * [生产力工具推荐(Mac)](#生产力工具推荐mac)
    * [前端相关工具](#前端相关工具)
    * [其他效率工具](#其他效率工具)
    * [其他收集](#其他收集)
* [相关技巧](#相关技巧)
* [参考数据](#参考数据)

## 规范梗概
----

##### 规范说明  
此规范为参考规范，不全是硬性要求，部分硬性约定见下一条[书写规范](#书写规范)，统一团队编码规范和风格。让所有代码都是有规可循的，并且能够得到沉淀，减少重复劳动。

##### 结构说明  
-- [项目结构](#项目结构)  
----|---- [CSS文件结构](#css-文件结构)  
----|---- [JS文件结构](#js-文件结构)  

## 书写规范
----
### 样式与内容分离

#### 项目结构  
>
    --- 
     |---- index.html             入口页    
     |---- js/                    JS //具体见JS细化结构                 
     |---- css/                   CSS //具体见CSS细化结构

#### 重构步骤约定
1. `index.html` 全部样式附着于 `class="xxx"` **注：** _此时文件中不包含任何一个 id="xxx"_
2. 为上一步书写 CSS style  
**\[至此重构完成\]**
3. 开始书写`js`交互文件，使用 `ID` 和 `Class` 定位被操作句柄
4. 向 `index.html` 中需要的地方添加 `id="xxx"` 及 `data-xxx="xxx"`  
**\[至此交互效果完成\]**

#### 命名规范  
* 文件及文件夹: 全部英文小写字母+数字或连接符"`-` , `_` "，不可出现其他字符
如：`../css/style.css, jquery.1.x.x.js` 
* 文件：调用 `/libs` 文件需包含版本号，压缩文件需包含`min`关键词，其他插件则可不包含
如：`/libs/jquery.1.9.1.js` `/libs/modernizr-1.7.min.js` `fileuploader.js` `plugins.js`
* ID: [匈牙利命名法] & [小駝峰式命名法]  
如：`firstName` `topBoxList` `footerCopyright`
* Class: [减号连接符]  
如：`top-item` `main-box` `box-list-item-1`
* 尽量使用语义明确的单词命名，避免 `left` `bottom` 等方位性的词语

#### 格式&编码
* 文本文件： `.xxx` UTF-8_\(无BOM\)_ 编码
* 图片文件： `.png` _(PNG-24)_ `.jpg` _(压缩率8-12)_
* 动态图片： `.gif`
* 压缩文件： `.tar.gz` `.zip`

### CSS 细化规范

#### CSS 文件结构 
>
    --- ../css/
     |---- css/libs/reset.css                  CSS reset文件
     |---- … … 
     |---- css/images/                         主 CSS-sprite 图片     
     |---- css/style.css                       主 CSS 样式表
     |---- … … 
     |---- css/images/xxx/sprite.png           xxx 的 CSS-sprite 图片
     |---- css/xxx-style.css                   xxx 的 样式表
     
#### CSS(含Less) 文件结构  
>
    --- ../css/
     |---- css/libs/reset.less            CSS reset文件
     |---- css/libs/elements.less         Less 函数复用文件
     |---- … … 
     |---- css/images/                         主 CSS-sprite 图片     
     |---- css/style.less                      主样式Less
     |---- css/style.css                       less -> css 自动生成
     |---- … … 
     |---- css/images/xxx/sprite.png           xxx 的 CSS-sprite 图片
     |---- css/xxx-style.less                  xxx 的 Less
     |---- css/xxx-style.css                   less -> css 自动生成

#### 使用Less
在 `.less`文件头部引入 [reset.less]&[elements.less]，之后调用如下属性传参即可，具体使用说明见->[Lesselements]官方文档   

    @import "reset.less";  
    @import "elements.less";
>
    .gradient
    .bw-gradient
    .bordered
    .drop-shadow
    .rounded
    .border-radius
    .opacity
    .transition-duration
    .rotation
    .scale
    .transition
    .inner-shadow
    .box-shadow
    .columns
    .translate

#### CSS reset
CSS reset 文件使用：[reset.css] 或 [reset.less]   

* reset文件用于重设各个浏览器的默认样式方案，解决其引起的耦合问题。  
* 也可使用 `.clearfix` 清除浮动

#### CSS 注释格式约定  
>
    /*
    @name: Drop Down Menu
    @description: Style of top bar drop down menu.
    @require: reset.css
    @author: Andy Huang(andyahung@geekpark.net)
    */

_其中，@require为可选项_ 

* CSS换行制表：使用 2 <del>或4</del> 个空格，而非\[Tab\]
* 书写格式：
    * CSS名称+冒号+属性  
    如：`.box1 {float:left;}`
    * 建议保留`{`左侧空格，字体名用`\`包含  
    如：`.box1,.box2,.box3 {font-family:Courier,'Courier New';}`
    * 避免中文，或使用转义，推荐前者  
    如：`font-family: "Microsoft YaHei";` `font-family:\5fae\8f6f\96c5\9ed1;`
        
#### CSS各属性的排列顺序：不做硬性要求  
_如：以下2种顺序均可_

    .box {
      /* 顺序1 */
      background: none repeat scroll 0 0 transparent;
      bottom: 11px;
      position: relative;
      width: 22px;
      z-index: 33;
    }
    .box {
      /* 顺序2 */
      z-index: 33;
      width: 22px;
      bottom: 11px;
      background: transparent none repeat scroll 0 0 ;
      position: relative;
    }
  
#### CSS嵌套规则    
    /* 推荐嵌套层级 */
    .ui-icon-rarr{}
    .ui-icon-larr{}
    .ui-title{}
    .ui-nav .ui-list{}
    .ui-table .ui-list{}

    /* 不推荐 */
    .ui-icon-rarr{}
    .ui-icon-larr{}
    .ui-title{}
    .ui-list{}
    .ui-nav{}

#### CSS格式化  
勿格式化，保留下面这种格式，增加可读性和可维护性，后期后台程序(如：PHP/Python)会将CSS压缩成 **一行** 输出：

    .box{
      /* 勿格式化，增加可读性 */
      background: none repeat scroll 0 0 transparent;
      bottom: 11px;
      position: relative;
      width: 22px;
      z-index: 33;
    }
    
### XHTML 细化规范

#### HTML 注释格式约定  
    <!--
    @name: Drop Down Menu
    @description: Style of top bar drop down menu.
    @author: Andy Huang(andyahung@geekpark.net)
    -->
    
    <div id="header">
        <div class="xxx">
            <span>HTML行内注释格式</span>
        </div>
    </div><!-- #header end-->

* HTML换行缩进：**采用 2 空格**

#### HTML嵌套规则  
    /* 推荐嵌套层级 */
      <ul class="ui-nav">
        <li class="ui-nav-item"> some text
          <ul class="ui-nav-item-child">
            <li> some text
              <ul class="ui-list">
                <li class="ui-list-item"> some text</li>
              </ul
            ...
           </ul>
        </li>
        <li
        ...
      </ul>

##### \* 第一行统一使用HTML5标准：<!DOCTYPE html>
    <!DOCTYPE html>
    <html dir="ltr" lang="zh-CN">
    <head>
        <meta charset="utf-8" />
        <title>极客公园 | 创新者社区</title>
        <meta name="keywords" content="xxxx, xxx, xxxxx" />
        <meta name="description" content="xxxxxxxxxxxxxxxxxxxx" />
        

##### Meta 的使用：（需根据具体项目选择）参考 [cool-head]
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <meta http-equiv="Cache-Control" content="max-age=7200" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="alternate" type="application/rss+xml" title="RSS 2.0" href="http://feeds.geekpark.net/" />
    <link rel="shortcut icon" href="favicon.ico">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
    
    <script type="text/javascript" src="/js/xxx.js"></script>
    <link rel="stylesheet" href="/css/xxx.css">
    
    <script type="text/javascript">
        Google 统计代码 的位置在离</head>最近的位置
	</script>
    </head>

* `<img>`标签默认缺省格式：`<img src="xxx.png" alt="缺省时文字" />` 避免出现[src="" 问题]
* `<a>`标签缺省格式：`<a href="###" title="链接名称">xxx</>` 注：`target="_blank"` 根据需求决定  
* <a>标签预留链接占位符使用`###`，参见：[a标签占位符问题]
* 所有标签需要符合XHTML标准闭合
* 一律统一标签结尾斜杠的书写形式：`<br />` `<hr />` 注意之间空格
* 避免使用已过时标签，如：`<b>` `<u>` `<i>` 而用 `<strong>` `<em>`等代替
* 使用`data-xxx`来添加自定义数据，如：`<input data-xxx="yyy"/>`
* 避免使用`style="xxx:xxx;"`的内联样式表
* 特殊符号使用参考[HTML 符号实体]

### JS 细化规范
----

##### JS 文件结构
>
    ---/js/
    |---- /libs/plugin-1/       使用到的js插件1  
    |---- /libs/plugin-2/       使用到的js插件2  
    |---- /libs/plugin-3/       使用到的js插件3  
    |---- script.js             单独书写的js  
    |---- plugins.js            调用的plugins汇总  
    |---- juqery-1.9.x.min.js   调用jq库文件  

* JS 换行缩进：采用 4 空格
* 结束行需添加分号`;`
* jQuery变量要求首字符为 `$`, 私有变量:首字符为`_`; 尽量避免全局变量.
* 避免使用 eval()，setTimeOut使用调用函数，考虑重绘，回流 操作对页面影响  参看：[reflows，repaints]
* JS调试使用`console.log()`及`console.dir()`进行，避免使用弹出框，线上版需要注释所有调试代码
* JS压缩混淆工具: [JS Compressor]  如果使用了压缩，需要留 `name-src.js`在同路径供今后修改使用

##### jQuery Call
    <!-- Grab Google CDN jQuery. fall back to local if necessary -->  
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>  
    <script>!window.jQuery && document.write('<script src="js/jquery-1.7.2.min.js"><\/script>')</script>            
##### jQuery Plugin

* IE对HTML5标签支持，以及浏览器特性检测：[Modernizr] & [html5shiv]
* IE6 PNG 图片支持：[DD_belatedPNG]
* 定制&统一 浏览器的滚动条样式：[jquery-scroll] & [Lionbars]
* hover提示效果文字：[bootstrap-tooltips] & [tipsy]
* 滚动条跟随nav效果：[bootstrap-scrollspy]
* 提示冒泡文字：[grumble.js]
* 导航栏过渡效果：[lavalamp]
* 移动设备的滚动效果：[iscroll 4]
* Mac OS Lion 风格的滚动条：[Lionbars]
* 弹性SlideShow：[kwicks for jQuery]
* 瀑布流：[isotope]
* 抖动效果：[jQ shake]
* LightBox：[fancyBox]
* KenDo UI：[KenDo UI]
* textarea自适应高度：[elastic]
* 提示区域 & 提示层：[noty]
* 浮动话题泡：[jQuery grumble]
* 旋转进度：[jQuery Knob]

##### JSON格式规范  
参考[JSON Style Guide翻译]，原版：[Google JSON Style Guide]

### HTML 细化规范
* HTML `head`部分的结构参看：[cool-head] \(摘取必要内容即可)
* `css` 文件置于都 **头部**
* `jQuery` 及 `Google Analytics`引用置于 **头部**
* 其他效果`js`及`统计代码` 文件置于 **尾部**
* HTML 代码尽量过一遍[HTML5 验证]
* HTML 占位图片使用 [temp.im] & [placehold.us] 图片服务


### Newletter 制作规范
* `CSS`只可使用 **内联样式表** ，如：`style="margin:0;"`
* 设计之初遵循： **图上无文本，文本后无底纹** 的规则
* 使用 `MailChimp HTML Email CSS Fix` 参看下文链接
* 引入 `CSS Reset for HTML Email` 参看下文链接
* 使用`Table`布局而非`DIV`
* 所有图片使用`IMG`标签，如：`<img style="style="display:block" "src="" />`
* 可以适当使用占位符`spacer.gif`
* 多用`<br />`换行而非`<p>`
* 整体最佳宽度为：`550-600px`
* 不使用`Javascript`
* 正式发送给用户之前，多次测试

更多细节参考下面链接：  
[12 Killer Tips and Tricks for Building HTML Email]  
[Coding HTML Newsletters(EDM’s)]


### 生产力工具推荐(Mac)
*for more app detial check -> [IUSETHIS](http://osx.iusethis.com/user/hzlzh 'App pack')*  
##### 前端相关工具

* 编辑器：[Sublime Text 2] / [TextMate 2] / [Vim]
* 命令行：[iTerm2]
* 浏览器调试环境：[Chrome] / [Firefox] + [Firebug]
* 移动设备浏览器：[Mozilla Fennec]
* 兼容性测试：[VirtualBox] + Win XP（IE 8）
* 版本控制工具：[GitHub for Mac] / [Versions] / [SourceTree]
* FTP工具：[Filezilla] / [ForkLift]
* HTTP抓包及Post/Get模拟：[Charles]
* PHP集成环境：[XAMPP for Mac]
* SQL数据库管理：[Sequel Pro]
* 标注工具：[Mark Man] / [xScope]
* 取色拾色器：[Sip] / [Snip] / [xScope]
* MarkDown编辑器：[Mou]
* 浏览器免刷新开发环境：[LiveReLoad] / [CodeKit]
* CSS Sprite切图工具：[SpriteRight]
* Less -> CSS 编译：[CodeKit] / [LiveReLoad] / [Less]
* 配色方案工具：[ColorSchemer Studio]
* 多浏览器Cookie管理：[Cookie]
* 图片素材收集：[Sparkbox] / [Pixa]

##### 其他效率工具

* 快速启动及切换app：[Alfred]
* 笔记：[Evernote]
* 压缩解压：[Keka] / [iPack]

##### 其他收集
* Firefox 扩展收藏集 -> [Firefox Add-ons collections]
* Chrome 扩展 -> 待添加
* Sublime Text 2 技巧  -> [ST2 资源技巧汇总]

### 相关技巧
[Wiki page index]

* [各浏览器的缓存清除方法]  
* [测试技巧Gmail 添加词缀\(.+\)获得多个邮件的方法]  
* [关于Mac Win Linux跨系统传文件，文件名乱码的解决方案]  
* [技术团队"路由代理"解决方案和使用须知]

### 参考数据
涉及到 `设计`->`重构`->`兼容性`->`测试` 时可参考各浏览器的占用情况  
*-- updated: `2012-08`*  via `Google Analytics of GeekPark`  

| 总浏览器分布     |     占有率 |
|:---------------|----------:|
| Chrome         |    38.41% |
| IE             |    23.10% |
| Mozilla Agent  |     9.57% |
| Android Browser|     9.02% |
| Firefox        |     7.99% |
| Safari         |     7.09% |
| Safari (in-app)|     2.45% |
| Opera          |     0.86% |

| IE版本分布     |       占有率 |
|:--------------|------------:|
| IE 8          |      57.73% |
| IE 9          |      21.63% | 
| *IE 6*        |      10.87% |
| *IE 7*        |       9.03% |  
| IE 10         |       0.70% | 

| 移动设备       |       占有率 |
|:--------------|------------:|
| iOS           |      57.99% |
| Android       |      40.72% |
| Nokia         |       0.55% |
| Windows Phone |       0.49% |  

| 屏幕分辨率     |       占有率 |
|:--------------|------------:|
| 1366x768      |      20.23% |
| 1440x900      |      13.17% |
| 1280x800      |      12.85% |
| 320x480       |      10.05% |
| 1024x768      |       5.93% |   

此规范基于 [MIT License] 开源，持续更新维护中，欢迎 `Star` 或 `Fork` 本项并目通过 `Pull Request` 贡献规范。

[GeekPark]: http://geekpark.net/ "http://geekpark.net/"
[ITvalue]: http://www.itvalue.com.cn/ "http://www.itvalue.com.cn/"
[BusinessValue]: http://www.businessvalue.com.cn/

[reflows，repaints]: http://www.zhangxinxu.com/wordpress/2010/01/%E5%9B%9E%E6%B5%81%E4%B8%8E%E9%87%8D%E7%BB%98%EF%BC%9Acss%E6%80%A7%E8%83%BD%E8%AE%A9javascript%E5%8F%98%E6%85%A2%EF%BC%9F/  "重绘,回流参考"
[src="" 问题]: http://js8.in/555.html "src="" 问题"
[a标签占位符问题]: http://www.v2ex.com/t/48511/ "a标签占位符问题"

[匈牙利命名法]: http://zh.wikipedia.org/wiki/%E5%8C%88%E7%89%99%E5%88%A9%E5%91%BD%E5%90%8D%E6%B3%95 "Wiki:匈牙利命名法"
[小駝峰式命名法]:http://zh.wikipedia.org/wiki/%E9%A7%9D%E5%B3%B0%E5%BC%8F%E5%A4%A7%E5%B0%8F%E5%AF%AB "小駝峰式命名法"
[CSS Compressor]: http://www.csscompressor.com/ "CSS 压缩"
[JS Compressor]: http://javascriptcompressor.com/ "JS 压缩和混淆"
[HTML 符号实体]: http://www.w3school.com.cn/html/html_entities.asp 
[Google JSON Style Guide]:http://google-styleguide.googlecode.com/svn/trunk/jsoncstyleguide.xml
[JSON Style Guide翻译]:https://github.com/darcyliu/google-styleguide/blob/master/JSONStyleGuide.md

[Lesselements]: http://lesselements.com/
[Bootstrap]: http://twitter.github.com/bootstrap/ "Bootstrap, from Twitter"
[reset.css]: https://github.com/hzlzh/cool-head/blob/master/Template/css/libs/reset.css "CSS reset 文件"
[reset.less]: https://github.com/hzlzh/cool-head/blob/master/Template/css/libs/elements.less "reset.less from HTML5 Boilerplate"
[elements.less]: https://github.com/hzlzh/cool-head/blob/master/Template/css/libs/reset.less "elements.less from lesselements"
[HTML5 验证]: http://html5.validator.nu/


[Modernizr]: http://modernizr.com/download/
[DD_belatedPNG]: http://www.dillerdesign.com/experiment/DD_belatedPNG/
[html5shiv]: https://github.com/aFarkas/html5shiv
[jquery-scroll]: https://github.com/thomd/jquery-scroll/
[Lionbars]: https://github.com/Charuru/lionbars
[bootstrap-tooltips]: http://twitter.github.com/bootstrap/javascript.html#tooltips
[bootstrap-scrollspy]: http://twitter.github.com/bootstrap/javascript.html#scrollspy
[grumble.js]: https://github.com/jamescryer/grumble.js
[lavalamp]: http://www.gmarwaha.com/blog/2007/08/23/lavalamp-for-jquery-lovers/
[iscroll 4]: https://github.com/cubiq/iscroll
[kwicks for jQuery]: https://github.com/Mottie/Kwicks
[isotope]: https://github.com/desandro/isotope
[jQ shake]: https://gist.github.com/3270711
[fancyBox]: https://github.com/fancyapps/fancyBox
[KenDo UI]: http://www.kendoui.com/purchase.aspx
[elastic]: http://unwrongest.com/projects/elastic/
[cool-head]: https://github.com/hzlzh/cool-head
[noty]: https://github.com/needim/noty
[jQuery grumble]: https://github.com/jamescryer/grumble.js
[tipsy]: https://github.com/jaz303/tipsy
[jQuery Knob]: https://github.com/aterrien/jQuery-Knob

[各浏览器的缓存清除方法]: https://github.com/GeekPark/Doc/wiki/%5B%E5%A6%82%E4%BD%95%E9%81%BF%E5%85%8D%E7%BC%93%E5%AD%98%5D%E5%90%84%E6%B5%8F%E8%A7%88%E5%99%A8%E6%B5%8B%E8%AF%95%E7%BD%91%E9%A1%B5%E6%97%B6%E6%B8%85%E9%99%A4%E7%BC%93%E5%AD%98%E7%9A%84%E6%96%B9%E6%B3%95
[测试技巧Gmail 添加词缀\(.+\)获得多个邮件的方法]: https://github.com/GeekPark/Doc/wiki/%5B%E6%B5%8B%E8%AF%95%E6%8A%80%E5%B7%A7%5DGmail-%E6%B7%BB%E5%8A%A0%E8%AF%8D%E7%BC%80(.--)%E8%8E%B7%E5%BE%97%E5%A4%9A%E4%B8%AA%E9%82%AE%E4%BB%B6%E7%9A%84%E6%96%B9%E6%B3%95
[关于Mac Win Linux跨系统传文件，文件名乱码的解决方案]: https://github.com/GeekPark/Doc/wiki/%E5%85%B3%E4%BA%8E%5BMac%5D-%5BWin%5D-%5BLinux%5D%E8%B7%A8%E7%B3%BB%E7%BB%9F%E4%BC%A0%E6%96%87%E4%BB%B6%EF%BC%8C%E6%96%87%E4%BB%B6%E5%90%8D%E4%B9%B1%E7%A0%81%E7%9A%84%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88
[技术团队"路由代理"解决方案和使用须知]: https://github.com/GeekPark/Doc/wiki/%E6%8A%80%E6%9C%AF%E5%9B%A2%E9%98%9F%5B%E8%B7%AF%E7%94%B1%E4%BB%A3%E7%90%86%5D%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88%E5%92%8C%E4%BD%BF%E7%94%A8%E9%A1%BB%E7%9F%A5

[Sublime Text 2]:http://www.sublimetext.com/2
[TextMate 2]:https://github.com/textmate/textmate
[Vim]:http://macvim.org/
[Chrome]:http://www.google.com/chrome
[Firefox]:http://www.mozilla.org/
[Firebug]:http://getfirebug.com/
[VirtualBox]:https://www.virtualbox.org/
[Versions]:http://versionsapp.com/
[GitHub for Mac]:http://mac.github.com/
[SourceTree]:http://www.sourcetreeapp.com/
[Filezilla]:http://filezilla-project.org/
[ForkLift]:http://itunes.apple.com/us/app/forklift/id412448059?mt=12
[Charles]:http://www.charlesproxy.com/
[XAMPP for Mac]:http://www.apachefriends.org/en/xampp-macosx.html
[Mark Man]:http://www.getmarkman.com/
[xScope]:http://itunes.apple.com/us/app/xscope/id447661441?mt=12
[Sip]:http://itunes.apple.com/app/sip/id507257563?mt=12
[Snip]:http://itunes.apple.com/us/app/snip/id512505421?mt=12
[Mou]:http://mouapp.com/
[LiveReLoad]:http://http://livereload.com/
[Cookie]:http://itunes.apple.com/us/app/cookie/id415585910?mt=12
[ColorSchemer Studio]:http://itunes.apple.com/us/app/colorschemer-studio/id417896628?mt=12
[Less]:http://incident57.com/less/
[CodeKit]: http://incident57.com/codekit/
[SpriteRight]:http://itunes.apple.com/us/app/spriteright/id488584662?mt=12
[iTerm2]: http://www.iterm2.com/
[Mozilla Fennec]: http://www.mozilla.org/projects/fennec
[Sequel Pro]: http://www.sequelpro.com/
[Sparkbox]: http://seesparkbox.com/
[Pixa]: http://www.pixa-app.com/
[Alfred]: http://www.alfredapp.com/
[Evernote]: http://www.evernote.com/
[Keka]: https://itunes.apple.com/us/app/keka/id470158793?mt=12
[iPack]: https://itunes.apple.com/us/app/ipack/id433386677?mt=12

[temp.im]: http://temp.im/
[placehold.us]:http://placehold.us/

[Firefox Add-ons collections]: https://addons.mozilla.org/en-US/firefox/collections/hzlzh/hzlzh/
[ST2 资源技巧汇总]: http://www.douban.com/group/topic/28027863/
[Wiki page index]: https://github.com/GeekPark/Doc/wiki/_pages

[12 Killer Tips and Tricks for Building HTML Email]: http://www.queness.com/post/8784/12-killer-tips-and-tricks-for-building-html-email
[Coding HTML Newsletters(EDM’s)]: http://www.web-ed.com.au/2011/05/coding-html-newsletters-edms-quick-guide/

[MIT License]: http://en.wikipedia.org/wiki/MIT_License
