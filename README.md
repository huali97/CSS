# CSS 选择器

## 基本选择器

### 通用选择器（Universal selector）

>选择所有元素。（可选）可以将其限制为特定的名称空间或所有名称空间。

语法：* ns|* *|*

例子：* 将匹配文档的所有元素。

### 元素选择器

> CSS元素选择器(也称为类型选择器)通过node节点名称匹配元素. 因此,在单独使用时,寻找特定类型的元素时,元素选择器都会匹配该文档中所有此类型的元素.

语法:

`元素 {样式声明 }`

### 类选择器

>  在一个HTML文档中，CSS类选择器会根据元素的类属性中的内容匹配元素。类属性被定义为一个以空格分隔的列表项，在这组类名中，必须有一项与类选择器中的类名完全匹配，此条样式声明才会生效。

语法:

`.类名 {样式声明 }`

注意它与下面的语句等价 ` attribute selector`:

`[class~=类名] {样式声明 }`


### ID 选择器

> 在一个HTML文档中,CSS ID 选择器会根据该元素的 ID 属性中的内容匹配元素,元素 ID 属性名必须与选择器中的 ID 属性名完全匹配，此条样式声明才会生效。

```
/* The element with id="demo" */
#demo {
  border: red 2px solid;
}
```

语法:

`#id属性值 {样式声明 }`

它与下面的属性选择器语句等价：

`[id=id属性值] {样式声明 }`

### 属性选择器

> CSS 属性选择器通过已经存在的属性名或属性值匹配元素

```
/* 存在title属性的<a> 元素 */
a[title] {
  color: purple;
}

/* 存在href属性并且属性值匹配"https://example.org"的<a> 元素 */
a[href="https://example.org"] {
  color: green;
}

/* 存在href属性并且属性值包含"example"的<a> 元素 */
a[href*="example"] {
  font-size: 2em;
}

/* 存在href属性并且属性值结尾是".org"的<a> 元素 */
a[href$=".org"] {
  font-style: italic;
}

/* 存在class属性并且属性值包含"logo"的<a>元素 */
a[class~="logo"] {
  padding: 2px;
}
```

语法:

`[attr]`
表示带有以 attr 命名的属性的元素。

`[attr=value]`
表示带有以 attr 命名的属性，且属性值为 value 的元素。

`[attr~=value]`
表示带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少有一个值为 value。

`[attr|=value]`
表示带有以 attr 命名的属性的元素，属性值为“value”或是以“value-”为前缀（"-"为连字符，Unicode 编码为 U+002D）开头。典型的应用场景是用来匹配语言简写代码（如 zh-CN，zh-TW 可以用 zh 作为 value）。

`[attr^=value]`
表示带有以 attr 命名的属性，且属性值是以 value 开头的元素。

`[attr$=value]`
表示带有以 attr 命名的属性，且属性值是以 value 结尾的元素。

`[attr*=value]`
表示带有以 attr 命名的属性，且属性值包含有 value 的元素。

`[attr operator value i]`
在属性选择器的右方括号前添加一个用空格隔开的字母 i（或 I），可以在匹配属性值时忽略大小写（支持 ASCII 字符范围之内的字母）。

`[attr operator value s] `
在属性选择器的右方括号前添加一个用空格隔开的字母 s（或 S），可以在匹配属性值时区分大小写（支持 ASCII 字符范围之内的字母）。

## 组合选择器

### 相邻兄弟选择器

>相邻兄弟选择器 (+) 介于两个选择器之间，当第二个元素紧跟在第一个元素之后，并且两个元素都是属于同一个父元素的子元素，则第二个元素将被选中。

```
/* 图片后面紧跟着的段落将被选中 */
img + p {
  font-style: bold;
}
```
语法:

`former_element + target_element { style properties }`

### 通用兄弟选择器

> 兄弟选择符，位置无须紧邻，只须同层级，A~B 选择A元素之后所有同层级B元素。

`former_element ~ target_element { style properties }`

### 子选择器

> 当使用  > 选择符分隔两个元素时,它只会匹配那些作为第一个元素的直接后代(子元素)的第二元素. 与之相比, 当两个元素由 后代选择器 相连时, 它表示匹配存在的所有由第一个元素作为祖先元素(但不一定是父元素)的第二个元素, 无论它在 DOM 中"跳跃" 多少次.

语法:

`元素1 > 元素2 {样式声明 }`


### 后代选择器

> 当使用 ␣ 选择符 (这里代表一个空格,更确切的说是一个或多个的空白字符) 连接两个元素时使得该选择器可以只匹配那些由第一个元素作为祖先元素的所有第二个元素(后代元素) . 后代选择器与 子选择器 很相似, 但是后代选择器不需要相匹配元素之间要有严格的父子关系.

```
span { background-color: white; }
div span { background-color: DodgerBlue; }
```

语法:

`元素1 元素2 {样式声明 }`

## 伪类选择器

参考 [MDN web 文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:active)



