<template>
  <div class="home">
    <Header></Header>
    <div class="home-body">
      <div class="nav">
        <Slider></Slider>
      </div>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from './../components/nav/header'
import Slider from './../components/nav/slider'

export default {
  name: 'home',
  components: {
    Header, Slider
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
.home-body {
  width: 100%;
  display: flex;
  justify-content: space-between;
  .nav {
    width: 15%;
  }
}
</style>

