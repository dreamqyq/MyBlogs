## 本篇文章主要写一些html（超文本标记语言，Hyper Text Markup Language）的基础知识（主要摘自维基百科和MDN）
#### 1. W3C 简介
万维网联盟（**World Wide Web Consortium**，**W3C**），又称**W3C理事会**，是万维网的主要国际标准组织。
>万维网联盟（W3C）由[蒂姆·伯纳斯-李](https://zh.wikipedia.org/wiki/%E6%8F%90%E5%A7%86%C2%B7%E6%9F%8F%E5%85%A7%E8%8C%B2-%E6%9D%8E "蒂姆·伯纳斯-李")于1994年10月离开[欧洲核子研究中心](https://zh.wikipedia.org/wiki/%E6%AD%90%E6%B4%B2%E6%A0%B8%E5%AD%90%E7%A0%94%E7%A9%B6%E7%B5%84%E7%B9%94 "欧洲核子研究中心")（CERN）后成立，在[欧盟执委会](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E5%9F%B7%E5%A7%94%E6%9C%83 "欧盟执委会")和[国防高等研究计划署](https://zh.wikipedia.org/wiki/%E5%9C%8B%E9%98%B2%E9%AB%98%E7%AD%89%E7%A0%94%E7%A9%B6%E8%A8%88%E5%8A%83%E7%BD%B2 "国防高等研究计划署")（DARPA）的支持下成立于[麻省理工学院](https://zh.wikipedia.org/wiki/%E9%BA%BB%E7%9C%81%E7%90%86%E5%B7%A5%E5%AD%B8%E9%99%A2 "麻省理工学院")[MIT计算机科学与人工智能实验室](https://zh.wikipedia.org/wiki/MIT%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8%E8%88%87%E4%BA%BA%E5%B7%A5%E6%99%BA%E6%85%A7%E5%AF%A6%E9%A9%97%E5%AE%A4 "MIT计算机科学与人工智能实验室")（MIT／LCS），DARPA曾率先推出了[互联网](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%AF%E7%B6%B2 "互联网")及其前身[ARPANET](https://zh.wikipedia.org/wiki/ARPANET)。
为解决网络应用中不同平台、技术和开发者带来的不兼容问题，保障网络信息的顺利和完整流通，万维网联盟制定了一系列标准并督促网络应用开发者和内容提供者遵循这些标准。标准的内容包括使用语言的规范，开发中使用的导则和解释引擎的行为等等。W3C也制定了包括[XML](https://zh.wikipedia.org/wiki/XML "XML")和[CSS](https://zh.wikipedia.org/wiki/CSS "CSS")等的众多影响深远的标准规范。
(摘自维基百科)

#### 2. MDN 简介
>**MDN Web Docs**（旧称Mozilla Developer Network、Mozilla Developer Center，简称MDN）是一个汇集众多Mozilla基金会产品和网络技术开发文档的免费网站。
(摘自维基百科)

当需要查询某种HTML标签用法时，可以使用Google关键字在MDN网站上查询
如：ananchor MDN 即可查询到`<a>`标签的用法。

#### 3. HTML 所有标签列表
https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element
上述链接为MDN所展示的所有html标签列表及具体用法，如有需要可以点击查询
#### 4. 空标签/空元素
>一个 **空元素empty element** 可能是 HTML，SVG，或者 MathML 里的一个不可能存在子节点（例如内嵌的元素或者元素内的文本）的element。
在 HTML 中，通常在一个空元素上使用一个闭标签是无效的。例如， `<input type="text"></input>` 的闭标签是无效的 HTML。
(摘自MDN)

在HTML中有以下空标签
*   [`<area>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/area "HTML <area> 元素 在图片上定义一个热点区域")
*   [`<base>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/base "HTML <base> 元素 指定用于一个文档中包含的所有相对URL的基本URL。一份中只能有一个<base>元素。")
*   [`<br>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/br "HTML 元素 换行 <br> 在文本中产生一个换行（回车键）。这对于写诗或写一个地址来说显得很有用。它可以将行明显地分开。")
*   [`<col>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/col "HTML <col> 元素 定义表格中的列，并用于定义所有公共单元格上的公共语义。它通常位于<colgroup>元素内。")
*   [`<colgroup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/colgroup "HTML 中的 表格列组（Column Group <colgroup>） 标签用来定义表中的一组列表。") when the [span](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/colgroup#attr-span) is present
*   [`<command>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/command "command元素用来表示一个用户可以调用的命令.")
*   [`<embed>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed "HTML <embed> 元素 用于表示一个外部应用或交互式内容的集合点，换句话说，就是一个插件。")
*   [`<hr>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/hr "HTML <hr> 元素表示段落级元素之间的主题转换（例如，一个故事中的场景的改变，或一个章节的主题的改变）。在HTML的早期版本中，它是一个水平线。现在它仍能在可视化浏览器中表现为水平线，但目前被定义为语义上的，而不是表现层面上。")
*   [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img "HTML Image 元素（ <img> ）代表文档中的一个图像。")
*   [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input "HTML <input> 元素用于为基于Web的表单创建交互式控件，以便接受来自用户的数据。")
*   [`<keygen>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/keygen "HTML <keygen> 元素是为了方便生成密钥材料和提交作为 HTML form 的一部分的公钥.这种机制被用于设计基于 Web 的证书管理系统。按照预想，<keygen> 元素将用于 HTML 表单与其他的所需信息一起构造一个证书请求，该处理的结果将是一个带有签名的证书。")
*   [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link "HTML 中<link>元素指定了外部资源与当前文档的关系. 这个元素的使用方法包括为导航定义关系框架.这个元素经常用来链接css文件。")
*   [`<meta>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta "HTML <meta> 元素表示那些不能由其它HTML元相关元素 (<base>, <link>, <script>, <style> 或 <title>) 之一表示的任何元数据信息.")
*   [`<param>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/param "HTML <param> 元素(或 HTML Parameter 元素) 定义了 <object>的参数")
*   [`<source>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/source "The HTML <source> element specifies multiple media resources for either the <picture>, the <audio> or the <video> element. It is an empty element. It is commonly used to serve the same media content in multiple formats supported by different browsers.")
*   [`<track>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/track "HTML <track> 元素 被当作媒体元素—<audio> 和 <video>的子元素来使用。它允许指定计时字幕（或者基于事件的数据），例如自动处理字幕。")
*   [`<wbr>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/wbr "HTML <wbr> 元素  — 一个文本中的位置，其中浏览器可以选择来换行，虽然它的换行规则可能不会在这里换行。")


#### 5. 可替换元素
CSS 里，**可替换元素replaced element** 的展现不是由CSS来控制的。这些元素是一类 外观渲染独立于CSS的 外部对象。 典型的可替换元素有 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img "HTML Image 元素（ <img> ）代表文档中的一个图像。")、 [`<object>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object "HTML <object> 元素（或者称作 HTML 嵌入对象元素）表示引入一个外部资源，这个资源可能是一张图片，一个嵌入的浏览上下文，亦或是一个插件所使用的资源。")、 [`<video>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/video "HTML <video> 元素 用于在HTML或者XHTML文档中嵌入视频内容。") 和 表单元素，如[`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea "HTML <textarea> 元素表示一个多行纯文本编辑控件。")、 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input "HTML <input> 元素用于为基于Web的表单创建交互式控件，以便接受来自用户的数据。") 。 某些元素只在一些特殊情况下表现为可替换元素，例如 [`<audio>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/audio "HTML <audio> 元素用于在文档中表示音频内容。 <audio> 元素可以包含多个音频资源， 这些音频资源可以使用 src 属性或者<source> 元素来进行描述； 浏览器将会选择最合适的一个来使用。对于不支持<audio>元素的浏览器，<audio>元素也可以作为浏览器不识别的内容加入到文档中。") 和 [`<canvas>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/canvas "<canvas>元素可被用来通过脚本（通常是JavaScript）绘制图形。比如,它可以被用来绘制图形,制作图片集合,甚至用来实现动画效果。你可以(也应该)在元素标签内写入可提供替代的的代码内容，这些内容将会在在旧的、不支持<canvas>元素的浏览器或是禁用了JavaScript的浏览器内渲染并展现。") 。 通过 CSS [`content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/content "CSS的 content CSS 属性用于在元素的  ::before 和 ::after 伪元素中插入内容。使用content 属性插入的内容都是匿名的可替换元素。") 属性来插入的对象 被称作 **匿名可替换元素（***anonymous replaced elements***）**。

CSS在某些情况下会对可替换元素做特殊处理，比如计算外边距和一些auto值。

需要注意的是，一部分（并非全部）可替换元素，本身具有尺寸和基线（baseline），会被像[`vertical-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align "CSS 的属性 vertical-align 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。")之类的一些 CSS 属性用到。

