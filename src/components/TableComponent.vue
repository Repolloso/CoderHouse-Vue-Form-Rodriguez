<template lang="html">

  <section class="table-componente">
    <h1>Usuarios Registrados</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Email</th>
          <th>Password</th>
          <th>País</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.index">
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.password }}</td>
          <td>{{ user.country }}</td>
        </tr>
      </tbody>
    </table>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'table-componente',
    props: {
      users: Array,
    },
    methods: {
      console(){
        console.log(this.users)
      }
    },
    computed: {

    }
}


</script>

<style scoped>

</style>
