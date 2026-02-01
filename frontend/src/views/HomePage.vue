<script setup>

</script>

<template>
  <div class="background">
    <div class="main">
        <div class="main__header">
          <div class="main__header__cont1">
            <h1>TODO</h1>
            <img src="/images/icon-sun.svg" alt="Солнышко">
          </div>
          <form>
            <input type="text" placeholder="Create a new todo...">
          </form>
        </div>
        <div class="main_bottom">

        </div>
    </div>
  </div>
</template>

<style scoped>
.background {
    width: 100%;
    height: 100%;
    background-image: url("/images/bg-desktop-dark.jpg");
    background-repeat: no-repeat;
    padding-top: 50px;
}
.main {
    max-width: 500px;
    margin: 0 auto;
}
.main__header__cont1 {
    display: flex;
    flex-direction: row;
}
.main__header__cont1 h1 {
    color: #FFF;
}
</style>
