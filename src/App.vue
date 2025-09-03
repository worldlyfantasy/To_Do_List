<template>
  <div class="todo-app">
    <div class="title">待办清单</div>
    
    <div class="todo-form">
      <input 
        v-model="newTodo" 
        @keyup.enter="addTodo"
        class="todo-input" 
        type="text" 
        placeholder="Add an item"
      >
      <div class="todo-button" @click="addTodo">Add Todo</div>
    </div>

    <div class="todo-list">
      <div 
        v-for="(todo, index) in todos" 
        :key="todo.id"
        class="todo-item"
        :class="{ 'deleted': todo.deleted }"
      >
        <span 
          class="todo-text"
          :class="{ 'strikethrough': todo.deleted }"
        >
          {{ todo.text }}
        </span>
        <button 
          class="delete-btn" 
          @click="deleteTodo(index)"
          :disabled="todo.deleted"
        >
          {{ todo.deleted ? '已删除' : '删除' }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

interface Todo {
  id: number
  text: string
  deleted: boolean
}

const newTodo = ref<string>('')
const todos = reactive<Todo[]>([])
let nextId = 1

function addTodo(): void {
  const text = newTodo.value.trim()
  if (text === '') {
    alert('请输入待办事项内容！')
    return
  }
  
  todos.push({
    id: nextId++,
    text: text,
    deleted: false
  })
  
  newTodo.value = ''
}

function deleteTodo(index: number): void {
  const todo = todos[index]
  if (todo.deleted) return
  
  // 添加删除线效果
  todo.deleted = true
  
  // 3秒后完全移除元素
  setTimeout(() => {
    const todoIndex = todos.findIndex((t: Todo) => t.id === todo.id)
    if (todoIndex > -1) {
      todos.splice(todoIndex, 1)
    }
  }, 3000)
}
</script>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(to right, #1e90ff, #8a2be2);
}

.todo-app{
  width: 96%;
  min-height: 500px;
  background-color: white;
  border-radius: 10px;
  margin-left: 2%;
  margin-top: 40px;
  padding-top: 30px;
  padding-bottom: 30px;
  box-sizing: border-box;
}

.title{
  font-size: 30px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 20px;
}

.todo-form {
  display: flex;
  justify-content: center;
  margin: 30px auto 30px auto;
  border-radius: 25px;
  padding: 3px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
}

.todo-input{
  border: none;
  outline: none;
  width: 60%;
  height: 60px;
  line-height: 60px;
  border-radius: 20px 0 0 20px;
  padding-left: 15px;
  font-size: 18px;
  border: 1px solid rgba(30, 144, 255, 0.6);
  transition: all 0.3s ease;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  color: #333;
}

.todo-input::placeholder {
  color: rgba(0, 0, 0, 0.6);
}

.todo-button{
  display: flex;
  justify-content: center; /* 水平居中 */
  align-items: center;     /* 垂直居中 */

  cursor: pointer;
  user-select: none;

  color: white;
  width: 100px;
  height: 62px;
  border: 1px solid rgba(30, 144, 255, 0.6);
  border-radius: 0 20px 20px 0;
  text-align: center;

  background: linear-gradient(to right, #1e90ff, #8a2be2);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  transition: all 0.3s ease;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

/* 当鼠标悬停在按钮上时，同时影响输入框 */
.todo-form:hover .todo-input,
.todo-form:hover .todo-button {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.15);
}

.todo-list {
  margin: 0 auto;
  width: 67%;

}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f8f9fa;
  margin-bottom: 10px;
  padding: 15px 20px;
  border-radius: 8px;
  border-left: 4px solid #1e90ff;
  transition: all 0.3s ease;
}

.todo-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.15);
  background-color: #ffffff;
  border-left-color: #007bff;
}

.todo-item:active {
  transform: translateY(1px);
  box-shadow: 0 3px 6px rgba(0,0,0,0.1);
  background-color: #f1f3f5;
  border-left-color: #0056b3;
}

.todo-item.deleted {
  opacity: 0.6;
  background-color: #f8f9fa;
}

.todo-text {
  user-select: none;
  flex: 1;
  font-size: 16px;
  color: #333;
  transition: all 0.3s ease;
}

.todo-text.strikethrough {
  text-decoration: line-through;
  opacity: 0.6;
  color: #6c757d;
}

.delete-btn {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.3s ease;
}

.delete-btn:hover {
  background-color: #c82333;
  transform: scale(1.05);
}

.delete-btn:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
  transform: none;
}
</style>
