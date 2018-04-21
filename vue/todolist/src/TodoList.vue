<template>
<div>
  <div>
    <input type="text" v-model="inputValue">
    <button @click="hanleSubmit">提交</button>
      </div>
    <ul>
      <todo-item v-for="(item,index) in list" :key="index"
      :content="item" :index="index" @delete="hanleDelete">
      </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem'
export default {
  components: {
    'todo-item': TodoItem
  },
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    hanleSubmit () {
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    hanleDelete (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
