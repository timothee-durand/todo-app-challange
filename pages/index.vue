<template>
  <div class="container">
    <div>
      <TaskList :list="list" />
    </div>
  </div>
</template>

<script>


import TaskList from "~/pages/TaskList.vue";

export default {
  name:"All",
  components: {TaskList},
  computed: {
    list(){
      return this.$store.state.todo.list
    }
  },
}
</script>

