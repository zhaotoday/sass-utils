## 介绍
一个极简的 Sass 工具库，包括 Mixins、Functions、Variables、Utils 等。

## 命名规范
[BEM 命名法。](https://github.com/zhaotoday/bem)

## 使用方法
```bash
# 安装
$ npm install --save sass-utils
```

```scss
/* 在 Sass 文件中导入 */
@import "~sass-utils";

.selector {
  /* 调用 Mixin */
  @include position--relative;
}
```

## Mixins

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
文字超出部分用省略号代替。
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

## Functions
#### _px2rem
像素转 rem。
```scss
// sass
@function px2rem ($px) {
  @return _px2rem($px, 75);
}

.selector {
  width: px2rem(750px);
}
```

```scss
// css
.selector {
  width: 10rem;
}
```

## Variables

#### $separator-element
BEM element 分隔符。

#### $separator-modifier
BEM modifier 分隔符。

#### $supports-ie8
是否兼容 IE8。

## Utils
```scss
.u-fwb {
  font-weight: bold;
}

.u-tac {
  text-align: center;
}

.u-tal {
  text-align: left;
}

.u-tar {
  text-align: right;
}

.u-cf {
  @include clearfix;
}

.u-lt {
  text-decoration: line-through;
}

.u-pr {
  position: relative;
}
```

## 命名空间
[BEM 命名空间](https://github.com/zhaotoday/bem#%E5%91%BD%E5%90%8D%E7%A9%BA%E9%97%B4)