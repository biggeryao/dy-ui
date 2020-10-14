<template>
  <Button @click="toggle">toggle</Button>
  <Dialog
      v-model:visible="x"
      :close-on-click-overlay="false"
      :ok="f1"
      :cancel="f2"
  />

</template>


<script lang="ts">
import Dialog from '../lib/Dialog.vue';
import Button from '../lib/Button.vue';
import {ref} from 'vue'
export default {
  components: {
    Dialog, Button
  },
  setup(props,context){
    const x=ref(false)
    const toggle=()=>{
      x.value=!x.value
    }
    const f1=()=>{
      return false
    }
    const f2=()=>{
    }
    return {
      x,toggle,f1,f2
    }
  }
};
</script>
