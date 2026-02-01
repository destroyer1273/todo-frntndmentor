<script setup>
import { ref } from "vue";

const userTodos = ref([
  {text: 'Complete online Javascript course', completed: true},
  {text: 'Jog around the park 3x', completed: false},
  {text: '10 minutes meditation', completed: false},
  {text: 'Read for 1 hour', completed: false},
  {text: 'Pick up groceries', completed: false},
  {text: 'Complete Todo App on Frontend Mentor', completed: false},
]);
</script>

<template>
  <div class="background">
    <div class="main">
        <div class="main__header">
          <div class="main__header__cont1">
            <h1>TODO</h1>
            <img src="/images/icon-sun.svg" alt="Солнышко">
          </div>
          <form class="main__header__form">
            <input type="radio" class="radio-input">
            <input type="text" placeholder="Create a new todo..." class="text-input">
          </form>
        </div>
        <div class="main_bottom">
          <div v-for="item in userTodos" class="todo-item">
            <input type="radio" class="todo-radio">
            <p>{{ item.text }}</p>
          </div>
          <div class="control-panel">
            <p class="indicator">{{ userTodos.length }} item(s) left</p>
            <div class="control-panel__toggle">
              <a>All</a>
              <a>Active</a>
              <a>Completed</a>
            </div>
            <a class="clear">Clear completed</a>
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
.clear {
  color: #8b8b8b;
  font-size: 14px;
}
.control-panel {
  background-color: #2e2c3a;
  display: flex;
  color: #FFF;
  padding: 16px 30px;
  justify-content: space-between;
  align-items: center;
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
}
.radio-input {
  appearance: none;
  position: relative;
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
.todo-item  {
  display: flex;
  background-color: #2e2c3a;
  padding: 16px 40px;
  padding-left: 60px;
  border: 0.1px solid #cacaca;
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
</style>
