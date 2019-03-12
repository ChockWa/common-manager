<template>
    <div class="slider">
        <Menu></Menu>
    </div>
</template>

<script>
import Menu from './../menu'
export default {
    name: 'Slider',
    components: {Menu}
}
</script>

<style lang="scss">
.slider {
  width: 100%;
  height: 100%;
}
</style>
