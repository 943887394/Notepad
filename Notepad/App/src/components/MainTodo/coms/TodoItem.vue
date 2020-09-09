<template>
  <div :class="['todo-item', todo.completed ? 'completed' : '']">
    <input type="checkbox" v-model="todo.completed">
    <label>{{todo.content}}</label>
    <button @click="delItem"></button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: Object
  },
  methods: {
    delItem() {
      this.$emit('del', this.todo.id)
    }
  }
}
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  font-size: 24px;
  border-top: 1px solid rgba(0, 0, 0, .1);
}
.todo-item:hover button::after {
  content: 'X';
  font-size: 24px;
  color: rgb(252, 157, 154)
}
.todo-item.completed label {
  color: #d9d9d9;
  text-decoration: line-through;
}
input {
  width: 50px;
  height: 30px;
  text-align: center;
  appearance: none;
  border: none;
  outline: none;
}
input::after {
  content: url('~images/UnChecked.jpg');
}
input:checked::after {
  content: url('~images/Checked.jpg');
}
label {
  flex: 1;
  transition: color 0.4s;
}
button {
  width: 40px;
  background-color: #fff;
  appearance: none;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>