<template>
  <div>
    Tab示例
  <Tabs>
    <Tab title="导航一">内容一</Tab>
    <Tab title="导航二">内容一</Tab>
  </Tabs>
  </div>
</template>

<script lang="ts">
import Tab from '../lib/Tab.vue'
import Tabs from  '../lib/Tabs.vue'
export default {
  components:{Tabs,Tab}
}
</script>