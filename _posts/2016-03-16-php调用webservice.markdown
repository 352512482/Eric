---
layout: post
title:  "php调用webservice"
date:   2016-03-16 19:47:39 +0800
category: PHP
---
<p>
　　最近项目后台需要做一个开发票的功能,对方使用的是webservice来做发票api,我是第一次用php去调用webservice,写这篇文章记录下来,以防日后忘记.
我用的是PHP的扩展Soap中的WSDL模式,WSDL就是描述XMLWeb服务的标准XML格式,它定义了一套基于XML的语法.具体请<a href="http://www.yesky.com/288/1774788.shtml" target="_blank">戳此链接</a>.
{% highlight ruby %}
//$data表示要传给webservice的参数
function sendInvoice($data) {
    header('Content-Type: text/html; charset=UTF-8');
    $wsdl = "http://xxxxxx/myServices?wsdl";  //webservice访问地址
    $soap = new SoapClient($wsdl);  //初始化一个SoapClient,注意,如果初始化失败,可能是本地的php没有开启此项扩展,在php.ini中去除extension=php_soap.dll之前的‘；’
    $result = $soap->createBill(array('json' => json_encode($data)));  //这里的createBill是webservice开放的一个方法,json则是它的参数名,这里参数名称要根据webservice给出的参数名来传,不可随便乱写
    $result = json_decode($result->return, true);
    return $result['result'];
}
{% endhighlight %}
</p>