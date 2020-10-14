<template>
  <div>
    <Dialog/>
    <header>标题</header>
    <mian>
      <p>第一行字</p>
      <p>第二行字</p>
    </mian>
    <footer>
      <Button>取消</Button>
      <Button>确定</Button>
    </footer>
  </div>
</template>

<script lang="ts">
  import Dialog from '../lib/Dialog.vue'
  import Button from '../lib/Button.vue';
export default {
    components:{Dialog,Button}
  }
</script>