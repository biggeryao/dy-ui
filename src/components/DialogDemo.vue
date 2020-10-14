<template>
  <Button @click="toggle">toggle</Button>
  <Dialog
      v-model:visible="x"
      :close-on-click-overlay="false"
      :ok="f1"
      :cancel="f2"
      :title="title">
    <div>
      <p>123</p>
      <p>456</p>
    </div>
  </Dialog>


</template>


<script lang="ts">
import Dialog from '../lib/Dialog.vue';
import Button from '../lib/Button.vue';
import {ref} from 'vue'
export default {
  components: {
    Dialog, Button
  },
  setup(){
    const title='提示'
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
      x,toggle,f1,f2,title
    }
  }
};
</script>
