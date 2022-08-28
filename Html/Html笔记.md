## HTML查漏补缺
### HTML入门
- HTML标签内的元素不区分大小写。\<title> 标签可以写成 \<Title>，\<TITLE> 或以任何其他方式。

- HTML元素：开始标签，内容，结束标签；元素也可以有属性。

  ![HTML 元素](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-small.png)

  ![HTML 属性](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-attribute-small.png)

- 不包含任何内容的元素称为空元素，比如\<img>元素。

### head中的元数据
- 许多 \<meta> 元素包含了 name 和 content 属性：name 指定了 meta 元素的类型；说明该元素包含了什么类型的信息。
content 指定了实际的元数据内容。
```HTML
<meta name="author" content="Chris Mills">
<!--description可以用来SEO-->
<meta name="description" content="The MDN Web Docs Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```
- \<link>用来引入CSS文件，rel="stylesheet" 表明这是文档的样式表，而 href 包含了样式表文件的路径：
```html
<link rel="stylesheet" href="my-css-file.css">
```
- \<script> 元素没必要非要放在文档的 <head> 中，并包含 src 属性来指向需要加载的 JavaScript 文件路径，同时最好加上 defer 以告诉浏览器在解析完成 HTML 后再执行 JavaScript。这样可以确保在加载脚本之前浏览器已经解析了所有的 HTML 内容（如果脚本尝试访问某个不存在的元素，浏览器会报错）。
```html
<script src="my-js-file.js" defer></script>
```

### html文字处理
-\<span> 是一个内联的（inline）无语义元素，最好只用于无法找到更好的语义元素来包含内容时，或者不想增加特定的含义时。

### 超链接
- 超链接\<a>，使用title属性，当鼠标悬停时展示提示信息。
- 可以将块级元素当做超链接，将块级元素放入\<a>标签内。
```html
<a href="https://www.mozilla.org/zh-CN/">
  <img src="mozilla-image.png" alt="链接至 Mozilla 主页的 Mozilla 标志">
</a>
```
- 锚点https://blog.csdn.net/Thedemonsword/article/details/124211438：超链接除了可以链接到文档外，也可以链接到 HTML 文档的特定部分（被称为文档片段）。要做到这一点，你必须首先给要链接到的元素分配一个 id 属性。例如，如果你想链接到一个特定的标题，可以这样做：
```html
<h2 id="Mailing_address">邮寄地址</h2>
<!--然后链接到那个特定的 id，你可以在 URL 的结尾使用一个井号指向它，例如：-->
<p>要提供意见和建议，请将信件邮寄至<a href="contacts.html#Mailing_address">我们的地址</a>。</p>
<!--你甚至可以在同一份文档下，通过链接文档片段，来链接到同一份文档的另一部分：-->
<p>本页面底部可以找到<a href="#Mailing_address">公司邮寄地址</a>。</p>
```
- 下载链接可以使用download属性提供默认保存文件名。

### 文档与页面结构
- \<br>换行，\<hr>水平分割线。