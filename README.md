##Web开发最佳实践

创造最好的全端web体验

[google Web Fundamental 原文地址](https://developers.google.com/web/fundamentals/)

[Github地址](https://github.com/google/WebFundamentals)

####目录

0. 你的第一个多终端网站
1. 多终端布局
2. 图片，声音和视频
3. 表单和输入
4. 性能优化

___



###你的第一个多终端网站


####1. 创造你的内容和结构

内容是网站最核心的部分，所以我们应是为了内容而设计，而不是让设计去强加到内容里，我们首先确定内容，在此基础上构建网站结构，然后使用一种线性布局使得窄屏和宽屏都可以完美展现页面。

#####设计页面结构

我们需要弄清楚：

1. 一个在高端角度描述我们的产品的区域（这句我就这么理解的）
2. 一个收集哪些用户是否对我们产品感兴趣信息的表单
3. 一段对产品的详细描述的文字或者视频
4. 交互式的产品图片
5. 一个数据图表来支持你的观点

**关键点**
    
    - 确定你所需要展现的内容
    - 画出你的信息结构（IA）的草图
    - 写一个没有样式页面的基本骨架

下面的代码作为页面的基本骨架，剩下的部分将会基于这个骨架完成

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

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addstructure.html)

#####添加页面内容

基本架构我们已经完成，我们知道我们需要多少个篇章，以及各个篇章内的内容和它们准备放置的位置。我们现在开始构建网站.

	大爷，别着急写样式
	
######头部和表单

头部和以及用户信息表单是页面的关键组成，这些必须非常清楚的展现给用户

下面代码增加头部和一下表单项

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

[完整栗子](https://google-developers.appspot.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent)

我们同样需要填写这表单，这个简单的表达收集用户名字，电话号码以及什么时候给他们电话最合适

所有的表单都应该有标签和占位符（placeholder）让用户可以清楚注意和理解需要填写表单项内容，而且自动表单填写工具能够清楚理解表单结构，所有的name属性都应该可以告诉浏览器自动填写工具如何帮助用户填写表单，而不是仅仅发送请求给服务器

我们需要设置input有意义的type属性，使得用户可以更加方便的输入表单内容。举个栗子，用户输入手机号的时候，用户应该只有看到数字键盘

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

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/withform.html)

###### 添加视频和详细信息区域

这个章节的内容一般相对更加有深度，通常有一个无序的产品功能介绍列和一个视频展现产品是如何服务用户的

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
    
    
视频是一种互动性比较强的内容展现方式，所以经常用来介绍整个产品和产品的概念

 * veido标签上使用**controls**属性方便用户控制视频
 * 增加**poster**属性来展现视频的预览图
 * 使用多个**<source>**标签来支持多个格式的视频
 * 增加异常情况的提醒，让用户在无法播放的情况可以下载视频

以上有一些最佳实践的点你可以让你的视频和你的网站更加完美地契合。
 
    <video controls poster="udacity.png">
      <source src="udacity.webm" type="video/webm"></source>
      <source src="udacity.mov" type="video/mov"></source>
      <p>Sorry your browser doesn't support video.
         <a href="udacity.mov">Download the video</a>.
      </p>
    </video>
    
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addvideo.html)
    
###### 添加图片区域

没图的网站好意思说自己狂炫酷炸天么，讲讲两种类型的图片：

* 内容型图片 —— 排版在内容里面的图片，用来更加清晰阐述内容本身
* 炫酷型图片 —— 跟名字一样，为了让网站更加炫酷，这些图片是背景图片，包括pattern和gradients，我们将会学习如何炫酷在**使其响应式**章节里

图片区域是一个我们产品图片集锦

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

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

内容型图片是阐述内容的爆点，想想汪峰为什么上不了头条

	 <div id="images">
      <img src="chriswilson.png" alt="Chris Wilson Course Instructor">
      <img src="peterlubbers.png" alt="Peter Lubbers Course Instructor">
      <img src="seanbennett.png" alt="Sean Bennet Course Developer">
    </div>
[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addimages.html)

图片宽度设置100%对窄屏端想对比较友好，但是在宽屏却不是，我们将会**使其响应式**章节详细讨论

###### 添加表格化数据区域

最后的区域是一个区域是表格化数据区域用来展现产品特定的数据

Table标签应该用来而且仅用来展现表格数据，例如，矩阵型的数据

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

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

###### 增加FOOTER

绝大部分网站都需要一个footer来展现期限和条约和免责声明和一些没有必要出现在导航以及主要内容区域的信息

在这个网站，我们只是单纯放置条款和期限，联系页面以及社交媒体介绍

	<div id="footer">
      <div class="container">
        <p>We always need a footer.</p>
      </div>
    </div>

[完整栗子](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent.html)

#### 总结

我们已经把页面的框架完成而且已经构建好了主要内容的骨架，我们需要注意的是是否所有关联的内容位置都已经符合业务需求

![image](https://developers.google.com/web/fundamentals/getting-started/your-first-multi-screen-site/images/content.png)
![image](https://developers.google.com/web/fundamentals/getting-started/your-first-multi-screen-site/images/narrowsite.png)

你发现现在的页面跟屎一样，但我不会告诉你故意的。内容做一切页面最重要的组成部分，我们需要保证有一个坚实的信息结构和密度。下面将会开始把页面变得炫酷起来

####2. 使其响应式


___

### 多终端布局

不要假设你的用户喜好单一设备。无论用户使用什么设备访问都应该提供最好的体验。响应式设计的主要目标：创造网站和app在所有的屏幕大小有着最好的体验。

####响应式web设计基础


####响应式web设计模式


####导航和指引设计模式


