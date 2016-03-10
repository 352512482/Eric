---
layout: post
title:  "highcharts图给tooltip加上超链接"
date:   2016-03-10 13:41:39 +0800
categories: jekyll update
---
<p>
　　highchart是一个js库，主要用来绘制图表，它的官网是 <a href="http://www.highcharts.com">[戳此链接]</a>，
里面有各种各样的图例，包括最常见的柱状图，饼图，折线图等等，针对每一种图都有对应的demo，这给开发者
带来极大的便利。这是它的中文api文档地址 <a href="http://www.hcharts.cn">[戳此链接]</a>，有兴趣可以看看。
</p>
<p>
　　最近公司的drupal项目就用到了highchart了，里面有个需求是让我在tooltip显示上加上超链接，以往敲代码的习惯就是直接加上<a href></a>标签，
这做法其实没错，我也是这样做的(下面是示例代码)
{% highlight ruby %}
formatter: function() {
    return '<a href="www.baidu.com">xxx</a>';
}
{% endhighlight %}
咋一看好像没啥问题，我刷新了页面也没报错，可是不管我怎么点击，就是没有反应，一开始我还以为是highchart不支持，后来自己随手把地址补完整，所谓的补完整就是
{% highlight ruby %}
formatter: function() {
    return '<a href="http://www.baidu.com">xxxx</a>';
}
{% endhighlight %}
没错，只是补上了一个http://，然后，就可以点击了，都是平常的代码习惯惹得祸，以后这种低级错误要避免再犯。
</p>
<p>
　　这里备注一下，我在tooltip上测试过，highchart是不支持a标签的target属性的，所以如果想点击之后可以新开标签页来跳转就需要另外想办法了，
我目前是还没想到对应的办法，如果有战友想到并实践成功的话，欢迎不吝赐教。
</p>