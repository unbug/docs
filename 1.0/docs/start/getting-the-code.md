---
layout: default
type: start
shortname: Start
title: Get the code
---

<style>
 paper-button[raised].cta {
      background-color: #0f9d58;
      color: white;
      fill: white;
      margin: 10px;
}

.download-button {
  background: #4285f4;
  color: #fff;
  font-size: 18px;
  fill: #fff;
}

.download-button:hover {
  background: #2a56c6;
}

.download-button::shadow paper-ripple {
  color: #fff;
}
</style>

{% include toc.html %}

## 安装{{site.project_title}} {#installing-polymer}

准备好开始自己的项目? 你可以使用如下任一方式来安装{{site.project_title}}库:

*   [Bower](#using-bower). Bower用来管理依赖, 所以安装一个component的同时也会安装所有依赖. Bower也可以对已安装的component进行更新.
    查看[使用Bower安装](#using-bower)了解更多.

*   [ZIP文件](#using-zip). 它包含全部的依赖, 所以你只要解压缩并直接使用即可. ZIP文件无需其它工具, 但同时它也不提供更新依赖的内置方法.
    查看[从ZIP文件安装](#using-zip)了解更多.

*   [GitHub](#using-github). 当你从GitHub克隆一个component, 你需要亲自去管理所有的依赖.

如果你不想从头开始的话, 也有一些起步项目供你选择:

*   [`<seed-element>`](#seed-element)是一个完整的模版, 你可以使用它来创建一个新的可复用的element, 包含文档及测试.

*   [Polymer Starter Kit](#psk) 是一个用来做Polymer应用的模版, 它内置了工具和离线兼容功能.

使用Bower来安装{{site.project_title}}, 会得到[Web Components polyfill库](/0.5/docs/start/platform.html).
在该版本的{{site.project_title}}用的是该库的 `webcomponents-lite` 版, 该版本不包含shadow DOM polyfill.

使用polyfills可以使得你可以在不支持Web Components规范的浏览器中使用{{site.project_title}}.

## 使用Bower安装 {#using-bower}

推荐使用Bowser安装**{{site.project_title}} {% polymer_version_dir %}**. 参见[Bower web site](http://bower.io/)安装Bower.

Bower可以让你在开发或定制elements时不用操心依赖管理问题, Bower会确保安装所有的依赖.


### 建立项目

如果你还没有为自己的应用创建 `bower.json` 文件, 在项目根目录下运行该命令:
    bower init

这会生成一个基本的 `bower.json` 文件. 一些诸如"What kind of modules do you expose,"的问题会被按下回车键跳过.

下一步是安装{{site.project_title}}:

    bower install --save Polymer/polymer#^1.0.0

Bower在你的项目根目录下添加一个 `bower_components/` 文件, 并放置{{site.project_title}}和它的依赖.

**提示:** `--save` 参数会在安装polymer的同时, 在 *你的* app的bower.json文件中添加该依赖项:

```
{
  "name": "my-project",
  "version": "0.0.0",
  "dependencies": {
    "polymer": "Polymer/polymer#^1.0.0
  }
}
```
{: .alert .alert-success }

#### 更新包 {#updatebower}

当有新版本的{{site.project_title}}可用时, 在你的app目录中运行 `bower update` 来更新你的依赖副本:

    bower update

这会将 `bower_components/` 中所有的包更新到最新的stable版.

## 从ZIP文件进行安装 {#using-zip}

点击下载按钮下载{{site.project_title}} {% polymer_version_dir %}的ZIP文件.

<p><a href="http://zipper.bowerarchiver.appspot.com/archive?polymer=Polymer/polymer%231.0.0">
  <paper-button class="cta" raised><core-icon icon="file-download"></core-icon>Download ZIP</paper-button>
</a></p>

当使用ZIP方式的下载时, 你会直接得到全部的依赖. 如果你不需要安装其它工具的话, 这也开始项目的好方法.

解压ZIP文件到你的项目目录, 来创建一个 `bower_components` 文件.

![](/{% polymer_version_dir %}/images/zip-file-contents.png)

和Bower不同, ZIP文件没有提供更新依赖的内置方法. 你只能通过下载新的ZIP文件来手动进行component更新.

**注:** 如果你决定后续安装Bower, 你可以使用Bower来更新从ZIP文件安装的component. 请按照[更新包](#updatebower)中的说明.
{: .alert .alert-info }

## 使用git{#using-git}

因为会有很多的依赖, 所以我们推荐使用Bower而不是git来安装{{site.project_title}}. 如果你想在项目上进行hack或提交一个pull request,
你可以[访问polymer在GitHub上的repo](https://github.com/Polymer/polymer).

## element起步 {#seed-element}

如果你想发布一个可供别人使用的element, 那么 `<seed-element>` 样板是一个很好的起点. 它包含完成element的构建、测试及展示element的工具.

[创建一个可复用的element](reusableelements.html)会指导你进行element的创建、测试、展示及发布的整个流程.

## Polymer Starter Kit {#psk}

这是一个 "batteries-included" 应用模版, [Polymer Starter Kit](https://developers.google.com/web/tools/polymer-starter-kit/)
包含一个响应式的app布局、测试工具和开发工具, 甚至选择性支持了如离线存取和发送通知这些增强型功能.

## 下一步 {#nextsteps}

现在你已经安装了{{site.project_title}}, 是时候学习下核心概念了. 继续吧~

<p><a href="quick-tour.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>{{site.project_title}}快速教程</paper-button>
</a></p>


<p><a href="../devguide/feature-overview.html">
  <paper-button raised><core-icon icon="arrow-forward"></core-icon>开发者指南</paper-button>
</a></p>

如果你是从{{site.project_title}}0.5过渡过来的, 请参阅下[迁移指南](../migration.html).