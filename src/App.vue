<template>
  <div>
    <demo01></demo01>
    <todoList></todoList>
  </div>
</template>

<script>
  import demo01 from "./components/demo01.vue"
  import todoList from "./components/todoList.vue"
  export default {
    components:{
      demo01,
      todoList
    }
  }
</script>

<style lang="less" scoped>

</style>