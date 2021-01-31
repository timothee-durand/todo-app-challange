<template>
  <div class="container">
    <h1>#todo</h1>
    <div class="links">
      <nuxt-link to="/" active-class="active">All</nuxt-link>
      <nuxt-link to="/active" active-class="active">Active</nuxt-link>
      <nuxt-link to="/completed" active-class="active">Completed</nuxt-link>
    </div>
    <div class="form-container">
      <transition name="slide">
        <form @submit.prevent="addTask" v-if="$route.name !== 'completed'" class="form-add">
          <input type="text" v-model="taskToAdd" class="input-add" placeholder="Add a task">
          <button type="submit" class="button-add">Add</button>
        </form>
      </transition>
    </div>
    <Nuxt/>


    <p class="ownership">Timothée DURAND @ DevChallenges.io</p>
  </div>
</template>
<script>

export default {
  name: "Layout",
  data() {
    return {
      taskToAdd: ""
    }
  },
  methods: {
    addTask() {
      this.$store.commit("todo/add", this.taskToAdd);
      this.taskToAdd = "";
    }
  },
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500;600&family=Raleway:wght@700&display=swap&family=Material+Icons');


html {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  box-sizing: border-box;
}

h1 {
  font-family: Raleway, sans-serif;
  font-style: normal;
  font-weight: 700;
  font-size: 36px;
  line-height: 42px;
  text-align: center;
  letter-spacing: -0.045em;
}

.container {
  margin: 32px auto 0 auto;
  max-width: 608px;
  position: relative;
}

.links {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-top: 60px;
  border-bottom: 1px solid #BDBDBD;
}

.links > a {
  flex: 1;
  text-align: center;
  padding: 20px 0;
  position: relative;
}

.links > a.nuxt-link-exact-active:after {
  position: absolute;
  bottom: 0;
  left: 0;
  content: "";
  display: block;
  width: 100%;
  height: 4px;
  background: #2F80ED;
  border-radius: 4px 4px 0 0;
}


a, a:hover, a:visited {
  color: black;
  text-decoration: none;
}

.form-add {
  width: 100%;
  margin: 20px 0 0 0;
  padding: 0;

  display: flex;
  justify-content: space-between;
}

.form-add > * {
  height: 56px;
}

.input-add {
  width: 80%;
  border: 1px solid #BDBDBD;
  box-sizing: border-box;
  border-radius: 12px;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 17px;
  color: #828282;
  padding: 20px 12px;
  transition: border-color ease 100ms;
}

.input-add:hover, .input-add:focus {
  border: 1px solid #797979;
  outline: none;
}

.button-add {
  background: #2F80ED;
  box-shadow: 0px 2px 6px rgba(127, 177, 243, 0.4);
  border-radius: 12px;
  width: 15%;
  color: white;
  outline: none;
  border: none;
  transition: background-color ease 300ms;
}

.button-add:hover, .button-add:focus {
  background: #20529b;
}

.ownership {
  font-style: normal;
  font-weight: 600;
  font-size: 14px;
  line-height: 17px;
  color: #A9A9A9;
  position: fixed;
  left: 0;
  width: 100%;
  bottom: 0;
  text-align: center;
}


.slide-enter-active, .slide-leave-active {
  transition: transform 300ms;
}

.slide-enter, .slide-leave-to {
  transform: translateY(-200px);
}

.form-container {
  overflow: hidden;
}


</style>
