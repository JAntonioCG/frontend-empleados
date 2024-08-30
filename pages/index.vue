<template>
  <login-card @show-alert="showAlert" />
</template>

<script>
import loginCard from '@/components/empleados/loginCard.vue'
export default {
  name: 'IndexPage',
  components: {
    loginCard
  },
  layout: 'login',
  methods: {
    showAlert (data) {
      // eslint-disable-next-line no-console
      console.log('"Data  owo => "', data)
      this.$nuxt.$emit('show-alert', data)
    }
  }
}
</script>
