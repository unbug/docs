---
layout: default
type: guide
shortname: Docs
author: addyosmani
title: Create a reusable element
subtitle: Publish reusable Polymer elements on GitHub
---

{% include toc.html %}
## 介绍

想发布你的第一个可复用{{site_project_title}}element?
很好! 这里将引导你进入整个过程:

完成后, 你将得到:

-   一个基于官方样板的本地git repo.
-   一个已发布在GitHub上的Bower安装版.
-   位于GitHub pages上的文档和运行demo.

**该向导假定你已安装了 `git` , [Node](http://nodejs.org/) 和 [Bower](http://bower.io/),
并且你有一个用于发布你的elements的GitHub账号.**

## 安装polyserve

受限于HTML的引入机制, 你需要一个本地web服务器来测试你的elements.

Polyserve是一个简单的web服务器, 你可以通过它使用本地的Bower组件. 对于开发过程中测试elements是非常好的方式. 使用 `npm` 来安装:

    npm install -g polyserve

**注:**
你可以跳过该步骤并使用其它本地web服务器来测试你的elements, 但是你将需要一些额外的配置. 见
[使用本地bower依赖测试elements](#local-dependencies)了解更多.
{: .alert .alert-info }

## 创建

1.  在你的系统上新建一个目录用来运行{{site.project_title}}elements (例如 `"development"` ).

2.  下载[seed-element](https://github.com/PolymerLabs/seed-element/archive/v0.1.5.zip)样板文件并将其解压到你的工作目录

3.  重命名element及其相应的文件. 例如, 如果你的element叫做 `<test-element>` 且你已经将 `seed-element` 目录重命名为了 `test-element` ,
    那么你的文件列表应该长这样:
![File list for the test-element directory showing that seed-element.html has been renamed to test-element.html](../../images/reusableelements/initial-folder-structure.png)

    接下来, 在你的element目录下运行 `bower install` 安装依赖. 依赖会被安装到 `bower_components` 目录中.
    现在你可以进行本地化开发并配置好服务以便测试.

## 开发和测试

在你的新element上添加逻辑特征并验证它的功能.

引入其它组件时, 按照 `<seed-element>` 中的示例, 写入路径时, 将要引入的组件所在文件夹看作和你的 `test-element` 文件夹是同级的.

    <link rel="import" href="../paper-button/paper-button.html">

一个快速健全地测试组件的方式就是使用polyserve访问你的demo.html文件. 有很多方式可以实现，但是最简单的莫过于运行一个 python 自带的 http服务器了,
命令如下:

    $ polyserve
    Starting Polyserve on port 8080
    Serving components from bower_components
    Files in this directory are available at localhost:8080/components/test-element/...

这就在8080端口上开启了一个web服务, 这样你就可以在浏览器上输入 `localhost:8080/components/test-element/demo/` 来测试你的新element了.

如果还有另一个进程监听8080端口, 你也可以使用 `-p` 参数来为Polyserve指定另一个端口:

    $ polyserve -p 9999

### 单元测试

一个好的element离不开好的单元测试. 使用[`web-component-tester`](https://github.com/Polymer/web-component-tester)
建立 `<seed-element>` 进行单元测试. 你可以使用 `test` 目录下的文件作参考来编写自己的单元测试.

### 文档

随`seed-element` repo一起的, 有一个使用[`iron-component-page`](https://github.com/PolymerElements/iron-component-page)
生成的内置文档. 打开element根目录下的 `index.html` 页面, 你将看到生成的文档:

`localhost:8080/components/test-element/`

这些文档工具会从代码中推断出一些信息, 并将其组织为JSDoc格式的注释. `seed-element` 包含这些你直接可以用的注释样例.
参考[PolymerElements style guide](http://polymerelements.github.io/style-guide/)了解关于文档原理的信息:

这可以让你:

* 提供你的element用法总结.
* 按照属性, 方法, 事件对你的文档进行自动分组
* 展示一个使用你的element的运行示例
* 链接到一个element [demo](http://polymerlabs.github.io/seed-element/components/seed-element/demo.html).

## 发布

通过以下两步来在GitHub上发布一个element:

-   将你的代码push到一个GitHub repo并使用一个release数字给它加上tag, 那么其它人就可以使用Bower来安装它了.

    在这一步你创建了一个*master*分支,它包含了供其它app或element使用的基础代码.

-   向你的repo发布一个 `gh-pages` 分支. 这会通过GitHub pages生成一个在线文档和该element的预览.

    这一步你会创建一个 *gh-pages (GitHub pages)* 分支, 该分支包含了一个你的element的展示页.
    该分支包含 **checked-in dependencies**, **demos** 和 **documentation**.


### 将你的element发布到GitHub

如果对自己的element满意, 你可以想将 `test-element` 的代码发布到GitHub并给它tag一个版本. 点击 [这里](https://github.com/new) 在GitHub上
创建一个新的repo. 该repo的名字应该和你的element的名字一致 ( e.g 如果你的element为 `<test-element>`, 那么你的repo应该叫 `test-element` ) .

接下来, 进入以下步骤:

    # 在你的开发目录中, 进入你的element目录
    cd test-element


    # 为test-element初始化一个新的Git repo
    git init

    # 给当前的代码加上commits
    git add .
    git commit -m 'My initial version'

    # 关联到GitHub的远程仓库
    git remote add origin https://github.com/<username>/test-element.git

    # 执行如下命令将你的代码发布到master分支
    git push -u origin master


接下来, 你可能想要给你的element tag一个新的版本. 你可以直接通过GitHub图形化界面操作 **或** 通过终端操作.

#### 使用终端

    # 如果有一个待发布的element的新版本, 给它打个tag
    # 例如, 标记为0.0.1版本
    git tag -a v0.0.1 -m '0.0.1'

    # 然后, 将你的tag发布到GitHub
    git push --tags


#### 使用GitHub的图形化界面

进入你的element的GitHub主界面, 点击主导航中的"releases"链接. 即如下标红的位置:
![Preview of the GitHub navigation bar for a repository listing four navigation items - commits, branches, releases, contributors. The releases link is highlighted](/images/publishing-polymer-elements/image_2.png)

它将引导你进入 *Releases* 页面. 对于一个没有任何release的项目, 该页面大致长这样:
![GitHub Releases page message stating that there aren't any releases here yet. The Create a new release button is highlighted](/images/publishing-polymer-elements/image_3.png)

点击 ‘Create a new release’ 按钮继续.

此时会显示一个发布预览页面, 你可以为你的element输入版本和发布信息. 例如, 将tag设置为v0.0.1并将 `master` 作为目标分支.
![The GitHub releases form displaying an input field for entering in a version number, a drop-down box for selecting the target branch, a release titles field and a description field](/images/publishing-polymer-elements/image_4.png)

确认好上述信息后, 点击 ‘Publish release’ 按钮来完成tag并发布你的element.
![Preview of the Publish release button in the GitHub releases page](/images/publishing-polymer-elements/image_5.png)

#### 测试安装你的element

现在你已经可以安装你的这个组件了. 切换到你用于测试的目录, 运行如下的命令:

    bower install <username>/test-element

### 为你的element发布demo和展示页

现在你的element已经有了一个tag版本了. 接下来, 为你的element创建一个有意义的demo和一个展示页.

这是可选项, 建议你将 `demo/index.html` 页面做下改变, 在它上面提供你的element的真实[示例]
(http://googlewebcomponents.github.io/google-chart/components/google-chart/demo.html).
这样开发者可以直接体验你的element, 并且可以使用你的demo作为参考从而将你的element应用到自己的项目中.

你也可以借此来更新你的element的公共接口[文档](#documentation)

再次启动Polyserve来检验你的文档和demo:

    $ polyserve

看一下对 `index.html`中的文档和 `demo/index.html` 的demo是否满意.

如果你觉得文档看起来还不错, **确定你已经将全部改动发布到了repo的 `master` 分支.** 并更新了名字和项目中的全部路径(包含 `bower.json` 中的路径). 
此时你不应保留任何对 `seed-element` 的引用.

现在你可以使用 `gp.sh` 脚本往GitHub pages上发布一个针对你的element的展示页. 在终端执行如下的命令.

**重点:** 确认你是在临时目录中运行 `gp.sh` 脚本(如下). 该脚本会覆盖当前目录中的内容.
{: .alert .alert-error } 

    # 进入到你的开发目录
    cd ..

    # clone {{sit.project_title}} 的repo
    git clone git://github.com/Polymer/tools.git

    # 创建一个临时目录来发布你的element, 并进入该目录
    mkdir temp && cd temp

    # 运行gp.sh脚本. 通过它来向你的repo的GitHub pages分支发布一个demo版和它的依赖项.
    ../tools/bin/gp.sh <username> test-element

    # 最后, 清除你的临时目录, 因为你不再用到它了.
    cd ..
    rm -rf temp

这会创建一个新的 `gh-pages` 分支(或clone并清除当前分支), 然后发布一个你的element的可共享版到该分支上.
使用以下地址查看你新发布的文档:

    http://<username>.github.io/test-element/


## 分享

现在你可以和世界分享你的element了! 正如我们使用 `seed-element` 那样, {{site.project_title}}
会提供你一个风格不错的组件页面, 就像下面这样:
![Preview of the component langing page, displaying the element title in the header with a demo link next to it. The rest of the page contains formatted summary and attribute/method/event information parsed from the documentation in your element](/images/publishing-polymer-elements/image_6.png)

你可以查看 `seed-element` 展示页[线上](http://polymerlabs.github.io/seed-element/components/seed-element/) 版.

现在你已经把你的 {{site.project_title}}element发布到了GitHub, 你可能还想再了解下如何[使用Bower来发布你的element](/0.5/articles/distributing-components-with-bower.html).
或者继续探索为什么 `<seed-element>` 要这么构建.


## 可复用的组件结构 {#structure}

该部分包含了创建可复用elements的 _底层_ 信息. 只要你遵循了上述的步骤并使用 `<seed-element>` 样板的模式, 你也能够发布一个可复用的element.

如果你对这些步骤或项目构建还有疑虑, 继续往下看.

### HTML的引入机制和依赖管理

为了使得HTMTL的引入机制可以正确复制你的资源, 你使用的每个组件都必须有一个单一且权威的URL. {{site.project_title}} components 处理这个问题时, 
会假定所有的component都安装在同级目录中.

    bower_components/
      iron-icon/
        iron-icon.html
      paper-icon-button/
        paper-icon-button.html
      paper-ripple/
        paper-ripple.html
      polymer/
        polymer.html

在该结构中, `iron-icon.html` 通过下面的方式来引入{{site.project_title}}:

    <link rel="import" href="../polymer/polymer.html">

`paper-icon-button.html` 可以通过下面的方法 _同时_ 引入{{site.project_title}}和 `<iron-icon>`:

    <link rel="import" href="../polymer/polymer.html">
    <link rel="import" href="../icon-icon/icon-icon.html">

如果你想创建一个依赖于{{site.project_title}}的可复用component, 你需要使用相同的相对路径结构.

### 使用本地bower依赖{#local-dependencies}测试elements

Bower将component安装在一个 _扁平依赖树_ 中, 该方式可以很好地运行在应用层面. 你会得到如下的目录结构:

    my-app/
      bower.json
      bower_components/
        my-element/
          my-element.html
        my-dependency/
          my-dependency.html
      index.html

所有的component都是同级的, 所以在 `my-element.html` 中可以这样引入 `my-dependency.html`:

        <link rel="import" href="../my-dependency/my-dependency.html">

但是, 如果在一个具有自身Bower依赖的独立的custom element的repo中, 默认Bower安装会产生一个这样的结构:

    my-element/
      bower.json
      bower_components/
        my-dependency/
          my-dependency.html
      my-element.html

这破坏了 `my-element` 和 `my-dependency` 路径的相对关系, 即和上面的结构不一样了.

最简单的修复方法就是建立一个本地服务器, 该服务器能重新映射这些路径, 这样的话 `bower_components` 
中所有的component都好像和 `my-element` 在同级目录中一样. Polyserve会自动为你做好这些事情.