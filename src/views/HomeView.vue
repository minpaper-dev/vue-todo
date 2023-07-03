<template>
  <div class="home">
    <div class="container">
      <h2 class="title">할 일 추가 앱</h2>
      <div class="add-area">
        <!-- <input class="add-input" v-model="todo" type="text" placeholder="할 일을 적어주세요"> -->
        <!-- <input class="add-input" :value="todo" @input="change" type="text" placeholder="할 일을 적어주세요"> -->
        <v-input v-model="todo" @enter="addToDo" />
        <v-button @click="addToDo">추가할거야</v-button>
        <!-- <button class="add-button" type="button" @click="addToDo">추가</button> -->
      </div>
      <todo-list :todoList="todoList" />
    </div>
  </div>
</template>

<script>
import VInput from "@/components/common/VInput.vue";
import VButton from "@/components/common/VButton.vue";
import TodoList from "@/components/todo/TodoList.vue";

export default {
  name: "HomeView",
  components: {
    VInput,
    VButton,
    TodoList,
  },
  data() {
    return {
      todo: "",
      todoList: [],
    };
  },
  methods: {
    addToDo() {
      const newTodo = {
        name: this.todo,
        isUpdate: false,
        isChecked: false,
      };
      this.todoList.push(newTodo);
      this.todo = "";
    },
    deleteToDo(idx) {
      this.todoList = this.todoList.filter((_, index) => index !== idx);
    },
    change(event) {
      this.todo = event.target.value;
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  width: 500px;
  height: 500px;
  border: 1px solid black;
  padding: 24px;
}
.title {
  text-align: center;
}
.add-area {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.add-button {
  width: 80px;
  height: 30px;
  background-color: #00c4c4;
  border: 1px solid #00c4c4;
  color: #fff;
  cursor: pointer;
  margin: 16px 0px;

  &:hover {
    border-color: #00b2b2;
    background-color: #00b2b2;
  }
}
</style>
