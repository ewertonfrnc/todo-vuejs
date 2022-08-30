<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo-input"> Qual a próxima tarefa? </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="label"
    />
    <button type="submit">Adicionar</button>
  </form>
</template>

<script>
export default {
  methods: {
    onSubmit() {
      if (this.label === undefined || this.label === '') return
      this.$emit('todo-added', this.label)
    },
    data() {
      return {
        label: '',
      }
    },
  },
}
</script>
