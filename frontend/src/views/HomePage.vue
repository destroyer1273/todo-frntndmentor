<script setup>
import { ref, watch } from "vue";

const userTodos = ref([
  {id: 1, text: 'Complete online Javascript course', completed: true},
  {id: 2, text: 'Jog around the park 3x', completed: false},
  {id: 3, text: '10 minutes meditation', completed: false},
  {id: 4, text: 'Read for 1 hour', completed: false},
  {id: 5, text: 'Pick up groceries', completed: false},
  {id: 6, text: 'Complete Todo App on Frontend Mentor', completed: false},
]);
const newTodo = ref({});
newTodo.value.completed = false;
const addTodo = () => {
    if(newTodo.value.text != "" && newTodo.value.text != undefined) {
        userTodos.value.push({text: newTodo.value.text, completed: newTodo.value.completed});
    }
};
const whatToDisplay = ref();
const clearCompleted = () => {
    userTodos.value = userTodos.value.filter(todo => !todo.completed);
};
const displayWhat = ref("All");
watch(displayWhat, (newValue, oldValue) => {
    console.log(newValue);
});
const activeStyle = {
    color: '#2b3ff5',
};
const inactiveStyle = {
    color: '#8b8b8b',
};


</script>

<template>
  <div class="background">
    <div class="main">
        <div class="main__header">
          <div class="main__header__cont1">
            <h1>TODO</h1>
            <img src="/images/icon-sun.svg" alt="Солнышко">
          </div>
          <form class="main__header__form" @submit.prevent="addTodo">
            <input v-model="newTodo.completed" type="checkbox" class="radio-input">
            <input v-model="newTodo.text" type="text" placeholder="Create a new todo..." class="text-input">
          </form>
        </div>
        <div class="main_bottom">
          <div v-for="item in userTodos" class="todo-item">
            <input type="checkbox" class="todo-radio" :checked="item.completed" v-model="item.completed">
            <p>{{ item.text }}</p>
          </div>
          <div class="control-panel">
            <p class="indicator">{{ userTodos.length }} item(s) left</p>
            <div class="control-panel__toggle">
              <a class="control-toggle-a" @click="displayWhat = 'All'" :style="displayWhat === 'All' ? activeStyle : inactiveStyle">All</a>
              <a class="control-toggle-a" @click="displayWhat = 'Active'" :style="displayWhat === 'Active' ? activeStyle : inactiveStyle">Active</a>
              <a class="control-toggle-a" @click="displayWhat = 'Completed'" :style="displayWhat === 'Completed' ? activeStyle : inactiveStyle">Completed</a>
            </div>
            <a class="clear" @click="clearCompleted">Clear completed</a>
          </div>
        </div>
    </div>
  </div>
</template>

<style scoped>
.indicator {
  color: #8b8b8b;
  font-size: 14px;
}

.control-toggle-a {
    cursor: pointer;
}
.control-toggle-a:hover {
    color: #FFF;
}
.clear {
  color: #8b8b8b;
  font-size: 14px;
  transition: color 0.3s ease-in-out;
  cursor: pointer;
}
.clear:hover {
    color: #FFF;
}
.control-panel {
  background-color: #2e2c3a;
  display: flex;
  color: #FFF;
  padding: 16px 30px;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 0.5px 2px 0 #e0e0e0;
}
.control-panel__toggle a {
  margin-right: 10px;
  color: #a1a1a1;
  font-size: 17px;
}
.background {
    width: 100%;
    height: 100%;
    background-image: url("/images/bg-desktop-dark.jpg");
    background-size: 100% auto;
    background-repeat: no-repeat;
    padding-top: 50px;
    background-color: #000;
}
.main {
    max-width: 500px;
    margin: 0 auto;
}
.main__header {
  margin-bottom: 20px;
}
.main__header__cont1 {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 30px;
}
.main__header__cont1 h1 {
    color: #FFF;
}
.main__header__cont1 img {
  align-self: center;
  object-fit: contain;
}
.main__header__form {
  background-color: #2e2c3a;
  padding: 16px 40px;
  padding-left: 60px;
  border-radius: 4px;
}
.text-input {
  background-color: inherit;
  outline: none;
  border: none;
  color: #fff;
}
.radio-input {
  appearance: none;
  position: relative;
  cursor: pointer;
}
.radio-input::before {
  content: '';
  width: 20px;
  height: 20px;
  border: 1px solid #8c8c8c;
  position: absolute;
  border-radius: 80px;
  left: -45px;
  top: -16px;
}
.radio-input:checked::before {
    content: "✓";
    text-align: center;
    color: #FFF;
    background: linear-gradient(to bottom right, blue, pink);
    border: none;
    width: 21px;
    height: 21px;
}
.todo-item  {
  display: flex;
  background-color: #2e2c3a;
  padding: 16px 40px;
  padding-left: 60px;
  box-shadow: 0 0.5px 2px 0 #e0e0e0;
}
.todo-item p {
  color: #cacaca;
  font-weight: 400;
  font-size: 15px;
}
.todo-radio {
  appearance: none;
  position: absolute;
}
.todo-radio::before {
  content: '';
  width: 20px;
  height: 20px;
  border: 1px solid #8c8c8c;
  position: absolute;
  border-radius: 80px;
  left: -45px;
  top: -1px;
}
.todo-radio:checked::before {
    content: "✓";
    text-align: center;
    color: #FFF;
    background: linear-gradient(to bottom right, blue, pink);
    border: none;
    width: 21px;
    height: 21px;
}
</style>
