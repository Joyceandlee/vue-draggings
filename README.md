vuedrag

## Usage

``` javascript
//main.js

import VueDND from 'vue_drag'

Vue.use(VueDND)
```

``` html
<!--your.vue-->
<script>
export default {
  data () {
    return {
        colors: [{
            text: "Aquamarine"
        }, {
            text: "Hotpink"
        }, {
            text: "Gold"
        }, {
            text: "Crimson"
        }, {
            text: "Blueviolet"
        }, {
            text: "Lightblue"
        }, {
            text: "Cornflowerblue"
        }, {
            text: "Skyblue"
        }, {
            text: "Burlywood"
        }]
    }
  },
  /* if your need multi drag
  mounted: function() {
      this.colors.forEach((item) => {
          Vue.set(item, 'isComb', false)
      })
  } */
}
</script>

<template>
  <div class="color-list">
      <div
          class="color-item"
          v-for="color in colors" v-dragging="{ item: color, list: colors, group: 'color' }"
          :key="color.text"
      >{{color.text}}</div>
  </div>
</template>
```

# API

`v-dragging="{ item: color, list: colors, group: 'color' }"`

#### Arguments:

 * `{item} Object`
 * `{list} Array`
 * `{group} String`
 * `{comb} String`

 `group` is unique key of dragable list.

 `comb` use for multi drag

#### Example

``` html
<!-- Vue2.0 -->
<div class="color-list">
    <div
        class="color-item"
        v-for="color in colors" v-dragging="{ item: color, list: colors, group: 'color' }"
        :key="color.text"
    >{{color.text}}</div>
</div>

<!-- Vue1.0 -->
<div class="color-list">
    <div
        class="color-item"
        v-for="color in colors" v-dragging="{ item: color, list: colors, group: 'color', key: color.text }"
        track-by="text"
    >{{color.text}}</div>
</div>
```

#### Event

``` html
<div class="color-list">
    <div
        class="color-item"
        v-for="color in colors" v-dragging="{ item: color, list: colors, group: 'color', otherData: otherData, comb: 'isComb' }"
        :key="color.text"
    >{{color.text}}</div>
</div>
```

``` javascript
export default {
  mounted () {
    this.$dragging.$on('dragged', ({ value }) => {
      console.log(value.item)
      console.log(value.list)
      console.log(value.otherData)
    })
    this.$dragging.$on('dragend', () => {

    })
  }
}
```


