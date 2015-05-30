---
layout: home_1_0
title: Welcome
---

<section id="future" class="main-bg">
  <div class="panel left">
    <img src="./images/polymer1.0-01.svg">
    <summary>
      <h1>适用于生产环境</h1>
      <p>Polymer 1.0 从根基上得到了重构,性能和效率得到质的飞越.简洁的核心库保证了开发高性能,美观,可共用的 web components 变得前所未有的高效.如果你还没有碰过 Polymer,那现在可以放心的拥抱它了!如果你已经好久没有关注 Polymer, 那士别三日, 刮目相看.</p>
      <a href="docs/start/getting-the-code.html">
        <paper-button raised unresolved>
          <core-icon icon="archive"></core-icon> 获取 {{site.project_title}}
        </paper-button>
      </a>
      <a href="https://github.com/polymer">
        <paper-button class="github" unresolved>
          <core-icon icon="social:post-github"></core-icon> 在 GitHub 上查看
        </paper-button>
      </a>
    </summary>
  </div>
</section>

<!-- <section id="release08" class="main-light-purple">
  <div class="panel">
    <summary>
      <a href="/0.9/">
        <h2 layout horizontal center>
          Join us @ Polypalooza, Sept. ???
        </h2>
      </a>
    </summary>
  </div>
</section> -->

<section id="catalog" class="main-purple">
  <div class="panel">
    <summary style="transform: translateZ(0);">
      <h1>Element 目录</h1>
      <a href="https://elements.polymer-project.org" target="_blank">
        <img src="/images/catalog_fadeout.png" alt="Launch the element catalog" title="Launch the element catalog">
      </a>
      <div>
        <p>
        Custom elements 由 Polymer 团队构建, 可直接在你的应用里使用.
        </p>
        <a href="https://elements.polymer-project.org" target="_blank">
          <paper-button>
            <core-icon icon="arrow-forward"></core-icon> 浏览 elements
          </paper-button>
        </a>
      </div>
    </summary>
  </div>
</section>

<!-- <section id="production" class="main-purple">
  <div class="panel" layout horizontal>
    <div flex>
      <h2>Lean, Mean, and Ready for Production</h2>
      <p class="one-oh-summary">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nulla facilis itaque, quo fuga veritatis odit hic magnam perspiciatis voluptatibus rem delectus omnis nisi inventore ea sapiente quibusdam a tenetur pariatur.</p>
    </div>
    <div flex>
      <div class="one-oh">1.0</div>
    </div>
  </div>
</section> -->

<section id="features" class="main-bg">
  <div class="panel">
    <div class="feature">
      <div class="badge">
        <div class="badge-wrapper">
          <core-icon icon="trending-up" style="color: #4CAF50;"></core-icon>
        </div>
      </div>
      <h2>高性能</h2>
      <p>Polymer 1.0 使用一个轻量级的 shim 将 shadow DOM 的 polyfill 替换掉了, 使用一个全新, 更快的数据绑定系统, 大大地精简了代码量.</p>
    </div>

    <div class="feature">
      <div class="badge">
        <div class="badge-wrapper">
          <core-icon icon="check-box" style="color: #00BCD4;"></core-icon>
        </div>
      </div>
      <h2>专攻主流浏览器</h2>
      <p>Polymer 以主流浏览器为基准, 使用最新的 web 平台 API. 那些没有被浏览器广泛支持的 API 也有 Polyfill 作支持。</p>
    </div>
    
    <div class="feature">
      <div class="badge">
        <div class="badge-wrapper">
          <core-icon icon="favorite" style="color: #E91E63;"></core-icon>
        </div>
      </div>
      <h2>使用 Web Components</h2>
      <p>Polymer 推动 <em>web components</em>, 一系列为了让 web 可重用 components 而全新的设计标准.</p>
    </div>
  </div>

</section>

<section id="examples">
  <div class="panel">

    <div class="example">
      <h2 class="example-header">使用 elements 目录里的elements</h2>
      <div class="example-wrapper">
        <div class="example-code">
        {% highlight html %}
{%raw%}
<!-- 给 Web Components 使用 Polyfills 以便支持旧的浏览器 -->
<script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>

<!-- 引入 element -->
<link rel="import" href="components/google-map/google-map.html">

