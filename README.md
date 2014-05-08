##Web开发最佳实践

创造最好的全端web体验

[google Web Fundamental 原文地址](https://developers.google.com/web/fundamentals/)

[Github地址](https://github.com/google/WebFundamentals)

####目录

0. 搞起你的第一个多终端网站（Getting Start）
1. 多终端布局(Multi-Device Layout)
2. 图片，声音和视频(Images, Audio and Video)
3. 表单和输入(Form and User Input)
4. 性能优化(Optmizing Performanceå)

___



###搞起你的第一个多终端网站


####1. 创造你的内容和结构

内容是网站最核心的部分，所以我们应是为了内容而设计，而不是让设计去强加到内容里，我们首先确定内容，在此基础上构建网站结构，然后使用一种线性布局使得窄屏和宽屏都可以完美展现页面。

#####设计页面结构

我们需要弄清楚：

1. 一个在高端角度描述我们的产品的区域（这句我就这么理解的）
2. 一个收集哪些用户是否对我们产品感兴趣信息的表单
3. 一段对产品的详细描述的文字或者视频
4. 交互式的产品图片
5. 一个数据图表来支持你的观点

> **尿点**
> 
> - 确定你所需要展现的内容
> - 画出你的信息结构（IA）的草图
> - 写一个没有样式页面的基本骨架

下面的代码作为页面的基本骨架，剩下的部分将会基于这个骨架完成

```html
	<!doctype html>
    <html>
      <head>
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>CS256: Mobile Web development - structure</title>
      </head>
      <body>
        <div id="headline">
          <h1></h1>
          <h2></h2>
          <div id="blurb">
            <p></p>
            <ul>
              <li>
            </ul>
          </div>
          <form method="post" id="register">
          </form>
        </div>
        <div id="section1">
          <h2></h2>
          <p></p>
          <ul>
            <li>
          </ul>
          <video></video>
        </div>
        <div id="section2">
          <h2></h2>
          <p></p>
          <div id="images">
            <img>
          </div>
        </div>
        <div id="section3">
          <h2></h2>
          <p></p>
        </div>
        <div id="footer">
          <p></p>
        </div>
          </body>
    </html>
```

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addstructure.html)

#####添加页面内容

基本架构我们已经完成，我们知道我们需要多少个篇章，以及各个篇章内的内容和它们准备放置的位置。我们现在开始构建网站.

	大爷，别着急写样式
	
######头部和表单

头部和以及用户信息表单是页面的关键组成，这些必须非常清楚的展现给用户

下面代码增加头部和一下表单项

```html
	<div id="headline">
      <div class="container">
        <h1>Mobile Web Development</h1>
        <h2>Building Mobile Web Experiences</h2>
        <div id="blurb">
          <p>So you've heard mobile is kind of a big deal, and you're not sure how to transform your traditional desktop-focused web apps into fast, effective multi-screen experiences.</p>
          <p>This course is designed to teach web developers what they need to know to create great cross-device web experiences.</p>
          <p>This course will focus on building mobile-first web apps, which will work across multiple platforms including:</p>
          <ul>
            <li>Android,
            <li>iOS,
            <li>and others.
          </ul>
        </div>
        <form method="post" id="register">
           <h2>Register for the launch</h2>
           <label for="name">Name</label>
           <input type="text" name="name" id="name"
              placeholder="Thomas A Anderson" required />
           <label for="email">Email address</label>
           <input type="email" name="email" id="email"
              placeholder="neo@example.com" required />
           <label for="tel">Telephone</label>
           <input type="tel" name="tel" id="tel"
              placeholder="(555) 555 5555" required />
           <input type="submit" value="Sign up">
        </form>
        <br>
      </div>
    </div>
```

[完整栗子](https://google-developers.appspot.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent)

我们同样需要填写这表单，这个简单的表达收集用户名字，电话号码以及什么时候给他们电话最合适

所有的表单都应该有标签和占位符（placeholder）让用户可以清楚注意和理解需要填写表单项内容，而且自动表单填写工具能够清楚理解表单结构，所有的name属性都应该可以告诉浏览器自动填写工具如何帮助用户填写表单，而不是仅仅发送请求给服务器

我们需要设置input有意义的type属性，使得用户可以更加方便的输入表单内容。举个栗子，用户输入手机号的时候，用户应该只有看到数字键盘

```html
	<form method="post" id="register">
      <h2>Register for the launch</h2>
      <label for="name">Name</label>
      <input type="text" name="name" id="name"
        placeholder="Thomas A Anderson" required />
      <label for="email">Email address</label>
      <input type="email" name="email" id="email"
        placeholder="neo@example.com" required />
      <label for="tel">Telephone</label>
      <input type="tel" name="tel" id="tel"
        placeholder="(555) 555 5555" required />
      <input type="submit" value="Sign up">
    </form>
```

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/withform.html)

###### 添加视频和详细信息区域

这个章节的内容一般相对更加有深度，通常有一个无序的产品功能介绍列和一个视频展现产品是如何服务用户的

```html
	<div id="section1">
      <div class="container">
        <h2>What will I learn?</h2>
        <p>After completing this class, you'll have built a web application with a first-class mobile experience.</p>
        <p>You'll understand what it takes to:</p>
        <ul>
          <li>build great web experiences on mobile devices</li>
          <li>use the tools you need to test performance</li>
          <li>apply your knowledge to your own projects in the future</li>
        </ul>
        <video controls poster="udacity.png">
          <source src="udacity.mp4" type="video/mp4"></source>
          <source src="udacity.webm" type="video/webm"></source>
          <p>Sorry your browser doesn't support video.
             <a href="udacity.mov">Download the video</a>.
          </p>
        </video>
        <br>
      </div>
    </div>
```
    
    
视频是一种互动性比较强的内容展现方式，所以经常用来介绍整个产品和产品的概念

 * video标签上使用**controls**属性方便用户控制视频
 * 增加**poster**属性来展现视频的预览图
 * 使用多个**<source>**标签来支持多个格式的视频
 * 增加异常情况的提醒，让用户在无法播放的情况可以下载视频

以上有一些最佳实践的点你可以让你的视频和你的网站更加完美地契合。



```html
<video controls poster="udacity.png">
  <source src="udacity.webm" type="video/webm"></source>
  <source src="udacity.mov" type="video/mov"></source>
  <p>Sorry your browser doesn't support video.
     <a href="udacity.mov">Download the video</a>.
  </p>
</video>
```
    
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addvideo.html)
    
