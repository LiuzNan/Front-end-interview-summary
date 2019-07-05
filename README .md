# 一、HTML

### 1.Doctype作用？标准模式与兼容模式各有什么区别?

```
<!DOCTYPE>声明位于HTML文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
标准模式（standards mode）：浏览器根据标准规约来渲染页面。
混杂模式（quirks mode）：浏览器采用更加宽松的、向后兼容的方式来渲染页面。
```

### 2.简述一下你对HTML语义化的理解？

```
1.正确的标签做正确的事情
2.页面内容结构化
3.无CSS样子时也容易阅读，便于阅读维护和理解
4.便于浏览器、搜索引擎解析。 利于爬虫标记、利于SEO
```

### 3.行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？它们有什么特点？

```
行内元素：a、b、span、img、input、strong、select、label、em、button、textarea
块级元素：div、ul、li、dl、dt、dd、p、h1-h6、blockquote
空元素:br、meta、hr、link、input、img

行内元素的特点：
1.和其他元素都在一行上
2.高，行高及外边距和内边距部分可改变
3.宽度只与内容有关
4.行内元素只能容纳文本或者其他行内元素
5.display属性为inline
水平方向的padding-left、padding-right、margin-left、margin-right都产生边距效果，
但竖直方向的padding-top、padding-bottom、margin-top、margin-bottom却不会产生边距效果。
不可以设置宽高，其宽度随着内容增加，高度随字体大小而改变，内联元素可以设置外边界，但是外边界不对上下起作用，只能对左右起作用。

块级元素的特点：
1.总在新行上开始，占据一整行
2.默认情况下，其宽度自动填满其父元素宽度
3.宽度始终是与浏览器宽度一样，与内容无关
4.它可以容纳内联元素和其他块元素
5.display属性为block
块级元素的垂直相邻外边距margin会合并。

空元素的特点：
没有内容的 HTML 内容被称为空元素。空元素是在开始标签中关闭的。
<br /> 就是没有关闭标签的空元素（<br /> 标签定义换行）。
在 XHTML、XML 以及 HTML 中，所有元素必须被关闭。
在开始标签中添加斜杠，比如 <br />，是关闭空元素的正确方法，HTML、XHTML 和 XML 都接受这种方式。
即使 <br> 在所有浏览器中都是有效的，但使用 <br /> 其实是更长远的保障。
```

### 4.页面导入样式时，使用link和@import有什么区别？

```
1.老祖宗的差别。link属于XHTML标签，而@import完全是CSS提供的一种方式。
link标签除了可以加载CSS外，还可以做很多其它的事情，比如定义RSS，定义rel连接属性等，@import就只能加载CSS了。
2.加载顺序的差别。当一个页面被加载的时候（就是被浏览者浏览的时候），link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。所以有时候浏览@import加载CSS的页面时开始会没有样式（就是闪烁），网速慢的时候还挺明显.
3.兼容性的差别。由于@import是CSS2.1提出的所以老的浏览器不支持，@import只有在IE5以上的才能识别，而link标签无此问题。
4.使用dom控制样式时的差别。当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。
```

### 5.介绍一下你对浏览器内核的理解？

```
主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。

JS引擎则：解析和执行javascript来实现网页的动态效果。

最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。
```

### 6.html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

```
 * HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
  	  绘画 canvas;
  	  用于媒介回放的 video 和 audio 元素;
  	  本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
        sessionStorage 的数据在浏览器关闭后自动删除;
  	  语意化更好的内容元素，比如 article、footer、header、nav、section;
  	  表单控件，calendar、date、time、email、url、search;
  	  新的技术webworker, websocket, Geolocation;

    移除的元素：
  	  纯表现的元素：basefont，big，center，font, s，strike，tt，u;
  	  对可用性产生负面影响的元素：frame，frameset，noframes；

  * 支持HTML5新标签：
  	 IE8/IE7/IE6支持通过document.createElement方法产生的标签，
    	 可以利用这一特性让这些浏览器支持HTML5新标签，
    	 浏览器支持新标签后，还需要添加标签默认的样式。

       当然也可以直接使用成熟的框架、比如html5shim;
  	 <!--[if lt IE 9]>
  		<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
  	 <![endif]-->

  * 如何区分HTML5： DOCTYPE声明\新增的结构元素\功能元素
```

### 7.HTML5的离线储存怎么使用，工作原理能不能解释一下？

