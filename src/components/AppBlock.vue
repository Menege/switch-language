<template>
  <div class="container">
    <app-alert
    v-if="alert"
text="Тот самый текст"
title="ССССССССССССВАП"
@close="alert=false"
 
    ></app-alert>
    <div class="card">
<button 

class="btn primary" @click="toogleAlert">{{ alert ?'скрыть':'показать'}} сообщение</button>
    </div>
  </div>
</template>
 
<script>
import AppAlert from './AppAlert.vue'
import alertMixin from './AlertMixin'

export default {
components:{AppAlert},
mixins:[
  alertMixin
]

}
</script>

