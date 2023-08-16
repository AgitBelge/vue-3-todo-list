<template>
<div>
  <form @submit.prevent="addTodo">
  <div class="content">
    <h1>intro to vue 3</h1>
    <div class="field">
      <label class="label">Todo</label>
      <div class="control">
        <input class="input" v-model="todo" type="text" placeholder="ödev yap">
      </div>
    </div>
    <button type="submet" class="button is-warning">ekle</button>
  </div>
 </form>
 <div v-for="todo in todos" :key="todo.id" class="card my-5 mx-5">
  <div class="card-content">
    <div class="media">
      <div class="media-content">
        <p @click="done(todo)" :class="{done :todo.done}" class="title is-4 cursor">{{todo.content}}</p>
        <p class="subtitle is-6">{{ todo.done }}</p>
      </div>
    </div>
  </div>
</div>
</div>
</template>
<script>
import {ref} from 'vue'
export default{
  setup(){
    const todo = ref('')
    const todos = ref([])
    function addTodo(){
      todos.value.push({
        done:false,
        content:todo.value,
        id:Date.now()
      })
      todo.value = ''
    }
    function done(todo){
      todo.done =  !todo.done
    }
    return{
      todo,
      todos,
      addTodo,
      done
    }
  }
}
</script>
<style lang="scss">
.done{
  text-decoration: line-through;
}
.cursor{
  cursor: pointer;
}
</style>
