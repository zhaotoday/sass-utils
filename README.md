## 介绍
一个极简的轻量级 Sass 工具库，包括 Sass 混合、函数、预设变量等。

## 遵循的原则
若无必要,勿增实体。

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

#### block--center
块级元素水平居中。

#### link--block
链接块化。

#### img--block
图片块化。

#### _font
字体。需要在业务代码中重写，方便调用。

#### b
BEM block。

#### e
BEM element。

#### m
BEM modifier。

#### text--ellipsis
文字超出部分用省略号代替。

#### clearfix
清除浮动。

#### margin
设置 margin。

#### padding
设置 padding。

#### text--overflow
超出文字用省略号代替。

#### only-ie8
仅 IE8 可用。

#### position--relative
相对定位。

#### position--absolute
绝对定位。

#### position--fixed
固定定位。

#### inline--block
兼容 IE8 的 display: inline-block。

#### size
设置宽高。

## 函数（function）
#### _px2rem
像素转 rem。

#### _color
获取颜色。需要在业务代码中重写，方便调用。

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