<template>
  <div>
    Tab示例
  <Tabs v-model:selected="x">
    <Tab title="导航1">内容一</Tab>
    <Tab title="导航2">内容2</Tab>
  </Tabs>
  </div>
</template>

<script lang="ts">
import Tab from '../lib/Tab.vue'
import Tabs from  '../lib/Tabs.vue'
import {
  ref
} from 'vue'
export default {
  components:{Tabs,Tab},
  setup() {
    const x = ref('导航1')
    return {
      x
    }
  }
}
</script>