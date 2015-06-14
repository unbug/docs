---
layout: default
type: start
shortname: Start
title: Quick tour of Polymer
subtitle: Get started
---

<style>
.learnmore {
  text-transform: uppercase;
}
</style>


{% include toc.html %}

{{site.project_title}}使我们方便地以声明式的方式创建web components.

custom elements可以利用{{site.project_title}}的特定功能来简化样板文件, 并使得构建复杂交互性element更加容易:

- 注册elements
- lifecycle回调
- 特性观察
- local DOM模版
- 数据绑定

在本阶段, 你可以在不进行任何安装的情况下, 快速了解{{site.project_title}}. 点击 **Edit on Plunker** 按钮来打开交互沙盒中的任一示例.

查看[开发者指南](../devguide/feature-overview.html)了解这些功能的更多信息.

### 注册一个element {#register}

通过调用 `{{site.project_title}}` 方法来注册一个新的element, 该方法会使用浏览器 _注册_ 一个新的element.
注册element时将tag名称和原型进行关联, 这样你就可以给自己的custom element添加特性和方法了.

{{site.project_title}}方法接收一个对象参数, 该参数定义了你的element的原型对象.

<demo-tabs selected="0" demoSrc="../../samples/start/proto-element/manifest.json">
  <demo-tab heading="proto-element.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">

