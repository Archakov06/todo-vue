<template>
  <!-- Сравнить бандлы всех тудушек на разных фреймворках -->
  <div id="app">
    <div class="todo">
      <div class="todo__header">
        <h4>Список задач</h4>
      </div>
      <TaskField @onAddTask="onAddTask" />
      <div class="todo__list">
        <ListItem
          v-for="(task, index) in tasks"
          :key="index"
          :index="index"
          :text="task.text"
          :completed="task.completed"
          @onToggleCompleted="onToggleCompleted"
          @onRemoveTask="onRemoveTask"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ListItem from "./components/ListItem";
import TaskField from "./components/TaskField";

export default {
  name: "App",
  data: () => ({
    tasks: [
      {
        text: "Изучить VueJS",
        completed: true,
      },
      {
        text: "Разработать ToDo на VueJS",
        completed: false,
      },
    ],
  }),
  methods: {
    onToggleCompleted(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    onRemoveTask(index) {
      this.tasks.splice(index, 1);
    },
    onAddTask(text) {
      this.tasks.push({
        text,
        completed: false,
      });
    },
  },
  components: {
    ListItem,
    TaskField,
  },
};
</script>

<style>
@import "./assets/app.css";
</style>
