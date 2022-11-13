<template>
  <q-page class="q-pt-md" padding>
    <q-card-section >
      <h4>🔍Plan to do</h4>
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <div>
          <div class="row">
          <div class="col-6"><q-input color="dark" v-model="todo" type="text" label="list" /></div>
        </div>
        <div class="row">
          <div class="col-3"><q-input color="dark" v-model="date" type="date" /></div><br>
          <div class="col-3"><q-input color="dark" v-model="time" type="time" /></div>
        </div>
        </div>
        <div>
          <q-btn label="Submit" type="submit" color="dark" />
          <q-btn label="Reset" type="reset" color="dark" flat class="q-ml-sm" />
        </div>
      </q-form> 
    </q-card-section>
    <q-card-section>
      <h4>🚀To do list</h4>
        <TodoList></TodoList>
    </q-card-section>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import TodoList from "../components/TodoList.vue";
import { useTodoStore } from "../stores/todoList";
export default defineComponent({
  name: "IndexPage",
  components:{
    TodoList
  },
  data(){
    return{
      todo:"",
      date:"",
      time:"",
      todolist:[],
      store: useTodoStore(),
    }
    
  },
  methods:{
    onReset(){
      this.todo = '';
      this.date = '';
      this.time = '';
    },
    onSubmit(){
      this.todolist = [this.todo,this.date,this.time]
      this.store.addToDo(this.todolist)
      console.log(`🥓Todolist:`,this.store.todoList);
      this.onReset()      
    }
  }
});
</script>
