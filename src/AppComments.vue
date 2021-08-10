<template>

    
 <div class="card">
      <h2>Комментарии</h2>
      <ul class="list" v-if="comments !==0">
        <li class="list-item" v-for='comment in comments' :key='comment.id'>
          <div>
            <p><strong>{{comment.email}}</strong></p>
            <small> {{comment.name}} </small>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
props:{comments:Array}
}
</script>

<style>

</style>