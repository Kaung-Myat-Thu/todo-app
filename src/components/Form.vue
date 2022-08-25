<template>
  <form @submit.prevent="addTask">
    <div class="text-center">
      <input
        type="text"
        v-model="task"
        placeholder="eg. do something"
        class="text-xl px-4 py-2 w-96 my-4 bg-orange-50 placeholder:text-orange-300 text-orange-500 focus:outline-none"
      />
    </div>
    <div class="text-center">
      <input
        type="submit"
        value="Add Task"
        class="px-4 py-2 w-96 my-4 bg-orange-500 rounded-sm text-white font-bold shadow-sm shadow-orange-300 hover:bg-orange-700 cursor-pointer"
      />
    </div>
  </form>
  <TodoItem @delete-task="deleteTask" :tasks="tasks" />
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  data() {
    return {
      task: "",
      tasks: [
        {
          id: null,
          task: "",
        },
      ],
    };
  },
  components: {
    TodoItem,
  },
  methods: {
    addTask() {
      if (this.task == null || this.task.trim() == "") {
        return;
      }
      this.tasks.push({
        id: this.tasks.length + 1,
        task: this.task,
      });
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
      this.task = "";
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((t) => t.id !== id);
      localStorage.removeItem("tasks");
    },
  },
  mounted() {
    this.tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  },
  emits: ["delete-task"],
};
</script>