```
在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。
  原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。
  使用：只要在你的页面头部像下面一样加入一个manifest的属性就可以了。
    <!DOCTYPE HTML>
    <html manifest = "cache.manifest">
    ...
    </html>
    
    然后cache.manifest文件的书写方式，就像下面这样：
    CACHE MANIFEST
    #v0.11

    CACHE:
    js/app.js
    css/style.css

    NETWORK:
    resourse/logo.png

    FALLBACK:
    / /offline.html
    
离线存储的manifest一般由三个部分组成:
1.CACHE:表示需要离线存储的资源列表，由于包含manifest文件的页面将被自动离线存储，所以不需要把页面自身也列出来。
2.NETWORK:表示在它下面列出来的资源只有在在线的情况下才能访问，他们不会被离线存储，所以在离线情况下无法使用这些资源。不过，如果在CACHE和NETWORK中有一个相同的资源，那么这个资源还是会被离线存储，也就是说CACHE的优先级更高。
3.FALLBACK:表示如果访问第一个资源失败，那么就使用第二个资源来替换他，比如上面这个文件表示的就是如果访问根目录下任何一个资源失败了，那么就去访问offline.html。
```

### 8.浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

```
在线的情况下：浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。
离线的情况下：浏览器就直接使用离线存储的资源。
```

### 9.请描述一下 cookies，sessionStorage 和 localStorage 的区别？

```
相同点：都存储在客户端
不同点：
1.存储大小
cookie数据大小不能超过4k。
sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
2.有效时间
localStorage 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
sessionStorage 数据在当前浏览器窗口关闭后自动删除。
cookie 设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
3. 数据与服务器之间的交互方式
cookie的数据会自动的传递到服务器，服务器端也可以写cookie到客户端
sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
```

### 10.iframe是什么？有哪些优缺点？

```
iframe的优点：
1.iframe能够原封不动的把嵌入的网页展现出来。
2.如果有多个网页引用iframe，那么你只需要修改iframe的内容，就可以实现调用的每一个页面内容的更改，方便快捷。
3.网页如果为了统一风格，头部和版本都是一样的，就可以写成一个页面，用iframe来嵌套，可以增加代码的可重用。
4.如果遇到加载缓慢的第三方内容如图标和广告，这些问题可以由iframe来解决。

iframe的缺点：
1.会产生很多页面，不容易管理。
2.iframe框架结构有时会让人感到迷惑，如果框架个数多的话，可能会出现上下、左右滚动条，会分散访问者的注意力，用户体验度差。
3.代码复杂，无法被一些搜索引擎索引到，这一点很关键，现在的搜索引擎爬虫还不能很好的处理iframe中的内容，所以使用iframe会不利于搜索引擎优化。
4.很多的移动设备（PDA 手机）无法完全显示框架，设备兼容性差。
5.iframe框架页面会增加服务器的http请求，对于大型网站是不可取的。

分析了这么多，现在基本上都是用Ajax来代替iframe，所以iframe已经渐渐的退出了前端开发
```

### 11.Label的作用是什么？是怎么用的？

```
label标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

属性：
Label标签有两个属性，一个是for，一个是 accesskey。
for功能：表示这个Lable是为哪个控件服务的，Label标签要绑定了for指定HTML元素的ID或name属性，你点击这个标签的时候，所绑定的元素将获取焦点 ，点击label所包裹内容，自动指向for指定的id或name
accesskey则定义了访问这个控件的热键( 所设置的快捷键不能与浏览器的快捷键冲突，否则将优先激活浏览器的快捷键)
用法：
<label for="username">姓名</label><input id="username" type="text">
<label for="username" accesskey＝"N">姓名</label><input id="username" type="text">
```

### 12.HTML5的form如何关闭自动完成功能？

```
给不想要提示的 form 或某个 input 设置为 autocomplete=off。
```

### 13.如何实现浏览器内多个标签页之间的通信？

