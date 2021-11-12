<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <div class="container">
    <Header title="Task Tracker??" />
    <AddTask @addTask="addtask" />
    <Tasks @toggle="toggleReminder" @remove="removeTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addtask(task) {
      // if (task.id === null) {
      //   task.id = this.tasks.length += 1;
      //   console.log(task);
      //   console.log(this.tasks.length);
      // }

      this.tasks = [...this.tasks, task];
      console.log(this.tasks);
    },
    removeTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((t) => t.id !== id);
        console.log(id);
      }
    },
    toggleReminder(id) {
      console.log(id);
      this.tasks = this.tasks.map((t) =>
        // copmpleted is equal to opposite !t.completed
        t.id === id
          ? { ...t, completed: !t.completed }
          : /* if id not match just return initial task */ t
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        title: "Docters Appointment",
        description: "march 1st at 2:30pm",
        completed: true,
      },
      {
        id: 2,
        title: "Meeting at School",
        description: "march 2nd at 8:30pm",
        completed: false,
      },
      {
        id: 3,
        title: "Food Shopping",
        description: "march 3rd at 3:30pm",
        completed: false,
      },
      {
        id: 4,
        title: "Clean clothes",
        description: "march 4th at 4:30pm",
        completed: false,
      },
      {
        id: 5,
        title: "Press Clothes",
        description: "march 5th at 5:30pm",
        completed: false,
      },
    ];
  },
};
</script>

<style>
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
