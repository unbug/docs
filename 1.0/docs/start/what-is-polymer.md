---
layout: default
type: guide
shortname: Docs
title: What is Polymer?
subtitle: Get started
---

{{site.project_title}}库使得开发者能更快更简单地创建强大可复用的component。

## Custom elements扩展web

HTML提供了一系列如`<button>`,`<form>`,`<table>`等内置元素. 每个元素都有自身的属性(attributes), 特性(properties), 方法(method)和事件(events)的API. 每个元素都有内置的样式, 和你可以使用CSS覆盖的样式特性一样.

任何人都可以通过使用这些元素去构建一张简单的web页面. 但是它们还是很有限的. 如果要构建如一组tab的这么一个简单的页面, 你就要用到HTML, css而且通常也包含script.

通过使用custom element, 你可以使用你自己的element来扩展HTML的词汇. 这些elements可以包含复杂的UI交互. 如下面这样, 可以很方便地将作为一个`<select>`使用:

    <my-tabstrip>
      <my-tab>
        Home
      </my-tab>
      <my-tab>
        Services
      </my-tab>
      <my-tab>
        Contact Us
      </my-tab>
    <my-tabstrip>


## {{site.project_title}}是web compoments吗? 是elements吗?

{{site.project_title}}既不是web components, 也不是elements. {{site.project_title}}建立在web components标准之上, 帮助你建立自己的custom elements.

![](../../images/webcomponents_stack.svg)

*   **Web components**. 这些标准提供了构建新component的基本类型. 你可以使用这些基本类型来构建自己的custom elements, 但是这需要大量的工作.
    并不是所有的浏览器都实现了这些标准, 而[web components polyfill库](http://webcomponents.org/polyfills/)
    填补了这些空白, 在JavaScript中实现了相应的API.

*   **{{site.project_title}}库**. 提供了一种更容易定义custom elements的声明式语法. 它还添加了如模版(templating), 双向数据绑定(two-way data binding)
    和特性观察(property observation)来帮助你使用更少的代码来构建强大且可复用的元素.

*   **Custom elements**. 如果你不想编写自己的elements, 那么这里也有很多 _使用{{site.project_title}}构建_ 的elements, 你可以直接在你的页面中使用它们.
    这些elements依赖{{site.project_title}}库, 但是你可以在不直接使用{{site_project_title}}的前提下使用它们.

    你可以将custom elements看作内置elements一样，和{{site.project_title}}构建的elements配合使用.

## 获取elements

{{site.project_title}}团队写了一些elements, 你可以直接在你的app中使用它们. 在[Element catalog](https://elements.polymer-project.org/)中可以找到这些elements.

## 编写自己的elements

心动了吧？也想使用{{site.project_title}}库来构建自己的elements？

快速学习这些功能:

<p>
<a href="../start/quick-tour.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>快速教程</paper-button>
</a>
</p>


或者直接跳到这里:

<p>
<a href="../devguide/feature-overview.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>开发者指南</paper-button>
</a>
</p>