```
方法一：使用localStorage
使用localStorage.setItem(key,value);添加内容
使用storage事件监听添加、修改、删除的动作   
window.addEventListener("storage",function(event){
        $("#name").val(event.key+”=”+event.newValue);
});

方法二：使用cookie+setInterval
HTML代码
<inputid="name"><input type="button" id="btnOK"value="发送">
JS代码-页面1   
 $(function(){
     $("#btnOK").click(function(){
         var name=$("#name").val();
         document.cookie="name="+name;
     });
  });
JS代码-页面2
 //获取Cookie天的内容
 function getKey(key) {
  	return JSON.parse("{\""+ document.cookie.replace(/;\s+/gim,"\",\"").replace(/=/gim, "\":\"") +"\"}")[key];
 }
 //每隔1秒获取Cookie的内容
 setInterval(function(){
    console.log(getKey("name"));
 },1000);
 
 方法三：websocket通讯
 
 方法四：html5浏览器的新特性SharedWorker
```

### 14.webSocket如何兼容低浏览器？

```
  Adobe Flash Socket 、
  ActiveX HTMLFile (IE) 、
  基于 multipart 编码发送 XHR 、
  基于长轮询的 XHR
```

### 15.页面可见性（Page Visibility API） 可以有哪些用途？

```
通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;
在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放。
```



# 二、CSS

### 1.介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？

```
  （1）盒模型有两种， IE 盒子模型、W3C 盒子模型；
  （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
  （3）区  别： IE的content部分把 border 和 padding计算了进去;
```

### 2.CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？

```
CSS 选择符：
1.id选择器(# myid)
2.类选择器(.myclassname)
3.标签选择器(div, h1, p)
4.相邻选择器(h1 + p)
5.子选择器(ul > li)
6.后代选择器(li a)
7.通配符选择器( * )
8.属性选择器(a[rel = "external"])
9.伪类选择器(a: hover, li:nth-child)

可继承的样式：
1.font-size
2.font-family
3.color
4.text-indent

不可继承的样式：
1.border
2.padding
3.margin
4.width
5.height

优先级算法：
1.优先级就近原则，同权重情况下样式定义最近者为准;
2.载入样式以最后载入的定位为准;
3.!important >  id > class > tag  
4.！imprtant>内联样式>id>class  
 
CSS3新增伪类举例：
p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
p:last-of-type  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
p:only-child    选择属于其父元素的唯一子元素的每个 <p> 元素。
p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。
:enabled :disabled 控制表单控件的禁用状态。
:checked        单选框或复选框被选中。
```

### 3.如何居中div？

```
1.水平居中：给div设置一个宽度，然后添加margin:0 auto属性
 div{
 	width:200px;
 	margin:0 auto;
  }
  
2.让绝对定位的div居中
 div {
 	position: absolute;
 	width: 300px;
 	height: 300px;
 	margin: auto;
 	top: 0;
 	left: 0;
 	bottom: 0;
 	right: 0;
 	background-color: pink;	/* 方便看效果 */
 }
 
3.水平垂直居中一
 确定容器的宽高 宽500 高 300 的层
 设置层的外边距
 div {
 	position: relative;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	margin: -150px 0 0 -250px;     	/* 外边距为自身宽高的一半 */
 	background-color: pink;	 	/* 方便看效果 */

  }
  
4.水平垂直居中二
 未知容器的宽高，利用 `transform` 属性
 div {
 	position: absolute;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	transform: translate(-50%, -50%);
 	background-color: pink;	 	/* 方便看效果 */
 }
 
5.水平垂直居中三
 利用 flex 布局
 实际使用时应考虑兼容性
 .container {
 	display: flex;
 	align-items: center; 		/* 垂直居中 */
 	justify-content: center;	/* 水平居中 */
 }
 .container div {
 	width: 100px;
 	height: 100px;
 	background-color: pink;		/* 方便看效果 */
 }  
```

### 4.display有哪些值？说明它们的作用。

```
	block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	元素不显示，并从文档流中移除。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
```

### 5.position有哪些值？说明它们的作用

```
1、static（静态定位）：默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。

2、relative（相对定位）：生成相对定位的元素，通过top,bottom,left,right的设置相对于其正常（原先本身）位置进行定位。可通过z-index进行层次分级。　　

3、absolute（绝对定位）：生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级。

4、fixed（固定定位）：生成固定定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级。
```

### 6.CSS3有哪些新特性？

```
	新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
    圆角		    （border-radius:8px）
    多列布局	    （multi-column layout）
    阴影和反射	（Shadow\Reflect）
    文字特效		（text-shadow、）
    文字渲染		（Text-decoration）
    线性渐变		（gradient）
    旋转		 	（transform）
    缩放,定位,倾斜,动画,多背景
    例如:transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:
```

### 7.请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