###### 添加图片区域

没图的网站好意思说自己狂炫酷炸天么，讲讲两种类型的图片：

* 内容型图片 —— 排版在内容里面的图片，用来更加清晰阐述内容本身
* 炫酷型图片 —— 跟名字一样，为了让网站更加炫酷，这些图片是背景图片，包括pattern和gradients，我们将会学习如何炫酷在**使其响应式**章节里

图片区域是一个我们产品图片集锦

```html
	<div id="section2">
  		<div class="container">
    		<h2>Who will teach me?</h2>
    		<p>The worlds leading mobile web developers.</p>
    	<div id="images">
      		<img src="chriswilson.png" alt="Chris Wilson Course Instructor">
      		<img src="peterlubbers.png" alt="Peter Lubbers Course Instructor">
      		<img src="seanbennett.png" alt="Sean Bennet Course Developer">
   		 </div>
   			 <br>
  		</div>
	</div>
```
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

内容型图片是阐述内容的爆点，想想汪峰为什么上不了头条

```html
	 <div id="images">
      <img src="chriswilson.png" alt="Chris Wilson Course Instructor">
      <img src="peterlubbers.png" alt="Peter Lubbers Course Instructor">
      <img src="seanbennett.png" alt="Sean Bennet Course Developer">
    </div>
``` 
 
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addimages.html)

图片宽度设置100%对窄屏端想对比较友好，但是在宽屏却不是，我们将会**使其响应式**章节详细讨论

###### 添加表格化数据区域

最后的区域是一个区域是表格化数据区域用来展现产品特定的数据

Table标签应该用来而且仅用来展现表格数据，例如，矩阵型的数据

