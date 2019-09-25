# HTML编码规范
> 来源：[bootstrap代码规范](https://codeguide.bootcss.com/) <br/>
> 来源：[百度EFE编码规范](https://github.com/ecomfe/spec) <br/>
> 此处只整理我常用的。

<br/>

　　[**目录**]()

[1 属性顺序](#1-属性顺序)

[2 class命名](#2-class命名)

[3 id命名](#3-id命名)

[4 name命名](#4-name命名)


## 1. 属性顺序
　　HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。
* `class`
* `id`，`name`
* `data-*`
* `src`，`for`，`type`，`href`，`value`
* `title`，`alt`
* `role`，`aria-*`

　　class 用于标识高度可复用组件，因此应该排在首位。

　　id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

示例：
```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

<br/>

## 2. class命名
* `class` 必须单词全字母小写，单词间以 `-` 分隔；
* `class` 必须代表相应模块或部件的内容或功能，不得以样式信息进行命名；
* 避免过度任意的简写。`.btn` 代表 `button`，但是 `.s` 不能表达任何意思；
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。

示例：
```html
<!-- good -->
<div class="sidebar"></div>

<!-- bad -->
<div class="left"></div>
```
　　常用命名可参考[alloyteam](http://www.alloyteam.com/2011/10/css-on-team-naming/)。

<br/>

## 3. id命名
* 元素 `id` 必须保证页面唯一；
* `id` 建议单词全字母小写，单词间以 `-` 分隔。同项目必须保持风格一致。
*  `id`、`class` 命名，在避免冲突并描述清楚的前提下尽可能短。

示例：
```html
<!-- good -->
<div id="nav"></div>
<!-- bad -->
<div id="navigation"></div>

<!-- good -->
<p class="comment"></p>
<!-- bad -->
<p class="com"></p>

<!-- good -->
<span class="author"></span>
<!-- bad -->
<span class="red"></span>
```

<br/>

## 4. name命名
* 同一页面，应避免使用相同的 `name` 与 `id`。
* `name` 一般与后端model中的字段名命名规则保持一致。
  * 例如Java使用驼峰命名法，Python使用下划线 `_` 连接两个小写单词。

解释：

　　IE 浏览器会混淆元素的 `id` 和 `name` 属性， `document.getElementById` 可能获得不期望的元素。所以在对元素的 `id` 与 `name` 属性的命名需要非常小心。

　　一个比较好的实践是，为 `id` 和 `name` 使用不同的命名法。

示例：
```html
<input name="foo">
<div id="foo"></div>
<script>
// IE6 将显示 INPUT
alert(document.getElementById('foo').tagName);
</script>
````

<br/>
<br/>

###### 最后一次更新：2019-09-25