```
   一个用于页面布局的全新CSS3功能，Flexbox可以把列表放在同一个方向（从上到下排列，从左到右），并让列表能延伸到占用可用的空间。
   较为复杂的布局还可以通过嵌套一个伸缩容器（flex container）来实现。
   采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。
   它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称"项目"。
   常规布局是基于块和内联流方向，而Flex布局是基于flex-flow流可以很方便的用来做局中，能对不同屏幕大小自适应。
   在布局上有了比以前更加灵活的空间。

   具体：http://www.w3cplus.com/css3/flexbox-basics.html
```

### 8.rgba() 和 opacity 设置透明度的区别是什么？

```
opacity作用于元素，以及元素内的所有内容的透明度
rgba()只作用于元素的颜色或其背景色。（设置rgba()透明的元素的子元素不会继承透明效果）
```

### 9.css中优雅降级和渐进增强有什么区别？

```
优雅降级和渐进增强是随着css3流出来的一个概念，由于低级浏览器不支持css3，但css3的效果又太优秀不忍放弃，所以在高级浏览器中使用css3而低级浏览器只保证最基本的功能。咋一看两个概念差不多，都是在关注不同浏览器下的不同体验，关键的区别是它们所侧重的内容，以及这种不同造成的工作流程的差异。
优雅降级：认为应该针对那些最高级、最完善的浏览器来设计网站
渐进增强：认为应关注于内容本身
```

### 10.有多少种清除浮动的方法？

```
1.父级div定义height
原理：父级div手动定义height，就解决了父级div无法自动获取到高度的问题。简单、代码少、容易理解，但只适合高度固定的布局。
2.结尾处加空div标签clear:both
原理：在浮动元素的后面加一个空div兄弟元素，利用css提供的clear:both清除浮动，让父级div能自动获取到高度，如果页面浮动布局多，就要增加很多空div，让人感觉很不好。
3.父级div定义伪类:after 和 zoom
// 清除浮动代码
.clearfix: after {
	content: '';
	display: block;
	visibility: hidden;
	height: 0;
	line-height: 0;
	clear: both
}
.clearfix {
	zoom: 1
}
原理：IE8以上和非IE浏览器才支持:after，原理和方法2有点类似，zoom（IE专有属性）可解决IE6、IE7浮动问题，推荐使用，建议定义公共类，以减少css代码。
4.父级div定义overflow:hidden
原理：超出盒子部分会被隐藏，不推荐使用
5.双伪元素法
.clearfix: before, .clearfix: after {
	content: '';
	display: block;
	clear:both;
}
.clearfix {
	zoom: 1
}
```

### 11.css精灵图的优缺点？

```
优点：
1.减少网页的http请求，从而加快了网页加载速度，提高用户体验。
2.减少图片的体积，因为每个图片都有一个头部信息，把多个图片放到一个图片里，就会共用同一个头信息，从而减少了字节数。
3.解决了网页设计师在图片命名上的困扰，只需对一张集合的图片上命名就可以了，不需要对每一个小元素进行命名。
4.更换风格方便，只需要在一张或少张图片上修改图片的颜色或样式，整个网页的风格就可以改变。

缺点：
1.在宽屏，高分辨率的屏幕下的自适应页面，你的图片如果不够宽，很容易出现背景断裂。
2.CSS Sprites在开发的时候，要通过photoshop或其他工具测量计算每一个背景单元的精确位置。
3.在维护的时候比较麻烦，如果页面背景有少许改动，一般就要改这张合并的图片。
4.精灵图不能随意改变大小和颜色。改变大小会失真模糊，降低用户体验，Css3新属性可以改变精灵图颜色，但是比较麻烦，并且新属性有兼容问题，现在一般用字体图标代替精灵图。
```

### 12.怎样实现三栏布局，两边宽度固定，中间自适应？

