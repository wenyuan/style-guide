# CSS编码规范
> 来源：[bootstrap代码规范](https://codeguide.bootcss.com/) <br/>
> 来源：[百度EFE编码规范](https://github.com/ecomfe/spec) <br/>
> 此处只整理我常用的。

<br/>

　　[**目录**]()

[1 声明顺序](#1-声明顺序)

[2 媒体查询的位置](#2-媒体查询的位置)


## 1. 声明顺序
　　相关的属性声明应当归为一组，并按照下面的顺序排列：
###### ① Positioning（元素定位）
###### ② Box model（盒模型）
###### ③ Typographic（字体排版）
###### ④ Visual（颜色视觉）
###### ⑤ Misc（其它杂项）

解释：

　　由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

　　其他属性只是影响组件的 内部 或者是不影响前两组属性，因此排在后面。

示例：
```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```
　　完整的属性列表及其排列顺序请参考 [Bootstrap property order for Stylelint](https://github.com/twbs/stylelint-config-twbs-bootstrap/blob/master/css/index.js)。

<br/>

## 2. 媒体查询的位置
　　将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。

示例：
```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

<br/>
<br/>

###### 最后一次更新：2019-09-25
