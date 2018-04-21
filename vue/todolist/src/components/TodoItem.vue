<template>
<li class="item" @click="handleDelete">{{content}}</li>
</template>

<script>
export default {
  props: ['content', 'index'],
  methods: {
    handleDelete () {
      this.$emit('delete', this.index)
    }
  }
}
</script>
<!--有scoped的时候代表这个样式只对你当前的组件有效，如果不加就是全局的一个样式-->
<style scoped>
.item{
  color:green;
}
</style>
