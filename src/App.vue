<template>
  <div id="app">
    <div class="container">
      <FormComponent @submit="user" class="mb-5"/>
      <!-- <div v-if="user > 0"> -->
        <TableComponent :users="users"/>
      <!-- </div> -->
    </div>
  </div>
</template>

<script>
import FormComponent from './components/FormComponent.vue'
import TableComponent from './components/TableComponent.vue'

export default {
  name: 'App',
  components: {
  FormComponent,
  TableComponent
  },
  data() {
    return {
      user: [],
      users: [],
    }
  },
  methods: {
    submit(user){
      this.users.push(user)
    }
  },
}
</script>

<style>
#app {
  background-image: url("./assets/signup-bg.jpg");
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  height: 100vh;
}
</style>
