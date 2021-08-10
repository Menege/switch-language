<template>
  <div class="container">
    <app-alert
    v-if="alert"
text="Тот самый текст"
title="ССССССССССССВАП"
type=" warning"
closable
@close="alert=false"
    ></app-alert>
    <div class="card">
<button 

class="btn primary" @click="toogleAlert">{{ alert ?'скрыть':'показать'}} сообщение</button>
    </div>
  </div>
</template>
 
<script>
import AppAlert from './components/AppAlert.vue'
export default {
  data(){return{
    alert:false
  }},
  methods:{
toogleAlert(){
  this.alert=!this.alert
}
  },
  
components:{AppAlert}
}
</script>

