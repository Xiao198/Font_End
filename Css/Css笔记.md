## CSS查漏补缺
- CSS规则：选择器，声明，属性，属性值。
  ![Html 元素](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics/css-declaration-small.png)
- 多元素选择：用逗号分开
```CSS
p, li, h1 {
  color: red;
}
```
- 不同类型的选择器

  | 选择器名称   | 选择的内容                               | 示例                                                         |
  | ------------ | ---------------------------------------- | ------------------------------------------------------------ |
  | 标签选择器   | 选择指定的HTML标签                       | p选择\<p>                                                    |
  | ID选择器     | 具有特定ID的元素                         | #my-id` 选择 `<p id="my-id">` 或 `<a id="my-id">             |
  | 类选择器     | 具有特定类的元素                         | .my-class` 选择 `<p class="my-class">` 和 `<a class="my-class"> |
  | 属性选择器   | 拥有特定属性的元素                       | img[src]` 选择 <img src="myimage.png">` 而不是 `<img>        |
  | 伪类选择器   | 特定状态下的指定元素（比如鼠标指针悬停） | `a:hover` 仅在鼠标指针悬停在链接上时选择 `<a>`               |
  | 伪元素选择器 | 选择元素的某个部分而不是元素本身         | p::first-line 始终选择\<p>元素内的第一行文本                 |

- CSS样式优先级：！important（权重：无穷）> 内联样式（1000）>ID选择器（100）>类选择器，属性选择器，伪类选择器（10）>标签选择器，伪元素选择器（1）>通用选择器，相邻兄弟选择器（+），兄弟选择器（~），子选择器（>）（0）>继承>默认

- CSS三种引入方式：外部样式表（link引入），内部样式表（style标签内），内联样式
  
- CSS中元素浮动后，文字环绕于浮动元素周围，没有与浮动元素重合：https://blog.csdn.net/csdn_ds/article/details/75145682?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-75145682-blog-83752020.pc_relevant_multi_platform_whitelistv4eslandingctr2&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-75145682-blog-83752020.pc_relevant_multi_platform_whitelistv4eslandingctr2&utm_relevant_index=1
早些时候，W3C规定出来的浮动并不是为了布局所用，当时就是为了做文字环绕才使用了浮动。浮动比较特殊，虽然脱离了文档流，但是最终还是可以影响到布局。绝对定位则是完全将元素从文档流中删除。  
- 浮动的功能：脱离文档流，文字环绕。

- 为元素开启绝对定位不设置偏移量，元素还在静态位置，只是脱离文档流。可以通过设置top,left = 0查看起点。