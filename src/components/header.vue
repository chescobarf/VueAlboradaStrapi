<template>
  <header>
    <div class="logo">
      <h1>
        <a href="https://mialborada.cl/">
          <img
            src="../assets/logo.png"
            alt="Descubre todos los descuentos y beneficios en estos Alboradays"
          />
        </a>
      </h1>
    </div>
  </header>
</template>

<script>
export default {
  name: "headerAlborada",
};
</script>

<style lang="scss">
header {
  background-color: #38205e;
  h1 {
    margin: 0;
    img {
      width: 60px;
    }
  }
}
</style>
