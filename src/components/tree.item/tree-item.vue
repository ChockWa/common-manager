<template>
  <div class="tree-item">
    <div style="display:flex;justify-content:flex-start;">
      <div @click="openChild">{{model.menuName}}</div>
    </div>
    <transition name="slide" mode="out-in">
      <div v-if="showChild">
        <tree-item
          v-for="(item,index) in model.childTree"
          :model="item"
          :key="index"
          v-on:select="select"
        ></tree-item>
      </div>
    </transition>
  </div>
</template>
 
<script>
export default {
  name: "tree-item",
  props: ["model"],
  data() {
    return {
      selections: [],
      showChild: false
    };
  },
  methods: {
    select(id) {
      this.$emit("select", id);
    },
    openChild() {
      this.showChild = !this.showChild;
    },
    selectChange() {
      this.$emit("select", this.model.id);
    }
  },
  computed: {}
};
</script>
 
<style scoped lang="scss">
.tree-item {
  position: relative;
  padding-left: 8%;
  cursor: pointer;
  background-color: #393e46;
}
.slide-enter-active,
.slide-leave-active {
  transition: all 0.2s;
}
.slide-enter,
.slide-leave-to {
  transform: translateY(-20px);
}
.slide-enter-to,
.slide-leave {
  transform: translateY(0px);
}
</style>