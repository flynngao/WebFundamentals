##Web开发最佳实践
===============

创造最好的全端web体验

[google web Fundamental 原文地址](https://developers.google.com/web/fundamentals/)


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

[完整代码](https://developers.google.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addstructure.html)

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

[完整页面](https://google-developers.appspot.com/web/fundamentals/resources/samples/getting-started/your-first-multi-screen-site/addcontent)



####2. 使其响应式


___

### 多终端布局

不要假设你的用户喜好单一设备。无论用户使用什么设备访问都应该提供最好的体验。响应式设计的主要目标：创造网站和app在所有的屏幕大小有着最好的体验。

####响应式web设计基础


####响应式web设计模式


####导航和指引设计模式


