<template>
  <div id="app">
    <div class="container">
      <FormComponent @submit="user" class="mb-5"/>
      <div v-if="users.length > 0">
        <TableComponent :data_user="users" @delete="data"/>
      </div>
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
      users: [],
    }
  },
  methods: {
    user(data) {
      this.users.push(data)
    },
    data(info) {
      this.users.splice(this.users.indexOf(info), 1)
    }
  },
}
</script>

<style>
#app {
  background-image: url("./assets/signup-bg.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  height: 100vh;
}
</style>
