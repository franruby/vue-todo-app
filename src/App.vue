<template>
  <div id="app-container">
    <TopNavBar />
    <div class="sizer-container">A</div>
    <div class="card-container">
      <task-card
        v-for="(task, i) in tasks"
        :key="i"
        :id="i"
        :title="task.title"
        :content="task.content"
        :deleter="deleteTask"
      />
    </div>
    <add-task-button :shower="showForm" />
    <Form v-if="showFormControl" :adder="addTask" :hideform="hideForm" />
  </div>
</template>

<script>
import TopNavBar from "./components/TopNavbar.vue";
import TaskCard from "./components/TaskCard.vue";
import AddTaskButton from "./components/AddTaskButton.vue";
import Form from "./components/Form.vue";

export default {
  name: "App",
  components: {
    TopNavBar,
    TaskCard,
    AddTaskButton,
    Form,
  },
  data: () => ({
    tasks: [
      {
        title: "Title 1",
        content:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto quo repellendus, suscipit dolorum eligendi possimus nesciunt nihil doloribus aperiam nobis in ad hic fuga est eum molestias blanditiis magnam quaerat.",
      },
      {
        title: "Title 2",
        content:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto quo repellendus, suscipit dolorum eligendi possimus nesciunt nihil doloribus aperiam nobis in ad hic fuga est eum molestias blanditiis magnam quaerat.",
      },
      {
        title: "Title 3",
        content:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto quo repellendus, suscipit dolorum eligendi possimus nesciunt nihil doloribus aperiam nobis in ad hic fuga est eum molestias blanditiis magnam quaerat.",
      },
    ],
    showFormControl: false,
  }),
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },
    deleteTask(taskId) {
      this.tasks.splice(taskId, 1);
    },
    showForm() {
      this.showFormControl = !this.showFormControl;
    },
    hideForm() {
      this.showFormControl = !this.showFormControl;
    },
  },
};
</script>

<style lang="scss" scoped>
.sizer-container {
  display: none;
  width: 100%;
  padding: 1.3rem;
  background: var(--first-color);
  color: #fff;
  border-radius: 0 0 1rem 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
