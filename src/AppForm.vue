<template>
   <form class="card card-w30" @submit.prevent="sendInfo">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select v-model="selected">
          <option v-for="option in options" :value="option.value" :key="option.value">{{option.text}}</option>
        </select>
        
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea v-model="textArea" id="value" rows="3"></textarea>
      </div>

      <button class="btn primary" :disabled='isInput' >Добавить</button>
    </form>
</template>

<script>

export default {
    data(){
        return {
       selected:'title',
       textArea:'',
            options :[
                {text:'Заголовок', value:'title'},
                {text:'Подзаголовок', value:'subtitle'},
                {text:'Аватар', value:'avatar'},
                {text:'Текст', value:'text'},
            ]
        }
    },
    methods:{
        sendInfo(){
            this.$emit('sendInfo', this.textArea, this.selected)
this.textArea=''
        }
    },
    computed:{
        isInput(){
           
            if (this.textArea.length<3) return true
         return false
        }
    }
   

}

</script>

<style>

</style>