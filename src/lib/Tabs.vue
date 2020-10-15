<template>
  <div class="dy-tabs">
    <div class="dy-tabs-nav">
      <div
          class="dy-tabs-nav-item"
          v-for="(t,index) in titles"
          :key="index"
          @click="select(t)"
          :class="{selected:t===selected}">{{ t }}</div>
    </div>
    <div class="dy-tabs-content">
      <component class="dy-tabs-content-item"
                 v-for="(c,index) in defaults" :key="index"
                 :class="{selected:c.props.title===selected}"
                  :is="c" />
    </div>
  </div>
</template>

<script lang="ts">
import Tab from './Tab.vue';
import {computed} from 'vue'

export default {
  props:{
    selected:{
      type:String
    }
  },
  components: {Tab},
  setup(props, context) {
    const defaults = context.slots.default();
    defaults.forEach((tag) => {
      if (tag.type !== Tab) {
        throw new Error('Tabs子组件必须是Tab');
      }
    });
    const titles = defaults.map((tag) => {
      return tag.props.title;
    });
    const current=computed(()=>{
      return defaults.filter((tag)=>{
        return tag.props.title===props.selected
      })[0]
    })
    const select=(title:string)=>{
      context.emit('update:selected',title)
    }
    return {defaults, titles,current,select};
  }
};
</script>
<style lang="scss">
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;
.dy-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;
      &:first-child {
        margin-left: 0;
      }
      &.selected {
        color: $blue;
      }
    }
  }
  &-content {
    padding: 8px 0;
    &-item {
      display: none;
      &.selected{
        display: block;
      }
    }
  }
}
</style>