```html
	<div id="section3">
      <h2>Mobile. Why should I care?</h2>
      <p>It is huge.  Everywhere.</p>
      <table>
        <caption>
          <p>Data from <a href="http://gs.statcounter.com/#desktop+mobile+tablet-comparison-ww-monthly-201303-201403">StatsCounter</a></p>
        </caption>
        <thead>
           <tr>
             <th>Country</th>
             <th>Desktop share</th>
             <th>Tablet share</th>
             <th>Mobile share</th>
           </tr>
        </thead>
        <colgroup>
           <col span="1">
           <col span="1">
           <col span="1">
           <col span="1">
        </colgroup>
        <tbody>
         <tr>
            <td data-th="Country"><a href="http://gs.statcounter.com/#desktop+mobile+tablet-comparison-IN-monthly-201303-201403">India</a></td>
            <td data-th="Desktop share">32%</td>
            <td data-th="Table share">1%</td>
            <td data-th="Mobile share">67%</td>
          </tr>
          <tr>
            <td data-th="Country"><a href="http://gs.statcounter.com/#desktop+mobile+tablet-comparison-GB-monthly-201303-201403">GB</a></td>
            <td data-th="Desktop share">69%</td>
            <td data-th="Table share">13%</td>
            <td data-th="Mobile share">18%</td>
          </tr>
          <tr>
            <td data-th="Country"><a href="http://gs.statcounter.com/#desktop+mobile+tablet-comparison-US-monthly-201303-201403">US</a></td>
            <td data-th="Desktop share">69%</td>
            <td data-th="Table share">9%</td>
            <td data-th="Mobile share">22%</td>
          </tr>
          <tr>
            <td data-th="Country"><a href="http://gs.statcounter.com/#desktop+mobile+tablet-comparison-CN-monthly-201303-201403">China</a></td>
            <td data-th="Desktop share">86%</td>
            <td data-th="Table share">4%</td>
            <td data-th="Mobile share">10%</td>
          </tr>
        </tbody>
      </table>
      <br>
    </div>
```

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

###### 增加FOOTER

绝大部分网站都需要一个footer来展现期限和条约和免责声明和一些没有必要出现在导航以及主要内容区域的信息

在这个网站，我们只是单纯放置条款和期限，联系页面以及社交媒体介绍

`html
	<div id="footer">
      <div class="container">
        <p>We always need a footer.</p>
      </div>
    </div>
`

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

##### 总结

我们已经把页面的框架完成而且已经构建好了主要内容的骨架，我们需要注意的是是否所有关联的内容位置都已经符合业务需求

