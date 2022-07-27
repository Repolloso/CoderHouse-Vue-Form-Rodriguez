<template lang="html">

  <section class="table-componente card">
    <h1 class="text-center border py-3">Usuarios Registrados</h1>
    <table class="table text-dark">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Email</th>
          <th>Password</th>
          <th>País</th>
          <th>Accion</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in data_user" :key="user.index">
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.password }}</td>
          <td>{{ user.country }}</td>
          <td>
            <button class="btn btn-danger" @click="deleteRegister(user)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'table-componente',
    props: {
      data_user: Array,
    },
    methods: {
      deleteRegister(user) {
        this.$emit('delete', user)
      },
    },
    computed: {
      
    }
}


</script>

<style scoped>

</style>
