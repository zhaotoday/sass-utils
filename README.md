## 介绍
一个极简的轻量级 Sass 工具库，包括 Sass 混合、函数、预设变量等。

## 遵循原则
若无必要,勿增实体。

## 命名规范
BEM 命名法。

## 使用方法
```bash
# 安装
$ npm install --save sass-utils
```

```scss
/* 在 sass 文件中导入 */
@import "~sass-utils";

.selector {
  /* 调用混合 */
  @include position--relative;
  
  /* 使用预设变量来设置字体 */
  font-family: $font-family-english;
}

/* 重写函数，方便调用 */
$colors: red yellow;

@function color($index) {
  @return _color($colors, $index);
}
```

## 混合（mixin）
#### text--middle
文字垂直居中。
```scss
// sass
.selector {
  @include text--middle(100px);
}
```

```scss
// css
.selector {
  height: 100px;
  line-height: 100px;
} 
```

#### block--center
块级元素水平居中。
```scss
// sass
.selector {
  @include block--center;
}
```

```scss
// css
.selector {
  margin-left: auto;
  margin-right: auto;
}
```

#### link--block
链接块化。
```scss
// sass
.selector {
  @include link--block(100px, 200px);
}
```

```scss
// css
.selector {
  display: block;
  text-decoration: none;
  width: 100px;
  height: 200px;  
}
```

#### img--block
图片块化。
```scss
// sass
.selector {
  @include img--block(100px, 200px);
}
```

```scss
// css
.selector {
  display: block;
  width: 100px;
  height: 200px;  
}
```

#### _font
字体。需要在业务代码中重写，方便调用。
```scss
// sass
$fonts: (12px) (13px bold);

@mixin font($index) {
  @include _font($fonts, $index);
}

.selector {
  @include font(2);
}
```

```scss
// css
.selector {
  font-size: 13px;
  font-weight: bold;
}

[data-dpr="2"] .selector {
  font-size: 26px;
}

[data-dpr="3"] .selector {
  font-size: 39px;
}
```

#### b
BEM block。
```scss
// sass
@include b(block) {
  // ...
  
  @include e(element) {
    // ...
  
    @include m(modifier) {
      // ...
    }
  }
}
```

```scss
// css
.block {
  // ...
}

.block__element {
  // ...
}

.block__element--modifier {
  // ...
}
```

#### e
BEM element。

#### m
BEM modifier。

#### text--ellipsis
文字超出部分用省略号代替。
```scss
// sass
.selector {
  @include text--ellipsis;
}
```

```scss
// css
.selector {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;  
}
```

#### clearfix
清除浮动。
```scss
// sass
.selector {
  @include clearfix;
}
```

```scss
// css
.selector::before,
.selector::after {
  content: "";
  display: table;
}

.selector::after {
  clear: both;
}
```

#### margin
设置 margin。
```scss
// sass
.selector {
  @include margin(100px, 200px, 300px, 400px);  
}
```

```scss
// css
.selector {
  margin-top: 100px;
  margin-right: 200px;
  margin-bottom: 300px;
  margin-left: 400px;
}
```

#### padding
设置 padding。
```scss
// sass
.selector {
  @include padding(100px, 200px, null, 400px);
}
```

```scss
// css
.selector {
  padding-top: 100px;
  padding-right: 200px;
  padding-left: 400px;  
}
```

#### text--overflow
超出文字用省略号代替。
```scss
// sass
.selector {
  @include text--overflow;
}
```

```scss
// css
.selector {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;  
}
```

#### only-ie8
仅 IE8 可用。
```scss
// sass
.selector {
  @include only-ie8(display, inline);
}
```

```scss
// css
.selector {
  display: inline\9;
}
```

#### position--relative
相对定位。
```scss
// sass
.selector {
  @include position--relative(100px, 200px);
}
```

```scss
// css
.selector {
  position: relative;
  top: 100px;
  right: 200px;
}
```

#### position--absolute
绝对定位。
```scss
// sass
.selector {
  @include position--absolute(100px, 200px);
}
```

```scss
// css
.selector {
  position: absolute;
  top: 100px;
  right: 200px;
}
```

#### position--fixed
固定定位。
```scss
// sass
.selector {
  @include position--fixed(100px, 200px);
}
```

```scss
// css
.selector {
  position: fixed;
  top: 100px;
  right: 200px;
}
```

#### inline--block
兼容 IE8 的 display: inline-block。
```scss
// sass
$supports-ie8: true;

.selector {
  @include inline--block;
}
```

```scss
// css
.selector {
  display: inline-block;
  display: inline\9;
  zoom: 1\9;  
}
```

#### size
设置宽高。
```scss
// sass
.selector {
  @include size(100px, 200px);
}
```

```scss
// css
.selector {
  width: 100px;
  height: 200px;
}
```

## 函数（function）
#### _px2rem
像素转 rem。
```scss
@function px2rem ($px) {
  @return _px2rem($px);
}
```


#### _color
获取颜色。需要在业务代码中重写，方便调用。
```scss
@function color($index) {
  @return _color($colors, $index);
}
```

## 预设变量（variables）
#### $font-family
字体 - 中文。

#### $font-family-mobile
字体 - 移动端。

#### $font-family-english
字体 - 英文。

#### $separator-element
BEM element 分隔符。

#### $separator-modifier
BEM modifier 分隔符。

#### $supports-ie8
是否兼容 IE8。

## 持续更新中...