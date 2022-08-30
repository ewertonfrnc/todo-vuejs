<template>
  <form @submit.prevent="onSubmit">
    <h2 class="label-wrapper">
      <label for="new-todo-input" class="label__lg">
        Qual sua próxima tarefa?
      </label>
    </h2>

    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="label"
      class="input__lg"
    />
    <button type="submit" class="btn btn__primary btn__lg">Adicionar</button>
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
