<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title" />
    <button type="submit" class="add">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ""
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        };

        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input {
  width: 400px;
}

.add {
  background-color: rgb(57, 204, 44);
  width: 100px;
  height: 30px;
  border-radius: 5px;
  border-color: rgb(24, 26, 26);
  border-width: 2px;
}
</style>