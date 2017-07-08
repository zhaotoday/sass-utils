## Introduction
A **SUPER** light sass utility library, includes sass functions, mixins, varibles and so on.

## How to use?
```bash
# install the package
$ npm install --save sass-utils
```

```scss
/* import in your sass file */
@import "~sass-utils";

.selector {
  /* use a mixin */
  @include position--relative;
}

/* overwrite a function */
$colors: red yellow;

@function color($index) {
  @return _color($colors, $index);
}
```
