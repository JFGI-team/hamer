<template>
  <div class="page">
    <h2 class="text-2xl tracking-wider">Todo List</h2>
    <hr />
    {{ todo }}
    <hr />
    <form v-on:submit.prevent>
      <input
        class="shadow-lg rounded-lg border-2"
        type="text"
        id="name"
        name="name"
        v-model="todo"
        @keydown.enter="todoinput"
        required />
      <!-- <input type="submit" v-on:click="todoinput" value="제출하기" /> -->
      <br />
    </form>

    <hr />
    <ul v-for="item in todolist" :key="item.id">
      <div class="">
        <li
          class="checkbox w-4/5"
          :class="item.check === true ? 'checked' : ''">
          <input type="checkbox" @click="checkTodo(item)" />
          {{ item.subject
          }}<button class="checkbox w-1/5" @click="deleteTodo(item.id)">
            삭제
          </button>
        </li>
      </div>
    </ul>

    <button class="btn"></button>
  </div>
</template>
<script setup>
let todolist = ref([]);
let todo = ref("s");
let todoinput = () => {
  console.log(todolist.value);
  todolist.value.push({
    id: Date.now(),
    subject: todo.value,
    check: false,
  });
};
let checkTodo = (item) => {
  item.check = !item.check;
  console.log(item);
  todolist = todolist;
};
let deleteTodo = (id) => {
  var index = todolist.value.findIndex((i) => i.id == id);
  todolist.value.splice(index, 1);
};
</script>
<style scoped>
.checked {
  text-decoration: line-through;
}
</style>