<!-- 使用 element -->
<google-map lat="37.790" long="-122.390"></google-map>
{%endraw%}
        {% endhighlight %}
        </div>
        
        <div class="example-result example-google-map">
          <iframe frameborder="0" src="samples/homepage/google-map/index.html" width="100%"></iframe>
        </div>
      </div>
      <div class="example-caption">
        <p>Polymer 的 element 效果和其他 HTML element 是一样的. 挑一个你想用的 element, 通过 HTML import 引入它, 将标签添加到你的页面就成.</p>
      </div>
    </div>

    <div class="example">
      <h2 class="example-header">创建你自己的 elements</h2>
      <div class="example-wrapper">
        <div class="example-code">
      {% highlight html %}
{%raw%}
<dom-module id="contact-card">
  <link rel="import" type="css" href="contact-card.css">
  <template>
    <content></content>
    <iron-icon icon="star" hidden$="{{!starred}}"></iron-icon>
  </template>
</dom-module>

<script>
  Polymer({
    is: 'contact-card',
    properties: {
      starred: Boolean
    }
  });
</script>
{%endraw%}
      {% endhighlight %}
      
      {% highlight html %}
{%raw%}
<contact-card starred>
  <img src="profile.jpg" alt="Eric's photo">
  <span>Eric Bidelman</span>
</contact-card>
{%endraw%}
      {% endhighlight %}
        </div>
        <div class="example-result example-contact-card">
          <iframe frameborder="0" src="samples/homepage/contact-card/index.html" width="100%"></iframe>
        </div>
      </div>
      <div class="example-caption">
        <p>Polymer 库能帮你创建强大 elements. 给你的 element 一个些标签和属性, 然后在网站上使用它. Polymer 提供非常实用的功能，像模板和数据绑定都大大的减少了你的代码量.</p>
      </div>
    </div>


    <div class="example">
      <h2 class="example-header">用数据驱动它</h2>
      <div class="example-wrapper">
        <div class="example-code">
        {% highlight html %}
{%raw%}
<dom-module id="friend-list">
  <link rel="import" type="css" href="friend-list.css">
  <template>
    <firebase-collection data="{{data}}"
                      location="https://users1.firebaseio.com/users">
    </firebase-collection>
    <template is="dom-repeat" items="{{data}}">
      <contact-card starred="{{item.starred}}">
        <img src="{{item.img}}" alt="{{item.name}}">
        <span>{{item.name}}</span>
      </contact-card>
    </template>
  </template>
</dom-module>

<script>
  Polymer({
    is: 'friend-list'
  });
</script>
{%endraw%}
        {%endhighlight%}
        {%highlight html%}
{%raw%}
<friend-list></friend-list>
{%endraw%}
        {%endhighlight html%}
        </div>
        <div class="example-result example-friend-list">
          <iframe frameborder="0" src="samples/homepage/friend-list/index.html" width="100%"></iframe>
        </div>
      </div>
      <div class="example-caption">
        <p>构建更加高级的 elements 则可以通过整合简单的 elements 到一起. Elements 完全可以提供从简单抽象到强大 API. 这里使用的 <code>&lt;firebase-collection&gt;</code> 是从 Firebase 的数据库拉数据的. </p>
      </div>
      
      <div class="button-row">
        <a href="docs/start/quick-tour.html">
          <paper-button raised>
            <core-icon icon="arrow-forward"></core-icon> Take a Tour
          </paper-button>
        </a>

        <a href="docs/start/getting-the-code.html">
          <paper-button raised>
            <core-icon icon="archive"></core-icon> Get The Code
          </paper-button>
        </a>

        <a href="docs/index.html">
          <paper-button raised>
            <core-icon icon="info"></core-icon> Learn More
          </paper-button>
        </a>
      </div>
    </div>
    
  </div>
</section>

{% comment %}
<section id="everything-element" class="main-purple">
  <div class="panel right">
    <summary>
      <h1>一切都是 element</h1>
      <p>从 <code>&lt;a&gt;</code> 标签到 <code>&lt;select&gt;</code> 标签, elements 就是 HTML 的积木. 但是主流的应用已经用烂了了这些 elements, 迫使开发者使用 JavaScript 框架来获得动态的, 自定义的行为.  最终应用变得臃肿复杂, 并且僵化, 在一个地方要行的组件在其他地方可能就不行了.
      <br><br>
      {{site.project_title}} 将 element 拾回了 web development 中心. 通过 {{site.project_title}}, 你可以构建自己的 HTML elements 并且将它们整合到更加复杂的应用中, 但是却更加灵活且易于维护.</p>
      <a href="docs/start/everything.html">
        <paper-button>
          <core-icon icon="arrow-forward"></core-icon> 了解更多
        </paper-button>
      </a>
    </summary>
    <img src="/images/logos/p-elements.svg">
  </div>
</section>
{% endcomment %}
