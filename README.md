# vue-layout-broker

[![npm](https://img.shields.io/npm/v/vue-layout-broker.svg) ![npm](https://img.shields.io/npm/dm/vue-layout-broker.svg)](https://www.npmjs.com/package/vue-layout-broker)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

Component provides the way to implement dynamic layout in a Vue app

## Table of contents

- [Installation](#installation)
- [Usage](#usage)
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

# Example

[Working example](https://codesandbox.io/s/84x24pkn49)

---

## License

[MIT](http://opensource.org/licenses/MIT)
