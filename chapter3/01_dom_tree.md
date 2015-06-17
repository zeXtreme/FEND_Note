## 文档树

Document Object Model (DOM) 既文档**对象**模型，其用对象的方式表示对应的文档结构及内容。

下面为一个样例 `p` 元素在文档中的对象所包含的所有属性。

```
p#targetaccessKey: ""align: ""attributes: NamedNodeMapbaseURI: ""childElementCount: 0childNodes: NodeList[1]children: HTMLCollection[0]classList: DOMTokenList[0]className: ""clientHeight: 0clientLeft: 0clientTop: 0clientWidth: 0contentEditable: "inherit"dataset: DOMStringMapdir: ""draggable: falsefirstChild: textfirstElementChild: nullhidden: falseid: "target"innerHTML: "Hello, World!"innerText: "Hello, World!"isContentEditable: falselang: ""lastChild: textlastElementChild: nulllocalName: "p"namespaceURI: "http://www.w3.org/1999/xhtml"nextElementSibling: nullnextSibling: nullnodeName: "P"nodeType: 1nodeValue: nulloffsetHeight: 0offsetLeft: 0offsetParent: nulloffsetTop: 0offsetWidth: 0onabort: nullonautocomplete: nullonautocompleteerror: nullonbeforecopy: nullonbeforecut: nullonbeforepaste: nullonblur: nulloncancel: nulloncanplay: nulloncanplaythrough: nullonchange: nullonclick: nullonclose: nulloncontextmenu: nulloncopy: nulloncuechange: nulloncut: nullondblclick: nullondrag: nullondragend: nullondragenter: nullondragleave: nullondragover: nullondragstart: nullondrop: nullondurationchange: nullonemptied: nullonended: nullonerror: nullonfocus: nulloninput: nulloninvalid: nullonkeydown: nullonkeypress: nullonkeyup: nullonload: nullonloadeddata: nullonloadedmetadata: nullonloadstart: nullonmousedown: nullonmouseenter: nullonmouseleave: nullonmousemove: nullonmouseout: nullonmouseover: nullonmouseup: nullonmousewheel: nullonpaste: nullonpause: nullonplay: nullonplaying: nullonprogress: nullonratechange: nullonreset: nullonresize: nullonscroll: nullonsearch: nullonseeked: nullonseeking: nullonselect: nullonselectstart: nullonshow: nullonstalled: nullonsubmit: nullonsuspend: nullontimeupdate: nullontoggle: nullonvolumechange: nullonwaiting: nullonwebkitfullscreenchange: nullonwebkitfullscreenerror: nullonwheel: nullouterHTML: "<p id="target">Hello, World!</p>"outerText: "Hello, World!"ownerDocument: documentparentElement: nullparentNode: nullprefix: nullpreviousElementSibling: nullpreviousSibling: nullscrollHeight: 0scrollLeft: 0scrollTop: 0scrollWidth: 0shadowRoot: nullspellcheck: truestyle: CSSStyleDeclarationtabIndex: -1tagName: "P"textContent: "Hello, World!"title: ""translate: truewebkitdropzone: ""__proto__: HTMLParagraphElement
```

通过使用 DOM 提供的 API (Application Program Interface) 可以动态的修改节点（node），也就是对 DOM 树的直接操作。浏览器中通过使用 JavaScript 来实现对于 DOM 树的改动。

**DOM 包含**

- DOM Core
- DOM HTML
- DOM Style
- DOM Event

### HTML 转换 DOM 树

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My title</title>
  </head>
  <body>
    <a href="">My Link</a>
    <h1>My header</h1>
  </body>
</html>
```

![](../img/D/dom-tree.gif)

### 节点遍历

```Javascript
var node = document.getElementsByTagName('h1')[0];

node.parentNode; // body
node.firstChild; // null
node.lastChild;  // null
node.previousBibling; // <a href="">My Link</a>
node.nextSibling;     // null
```

### 节点类型

**常用节点类型**

- ELEMENT_NODE 可使用 `document.createElement('elementName');`创建
- TEXT_NODE 可使用 `document.createTextNode('Text Value');` 创建

**不常用节点类型**

- COMMENT_NODE
- DOCUMENT_TYPE_NODE

### 元素遍历

元素节点符合 HTML DOM 树规则。

```
<p>Hello, <em>Xinyang</em>! 回到<a href="http://li-xinyang.com">主页</a>。</p>
```

```
p.firstElementChild; // <em>Xinyang</em>
p.lastElementChild;  // <a href="http://li-xinyang.com">主页</a>

em.nextElementSibling; // <a href="http://li-xinyang.com">主页</a>
em.previousElementSibling; // null
```