<template>
  <div class="container">
    <div>
      <TaskList :list="list" can-remove></TaskList>
      <button type="button" @click="delAll()" class="button-delete-all"> <i class="material-icons">delete_outline</i> delete all</button>
    </div>
  </div>
</template>

<script>


import TaskList from "~/pages/TaskList.vue";

export default {
  name: "All",
  components: {TaskList},
  computed: {
    list() {
      return this.$store.state.todo.list.filter(function (task) {
        return task.done
      })
    }
  },
  methods: {

    delAll() {
      this.$store.commit("todo/setEmpty");
    }
  },
  mounted() {

  }
}
</script>

<style scoped>
  .button-delete-all {
    background: #EB5757;
    border-radius: 4px;
    width: 124px;
    height: 40px;
    outline: none;
    border: none;
    margin-left: auto;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 37px;
    transition: background-color 100ms ease;
  }

  .button-delete-all:hover,  .button-delete-all:focus {
    background: #bc4747;
  }
</style>

