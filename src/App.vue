<template>
  <div>
    <h1>Lista de tarefas</h1>

    <to-do-form @todo-added="addToDo" />

    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item :id="item.id" :label="item.label" :done="item.done" />
      </li>
    </ul>
  </div>
</template>

<script>
import uniqueid from 'lodash.uniqueid'

import ToDoForm from './components/ToDoForm.vue'
import ToDoItem from './components/ToDoItem.vue'

export default {
  name: 'App',
  components: {
    ToDoForm,
    ToDoItem,
  },
  data() {
    return {
      ToDoItems: [
        { id: uniqueid('todo-'), label: 'Aprender Vue', done: false },
        {
          id: uniqueid('todo-'),
          label: 'Criar um projeto com o CLI',
          done: true,
        },
        { id: uniqueid('todo-'), label: 'Beber 2 litros de água', done: true },
        {
          id: uniqueid('todo-'),
          label: 'Fazer uma lista de tarefas',
          done: false,
        },
      ],
    }
  },
  methods: {
    addToDo(toDoLabel) {
      this.ToDoItems.push({
        id: uniqueid('todo-'),
        label: toDoLabel,
        done: false,
      })
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
