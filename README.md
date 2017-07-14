# 如何适配
> 本文档仅供客户查阅。

在原PC网站头部源文件中插入一行代码，引用适配文件，适配文件由用户通过平台提供的可视化编辑器进行编辑，由平台打包生成，适配文件主要作用是判断终端类型、URL解析、适配样式应用、数据绑定等功能。当客户通过手机浏览器访问适配成功的PC网站时，手机浏览器会下载适配代码并在手机端运行，适配代码根据适配规则在手机端进行展示。

## 怎么做
为了使移动适配工作变得轻松简单，飞天移动适配云提供了友好的可视化编辑器，集成了大量的移动端UI组件，能够适应移动设备上的各种样式布局，适配人员可以在线使用，通过拖拽UI组件，完成页面布局，对组件属性进行设置，调整成想要的样式，即可完成适配编辑工作，大大缩减了开发周期，平均两个工作日即可完成PC网站的适配规则设置。
我们也为开发人员提供了高级功能，有开发能力的程序员，可以自定义样式代码和数据选择脚本。


## [规则配置基础知识]

> 在规则配置时，首先需要了解一下知识，不用担心，花少量时间，即可基本掌握.

* [`[CSS]` CSS选择器](/sections/css.md#类型判断)
* [`[Regex]` 正则表达式](/sections/regex.md#作用域)


## [规则配置代码片段]
> 您可以直接以下代码片段，完成您的转换.

**轮播图适配**
```javascript
function(set) {
  var pic = window.pics.split("|");
  var link = window.links.split("|");
  var title = window.texts.split("|");
  var data = [];
  for (var i = 0; i < pic.length; i++) {
    if (pic[i]) {
      data.push({
        src: pic[i],
        title: title[i],
        link: link[i]
      });
    }
  }
  return data;
}
```

**新闻列表适配**
```javascript
function(){
  var r=[];
  _$('#newsList > ul >li').each(function(){
    r.push(
      {
        name:_$(this).find('a').attr('title'),
        url:_$(this).find('a').attr('href'),
        ctime:false,
        pic:false
      }
    );
  });
  return r;
}
```
