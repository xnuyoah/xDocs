## `Docsify` 的基本使用

[docsify 文档地址](https://docsify.js.org/#/zh-cn/)

### 1.快速开始

#### a.全局安装

```bash
# 全局安装 docsify-cli 工具
npm i docsify-cli -g
```

#### b.初始化 `docs`

```bash
docsify init ./docs  # echo y | docsify init .
```

#### c.启动项目

```bash
docsify serve . # docsify s [path]
```

### 2.多页文档

#### a.定制侧边栏: loadSidebar

> 开启侧边栏之前需要使用 `docsify generate .` 生成侧边栏文件 `_sidebar.md` 

```javascript
window.$docsify = {
  // 加载 _sidebar.md
  loadSidebar: true,

  // 加载 summary.md
  loadSidebar: 'summary.md',
};
```

#### b.显示目录: subMaxLevel

设置生成目录的最大层级

```javascript
window.$docsify = {
  subMaxLevel: 2,
};
```

##### 忽略副标题

当设置了 `subMaxLevel` 时，默认情况下每个标题都会自动添加到目录中。如果你想忽略特定的标题，可以给它添加 `<!-- {docsify-ignore} -->` 

```markdown
# Getting Started

## Header <!-- {docsify-ignore} -->

该标题不会出现在侧边栏的目录中。
```

要忽略特定页面上的所有标题，你可以在页面的第一个标题上使用 `<!-- {docsify-ignore-all} -->` 

```markdown
# Getting Started <!-- {docsify-ignore-all} -->

## Header

该标题不会出现在侧边栏的目录中。
```

在使用时， `<!-- {docsify-ignore} -->` 和 `<!-- {docsify-ignore-all} -->` 都不会在页面上呈现

#### c.定制导航栏: loadNavbar

```javascript
window.$docsify = {
    loadNavbar: true
};
```

##### HTML

如果你需要定制导航栏，可以用 HTML 创建一个导航栏

> 注意：文档的链接都要以 `#/` 开头。

```html
<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">中文</a>
  </nav>
  <div id="app"></div>
</body>
```

##### 配置文件

可以通过 `Markdown` 文件来配置导航。首先配置 `loadNavbar`，默认加载的文件为 `_navbar.md`

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

```markdown
<!-- _navbar.md -->

* [En](/)
* [简体中文](/zh-cn/)
```

`_navbar.md` 加载逻辑和 `sidebar` 文件一致，从每层目录下获取。例如当前路由为 `/zh-cn/custom-navbar` 那么是从 `/zh-cn/_navbar.md` 获取导航栏

##### 嵌套

如果导航内容过多，可以写成嵌套的列表，会被渲染成下拉列表的形式

```markdown
<!-- _navbar.md -->

* 入门

  * [快速开始](zh-cn/quickstart.md)
  * [多页文档](zh-cn/more-pages.md)
  * [定制导航栏](zh-cn/custom-navbar.md)
  * [封面](zh-cn/cover.md)


* 配置
  * [配置项](zh-cn/configuration.md)
  * [主题](zh-cn/themes.md)
  * [使用插件](zh-cn/plugins.md)
  * [Markdown 配置](zh-cn/markdown.md)
  * [代码高亮](zh-cn/language-highlight.md)
```

### 3.定制封面

通过设置 `coverpage` 参数，可以开启渲染封面的功能

#### a.基本用法

封面的生成同样是从 markdown 文件渲染来的。开启渲染封面功能后在文档根目录创建 `_coverpage.md` 文件

```javascript
window.$docsify = {
    coverpage: true
};
```

```markdown
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> 一个神奇的文档网站生成器。

- 简单、轻便 (压缩后 ~21kB)
- 无需生成 html 文件
- 众多主题

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)
```

#### b.自定义背景

目前的背景是随机生成的渐变色，我们自定义背景色或者背景图。在文档末尾用添加图片的 Markdown 语法设置背景

```markdown
<!-- _coverpage.md -->

# docsify <small>3.5</small>

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#quick-start)

<!-- 背景图片 -->

![](_media/bg.png)

<!-- 背景色 -->

![color](#f0f0f0)
```

#### c.封面作为首页

通常封面和首页是同时出现的，当然你也是当封面独立出来通过设置 `onlyCover` 选项

##### onlyCover

```javascript
window.$docsify = {
  onlyCover: false,
};
```

### 4.插件的使用

#### a.右侧目录显示

```html
<!-- index.html 添加以下内容 -->

<!-- toc 右侧目录显示 css 样式 -->
<link rel="stylesheet" href="https://unpkg.com/docsify-plugin-toc@1.3.1/dist/light.css">


<script>

// toc 配置项
window.$docsify = {
  toc: {
    tocMaxLevel: 5,
    target: 'h2, h3, h4, h5, h6',
    ignoreHeaders:  ['<!-- {docsify-ignore} -->', '<!-- {docsify-ignore-all} -->']
  },
}
</script>



<!-- toc 右侧目录显示 -->
<script src="https://unpkg.com/docsify-plugin-toc@1.3.1/dist/docsify-plugin-toc.min.js"></script>
```

#### b.最近更新时间

```html
<!-- index.html 添加以下内容 -->

<!-- toc 配置项
最近更新时间配置 -->
<script>
window.$docsify = {
    timeUpdater: {
        text: "<div align='right' width='100%' style='color: grey;font-size: 16px;margin-top: 10px'>最后更新时间: {docsify-updated}</div>",
        formatUpdated: "{YYYY}-{MM}-{DD} {HH}:{mm}:{ss}",
        whereToPlace: "bottom",
    },
}
</script>

<!-- 最近更新时间 -->
<script src="https://cdn.jsdelivr.net/npm/docsify-updated/src/time-updater.min.js"></script>
```

#### c.阅读条进度美化

```html

<script>
window.$docsify = {
    progress: {
        position: "top",
        color: "var(--theme-color,#42b983)",
        height: "3px",
    }
}
</script>

<script src="https://cdn.jsdelivr.net/npm/docsify-progress@latest/dist/progress.min.js"></script>
```

#### d.回到顶部

```html

<script>
    docsifyBackTop = {
        size: 32,                   // 数值，组件大小，默认值32。
        bottom: 15,                 // 数值，组件底部偏移距离，默认值15。
        right: 15,                  // 数值，组件右侧偏移距离，默认值15。
        logo: 'top',                                // logo:字符串或svg矢量图代码，默认为svg代码图标。
        bgColor: '\#2096ff'            // 背景颜色，#fff、pink等，logo为svg图标时，不填。
    };
</script>



<script src="https://cdn.jsdelivr.net/gh/Sumsung524/docsify-backTop/dist/docsify-backTop.min.js"></script>
```

#### e.中文英文之间自动添加空格

```html
<script src="//cdn.jsdelivr.net/npm/docsify-pangu/lib/pangu.min.js"></script>
```

#### f.支持文字转图片

```html
<script src="//unpkg.com/docsify-kroki"></script>
```

#### g.内置搜索

```html

<!-- 搜索配置 -->
<script>
search: {
    placeholder: '搜索',
    noData: '没有搜索到相关内容',
    depth: 3
},
</script>

<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

#### h.代码高亮

```html
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-shell.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
```

#### i.emoji表情支持

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```

#### j.代码复制

```html
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code@2"></script>
```

#### l.分页

```html

<script>
pagination: {
    previousText: '上一章节',
    // or
    nextText: {'/en/': 'NEXT','/': '下一章节'},
    crossChapter: true,
    crossChapterText: true,
},
</script>


<script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

### 5.参考配置项

#### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  
  <head>
    <meta charset="UTF-8">
    <title>xeliauk's Docs</title>
    <link rel="icon" href="https://avatars.githubusercontent.com/u/138242082?v=4">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="description" content="Description">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-darklight-theme@latest/dist/style.min.css" title="docsify-darklight-theme" type="text/css" /></head>
  
  <body>
    <div id="app">加载中...</div>
    <script>window.$docsify = {
        name: "xeliauk's Docs",
        repo: 'https://github.com/xnuyoah/xDocs',
        // 主页加载封面
        onlyCover: true,
        // 加载 _sidebar.md
        loadSidebar: true,
        // 加载封面
        coverpage: true,
        // 加载导航栏
        loadNavbar: true,
        // 自动回到顶部
        auto2top: true,
        maxLevel: 2,
        subMaxLevel: 4,
        // 搜索
        search: {
          placeholder: '搜索',
          noData: '没有搜索到相关内容',
          depth: 3
        },
        // 分页
        pagination: {
          previousText: '上一章节',
          // or
          nextText: {
            '/en/': 'NEXT',
            '/': '下一章节'
          },
          crossChapter: true,
          crossChapterText: true,
        },
      }</script>
    <!-- Docsify v4 -->
    <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
    <!-- 中文英文之间自动添加空格 -->
    <script src="//cdn.jsdelivr.net/npm/docsify-pangu/lib/pangu.min.js"></script>
    <!-- 搜索 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
    <!-- 代码高亮 -->
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-shell.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-markdown.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-java.min.js"></script>
    <!-- emoji -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
    <!-- 代码复制 -->
    <script src="//cdn.jsdelivr.net/npm/docsify-copy-code@2"></script>
    <!-- 分页 -->
    <script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
    <!-- 黑/白模式切换 -->
    <script src="//cdn.jsdelivr.net/npm/docsify-darklight-theme@latest/dist/index.min.js" type="text/javascript"></script>
  </body>

</html>
```

#### `_coverpage.md`

```markdown
# xDocs <small>v1</small>

> 不限于 coding 的知识库

[GitHub](https://github.com/xnuyoah/xDocs)
[Get Started](README.md)
```

#### `_navbar.md`

```markdown
* Docker
  * [自定义镜像构建](Docker/自定义镜像构建.md)

* AwesomeTools
  * [docsify的基本使用](/AwesomeTools/docsify的基本使用.md)
```

#### `README.md`

```markdown
# xDocs

> 不限于 coding 的知识库
```

