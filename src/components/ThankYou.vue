<template>
  <div class="thank-you-page">
    <h1>Thank you for submitting your message!</h1>
    <h3>You will be redirected to our Home Page in 5 seconds...</h3>
  </div>
</template>

<script>
export default {
  mounted() {
    // Redirige a la página de inicio después de 3 segundos
    setTimeout(() => {
      this.$router.push('/'); // Asegúrate de tener vue-router configurado
    }, 5000);
  }
}
</script>

<style scoped>
body {
  font-family: 'Roboto', sans-serif;
}

.thank-you-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #080C1E;
  background-size: cover;
  color: white;
  text-align: center;
  padding: 30px 80px;
}

h1,
h3 {
  margin: 0;
  padding: 0;
}

h1 {
  font-weight: 900;
  color: #FFFFFF;
}

h3 {
  margin-top: 40px;
  color: #08529d;
  font-size: 1.5rem;
}
</style>