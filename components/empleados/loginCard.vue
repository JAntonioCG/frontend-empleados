<template>
  <v-card elevation="0" color="blue darken-8" width="400" height="300" rounded>
    <!-- Color del cuadrado -->
    <v-card-title>
      <v-row align="center" justify="center">
        <span style="color: aliceblue">Bienvenido</span>
      </v-row>
    </v-card-title>
    <v-card-text class="mt-4 mb-4 pt-4 pb-4">
      <v-form ref="form">
        <div class="textFields">
          <v-row style="width: 100%;">
            <v-text-field v-model="usuario" :rules="size" solo />
          </v-row>
          <v-row style="width: 100%;">
            <v-text-field v-model="password" :rules="size" type="password" solo />
          </v-row>
        </div>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-row align="center" justify="center">
        <v-btn block elevation="0" @click="loginBackend">
          <!-- <span style="text-transform: none; color: black;">Login</span> -->
          Login
        </v-btn>
      </v-row>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      usuario: '',
      password: '',
      size: [
        v => v.trim().length !== 0 || 'No puede estar en blanco'
      ]
    }
  },
  methods: {
    loginBackend () {
      // eslint-disable-next-line no-console
      console.log('Variables uwu', this.usuario, this.password)
      const isValid = this.$refs.form.validate()
      if (isValid) {
        const body = {
          correo: this.usuario,
          contrasena: this.password
        }
        this.$axios.post('/login', body)
          .then((res) => {
          // eslint-disable-next-line no-console
            console.log('Respuesta iwi', res)
          })
          .catch((error) => {
          // eslint-disable-next-line no-console
            console.error('error owo => ', error)
          })
      } else {
        // comentario
        this.$emit('show-alert', {
          showAlert: true,
          color: 'red',
          type: 'error',
          message: 'Los datos son incorrectos',
          icon: 'mdi-error'
        })
      }
    }
  }
}
</script>
<style scoped>
.textFields {
  width: 100%;
  margin: 10px;
}</style>
