## 属性操作

### HTML 属性与 DOM 属性的对应

每个 HTML 属性都会对应相应的 DOM 对象属性。

```html
<div>
  <label for="username">User Name: </label>
  <input type="input" name="username" id="username" class="text" value="">
</div>
```

```javascript
input.id;        // 'username'
input.type;      // 'text'
input.className; // 'text'

label.htmlFor;   // 'username'
```

#### Property Accessor

通过属性方法符得到的属性为转换过的实例对象（并非全字符串）。

**特点**

- X 通用行差（命名异常，使用不同的命名方式进行访问）
- X 扩展性差
- √ 实用对象（取出后可直接使用）

**读取属性**

```html
<div>
  <label for="username">User Name: </label>
  <input type="input" name="username" id="username" class="text" value="">
</div>
```

```javascript
input.className; // 'text'
input[id];        // 'username'
```

**写入属性**

可增加新的属性或改写已有属性。

```javascript
input.value = 'new value';
input[id] = 'new-id';
```

#### getAttribute / setAttribute

**特点**

- X 仅可获取字符串（使用时需转换）
- √ 通用性强

**读取属性**

获取到的均为属性的**字符串**。

```javascript
var attribtue = element.getAttribute('attributeName');
```

**写入属性**

可增加新的属性或改写已有属性。

```javascript
element.setAttribute('attributeName', value);
```

#### dataset

自定义属性，其为 `HTMLElement` 上的属性也是 `data-*` 的属性集。主要用于在元素上保存数据。获取的均为**属性字符串**。数据通常使用 JAXA 获取并存储在节点之上。

```html
<div id='user' data-id='1234' data-username='x' data-email='mail@gmail.com'></div>
```

```javascript
div.dataset.id;         // '1234'
div.dataset.username;   // 'x'
div.dataset.email;      // 'mail@gmail.com'
```

NOTE：`dataset` 在低版本 IE 不可使用，但可通过 `getAttribute` 与 `setAttribute` 来做兼容。