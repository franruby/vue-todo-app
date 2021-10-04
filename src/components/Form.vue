<template>
  <div class="l-form">
    <form action="" class="form">
      <button class="hide-form" @click.prevent="closeForm()">
        <i class="bx bx-plus bx-sm"></i>
      </button>

      <div class="form__div">
        <input
          v-model="title"
          type="text"
          class="form__input"
          placeholder=" "
        />
        <label for="" class="form__label">Task Title</label>
      </div>

      <div class="form__div">
        <input
          v-model="content"
          type="password"
          class="form__input"
          placeholder=" "
        />
        <label for="" class="form__label">Task Content</label>
      </div>

      <div class="adding-button">
        <input
          type="submit"
          class="form__button"
          value="Add"
          @click.prevent="addItem()"
        />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
  props: {
    adder: Function,
    hideform: Function,
  },
  data: () => ({
    title: null,
    content: null,
    invalidTaskAlert: false
  }),
  methods: {
    closeForm() {
      this.hideform();
    },
    addItem() {
      let newTask = {
        title: this.title,
        content: this.content,
      };
      if (!newTask.title) {
        alert('La el título de la tarea no puede ir vacía')
      } else {
        this.adder(newTask)
        this.title = ''
        this.content = ''
      }
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
  margin: 1rem;
  i {
    color: var(--input-color);
    transform: rotate(45deg);
  }
}

.l-form {
  width: 100%;
  position: fixed;
  bottom: 0;
  z-index: 100;
  background: #fff;
  border-radius: 1rem 1rem 0 0;
  box-shadow: -3px 4px 35px 7px rgba(82, 82, 82, 1);
}
.form {
  padding: 3rem 2rem;
  border-radius: 1rem 1rem 0 0;
  box-shadow: 0 10px 25px rgba(92, 99, 105, 0.2);
}
.form__title {
  font-weight: 400;
  margin-bottom: 3rem;
}
.form__div {
  position: relative;
  height: 48px;
  margin-bottom: 1.5rem;
}
.form__input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  font-size: var(--normal-font-size);
  border: 1px solid var(--border-color);
  border-radius: 0.5rem;
  outline: none;
  padding: 1rem;
  background: none;
  z-index: 1;
}
.form__label {
  position: absolute;
  left: 1rem;
  top: 1rem;
  padding: 0 0.25rem;
  background-color: #fff;
  color: var(--input-color);
  font-size: var(--normal-font-size);
  transition: 0.3s;
}
.adding-button {
  display: flex;
  justify-content: center;
  align-items: center;
}
.form__button {
  display: block;
  padding: 0.75rem 2rem;
  outline: none;
  border: none;
  background-color: var(--first-color);
  color: #fff;
  font-size: var(--normal-font-size);
  border-radius: 0.5rem;
  cursor: pointer;
  transition: 0.3s;
}
.form__button:hover {
  box-shadow: 0 10px 36px rgba(0, 0, 0, 0.15);
}

/*Input focus move up label*/
.form__input:focus + .form__label {
  top: -0.5rem;
  left: 0.8rem;
  color: var(--first-color);
  font-size: var(--small-font-size);
  font-weight: 500;
  z-index: 10;
}

/*Input focus sticky top label*/
.form__input:not(:placeholder-shown).form__input:not(:focus) + .form__label {
  top: -0.5rem;
  left: 0.8rem;
  font-size: var(--small-font-size);
  font-weight: 500;
  z-index: 10;
}

/*Input focus*/
.form__input:focus {
  border: 1.5px solid var(--first-color);
}
</style>