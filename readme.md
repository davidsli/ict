#爬虫及文本分析实现

文档说明：

1.  爬虫代码在spider文件夹中。其中，news_spider.py是我写的一个很简单的单线程爬虫，可以直接用来爬取中国教育信息化网站上的新闻报道。网站地址：http://www.ict.edu.cn/


    该网站对爬虫十分友好，甚至不用伪装成浏览器即可访问，代理IP什么的就更不用了，是爬虫新手练习的好地方。不过，抓取量比较大的话，还是建议分批次抓取，设置好延迟时间，不要在短时间内猛爬，不然会给网站的服务器带去压力。
   
    我没有使用现有的爬虫框架；由于数据量不算大，我也没有给出重试机制的代码，写一个循环即可实现。
  
2.  爬取中国知网的论文信息前，需要先获得相关论文的url队列，知网搜索后，论文的链接在静态页面中是看不到的；可以自己写代码解析js的返回值，以获取url。但知网对爬虫并不友好，很可能面临验证码输入(robot-check)甚至封锁IP的问题。

    我使用了专门的爬虫工具批量获取相关的论文链接，弹出验证码的检验框时，手工输入解决。
 
    详情可参考集搜客的相关教程 -- http://www.gooseeker.com/ <br>
   
    获取了url队列后，即可直接批量解析页面内容，爬取并保存需要的信息。由于硕士、博士学位论文和期刊论文的页面排版及需要抓取的内容略有差异，所以我写了三份代码。详情见：cnki_xxx.py。

3.  中文分词、关键词提取及词向量训练的示例代码在words_segmentation文件夹中，以对新闻文本的处理为例进行了说明，并附上了用到的自定义词典和停用词表。

4.  文本聚类和树状图绘制的代码可参考[《集体智慧编程》](https://book.douban.com/subject/3288908/)第三章的内容。我主要借鉴了书中的方法，实现上还需要制定一个关键词词频-论文标题的文本矩阵，这个并不难做到；不过要注意txt文件的中文编码问题，当时因为某个中文编码上的bug，我折腾了一整夜。

    另外，win7系统下，在通常的python上安装gensim module很可能会报错（反正我没成功），后来使用anaconda —— 一个用于科学计算的python发行版本 —— 解决了问题。

    最后，如果用python3.X绘制树状图报错，可以改用python2.7作为interpreter试试。




***

使用的IDE：PyCharm  ---- windows系统下学习python的最佳集成开发工具之一，用edu后缀的邮箱申请，可以免费获得pro版本的使用权（一年一注册），堪称业界良心，学生党福利。

最后的说明：上述代码我基本都修改完善过，但并没有再实现一遍，因此可能存在我没有察觉到的错误，欢迎批评指正。

*我是python初学者和爱好者。邮箱：betterus@126.com*