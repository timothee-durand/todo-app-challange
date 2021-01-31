<template>

  <ul>
    <transition-group name="fade">
      <Li v-for="(task,index) in list" :key="index">
        <label class="container-todo">
          <input type="checkbox" class="checkbox-task" v-model="task.done">
          <span class="checkmark"></span>
          <span class="text-todo" :class="{'done':task.done}">{{ task.text }}</span>
        </label>
        <button @click="removeTask(task)" class="button-delete" v-if="canRemove"><i class="material-icons">delete_outline</i>
        </button>
      </Li>
    </transition-group>
  </ul>


</template>
<script>
export default {
  name: 'TaskList',
  props: {
    list: {},
    canRemove: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    setActive(task) {
      console.log(this.$store)
      this.$store.commit("todo/toggle", task)
    },
    removeTask(task) {
      this.$store.commit("todo/remove", task);
    },
  }
}
</script>
<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.checkbox-task {
  width: 24px;
  height: 24px;
  background: #2F80ED;
  border-radius: 4px;
}

ul  li {
  margin-top: 22px;
  display: flex;
  align-items: center;
}

.text-todo {
  margin-left: 10px;

}

.text-todo.done {
  text-decoration: line-through;
}

.container-todo {
  display: flex;
  align-items: center;
}

.button-delete {
  margin-left: auto;
  display: block;
  background-color: transparent;
  border: none;
  outline: none;
  color: #BDBDBD;
  font-size: 14px;
  transition: color ease 100ms;
  cursor: pointer;
}

.button-delete:hover, .button-delete:focus {
  color: #797979;
}


/* Customize the label (the container) */
.container-todo {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container-todo input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: transparent;
  border-radius: 4px;
  border: 1px solid #828282;
  transition: all ease 100ms;
}

/* On mouse-over, add a grey background color */
.container-todo:hover input ~ .checkmark {
  background: #20529b;
  border: none;
}

/* When the checkbox is checked, add a blue background */
.container-todo input:checked ~ .checkmark {
  background: #2F80ED;
  border: none;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container-todo input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container-todo .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}


.fade-enter-active, .fade-leave-active {
  transition: opacity .2s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}


</style>
