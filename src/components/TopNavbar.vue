<template>
  <div class="navbar-container">
    <div class="logo">Task App</div>
  </div>
</template>

<script>
export default {
  name: "TopNavBar",
};
</script>

<style lang="scss" scoped>
.navbar-container {
  position: fixed;
  z-index: 100;
  width: 100%;
  padding: 1rem;
  background: var(--first-color);
  color: #fff;
  border-radius: 0 0 1rem 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
  .logo {
    font-size: 1.5rem;
    font-weight: bold;
  }
}
</style>