![未完成图](https://developers.google.com/web/fundamentals/getting-started/your-first-multi-screen-site/images/content.png)

未完成图

![完成图](https://developers.google.com/web/fundamentals/getting-started/your-first-multi-screen-site/images/narrowsite.png)

完成图

你发现现在的页面跟屎一样，但我不会告诉你故意的。内容做一切页面最重要的组成部分，我们需要保证有一个坚实的信息结构和密度。下面将会开始把页面变得炫酷起来

####2. 使其响应式

现在网站的访问的终端跨度非常大，从小手机倒巨屏电视，所有的设备都有它们的好处和限制。作为一个web开发者，你的页面应该尽可能去支持所有的设备

此章内容
- 增加一个veiwport
- 使用简单的样式
- 设定你的第一个响应式宽度
- 限制设计的最大宽度
- 改变padding值和字体大小
- 让元素适应宽屏
- 结束语

> 尿点
> 
> - 一定要使用veiwport
> - 先以窄屏为基础来进行设计，然后在进行拓展
> - 在你设定的各级响应式宽度为最低值来进行设计
> - 在主要的几个响应式宽度对用户有着很好的展现（3，4大家自己看看原句理解）

##### 增加一个viewport

即使是最基本的页面，你**必须必须必须必须**有一个veiwport meta标签，veiwport是你构建多终端页面的最重要的组件，没有它你的网站在在移动端就是屎

veiwport告诉浏览器页面必须撑开到整个页面。veiwport有很多设置项你可以专门来控制你的页面，默认我们都是设置成：

```html
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/viewport.html)

viewport写在head而且只需要声明一次

##### 使用简单的样式

我们的产品和公司已经样式规范提供了特定的品牌和字体规范

###### 样式规范
一个样式规范能够让用户对页面展现有着深入的理解而且保证页面设计的一致性

配色：
<div class="styles" style="font-family: monospace"><div style="background-color: #39b1a4">#39b1a4</div><div style="background-color: white">#ffffff</div><div style="background-color: #f5f5f5">#f5f5f5</div><div style="background-color: #e9e9e9">#e9e9e9</div><div style="background-color: #dc4d38">#dc4d38</div></div>

###### 添加炫酷式（风格式）图片

在上一章，我们已经完成了内容式图片的添加，这些图片对于产品描述是非常关键的。而炫酷式图片的不是内容上必要的，但是它是用户对各个内容关注度的指明灯

一个很好的栗子就是首屏区域的图片，它们就是用来勾引用户进行更仔细的阅读（参考上面完成图）

```css
	#headline {
  		padding: 0.8em;
  		color: white;
  		font-family: Roboto, sans-serif;
  		background-image: url(backgroundimage.jpg);
  		background-size: cover;
	}
```
	
我们使用模糊化的背景图片不会抢了内容的风头，同时我们使用**cover**让元素在被拉伸的时候仍然保持正确的比例

##### 设定你的第一个响应式宽度

这个设计开始往凤姐方向发展在大概宽度为600px的时候，在现在这个栗子里，文本的长度就要超过10个单词（最佳英文阅读长度，中文呢？），这里就是我们要进行改造的点

600px似乎是一个很好的分界点，因为这个点给了我们空间去重塑元素的位置去适应屏幕，我们将使用[Media Queries](https://developers.google.com/web/fundamentals/documentation/multi-device-layouts/rwd-fundamentals/#use-css-media-queries-for-responsiveness)

```
@media (min-width: 600px) {
    
}
```
	
大屏的空间将会给我们更大的灵活性去展现我们的内容。

	你不需要一次性重写所有的元素，只需要一些必要的小调整
	
对于页面的正文我们需要：

- 限制设计的最大宽度
- 改变元素的padding和减少文字字体大小
- 把表单使用浮动跟头部同行
- 把video跟内容排版融合
- 把图片变小同时让它们用更好的网格形式展现


##### 限定设计的最大宽度

我们需要做选取是两个主要的布局：窄屏下的viewport和宽屏的viewport，在我们刚刚构建的过程里已经极大的简化了。

我们同样需要添加全屏显示（full-bleed）区域无论是两种viewport都是全屏显示，这样意味着我们限制最大宽度防止文字和图片不会变成超长的单行状态尤其是在超长屏幕（ultra-wide screens）。我们通常把这个值设置为**800px**

为了做到这样效果，我们需要一个限制宽度和居中所有元素，我们要一个容器（container）包住所有主要区域和使用**margin：auto**。这在显示区域拖动的时候仍然能够保持最大宽度800px同时居中

	<div class="container">...</div>

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)

	.container {
      margin: auto;
      max-width: 800px;
    }
 
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)

##### 改变padding和字体变小

在窄屏的viewport的时候，我们没有很多空间来展现内容，所以为了适应屏幕，排版的大小和分量经常需要彻底压缩

在大点的viewport的时候，我们需要考虑的是用户在阅读是虽然屏幕变大了，但是同时距离也变远了。为了增加可读性，我们需要增加排版的大小和分量，所以我们通过改变padding来让区域之间更加清晰

在我们的项目中，我们将会把区域的padding设置成宽度的5%，我们同时会增加每个区域头部的字体大小

	#headline {
      padding: 20px 5%;
    }
    
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)

##### 使元素适应宽屏

在我们的窄屏viewport的时候是垂直的线性布局，所有主要区域都是以上下的形式来展现

在宽屏的viewport下有着更多的空间可以用来优化内容的展现形式，以我们的页面来看，基于页面的信息结构我们可以：

- 移动表单围绕头部的地方
- 把视频放置到右边的关键位置
- 铺开图片
- 扩展表格

###### 浮动表单元素

窄屏viewport意味着我们缺少水平的空间舒服的放置我们所有元素

为了更加有效使用水平空间需要打破直线的头部布局使得表单和列表并列一起

	#headline #blurb {
      float: left;
      font-weight: 200;
      width: 50%;
      font-size: 18px;
      box-sizing: border-box;
      padding-right: 10px;
    }
 


    #headline #register {
      float:right;
      padding: 20px;
      width: 50%;
      box-sizing: border-box;
      font-weight: 300;
    }

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)

	#headline {
      padding: 20px 5%;
    }
    
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)


###### 浮动视频元素

video标签在窄屏的情况下设计成全屏宽度显示并且放置在了关键点列表后面，在宽屏的时候，video标签会变得太大导致放置在关键点列表下边的时候看起来很挫

所以video元素需要移出垂直型的布局，放置倒关键点列表的旁边

	#section1 ul {
      box-sizing: border-box;
      float: left;
      width: 50%;
      padding-right: 1em;
    }
    
    #section1 video {
      width: 50%;
      float: right;
    }

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/fixingfirstbreakpoint.html)

###### 铺垫图片

在窄屏的时候，图片是以全宽度进行垂直并列，但是要是宽屏的话就搓爆了

为了让图片看起来比较舒服，此栗子把图片缩小到容器的宽度30%同时把图片都水平排列，同时加入了边界圆角（border-radius）和阴影（box-shadow）提高图片吸引力

	#section2 div img {
       width: 30%;
       margin: 1%;
       box-sizing: border-box;
       border-radius: 50% 50%;
       box-shadow: black 0px 0px 5px;
     }

###### 图片根据DPI变动

我们需要考虑展现图片的时候是否是高清屏

我们是以96dpi的屏幕来构建网站的，我们需要考虑高清屏底下的效果包括笔记本的retina屏幕的效果，通常的图片在高清屏就是马赛克

我们的解决方案还没有全面铺开，下面的代码有一部分支持的浏览器可以这么写（译者本人通常使用js来在加载页面的时候进行判断dpi然后设置对应的图片）

	<img src="photo.png" srcset="photo@2x.png 2x" />  

###### 表格

表格通常非常难适应窄屏所以需要特别考虑清楚

我们推荐你在窄屏的情况下把表格变成两列，把对应的头部和单元格转换的更加垂直化

在我们的网站里，我们为表格单独创造了一级响应式宽度，因为我们是先构造窄屏的样式在先，导致很难消除已经完成的样式，所以我们必须先写表格的宽屏样式，然后再写窄屏样式，，这样让我们有一个更加清晰的样式分离（这句译者表示不一定翻译对了）

	@media screen and (max-width: 600px) {
      table thead {
        display: none;
      }

      table td {
        display: block;
        position: relative;
        padding-left: 50%;
        padding-top: 13px;
        padding-bottom: 13px;
        text-align: left;
        background: #e9e9e9;
      }

      table td:before {
        content: attr(data-th) " :";
        display: inline-block;
        color: #000000;
        background: #e9e9e9;
        border-right: 2px solid transparent;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        width: 33%;
        max-height: 100%;

        font-size: 16px;
        font-weight: 300;
        padding-left: 13px;
        padding-top: 13px;
      }
    }
    
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/content-with-styles.html)

##### 结束语

**恭喜！**. 当你跟着走到这里的时候，你已经完成了你第一个简单多终端产品页面了

如果你跟着下面的建议继续做，你将走向炸天的旅途：

1. 在你写下第一行代码之前，建立一个基本的信息结构和彻底明白你的要表现的内容
2. 一定要设置viewport
3. 先考虑窄屏（移动）端的内容展现形式
4. 一旦你确立窄屏（移动）端的内容展现形式，增加宽度直到页面变成屎，你就开始设计第一级的响应式区域了
5. 持续迭代

---
### 多终端布局（Coming Soon）

不要假设你的用户喜好单一设备。无论用户使用什么设备访问都应该提供最好的体验。响应式设计的主要目标：创造网站和app在所有的屏幕大小有着最好的体验。

####响应式web设计基础


####响应式web设计模式


####导航和指引设计模式

---

### MIT license
Copyright (c) 2013 Flynngao &lt;flynn.gao.y@gmail.com&gt;

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

---
译者：[@秃一了](http://www.weibo.com/1674540501/profile?rightmod=1&wvr=5&mod=personinfo)