<template>
  <div class="container column">
    <app-form @sendInfo='sendInfo'></app-form>

    <div class="card card-w70">

      <app-title :title='title'></app-title>

      <app-ava :link="link"></app-ava>

      <app-discr :subtitle="subtitle"></app-discr>

      <app-text :text="text"></app-text>

     <first-word v-if="isFull"></first-word>
      
    </div> 
  </div>
  <div class="container">
    <p>
      <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
    </p>
    <app-loader v-if="loading"></app-loader>
    <app-comments v-if="onCommit" :comments='comments'></app-comments>
  </div>
</template>

<script>
import AppTitle from './AppTitle.vue'
import AppAva from './AppAva.vue'
import AppDiscr from './AppDiscr.vue'
import AppText from './AppText.vue'
import FirstWord from './FirstWord.vue'
import AppForm from './AppForm.vue'
import AppComments from './AppComments.vue'
import AppLoader from './AppLoader.vue'
import axios from 'axios'
export default {
  data(){
    return {
      title:'',
      text:'',
      subtitle:'',
      onCommit:false,
      loading:false,
      link: '',
      comments:[]    }
  },
  components:{AppTitle, AppAva, AppDiscr, AppText, FirstWord, AppForm,AppComments,AppLoader},
  methods:{
 
   loadComments() {
     this.loading=true
     setTimeout(async () =>{
try {
        const {data}=await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
   if (!data) {
     throw new Error('Список комментариев пуст')
   }
   this.comments= Object.keys(data).map(key=>{
     return {
       id:key,
       ...data[key]
     }
   })
   this.loading=false
   if (!this.onCommit) return this.onCommit=true
      } catch (e) {
        this.alert={
          type:'danger',
          title:'Ошибка',
          text:e.message
        }
        this.loading=false
        console.log(e.message)
      }
     }, 1500)
},
sendInfo(textArea,selected){
if (selected==='title') {this.title=textArea}
else if (selected==='subtitle') {this.subtitle=textArea}
else if (selected==='avatar') {this.link=textArea}
else if (selected==='text') { this.text=textArea}
else alert('Выберите тип блока')
}},
  computed:{
    isFull(){
      if (this.title.length ===0&&this.subtitle.length ===0&&this.text.length ===0&&this.link.length ===0)
 return true  
      return false
      }
    }
  } 
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
