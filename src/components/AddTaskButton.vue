<template>
  <div class="add-task-button">
    <button @click.prevent="show()">
      <i class="bx bx-plus bx-sm"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "AddTaskButton",
  props: {
    shower: Function,
  },
  methods: {
    show() {
      this.shower();
    },
  },
};
</script>

<style lang="scss" scoped>
.add-task-button {
  position: fixed;
  bottom: 0;
  z-index: 2;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 0 1rem 0;
  button {
    background: var(--border-color);
    border: none;
    padding: 1.5rem;
    border-radius: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: -3px 4px 35px 7px rgba(82,82,82,1);
    i {
      font-weight: bold;
    }
  }
}
</style>