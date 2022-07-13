<script setup>
/**
 * 이번 프로젝트에서는 Option API 대신 Composition API를 사용하려고 합니다!
 * 서로 기능이 다른 부분은 없어 어떤 문법으로 작성해도 상관없지만,
 * 프로젝트 코드의 일관성을 위해 통일합니다 :)
 */

let id = 0;

/**
 * 이전의 newTodo 입니다.
 * newTodo 도 괜찮았지만 사용자한테 입력 받은 값이라는 걸 더 잘 알려주는
 * 이름으로 바꿨습니다 :)
 */
const inputValue = ref("");
/**
 * 이전의 todos 입니다.
 * todo는 -s 로 복수형이 될 수 없어서 이름을 바꿨습니다.
 * 일반적으로는 상관없지만 저는 최대한 지키려고 하는 편입니다.
 */
const todoList = ref([]);
/**
 * 이전의 activecheck 입니다.
 * 이름을 용도에 맞춰 변경하고, 값도 문자열로 변경했습니다.
 * 바로 알아볼 수 없는 숫자보다 의미를 갖는 단어가 더 유용할 수 있습니다.
 * 원래 방식처럼 숫자를 사용하는 방법을 개발에서 매직 넘버라고 합니다.
 *
 * # 참고
 * Magic number (programming) - Wikipedia - https://en.wikipedia.org/wiki/Magic_number_(programming)
 */
const filterType = ref("all");

/**
 * <template> 영역을 최대한 단순하게 가져가기 위해
 * 스크립트에서 계산할 수 있는 부분은 처리해주는 것이 좋습니다.
 *
 * computed는 안에 ref로 지정된 값이 변할 때 마다 다시 계산되는 값입니다.
 * filterType이나 todoList가 바뀔 때 마다 다시 계산됩니다.
 *
 * # 참고
 * 계산된 속성 | Vue.js - https://v3-docs.vuejs-korea.org/guide/essentials/computed.html
 */
const filteredList = computed(() => {
  switch (filterType.value) {
    case "all":
      return todoList.value;
    case "active":
      return todoList.value.filter((todo) => !todo.done);
    case "done":
      return todoList.value.filter((todo) => todo.done);
  }
});
const leftCount = computed(() => {
  return todoList.value.filter((todo) => !todo.done).length;
});

function addTodo() {
  todoList.value.push({
    id: id++,
    text: inputValue.value,
    done: false,
  });
  inputValue.value = "";
}
function removeTodo(todo) {
  const index = todoList.value.findIndex((item) => item.id === todo.id);
  todoList.value.splice(index, 1);
}
</script>

<template>
  <h1>Todo List</h1>
  <div class="add">
    <form @submit.prevent="addTodo">
      <input v-model="inputValue" placeholder="무엇을 하나요?" />
    </form>
  </div>
  <div class="list" v-if="todoList.length">
    <ul>
      <!--
        Vue 3 의 v-for에는 key가 필요하지 않습니다!
        근데 여기서는 todo.done을 위해 필요하네요...
      -->
      <li v-for="todo in filteredList" :key="todo.id">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
    <p>{{ leftCount }} items left</p>
  </div>
  <div>
    <button @click="filterType = 'all'">All</button><br />
    <button @click="filterType = 'active'">Active</button><br />
    <button @click="filterType = 'done'">Completed</button>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}

button {
  background-color: black;
  color: white;
}
</style>