<template>
  <div>
      <h3>Todo</h3>
      <div class="todos">
        <div class="todo" v-for="todo in allTodos" :key="todo.id">
          {{ todo.title }}
          <div @click="deleteTodo(todo.id)">
            <span  class="iconify" data-icon="fluent:delete-16-filled" data-inline="false"></span>
          </div>
          
        </div>
      </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
    name:"Todo",
    methods:{
      ...mapActions(['fetchTodos', 'deleteTodo']),
    },
    computed:{
      ...mapGetters(['allTodos'])
    },
    created(){
      this.fetchTodos();
    }
}
</script>

<style scoped>
  .todos{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
  }
  .todo{
    border: 1px solid #ccc;
    background: #41b883;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;;
    cursor: pointer;
  }
  .iconify{
    position: absolute;
    bottom:10px;
    right: 10px;
    color:#fff;
    cursor: pointer;
  }
</style>>
