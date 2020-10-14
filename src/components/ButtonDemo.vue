<template>
  <div>
    <Button
      @click="a"
    @focus="a"
    @mouseover="a"
    size="small">123</Button>
  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
export default {
  components:{Button},
  setup(){
    const a=()=>{
      console.log(1);
    }
    return{a}
  }

};
</script>