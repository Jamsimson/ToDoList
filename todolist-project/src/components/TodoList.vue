<template>
  <q-page class="q-pt-md">
    <q-list bordered separator>
      <q-item clickable v-ripple v-for="todo in store.todoList" :key="todo.id">
        <q-item-section :class="{ completeClass: todo.completed }">
          ✏️{{ todo.item[0] }} : {{ todo.item[1] }} :
          {{ todo.item[2] }}</q-item-section
        >
        <q-item-section avatar>
          <q-icon
            name="check"
            color="green"
            @click.stop="store.toggleCompleted(todo.id)"
          />
        </q-item-section>
        <q-item-section avatar>
          <q-icon
            name="delete"
            color="red"
            @click="store.deleteToDo(todo.id)"
          />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
import { useTodoStore } from "../stores/todoList";
export default {
  name: "TodoList",
  data() {
    return {
      store: useTodoStore(),
    };
  },
};
</script>

<style>
.completeClass {
  text-decoration: line-through;
}
</style>