```
1. 流体布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    background-color: blue;
	    float: right;
	}
	.main {
	    margin-left: 120px;
	    margin-right: 220px;
	    height: 200px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="right"></div>
        <div class="main"></div>
    </div>
</body>
</html>
左右模块各自向左右浮动，并设置中间模块的 margin 值使中间模块宽度自适应。
缺点就是主要内容无法最先加载，当页面内容较多时会影响用户体验。

2. BFC 三栏布局
BFC 规则有这样的描述：BFC 区域，不会与浮动元素重叠。因此我们可以利用这一点来实现 3 列布局。
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    margin-right: 20px;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    float: right;
	    margin-left: 20px;
	    background-color: blue;
	}	
	.main {
	    height: 200px;
	    overflow: hidden;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="right"></div>
        <div class="main"></div>
    </div>
</body>
</html>
缺点跟方法一类似，主要内容模块无法最先加载，当页面中内容较多时会影响用户体验。因此为了解决这个问题，有了下面要介绍的布局方案双飞翼布局。

3. 双飞翼布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        .content {
  	    float: left;
  	    width: 100%;
        }
        .main {
  	    height: 200px;
  	    margin-left: 110px;
  	    margin-right: 220px;
  	    background-color: green;
        }
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    margin-left: -100%;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    float: right;
	    margin-left: -200px;
	    background-color: blue;
	}	
    </style>
</head>
<body>
    <div class="content">
        <div class="main"></div>
    </div>
    <div class="left"></div>
    <div class="right"></div>
</body>
</html>
利用的是浮动元素 margin 负值的应用，感兴趣的同学可以上网搜搜原理。
主体内容可以优先加载，HTML 代码结构稍微复杂点。

4. 圣杯布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
	    margin-left: 120px;
	    margin-right: 220px;
	}
	.main {
	    float: left;
	    width: 100%;
	    height: 300px;
	    background-color: red;
	}
	.left {
	    float: left;
	    width: 100px;
	    height: 300px;
	    margin-left: -100%;
	    position: relative;
	    left: -120px;
	    background-color: blue;
	}
	.right {
	    float: left;
	    width: 200px;
	    height: 300px;
	    margin-left: -200px;
	    position: relative;
	    right: -220px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
	<div class="main"></div>
	<div class="left"></div>
	<div class="right"></div>
    </div>
</body>
</html>
跟双飞翼布局很像，有一些细节上的区别，相对于双飞翼布局来说，HTML 结构相对简单，但是样式定义就稍微复杂，也是优先加载内容主体。

5. Flex 布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
            display: flex;
	}
	.main {
            flex-grow: 1;
	    height: 300px;
	    background-color: red;
	}
	.left {
	    order: -1;
	    flex: 0 1 200px;
	    margin-right: 20px;
	    height: 300px;
	    background-color: blue;
	}
	.right {
	    flex: 0 1 100px;
            margin-left: 20px;
	    height: 300px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
	<div class="main"></div>
	<div class="left"></div>
	<div class="right"></div>
    </div>
</body>
</html>
简单实用，未来的趋势，需要考虑浏览器的兼容性。

6. Table 布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        .container {
	    display: table;
	    width: 100%;
        }
        .left, .main, .right {
	    display: table-cell;
        }
        .left {
	    width: 200px;
	    height: 300px;
	    background-color: red;
        }
        .main {
	    background-color: blue;
        }
        .right {
	    width: 100px;
	    height: 300px;
	    background-color: green;
        }
    </style>
</head>
<body>
    <div class="container">
	<div class="left"></div>
	<div class="main"></div>
	<div class="right"></div>
    </div>
</body>
</html>
缺点：无法设置栏间距

7. 绝对定位布局
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
	    position: relative;
	}
	.main {
	    height: 400px;
	    margin: 0 120px;
	    background-color: green;
	}
	.left {
	    position: absolute;
	    width: 100px;
	    height: 300px;
	    left: 0;
	    top: 0;
	    background-color: red;
	}
	.right {
	    position: absolute;
	    width: 100px;
	    height: 300px;
	    background-color: blue;
            right: 0;
	    top: 0;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="main"></div>
	<div class="left"></div>
	<div class="right"></div>
    </div>
</body>
</html>
简单实用，并且主要内容可以优先加载。

8.网格布局
最后再来看一个比较新的东西，网格布局，这个布局是新的css标准下的特性,在响应式布局大行其道的移动互联网时代，bootstrap之类的是对栅格化布局框架非常流行，而网格布局，就是对栅格布局的标准化实现，下面是用网格布局实现代码和效果
<style>
   .container {
       display: grid;
       width: 100%;
       grid-template-rows: 200px;
       grid-template-columns: 300px auto 300px;
   }
   .left {
       background: red;
   }
   .center {
       background: yellow;
   }
   .right {
       background: blue;
   }
</style>
<div class="container">
    <div class="left"></div>
    <div class="center">
        <h1>网格布局</h1>
    </div>
    <div class="right"></div>
</div>

可以很明显地看出来，这种布局方式特别清晰，把整个页面设置成网格，设置网格内元素占的行和列，可以很容易实现想要的自适应效果。这种布局方式产生的时间相对较短，最大的问题是浏览器兼容性，不过新技术至少是要了解的。
```

