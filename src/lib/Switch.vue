<template>
    <button class="dy-switch" :class="{'dy-checked':value}" @click="toggle">
      <span ></span>
    </button>
</template>

<script lang="ts">

export default {
  props:{
    value:Boolean
  },
  setup(props,context){ 
    const toggle=()=>{
        context.emit('update:value',!props.value)
    }
    return{toggle}
  }
}
</script>

<style lang="scss" >
$h: 22px;
$h2: $h - 4px;
.dy-switch {
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
  transition: left 250ms;
}
.dy-switch.dy-checked{
  background-color: blue;
}
.dy-switch.dy-checked span{
  left: calc(100% - #{$h2} - 2px);
}
.dy-switch:focus{
  outline: none;
}
.dy-switch:active{
  > span {width: $h2 + 4px;}
}
.dy-switch.dy-checked:active{
  > span {width: $h2 + 4px; margin-left: -4px;}
}
</style>
