<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

    - [常见布局样例](#%E5%B8%B8%E8%A7%81%E5%B8%83%E5%B1%80%E6%A0%B7%E4%BE%8B)
      - [自动居中一列布局](#%E8%87%AA%E5%8A%A8%E5%B1%85%E4%B8%AD%E4%B8%80%E5%88%97%E5%B8%83%E5%B1%80)
- [Title](#title)
- [Title](#title-1)
      - [横向两列布局](#%E6%A8%AA%E5%90%91%E4%B8%A4%E5%88%97%E5%B8%83%E5%B1%80)
    - [Aside Title](#aside-title)
- [Title](#title-2)
    - [Aside Title](#aside-title-1)
      - [绝对定位的横向两列布局](#%E7%BB%9D%E5%AF%B9%E5%AE%9A%E4%BD%8D%E7%9A%84%E6%A8%AA%E5%90%91%E4%B8%A4%E5%88%97%E5%B8%83%E5%B1%80)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### 常见布局样例

#### 自动居中一列布局

所需知识：

- 标准文档流
- 块级元素
- margin 外边距属性

```html
<style type="text/css" media="screen">
  article {
    width: 800px;
    margin: 0 auto;
  }
</style>

<body>
  <article>
    <h1>Title</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. A natus repellendus, modi culpa, dolor ducimus debitis, facere dolorum cum aspernatur, soluta molestias est illo vel iusto esse ex ullam amet!</p>
  </article>
</body>
```

NOTE：设置 auto 会根据浏览器宽度自动设置外边距尺寸。在设置浮动或绝对定位则会使自动居中失效，因为其会脱离文档流。

`(浏览器宽度 - 外包含层的宽度)/ 2 = 外边距`。

#### 横向两列布局

此方法也同时可以实现横向多列布局（原理与两列布局相同）。

所需知识：

- float 属性，使纵向排列的块级元素，横向排列
- margin 属性，设置列直接的间距

```html
<style type="text/css" media="screen">
  .clearfix:after {
     content: "."; /* Older browser do not support empty content */
     visibility: hidden;
     display: block;
     height: 0;
     clear: both;
  }
  .clearfix {zoom: 1;} /* 针对 IE 不支持 :after */
  body {
    width: 930px;
    margin: 0 auto; /* 横向居中 */
  }
  article {
    width: 800px;
    float: left;
    margin-right: 10px;
  }
  aside {
    width: 120px;
    float: right;
  }
</style>
<body class="clearfix">
  <article>
    <h1>Title</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Explicabo, quam, fugit. Accusamus voluptates nesciunt in, autem ipsa assumenda a iusto, reiciendis earum repudiandae, nulla natus blanditiis, aliquam asperiores commodi qui.</p>
  </article>
  <aside>
    <h3>Aside Title</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Expedita, molestiae!</p>
  </aside>
</body>
```

#### 绝对定位的横向两列布局

应用场合较少，常用与一列定宽，另一列自适应。

需要知识：

- relative positon 父元素相对定位
- absolute 自适应宽度元素绝对定位

注意：固定宽度列的高度需大于自适应的列（原因是绝对定位会脱离文档流，不能撑开父元素）。

```html
<style type="text/css" media="screen">
  body {
    position: relative;
    width: 100%;
  }

  article {
    position: absolute;
    top: 0;
    right: 0;
    width: 800px;
  }
  aside {
    position: absolute;
    top: 0;
    right:800px;
    left: 0;
  }
</style>

<body>
  <article>
    <h1>Title</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error obcaecati sint minima totam fuga, tempora, id quia soluta officia iure eligendi sequi non dicta, doloribus accusamus odit fugiat quam quibusdam.</p>
  </article>
  <aside>
    <h3>Aside Title</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Atque, doloremque.</p>
  </aside>
</body>
```