### 13.如何实现满屏品字布局？

```
方法一：
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>品字布局</title> 
<style>
   * {
   		margin: 0;
   		padding: 0;
   }
   html, body {
   		height: 100%;
   }
   .header {
   		height: 50%;
   		width: 50%;
   		background-color:  rgb(255,2545,167);
   		margin: 0 auto;
   }
   .main {
   		height: 50%;
   		width: 100%;
   }
   .main .left {
   		float: left;
   		width: 50%;
   		height: 100%;
   		background-color: rgb(204,255,102);
   }
   .main .right {
   		float: left;
   		width: 50%;
   		height: 100%;
   		background-color: rgb(189,255,255);
   }
</style>
</head>
<body>
<div class="header"></div>
<div class="main">
    <div class="left"></div>
    <div class="right"></div>
</div>  
</body>
</html>

方法二：
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>品字布局</title> 
<style>
  * {
  		margin: 0;padding: 0;
  }
  html, body {
  		height: 100%;
  }
  .pinzi-flex {
  		position: fixed;
  		left: 0;top: 0;
  		height: 100%;
  		width: 100%;
  }
  .header {
  		height: 50%;
  }
  .header .div-up {
  		width: 50%;
  		height: 100%;
  		background-color:  rgb(255,2545,167);
  		margin: 0 auto;
  }
  .main {
  		height: 50%;
  		position: relative;
  }
  .main .div-left {
  		position: absolute;
  		left: 0; width: 50%;
  		height: 100%;
  		background-color: rgb(204,255,102);
  }
  .main .div-right {
  		position: absolute;
  		right: 0; 
  		width: 50%;
  		height: 100%;
  		background-color: rgb(189,255,255);
  }
</style>
</head>
<body>
<div class="pinzi-flex">
<div class="header">
    <div class="div-up"></div>
</div>
<div class="main">
    <div class="div-left"></div>
    <div class="div-right"></div>
</div>
</div>  
</body>
</html>
```

### 14.用css模拟红绿灯

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /*
        思路：
            总共三个灯，分别红黄绿，要一个一个按顺序点亮，我们可以这样暂定一个循环需要10秒中，每盏灯点亮3秒，
            那么在keyframes中对应写法就如下所示（红灯点亮时间为10%--40%，黄灯点亮时间为40%--70%，绿灯点亮时间为70%--100%）
        */

        @keyframes redLamp {
            0% {
                background-color: #999;
            }
            9.9% {
                background-color: #999;
            }
            10% {
                background-color: red;
            }
            40% {
                background-color: red;
            }
            40.1% {
                background-color: #999;
            }
            100% {
                background-color: #999;
            }
        }

        @keyframes yellowLamp {
            0% {
                background-color: #999;
            }
            39.9% {
                background-color: #999;
            }
            40% {
                background-color: yellow;
            }
            70% {
                background-color: yellow;
            }
            70.1% {
                background-color: #999;
            }

            100% {
                background-color: #999;
            }
        }

        @keyframes greenLamp {
            0% {
                background-color: #999;
            }
            69.9% {
                background-color: #999;
            }
            70% {
                background-color: green;
            }
            100% {
                background-color: green;
            }
        }
        #lamp,
        #lamp:before,
        #lamp:after {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: #999;
            position: relative;
        }
        #lamp {
            left: 100px;
            animation: yellowLamp 10s ease infinite;
        }
        #lamp:before {
            display: block;
            content: '';
            left: -100px;
            animation: redLamp 10s ease infinite;
        }
        #lamp:after {
            display: block;
            content: '';
            left: 100px;
            top: -100px;
            animation: greenLamp 10s ease infinite;
        }
    </style>
</head>
<body>
    <div id="lamp"></div>
</body>
</html>
```

# 三、JavaScript

### 1.JavaScript有哪些数据类型？

```
基本数据类型：Boolean、Null、Undefined、Number、String、Symbol (ECMAScript 6 新定义)
引用数据类型：Object
```

### 2.undefined和null的区别？

```
null表示"没有对象"，即该处不应该有值。典型用法是：
（1） 作为函数的参数，表示该函数的参数不是对象。
（2） 作为对象原型链的终点。

undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义。典型用法是：
（1）变量被声明了，但没有赋值时，就等于undefined。
（2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。
（3）对象没有赋值的属性，该属性的值为undefined。
（4）函数没有返回值时，默认返回undefined。

用一句话总结两者的区别就是：undefined 表示一个变量自然的、最原始的状态值，而 null 则表示一个变量被人为的设置为空对象，而不是原始状态。所以，在实际使用过程中，为了保证变量所代表的语义，不要对一个变量显式的赋值 undefined，当需要释放一个对象时，直接赋值为 null 即可。
```

### 3.JavaScript中如何判断变量类型？

```
Object.prototype.toString.call(variable) 用这个方法来判断变量类型目前是最可靠的了，它总能返回正确的值。

该方法返回 "[object type]", 其中type是对象类型。
```

### 4.使用JavaScript如何实现红绿灯？

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        #green {
            width: 100px;
            height: 100px;
            border-radius: 50px;
        }
        #yellow {
            width: 100px;
            height: 100px;
            border-radius: 50px;
        }
        #red {
            width: 100px;
            height: 100px;
            border-radius: 50px;
        }
        .lamp {
            width: 400px;
            height: 140px;
            border: 1px solid #666;
            border-radius: 20px;
            background: #f7f7f7;
            display: flex;
            justify-content: space-around;
            align-items: center;
        }
    </style>
</head>
<body>
    <div class="lamp">
        <div id="green"></div>
        <div id="yellow"></div>
        <div id="red"></div>
    </div>
</body>
<script>
    window.onload = () => {
        let bg1 = document.getElementById('green')
        let bg2 = document.getElementById('yellow')
        let bg3 = document.getElementById('red')
        let setColor = (color, duration, num) => {
            return new Promise((res, rej) => {
                colors(num, color)
                setTimeout(res, duration)
            })
        }
        let colors = (num, color) => {
            if (num === 1) {
                bg1.style.background = color
                bg2.style.background = '#E2DCDC'
                bg3.style.background = '#E2DCDC'
            }
            if (num === 2) {
                bg2.style.background = color
                bg1.style.background = '#E2DCDC'
                bg3.style.background = '#E2DCDC'
            }
            if (num === 3) {
                bg3.style.background = color
                bg2.style.background = '#E2DCDC'
                bg1.style.background = '#E2DCDC'
            }
        }
        async function setLamp() {
            await setColor('green', 6000, 1)
            await setColor('yellow', 2000, 2)
            await setColor('red', 4000, 3)
            await setLamp()
        }
        setLamp()
    }
</script>
</html>
```

### 5.如何理解JSON

```
JSON是JS的一个对象，也是一种数据格式，JSON中的两个api如下

1.将JSON字符串转换成JSON对象 JSON.parse()
2.将JSON对象转换成JSON字符串 JSON.stringify()
```

### 6.数组对象常用方法

```
concat()	连接两个或更多的数组，并返回结果。
copyWithin()	从数组的指定位置拷贝元素到数组的另一个指定位置中。
every()	检测数值元素的每个元素是否都符合条件。
fill()	使用一个固定值来填充数组。
filter()	检测数值元素，并返回符合条件所有元素的数组。
find()	返回符合传入测试（函数）条件的数组元素。
findIndex()	返回符合传入测试（函数）条件的数组元素索引。
forEach()	数组每个元素都执行一次回调函数。
indexOf()	搜索数组中的元素，并返回它所在的位置。
join()	把数组的所有元素放入一个字符串。
lastIndexOf()	返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。
map()	通过指定函数处理数组的每个元素，并返回处理后的数组。
pop()	删除数组的最后一个元素并返回删除的元素。
push()	向数组的末尾添加一个或更多元素，并返回新的长度。
reduce()	将数组元素计算为一个值（从左到右）。
reduceRight()	将数组元素计算为一个值（从右到左）。
reverse()	反转数组的元素顺序。
shift()	删除并返回数组的第一个元素。
slice()	选取数组的的一部分，并返回一个新数组。
some()	检测数组元素中是否有元素符合指定条件。
sort()	对数组的元素进行排序。
splice()	从数组中添加或删除元素。
toString()	把数组转换为字符串，并返回结果。
unshift()	向数组的开头添加一个或更多元素，并返回新的长度。
valueOf()	返回数组对象的原始值。
```

