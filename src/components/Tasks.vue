<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      @toggle="$emit('toggle', task.id)"
      @remove="$emit('remove', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  components: {
    Task,
  },
  props: {
    tasks: Array,
  },
  emits: ["remove", "toggle"],
};
</script>
