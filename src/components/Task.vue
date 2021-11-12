<template>
  <div
    @dblclick="$emit('toggle', task.id)"
    :class="[task.completed ? 'completed' : '', 'task']"
  >
    <h3>{{ task.title }}</h3>
    <p>{{ task.description }}</p>
    <!-- <p>{{ task.completed }}</p> -->
    <button @click="$emit('remove', task.id)">Remove</button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.task {
  padding: 1em;
  border: 1px solid #ccc;
  background-color: #f0f0f0;
  margin-bottom: 1em;
}
.task.completed {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
