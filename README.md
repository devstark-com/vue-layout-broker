# vue-layout-broker

[![npm](https://img.shields.io/npm/v/vue-layout-broker.svg) ![npm](https://img.shields.io/npm/dm/vue-layout-broker.svg)](https://www.npmjs.com/package/vue-layout-broker)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

Component provides the way to implement dynamic layout in a Vue app

## Table of contents

- [Installation](#installation)
- [Usage](#usage)
- [Interface](#interface)
- [Example](#example)

# Installation

`npm install --save vue-layout-broker`

# Usage

In routes config
```js
// ...

const routes = [
  {
    name: 'some-route',
    path: '/some-route',
    component: SomePage,
    meta: {
      layout: 'FirstLayout'
    }
  },
  {
    name: 'some-another-route',
    path: '/some-another-route',
    component: SomeAnotherPage,
    meta: {
      layout: 'SecondLayout'
    }
  },

// ...
```

In your App.vue
```html
<template>
  <div id="app">
    <LayoutBroker
      :layouts="layouts"
      :current="$route.meta.layout"
    />
  </div>
</template>

<script>
import LayoutBroker from 'vue-layout-broker'

import FirstLayout from '@/path/to/first/layout'
import SecondLayout from '@/path/to/second/layout'
const layouts = {
  FirstLayout,
  SecondLayout
}

export default {
  name: 'App',
  components: {
    LayoutBroker
  },
  data () {
    return {
      layouts
    }
  }
}
</script>
```

# Interface

## Props

| Props              | Required | Type            | Default            | Description  |
| ------------------ | -------- | --------------- | ------------------ | -------------|
| layouts            | false    | Object          | `{}`               | Layouts components list |
| current            | false    | String          | `null`             | Current layout component name |
| layoutClasses      | false    | [Object, Array] | `['layout']`       | Layout classes to be bound in [array](https://vuejs.org/v2/guide/class-and-style.html#Array-Syntax) or [object](https://vuejs.org/v2/guide/class-and-style.html#Object-Syntax) notation |
| pageWrapperClasses | false    | [Object, Array] | `['page-wrapper']` | List of classes to be bound to `<router-view>` in array or object notation |

## Slots

Component provides two named slots `before-page` and `after-page` to inject content before or after `<router-view>`. Both slots have no any content by default.

# Example

[Working example](https://codesandbox.io/s/42m1lrj6l7)

---

## License

[MIT](http://opensource.org/licenses/MIT)
