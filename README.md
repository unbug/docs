Polymer docs 大部分是带有 HTML 的 Markdown 文档. [Jekyll][jekyll] 用于生成网站的 HTML 静态文件。生成结果在 `_site` 目录下，由 Google App Engine 当服务。

## 预备及安装必要的条件

我们使用 Jekyll 2.4 和 [Grunt][grunt] 来生成文档, 用 compass 编译 SASS 成 CSS. 你要安装以下必要条件才能进行(本指南假设你已经 [安装了 NPM](http://nodejs.org/download/)):

    gem install bundler
    npm install -g grunt-cli vulcanize bower

**注意:** 如果有权限问题，用 `sudo` 来运行.

你还需要 Python 版的 App Engine SDK 来运行 dev_appserver 以便在本地预览文档.[下载 SDK](https://developers.google.com/appengine/downloads).


### 准备开始

- `git clone https://github.com/Polymer/docs.git`
- `bundle install`
- `npm install`
- `cd 0.5`
- `bower install`
- `cd 1.0`
- `bower install`
- `grunt docs`
- `grunt` (or `npm start`)

> 翻译的同学做到这里就可以预览了，查看 console 里的连接 [localhost:3000](localhost:3000)。余下的内容是 Polymer 团队才需要看的。

## 修改文档和预览结果

本 repo (`Polymer/docs`) 就是文档存放的位置.要做修改:

1. 如果你的 docs 目录是新 checkout 的 请确保运行了 `npm install`.
2. 运行 `grunt` 任务. 本任务会做以下处理：一个本地的app engine 服务, jekyll, compass, and vulcanize. jekyll, compass, 和 vulcanize 任务会监听并自动更新相关文件的变更。
**注意:** Jekyll 生成的本站的静态文件在 `_site` 目录下. 它在生成和将文件复制到对应目录的过程需要时间，不停的刷新网站就会出来了!
3. 做修改.

当你修改好后, `git commit` 提交修改并 push.

## 发布: push 文档

**注意**: 只有文档的所有者才能发布本文档。

### 本地预览

在 push 文档之前运行 `grunt` 是个好习惯, 本命令会执行很多任务，效验各种必要条件，并让你在本地预览结果。

### 更新 app

每当更新 Polymer 的版本，应该同时更新以下 app:

- [Tutorial](https://github.com/Polymer/polymer-tutorial)
- [Topeka](https://github.com/Polymer/topeka)
- [Designer](https://github.com/Polymer/designer)

解压对应 app 文件到 `bower_components` 目录, 校验, 然后运行 app 的 `deploy.sh` 脚本. 如果是 Tutorial, 你需要按它自己的指南安装.

### 发布

运行 `bower update` 以确保你的 component 的依赖是最新的.

更新好后,你需要更新本文档的一些版本号:

- 在`app.yaml` 里增加版本号;
- 更新 Polymer 发布版本号在 `_config.yml` 文件里.
- 在 `changelog.md` 文件里追加更新日志.

编译文档:

    grunt docs
    
运行 `grunt` 的同时会运行 Google App Engine 服务, 最好先预览避免不会因为 Polymer 和 elements 更新引起 糟糕的结果。

接着, 运行 `Polymer/docs` 目录的脚本:

    ./scripts/deploy_site.sh
    
本脚本 script 会构建站点, api 文档, 执行 Vulcanizer, 并部署到 App Engine.    

最后到 App Engine 的管理后台切换版号. 点击 https://appengine.google.com/deployment?&app_id=s~polymer-project 并选择你刚刚发布的版号查看上线的版本.

[jekyll]: http://jekyllrb.com/
[grunt]: http://gruntjs.com/
