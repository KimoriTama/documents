---
layout: default
title: 类型指定语法
---

<!-- 吉里吉里Zでは型指定されたTJSが実行可能。
型を指定してもエラーにならないだけで、スクリプトの動作は型指定しない場合と全く同じになる。エディタのインテリセンスを利用するためなどに使われる。

構文は以下の例のようになる。 -->
在吉里吉里Z中可以执行指定类型的TJS脚本。
即使指定了类型也不会出错，脚本的动作与不指定类型的情况完全相同。
它用于编辑器的智能提示等。

语法如下所示。

## 变量声明
变量名称可以后接冒号，后跟类型。
{% highlight javascript %}
var i:int;
var win:Window = new Window();
{% endhighlight %}

## 函数定义
<!-- 引数名にコロンをつけ、その後に型を指定できる。
戻り値は引数リストの後に指定できる。 -->
参数名称可以后接冒号，后跟类型。
返回值可以在参数列表之后指定。
{% highlight javascript %}
function add(param1:int, param2:int) : int {
    return param1 + param2;
}
{% endhighlight %}

## 表达式中的函数
<!-- 関数定義と同様に引数と戻り値の型を指定できる。 -->
与函数定义一样，可以指定参数和返回值的类型。
{% highlight javascript %}
var f = function(param1:string) : void {};
{% endhighlight %}

## 属性定义
<!-- setterの引数とgetterの戻り値の型をそれぞれ指定できる。 -->
可以分别指定setter参数和getter返回值的类型。
{% highlight javascript %}
property prop {
    setter(value:int) {}
    getter:int { return 0; }
}
{% endhighlight %}
