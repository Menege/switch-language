
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
    <app-block></app-block>
  </div>
</template>
 
<script>
import AppAlert from './components/AppAlert.vue'
import AppBlock from './components/AppBlock.vue'
import alertMixin from './components/AlertMixin'
export default {
components:{AppAlert, AppBlock},
mixins:[
  alertMixin
]
}
</script>