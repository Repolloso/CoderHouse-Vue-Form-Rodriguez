<template lang="html">

  <section class="form-component">
    <h1 class="text-center text-white">Formulario</h1>
    <div v-if="errors.length > 0" class="alert alert-danger alert-dismissible fade show" role="alert">
      <p>Errores detectados:</p>
      <ul>
        <div >
          <li v-for="error in errors" :key="error.index">{{ error }}</li>
          <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
        </div>
      </ul>
    </div>
    <form @submit.prevent="ValidateData" action="/" method="POST" class="card form-control">
      <div class="form-group mb-3">
        <label for="name">Nombre</label>
        <input type="text" class="form-control" id="name" v-model="name" placeholder="Nombre" >
      </div>
      <div class="form-group mb-3">
        <label for="email">Email</label>
        <input type="email" class="form-control" id="email" v-model="email" placeholder="Email" >
      </div>
      <div class="form-group mb-3">
        <label for="password">Password</label>
        <input type="password" class="form-control" id="password" v-model="password" placeholder="Password" >
      </div>
      <div class="form-group">
        <label for="country">Country</label>
        <select id="country" class="form-control" v-model="country" placeholder="Country" >
          <option v-for="(item, i) in countries" :key="i" :value="item.name">{{ item.name }}</option>
        </select>
      </div>
      <div class="input-group d-flex justify-content-between">
        <div v-if="(this.name.length > 0 || this.email.length > 0 || this.password.length > 0)">
          <button type="button" class="btn btn-danger mt-3" @click="resetForm">Reset Form</button>
        </div>
        <input type="submit" name="submit" value="Submit" class="btn btn-primary mt-3 col-lg-12">
      </div>
    </form>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'form-component',
    props: [],
    mounted () {

    },
    data () {
      return {
          name: '',
          email: '',
          password: '',
          country: '',
        errors: [],
        countries: [
          {
            name: 'Argentina'
          },
          {
            name: 'Brasil'
          },
          {
            name: 'Chile'
          },
          {
            name: 'Colombia'
          },
          {
            name: 'Costa Rica'
          },
          {
            name: 'Cuba'
          },
        ]
      }
    },
    methods: {
      ValidateData () {
        if (this.name && this.email && this.password && this.country) {
          this.$emit('submit', {
            name: this.name,
            email: this.email,
            password: this.password,
            country: this.country
          })
        } else {
          this.errors = []
          if (!this.name) {
            this.errors.push('El nombre es requerido')
          }
          if(this.name.length < 3) {
            this.errors.push('El nombre debe tener al menos 3 caracteres')
          }
          if (!this.email) {
            this.errors.push('El email es requerido')
          } 
          if(!this.email.includes('@')) {
            this.errors.push('El email debe tener un @')
          }
          if (!this.password) {
            this.errors.push('El password es requerido')
          }
          if (!this.country) {
            this.errors.push('El país es requerido')
          }
        }
      },
      resetForm () {
        this.name = ''
        this.email = ''
        this.password = ''
        this.country = ''
      }
    },
    computed: {

    }
}


</script>

<style scoped>

</style>
