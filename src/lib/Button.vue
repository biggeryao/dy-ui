<template>
  <div>
    <button v-bind="$attrs">
      <slot/>
    </button>
  </div>

</template>

<script lang="ts">
export default {
  inheritAttrs:false,
}
</script>

<style lang="scss" scoped>

</style>



