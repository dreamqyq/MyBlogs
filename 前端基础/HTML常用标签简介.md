## HTML常用标签简介
[MDN中所列出的html标签列表](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
### 1. 一些简单的常见标签
- `<h1>- <h6>` 标题元素
- `<p>` 段落元素
- `<ul>` 无序列表
- `<ol>` 有序列表
- `<small>` 不重要的文字
- `<strongv` 重要的文字
- `<kbd>` 键盘输入元素
- `<video>` 视频元素 `audio>` 音频元素
- `<svg>` 可缩放矢量图形
- `<div>` 区块元素
- `<span>` 短语内容
### 2. `<a>` && `<ifram>` 
- `<a>` 锚点，在http中进行get请求，有以下常用属性

    （1）`href` 属性：必需属性，为锚定义一个超文本链接来源  

    ==> `href="qq.com"` 会当成文件打开（因未设定打开协议）

    ==> `href="//qq.com"` 无协议绝对地址，当前时什么协议就以什么协议打开

    ==> `href="index.html"` 相对路径，以ftp协议

    ==> `href="#XX"` 定义当前页面的锚点

    ==> `href="?xx=yy"` 查询参数

    ==> `href="javascript:alert('1')"` JavaScript伪协议

    ==> `href="javascript:;"` 为达到点击链接不做跳转的效果

    （2）`target` 属性：该属性指定在何处显示链接的资源，可以`<iframe>`标签连用，指向`iframe`的`name`

    ==> `target=_blank` 在新的页面打开

    ==> `target=_self` 在自身打开

    ==> `target=_top` 若在iframe中，在其最外层打开

    ==> `target=_parent` 若在iframe中，在其上一层iframe打开

    （3）`download` 属性：当网页的响应`Content-Type`设置为`“application/octet-stream”`时，可以不用`download`

    当Content-Type设置为`“text/html”`时，若想下载如`<a href="index.html" download>link</a>`必须用`download`
- `<iframe>` 内联框架元素，有以下常用属性

    ==> `src` 属性 `iframe`指向的路径

    ==> `name` 属性 与`<a>`标签配合使用，用于`<a>`标签的指向链接

    ==> `frameborder` 属性 `iframe`标签外边框，一般设置为0
### 3. 表单标签
注：表单元素若要正常提交至服务器，需有name属性
- `<form>` 在http中一般进行post请求

    ==> `action` 属性 用于制定表单提交的目标

    ==>  `method` 属性 用于表示表单以何种方式发至目标

    ==> `target` 属性 同`<a>`标签的`target`
- `<input type="submit">`&&`<input type="button">`&&`<button>`

    PS：一个表单中，必须得有提交按钮，否则表单数据无法提交

    ==> `<input type="submit">` 提交按钮，输入完数据 <kbd>Enter</kbd> 即可上传表单数据

    ==> `<button>` 一个表单中若没有提交按钮，仅有button标签，该标签会自动升级为`submit`

    ==> `<input type="button">` 这么写就仅仅是一个普通的按钮，即使表单没有提交按钮也不会自动升级 
- `<input typt="checkbox>"`&&`<label>`

    ==> `<input type="checkbox">` 复选框

    ==> 达到点击文字就可以选中复选框时可以和`<label>`连用，如：

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<input type="checkbox" id="btn"> <label for="btn">apple</label>`

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不过常用下面这种写法：

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<label>apple<input type="checkbox"></label>`
- `<input type="radio">` 单选框，也可以同复选框一样与`<label>`标签连用

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;若达到几个单选框只能选择一个的效果，要设置一样的`name`属性
- `<select>` 下拉表单，常用的有`name`属性，`multiple`（可多选）属性
- `<option>` 下拉表单中的选项，有以下常用属性

    ==> `<optgroup>` 为多个`option`标签划分一个组，用`label`属性设置组名，如:

    ```
     <optgroup label="x1">
      <option value="1">10</option>
      <option value="2">12</option>
    </optgroup>
  ```

  ==> `<option>`标签的常用属性有value,设置选项上传至服务器的值

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`disabled` 属性 设置选型不可选

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`selected` 属性 设置该选项默认选中
- `<textarea>` 多行文本域

    ==> 虽然该标签有cols属性和rows属性分别控制列数和行数，但都不是很准确，所以一般`<texrtarea>`标签的大小用css的`height`和`width`来控制

    ==> 在css中，还可以设置其`resize=none;`用来控制该多行文本域不可被用户拉动，防止影响网页布局
### 4. `<table>`表格元素
- `<table>`表格标签中只能有`<thead>`、`<tbody>`、`<tfoot>`三种标签。
- 如果没有`<thead>`和`<tfoot>`标签，所有的内容默认添加在`<tbody>`标签中，如果没有`<tbody>`标签，浏览器会自动添加。
- 在设置了`<thead>`、`<tbody>`、`<tfoot>`三种标签后，三种标签在代码中的顺序将不会影响网页渲染的效果，永远以`<thead>`、`<tbody>`、`<tfoot>`顺序进行展示。
- `<td> `表示表的数据、`<th>`表示表头(默认样式包括加粗和居中)，`<tr>`表示每一行
- 所有的`<td> `、`<th>`标签都要在`<tr>`标签里面
- `<colgroup>`(有闭合标签)、`<col>`(空标签)
代码实例参上，以观标签效果
```
<table border=1>
    <colgroup>
      <col width=100> <!-- 控制第一列的宽度-->
      <col width=100 bgcolor="blue"><!-- 控制第二列的宽度和背景颜色-->
      <col width=100>
      <col width=100>
    </colgroup>
    <thead>
      <tr>
        <th>h1</th>
        <th>h2</th>
        <th>h3</th>
        <th>h4</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>11</td>
        <td>12</td>
        <td>13</td>
        <td>14</td>
    </tbody>
    <tfoot>
      <tr>
        <td>31</td>
        <td>32</td>
        <td>33</td>
        <td>34</td>
      </tr>
    </tfoot>
  </table>
```

- css中，设置标签的边框合并
 ```
table{
      border-collapse:collapse;
    }
```
### 5. 常用的内容分区语义化标签
- `<article>` 表示文档、页面、应用或网站中的独立结构
- `<aside>` 其通常表现为侧边栏或者嵌入内容
- `<footer>` 表示最近一个章节内容或者根节点元素的页脚
- `<header>` 表示一组引导性的帮助，可能包含标题元素
- `<nav>`导航栏，描绘一个含有多个超链接的区域
- `<section>` 表示文档中的一个区域（或节），比如，内容中的一个专题组，一般来说会有包含一个标题
- `<dl>`、`<dt>`、`<dd>`

    ==> `<dl> `是一个包含术语定义以及描述的列表

    ==> `<dt> `用于在一个定义列表中声明一个术语

    ==> `<dd>` 用来指明一个描述列表`<dl>`元素中一个术语的描述
- `<main>` 表示文档的主体内容，由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。
- `<address>` 可以让作者为它最近的`<article>`或者`<body>`]祖先元素提供联系信息。在后一种情况下，它应用于整个文档。

