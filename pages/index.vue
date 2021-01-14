<template>
  <div class="body">
    <h2>Day 1 - ToDo List</h2>
    <todo />
  </div>
</template>
<script>
import todo from '@/components/todo'
export default {
  components: {
    todo
  },
  head () {
    return {
      title: 'ToDo List'
    }
  }
}
</script>

<style lang="less">
body{
  text-align: center;
  background-color: #2d3540;
  color: white;
  height: 100%;
  padding: 30px;
  max-width: 600px;
  margin: auto;
  h2{
    font-size: 30px;
    margin: 20px 0;
    ;
  }
}
</style>
