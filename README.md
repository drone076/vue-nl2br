# vue-nl2br

![main workflow](https://github.com/inouetakuya/vue-nl2br/actions/workflows/main.yml/badge.svg)

A vue component which turns new lines into line breaks. Fixed version.

Original library doesn't work with Webpack 5. Errors:
WARNING in ./node_modules/vue-nl2br/dist/Nl2br.js 3:24-31
Critical dependency: require function is used in a way in which dependencies cannot be statically extracted
WARNING in ./node_modules/vue-nl2br/dist/index.js 6:24-31
Critical dependency: require function is used in a way in which dependencies cannot be statically extracted

The problem in UMD module compilation. This issue is fixed in this fork.


## Why not just use CSS?

See [Why not just use CSS `white-space: pre;`? · Issue #7](https://github.com/inouetakuya/vue-nl2br/issues/7)

## Requirement

- [Vue.js](https://github.com/vuejs/vue) `^2.0.0`

## Installation

```shell
npm install --save vue-nl2br
```

## Usage

```html
<nl2br tag="p" :text="`myLine1\nmyLine2`" class-name="foo bar" />
```

is rendered to

```html
<p class="foo bar">myLine1<br>myLine2</p>
```

### (1) Global registration

https://vuejs.org/v2/guide/components.html#Registration

```js
import Vue from 'vue'
import Nl2br from 'vue-nl2br'

Vue.component('nl2br', Nl2br)
```

### (2) Local registration

https://vuejs.org/v2/guide/components.html#Local-Registration

```vue
// MyComponent.vue

<template>
  <nl2br tag="p" :text="`myLine1\nmyLine2`" />
</template>

<script>
import Nl2br from 'vue-nl2br'

export default {
  name: 'MyComponent',
  components: {
    Nl2br,
  },
  // ...
}
</script>
```

## Props

- `tag`: HTML tag name which is passed to [createElement function](https://vuejs.org/v2/guide/render-function.html#createElement-Arguments)
  - Type: `String`
  - Required: true
- `text`: Text in the tag.
  - Type: `String`
  - Default: null
- `className`: HTML class name(s) 
  - Type: `String`
  - Required: false

Note: when `text` property is empty or null, it renders an empty tag. ex) `<p></p>`.

If you prefer to render nothing at all, use `v-if` directive:

```html
<nl2br v-if="myText" tag="p" :text="myText" />
``` 

## License

[MIT](https://opensource.org/licenses/MIT)