{% include_external /samples/start/proto-element/proto-element.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="proto-element.html">
  </head>
  <body>
    <proto-element></proto-element>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/proto-element/index.html" width="100%" height="200"></iframe>
  </div>
</demo-tabs>

该示例使用了一个lifecycle回调, 该回调在 `<proto-element>` 初始化时给它添加内容. 一旦custom element完成了初始化, 便会调用 `ready` 这个lifecycle回调.
`ready` 回调很适合用来进行类似结构初始化的工作.

<p>
  <a href="../devguide/registering-elements.html">
    <paper-button>
      了解更多: element注册
    </paper-button>
  </a>
</p>

<p>
  <a href="../devguide/registering-elements.html#lifecycle-callbacks">
    <paper-button>
      了解更多: lifecycle callbacks
    </paper-button>
  </a>
</p>

### 添加local DOM

很多element都包含一些内部的DOM节点, 以用来进行element的UI和行为表现. {{site.project_title}}称它们为 _local DOM_ ,
并给出了定义它的简单方法:

<demo-tabs selected="0" demoSrc="../../samples/start/dom-element/manifest.json">
  <demo-tab heading="dom-element.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">

{% include_external /samples/start/dom-element/dom-element.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="dom-element.html">
  </head>
  <body>
    <dom-element></dom-element>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/dom-element/index.html" width="100%" height="200"></iframe>
  </div>
</demo-tabs>

在element中封装Local DOM.

<p>
  <a href="../devguide/local-dom.html">
    <paper-button>
      了解更多: local DOM
    </paper-button>
  </a>
</p>

### 和local DOM进行合成

local DOM可以让你控制 _合成_ . 该element的子元素可以被 _分解_ , 这样的话, 这些子元素就如同是插入到该local DOM树中一样被渲染出来.

以下的示例创建了一个简单的标签, 它通过在图片外层添加一个带有样式的 `<div>` 来装饰它.

<demo-tabs selected="0" demoSrc="../../samples/start/picture-frame/manifest.json">
  <demo-tab heading="picture-frame.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">

{% include_external /samples/start/picture-frame/picture-frame.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="picture-frame.html">
  </head>
  <body>
    <picture-frame>
      <image src="images/p-logo.svg">
    </picture-frame>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/picture-frame/index.html" width="100%" height="100"></iframe>
  </div>
</demo-tabs>


**注:** 定义在 `<dom-module>` 中的样式只 _针对_ 该element中的local DOM. 所以这里的 `div` 样式规则只对 `<picture-frame>` 中的 `div` 标签起作用.
{: .alert .alert-info }


<p>
  <a href="../devguide/local-dom.html#dom-distribution">
    <paper-button>
      了解更多: 合成 & 分解
    </paper-button>
  </a>
</p>

### 数据绑定

只有静态的local DOM当然是不够的. 通常情况下, 你需要让你的element动态更新其中的local DOM.

数据绑定会很好地快速传播element中的改变,并简化样本代码. 你可以在自己的component中使用"double-mustache"语法(`{%raw%}{{}}{%endraw%}`)来进行特性绑定.
`{%raw%}{{}}{%endraw%}`会被花括号中的引用的特性替换掉.

<demo-tabs selected="0" demoSrc="../../samples/start/name-tag/manifest.json">
  <demo-tab heading="name-tag.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">

{% include_external /samples/start/name-tag/name-tag.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="name-tag.html">
  </head>
  <body>
    <name-tag></name-tag>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/name-tag/index.html" width="100%" height="200"></iframe>
  </div>
</demo-tabs>

<p>
  <a href="../devguide/data-binding.html">
    <paper-button>
      了解更多: 数据绑定
    </paper-button>
  </a>
</p>


### 已声明特性

特性是element公共API的重要组成部分. {{site.project_title}} _已声明特性_ 支持特性的几种常见模式 - 设置特性的默认值, 通过标记对特性进行配置, 观察特性的改变等等.

在下面的示例中, 我们添加了一个有默认值的 `owner` 已声明特性, 并在index.html中对其进行了配置.

<demo-tabs selected="0" demoSrc="../../samples/start/configurable-name-tag/manifest.json">
  <demo-tab heading="configurable-name-tag.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">

{% include_external /samples/start/configurable-name-tag/configurable-name-tag.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="configurable-name-tag.html">
  </head>
  <body>
    <!-- configure a property from markup by setting
         the corresponding attribute                 -->
    <!-- 使用标记来配置特性的相关属性 -->
    <configurable-name-tag owner="Scott"></configurable-name-tag>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/configurable-name-tag/index.html" width="100%" height="200"></iframe>
  </div>
</demo-tabs>

<p>
  <a href="../devguide/properties.html">
    <paper-button>
      了解更多: 声明的特性
    </paper-button>
  </a>
</p>

#### 绑定到特性

除了上面提到的文本内容上的绑定, 你也可以在元素的 _属性_ 上进行绑定(通过 `property-name="{%raw%}{{binding}}{%endraw%}"` ).
{{site.project_title}}特性选择性支持双向绑定.

该示例使用了双向绑定: 将custom input element( `icon-input` )的值绑定到该element的 `owner` 属性上, 那么它将随着用户的输入做相应的更新.

<demo-tabs selected="0" demoSrc="../../samples/start/editable-name-tag/manifest.json">
  <demo-tab heading="editable-name-tag.html">
{% highlight html %}
<link rel="import"
      href="bower_components/polymer/polymer.html">
<!-- import the iron-input custom element -->
    <!-- 引入iron-input custom element -->
<link rel="import"
      href="bower_components/iron-input/iron-input.html">

{% include_external /samples/start/editable-name-tag/editable-name-tag.html docs-sample version_prefix:1.0 %}
{% endhighlight %}
  </demo-tab>
  <demo-tab heading="index.html">
{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
    <link rel="import" href="editable-name-tag.html">
  </head>
  <body>
    <editable-name-tag></editable-name-tag>
  </body>
</html>
{% endhighlight %}
  </demo-tab>
  <div class="result">
    <iframe frameborder="0" src="../../samples/start/editable-name-tag/index.html" width="100%" height="200"></iframe>
  </div>
</demo-tabs>

**注:**  `is="iron-input"` 属性表明了这个input是一个 _类型扩展_ 的custom element; 该element的名字为 `iron-input` , 它 _扩展_ 了原生的 `<input>` 元素.
{: .alert .alert-info }


## 下一步 {#nextsteps}

现在你已经知道了如何创建自己的element, [获取代码](getting-the-code.html)来创建自己的第一个{{site.project_title}}项目吧, 或者到[开发者指南](../devguide/feature-overview.html)进一步学习. 继续~

<p>
<a href="getting-the-code.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>获取代码</paper-button>
</a>
</p>

<p>
<a href="../devguide/feature-overview.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>开发者指南</paper-button>
</a>
</p>


