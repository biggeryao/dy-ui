<template>
  <button :class="{checked:checked}" @click="toggle">
    <span ></span>
  </button>
</template>

<script lang="ts">
import {ref} from 'vue'
export default {
  setup(){
    const checked=ref(true)
    const toggle=function (){
      checked.value=!checked.value
    }
    return{checked,toggle}
  }
}
</script>

<style lang="scss" scoped>
$h: 22px;
$h2: $h - 4px;
button {
  height: $h;
  width: $h*2;
  border: none;
  background-color: gray;
  border-radius: $h/2;
  position: relative;
}

span {
  position: absolute;
  top: 2px;
  left: 2px;
  height: $h2;
  width: $h2;
  background: white;
  border-radius: $h2/2;
}
button.checked{
  background-color: blue;
}
button.checked span{
  left: calc(100% - #{$h2} - 2px);
}

</style>
