# 如何适配
> 本文档仅供客户查阅。

在原PC网站头部源文件中插入一行代码，引用适配文件，适配文件由用户通过平台提供的可视化编辑器进行编辑，由平台打包生成，适配文件主要作用是判断终端类型、URL解析、适配样式应用、数据绑定等功能。当客户通过手机浏览器访问适配成功的PC网站时，手机浏览器会下载适配代码并在手机端运行，适配代码根据适配规则在手机端进行展示。

## 怎么做
为了使移动适配工作变得轻松简单，飞天移动适配云提供了友好的可视化编辑器，集成了大量的移动端UI组件，能够适应移动设备上的各种样式布局，适配人员可以在线使用，通过拖拽UI组件，完成页面布局，对组件属性进行设置，调整成想要的样式，即可完成适配编辑工作，大大缩减了开发周期，平均两个工作日即可完成PC网站的适配规则设置。
我们也为开发人员提供了高级功能，有开发能力的程序员，可以自定义样式代码和数据选择脚本。


## [规则配置基础知识]

> 在规则配置时，首先需要了解一下知识，不用担心，花少量时间，即可基本掌握.

* [`[CSS]` CSS选择器](http://www.w3school.com.cn/cssref/css_selectors.asp)
* [`[Regex]` 正则表达式](/regex.md)


## [规则配置代码片段]
> 您可以直接以下代码片段，完成您的转换.

**轮播图适配**
```javascript
一、原PC网站为Flash，但有js定义轮播图数组的情况

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

二、图片和说明不在一起定义

function ()
{
  var r=[];
  var pic=[];
  _$("#pic > li").each(function() {
    pic.push(
      _$(this).find("img").attr("ysrc")
    );
  });
  var i=0;
  _$("#txt > li").each(function() {
    r.push({
      title:_$(this).find("a").text(),
      link:_$(this).find("a").attr("href"),
      src:pic[i]
    });
    i++;
  });
  
  return r;
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

**点击图片控件后，弹出二维码图片**
```javascript

function()
{
  let data={
    src:"http://hlzw-10002785.file.myqcloud.com/Upload/imgs/20170711/file_5964998eded45.png",
    href:'',
    title:false,
    description:'',
  };
  setTimeout(()=>{
    _$('#Img57772').click(()=>{
      var oDiv = document.createElement('div');
      oDiv.id="mask57772";
      oDiv.innerHTML = '<span>X</span><img style="width: 50%;top: 100px;position: relative;display: block;margin: auto;" src="http://www.gzgov.gov.cn/images/E01201E6-6A96-409A-99D0-35520E0C4B35.png"/>';
     	oDiv.onclick=function(e){
      	_$('#mask57772').remove();
      };
      oDiv.style.position="fixed"
      oDiv.style.top="0px";
      oDiv.style.bottom="0px";
      oDiv.style.width="100%";
      oDiv.style.textAlign="center";
      oDiv.style.background="rgba(0, 0, 0, 0.71)";
      document.body.appendChild(oDiv);
    });
  },500);
  return data;
}
```
