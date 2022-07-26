<template lang="html">

  <section class="form-component">
    <h1 class="text-center text-white">Formulario</h1>
    <div v-if="errors.length > 0" class="alert alert-danger" role="alert">
      <p>Errores detectados:</p>
      <ul>
        <li v-for="error in errors" :key="error.index">{{ error }}</li>
      </ul>
    </div>
    <form @submit.prevent="ValidateData" action="/" method="POST" class="card form-control">
      <div class="form-group mb-3">
        <label for="name">Nombre</label>
        <input type="text" class="form-control" id="name" v-model="user.name" placeholder="Nombre" >
      </div>
      <div class="form-group mb-3">
        <label for="email">Email</label>
        <input type="email" class="form-control" id="email" v-model="user.email" placeholder="Email" >
      </div>
      <div class="form-group mb-3">
        <label for="password">Password</label>
        <input type="password" class="form-control" id="password" v-model="user.password" placeholder="Password" >
      </div>
      <div class="form-group">
        <label for="country">Country</label>
        <select id="country" class="form-control" v-model="user.country" placeholder="Country" >
          <option v-for="(item, i) in countries" :key="i" :value="item.name">{{ item.name }}</option>
        </select>
      </div>
      <input type="submit" name="submit" value="Submit" class="btn btn-primary mt-3"> 
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
        user: {
          name: '',
          email: '',
          password: '',
          country: ''
        },
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
          {
            name: 'Ecuador'
          },
          {
            name: 'El Salvador'
          },
          {
            name: 'Guatemala'
          },
          {
            name: 'Honduras'
          },
          {
            name: 'México'
          },
          {
            name: 'Nicaragua'
          },
          {
            name: 'Panamá'
          },
          {
            name: 'Paraguay'
          },
          {
            name: 'Perú'
          },
          {
            name: 'Puerto Rico'
          },
          {
            name: 'República Dominicana'
          },
          {
            name: 'Uruguay'
          },
          {
            name: 'Venezuela'
          }
        ]
      }
    },
    methods: {
      ValidateData () {
        if (this.user && this.user.name && this.user.email && this.user.password && this.user.country) {
          this.$emit('submit', this.user);
        } else {
          this.errors = []
          if (!this.user.name) {
            this.errors.push('El nombre es requerido')
          }
          if(this.user.name.length < 3) {
            this.errors.push('El nombre debe tener al menos 3 caracteres')
          }
          if (!this.user.email) {
            this.errors.push('El email es requerido')
          } 
          if(!this.user.email.includes('@')) {
            this.errors.push('El email debe tener un @')
          }
          if (!this.user.password) {
            this.errors.push('El password es requerido')
          }
          if (!this.user.country) {
            this.errors.push('El país es requerido')
          }
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped>

</style>
