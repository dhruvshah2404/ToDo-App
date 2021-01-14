/* eslint-disable no-var */
<template>
  <div class="form">
    <input v-model="input" type="text" class="input" placeholder="Start Typing ..." @keyup.enter="addTodo">
    <button class="main-btn" @click="addTodo">
      Add To Do
    </button>
    <div>
      <h2>Today's ToDo</h2>
      <hr>
    </div>
    <div class="todo-container">
      <ul v-if="todos.length >=1">
        <p class="extra">
          (Click on todo to complete it)
        </p>
        <li v-for="todo in todos" :key="todo.id" :class="{completed: todo.completed}" @click="uncomplete(todo)">
          {{ todo.title }}
        </li>
      </ul>
      <div class="footer">
        <p v-if="uncompletedTodos.length >= 1" class="extra">
          {{ uncompletedTodos.length }} task left
        </p>
        <p v-if="todos.length === 0" class="completed-txt">
          You have completed all task!!!
        </p>
        <button v-if="completedTodos.length >=1" class="item-btn" @click="todos = []">
          clear completed
        </button>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  data () {
    return {
      input: '',
      todos: []
    }
  },
  computed: {
    uncompletedTodos () {
      return this.todos.filter((t) => {
        return !t.completed
      })
    },
    completedTodos () {
      return this.todos.filter((t) => {
        return t.completed
      })
    }
  },
  methods: {
    completed (item) {
      item.completed = !item.completed
    },
    uncomplete (item) {
      item.completed = !item.completed
    },
    addTodo () {
      const newtodo = this.input.trim()
      if (!newtodo) {
        alert('Please add a task')
        return
      }
      this.todos.push({
        title: newtodo,
        completed: false
      })
      this.input = ''
    }
  }
}
</script>

<style lang='less'>
@border : #77a4b9;
hr {
  border-color: @border;
}
ul{
  padding: 0;
  list-style: none;
}
p.completed-txt{
  margin: 20px;
  color: #69828e;
  font-size: 20px;
  font-weight: bold;
}
p.extra{
font-size: 17px;
margin-top: 10px;
}
li{
  border: 2px solid @border;
  width: 95%;
  margin: auto;
  padding: 15px 10px;
  height: 55px;
  align-items: center;
  display: flex;
  border-radius: 10px;
  margin-top: 20px;
  justify-content: space-between;
  font-size: 20px;
  cursor: pointer;
}
li.completed{
  text-decoration: line-through;
  color:@border
}
.input {
  width: 100%;
  height: 55px;
  background: transparent;
  color: white;
  border: 2px solid @border;
  padding: 0 10px;
  border-radius: 10px;
  margin-top: 10px;
  font-size: 20px;
}
::placeholder {
    color: white;
  }
button.main-btn{
  width: 100%;
  font-size: 20px;
  font-weight: bold;
  height: 55px;
  margin-top: 10px;

}
button.item-btn{
  margin-top: 10px;
  padding: 4px 8px;
}
button{
  background: #77a4b9 !important;
  border-radius: 10px;
  border: none;
  outline: none;
  color: white;
}

</style>
