<template>
  <div>
    <Navbar />
    <div class="flex justify-center items-center space-x-3">
      <img class="w-10 h-10" src="~/assets/images/todo.png" alt="todo" />
      <p class="text-xl font-bold">
        Todo
        <span>
          ({{ totalTodo }})
          <span class="text-red-400">({{ lengthPriority }})</span>
          <del>({{ lengthDone }})</del>
        </span>
      </p>
    </div>
    <div
      class="pt-5 flex flex-col items-center justify-center w-full space-y-3 absolute"
    >
      <div class="w-2/3 flex justify-between space-x-3">
        <input
          @keyup.enter="addTodo"
          v-model="todo"
          class="bg-green-300 w-full h-10"
          type="text"
        />
        <Button @click="addTodo" content="+" />
      </div>
      <div
        class="w-2/3 flex justify-between items-center space-x-3"
        v-for="(todo, id) in todos"
        :key="id"
      >
        <p v-if="todo.isDone" class="w-full">
          <del>{{ todo.actifity }}</del>
        </p>
        <p v-else-if="todo.isPriority" class="w-full">
          <span class="text-red-400">{{ todo.actifity }}</span>
        </p>
        <p v-else class="w-full">
          {{ todo.actifity }}
        </p>

        <Button @click="priorityTodo(id)" type="priority" content="A1" />
        <Button @click="deleteTodo(id)" type="warning" content="x" />
        <Button @click="doneTodo(id)" type="secondary" content="Done" />
      </div>
      <Button @click="resetTodo()" type="success" content="Reset" />
    </div>
  </div>
</template>

<script>
import Button from "../components/atoms/Button.vue";
import Navbar from "../components/Navbar.vue";
export default {
  components: { Button, Navbar },
  data() {
    return {
      todo: "",
      todos: [],

      reset: [
        {
          actifity: "Bersihkkan Tempat Tidur",
          isDone: false,
          isPriority: false,
        },
        {
          actifity: "Mandi",
          isDone: false,
          isPriority: false,
        },
        {
          actifity: "Sholat Tahajud",
          isDone: false,
          isPriority: false,
        },
        {
          actifity: "Sholat Shubuh",
          isDone: false,
          isPriority: false,
        },

        {
          actifity: "Baca Quran ",
          isDone: false,
          isPriority: true,
        },
        {
          actifity: "Sarapan",
          isDone: false,
          isPriority: false,
        },
        {
          actifity: "Kerja",
          isDone: false,
          isPriority: false,
        },
        {
          actifity: "Sholat Dhuha",
          isDone: false,
          isPriority: false,
        },
      ],
    };
  },

  beforeMount() {
    this.todos = this.reset;
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todos"));
  },

  computed: {
    totalTodo() {
      return this.todos.length;
    },
    lengthDone() {
      let newArrayD = this.todos.filter((el) => {
        return el.isDone == true;
      });
      return newArrayD.length;
    },
    lengthPriority() {
      let newArrayP = this.todos.filter((el) => {
        return el.isPriority == true;
      });
      return newArrayP.length;
    },
  },

  methods: {
    addTodo() {
      this.todos.push({
        actifity: this.todo,
        isDone: false,
        isPriority: false,
      });
      this.todo = "";
      this.saveToLocalStorage();
    },
    deleteTodo(index) {
      this.todos = this.todos.filter((todo, id) => {
        if (index != id) {
          return todo;
        }
      });
      this.saveToLocalStorage();
    },
    priorityTodo(index) {
      this.todos = this.todos.filter((todo, id) => {
        if (index == id) {
          todo.isPriority = true;
        }
        return todo;
      });
      this.saveToLocalStorage();
    },
    doneTodo(index) {
      // console.log(id);
      // this.todos[id].isDone = true;

      this.todos = this.todos.filter((todo, id) => {
        if (index == id) {
          todo.isDone = true;
        }
        return todo;
      });
      this.saveToLocalStorage();
    },
    resetTodo() {
      this.todos = this.reset;
    },
    saveToLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
};
</script>

<style></style>
