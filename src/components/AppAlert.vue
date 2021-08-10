<template>
  <div class="alert" :class="type">
      <p class="alert-title"> {{title}} </p>
      <p> {{text}} </p>
      <button class="btn" :class="type" v-if="closable" @click="$emit('close')">Закрыть</button>
  </div>
</template>

<script>
export default {
    props:{
title:String,
text  :String,
closable:{
type:Boolean,
required:false,
default:false
},
type: {
    type:String,
    required:false,
    default:'primary',
    validator (val){
        return ['primary','danger', 'warning'].includes(val)
    }
}
    },
    emits:['close']
        

}
</script>

<style>

</style>