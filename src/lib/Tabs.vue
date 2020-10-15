<template>
  <div class="dy-tabs">
    <div class="dy-tabs-nav" ref="container">
      <div
          class="dy-tabs-nav-item"
          v-for="(t,index) in titles"
          :ref="el=>{if (el) navItems[index] =el}"
          :key="index"
          @click="select(t)"
          :class="{selected:t===selected}">{{ t }}</div>
      <div class="dy-tabs-nav-indicator" ref="indicator"></div>
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
import {computed,ref,onMounted, onUpdated} from 'vue'

export default {
  props:{
    selected:{
      type:String
    }
  },
  components: {Tab},
  setup(props, context) {
    const navItems=ref<HTMLDivElement[]>([])
    const indicator=ref<HTMLDivElement>(null)
    const container=ref<HTMLDivElement>(null)
    const x=()=>{
      const divs=navItems.value
      const result=divs.filter(div=>div.classList.contains('selected'))[0]
      const { width }=result.getBoundingClientRect()
      indicator.value.style.width=  width+'px'
      const {left:left1}=container.value.getBoundingClientRect()
      const {left:left2}=result.getBoundingClientRect()
      const left=left2-left1
      indicator.value.style.left=left+'px'
    }
    console.log(container.value);
    onMounted(x)
    onUpdated(x)
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
    return {defaults, titles,current,select,navItems,indicator,container};
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
    position: relative;
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
    &-indicator {
      position: absolute;
      height: 3px;
      background: $blue;
      left: 0;
      bottom: -1px;
      width: 100px;
    }
  }
  &-content {
    padding: 8px 0;
    &-item {
      display: none;
      &.selected {
        display: block;
      }
    }
  }
}
</style>