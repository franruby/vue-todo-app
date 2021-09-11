<template>
  <div class="task-card">
    <button class="hide-form" @click.prevent="deleteTask(id)">
      <i class="bx bx-plus bx-sm"></i>
    </button>
    <span class="card-title">{{ title }}</span>
    <div class="card-content">
      {{ content }}
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskCard",
  props: {
    id: Number,
    title: String,
    content: String,
    deleter: Function,
  },
  methods: {
    deleteTask(id) {
      this.deleter(id);
    },
  },
};
</script>

<style lang="scss" scoped>
.hide-form {
  padding: 0;
  border: none;
  background: none;
  position: absolute;
  top: 0;
  right: 0;
  margin: 0.6rem;
  i {
    color: #fff;
    transform: rotate(45deg);
  }
}
.task-card {
  position: relative;
  z-index: 1;
  margin: 1rem;
  padding: 1rem;
  background: var(--first-color);
  color: #fff;
  border-radius: 1rem;
  .card-title {
    font-size: 1.5rem;
  }
  .card-content {
    margin: 1rem 0;
  }
}
</style>