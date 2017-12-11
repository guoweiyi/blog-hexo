---
title: Coding WebIDE 云端开发实验室
tags:
  - web
  - 分享
  - 学习
id: 542
categories:
  - 朋友吃安利吗？
date: 2017-10-11 16:21:12
---

之前就有听说过 WebIDE , 不过一直没有去用。毕竟本地的开发也有许多便利，平时写写前端、php之类的环境也挺方便配置，空间也不大。

接下来就要说到，某个恰巧差了0.5学分的人的选课问题了。冲着名字选了 `Web开发技术` 后，发现老师讲的是JavaEE，而且书本上的知识十分老旧。 = =，实验的内容也是意外的简陋。总之，自己不是很感兴趣吧。（<del>毕竟，php是世界上最好的语言！）</del>

至于实验室的机器环境更是落后，老版的 `MyEclipse` 加上 `Windows XP` 系统，让人更是提不起兴 ♂ 趣。自己也懒得在自己空间有限的机子上装JavaEE的环境和开发工具了。

这时就想到了 [Coding.net](http://coding.net) , 大概因为是国产，比其他同类型 WebIDE 网站要快很多！而且是中文界面嘛~

> 以上都是废话

* * *

进入正式试用。[https://ide.coding.net](https://ide.coding.net)

网站也提供了 [快速体验~](https://ide.coding.net)

> 以下数据目前截至 2017.10.11

## 环境参数

(个人免费版)

*   多种环境可选
*   官方提供的Java基础环境是 `Java &amp; Maven environment` 。
*   JDK : java version "1.8.0_111"
*   命令行类似 `Git Bash` 风格, 提供 git 环境
*   系统 : Linux Ubuntu 16.04.1 LTS
*   CPU : 1 内核
*   内存 : 128 M
*   磁盘 : 1 GB

## 优点

*   目前而且以后估计也会是 **免费** 的，不过一个人只能建一个空间。（当然也有一些付费服务啦
*   可以与 `GitHub` 项目关联
*   提供在线链接预览

* * *

## 配置过程与问题

先创建属于自己的空间。

#### Java

因为课上实验用的是 `JavaEE` ，所以想的就是配置个在线写 `jsp` 之类的环境，而且还能在线预览测试。

预置 Maven 环境，所以使用 Maven 创建 Web 应用程序项目。

**1.** 在终端输入以下命令，并确定项目名称，创建 Web 项目。

    $ mvn archetype:generate -DgroupId=com.yiibai -DartifactId=项目名称 -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
    `</pre>

    **2.** 此时项目文件夹下会生成 `pom.xml` 文件，打开，并找到如下 `&lt;build&gt;` 标签。

    <pre class="line-numbers prism-highlight" data-start="1">`&lt;build&gt;
    &lt;finalName&gt;你的项目名称&lt;/finalName&gt;
    &lt;/build&gt;
    `</pre>

    **3.** 在 `&lt;build&gt;` 中增加如下的 `&lt;plugins&gt;` 标签。

    <pre class="line-numbers prism-highlight" data-start="1">`&lt;plugins&gt;
    &lt;plugin&gt;
    &lt;groupId&gt;org.apache.tomcat.maven&lt;/groupId&gt;    &lt;artifactId&gt;tomcat7-maven-plugin&lt;/artifactId&gt;
    &lt;version&gt;2.1&lt;/version&gt;
    &lt;/plugin&gt;
    &lt;/plugins&gt;
    `</pre>

    (此处作用是添加 `maven tomcat7` 插件，默认配置的是 `tomcat6` 插件，不支持 `jdk1.8`)

    **4.** 进入项目文件夹，运行如下命令，开启 `tomcat7` 服务器。（注意要加 7 ）

    <pre class="line-numbers prism-highlight" data-start="1">`cd 你的项目文件夹
    mvn tomcat7:run

**5.** 点击 Coding WebIDE 界面右边界处的生成链接(默认是8080端口)，访问生成的链接即可看到 JavaWeb 的页面了。

> 参考教程： [http://www.yiibai.com/maven/create-a-web-application-project-with-maven.html](http://www.yiibai.com/maven/create-a-web-application-project-with-maven.html)

* * *

#### 后记

做实验省得配置一堆环境，又可以随时备份代码，更换机器。感觉真的很方便，而且实验内容需求往往也不会触及到免费性能的瓶颈。