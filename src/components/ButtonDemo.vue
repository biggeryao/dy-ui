<template>
  <div>
    <Button
      @click="a"
    @focus="a"
    @mouseover="a"
>123</Button>
  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
export default {
  components:{Button},
  setup(){
    const a=()=>{

    }
    return{a}
  }

};
</script>