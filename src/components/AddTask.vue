<template>
  <form @submit="myfunction" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="title" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="description"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="completed" name="completed" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      title: "",
      description: "",
      completed: false,
    };
  },
  methods: {
    myfunction(e) {
      e.preventDefault();

      if (!this.title || !this.description) {
        alert("Plz Fill Task and day field Properly");
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        // id: null,
        title: this.title,
        description: this.description,
        completed: this.completed,
      };

      this.$emit("addTask", newTask);

      this.title = "";
      this.description = "";
      this.completed = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px;
}

.form-control label {
  display: block;
  font-weight: 500;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
