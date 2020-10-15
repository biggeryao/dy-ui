<template>
  <div>123</div>
</template>

<script lang="ts">
import Tab from './Tab.vue'
export default {
  components:{Tab},
  setup(props,context){
    const defaults=context.slots.default()
    defaults.forEach((tag)=>{
      if(tag.type!==Tab){
        throw new Error('Tabs子组件必须是Tab')
      }
    })
    return{defaults}
  }
}
</script>