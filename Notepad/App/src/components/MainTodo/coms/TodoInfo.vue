<template>
  <div class="todo-info">
    <span class="total">还有{{ total }}件事未完成</span>
    <div class="tabs">
      <a v-for="(item, index) in states" :key="index" @click="toggleState(item)" :class="state == item ? 'actived' : ''">{{item}}</a>
    </div>
    <button class="clear" @click="clearCompleted">清除已完成事项</button>
  </div>
</template>

<script>
export default {
  name: 'TodoInfo',
  props: {
    total: Number
  },
  data() {
    return {
      states: ['所有', '未完成', '已完成'],
      state: '所有'
    }
  },
  methods: {
    toggleState(state) {
      this.state = state
      this.$emit('toggleState', state)
    },
    clearCompleted() {
      this.$emit('clearCompleted')
    }
  }
}
</script>

<style scoped>
.todo-info {
  display: flex;
  justify-content: space-between;
  font-weight: 400;
  padding: 5px 10px;
  line-height: 30px;
  border-top: 1px solid rgba(0, 0, 0, .1);
}
.total {
  color: rgb(254, 67, 101);
}
.tabs {
  display: flex;
  justify-content: space-between;
  width: 200px;
}
a {
  border: 1px solid rgb(252, 157, 154);
  border-radius: 5px;
  padding: 0 10px;
  cursor: pointer;
}
a.actived {
  background-color: rgb(252, 157, 154);
  color: #fff;
}
.clear {
  padding: 0 10px;
  background-color: rgb(131, 175, 155);
  border-radius: 5px;
  color: #fff;
  appearance: none;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>