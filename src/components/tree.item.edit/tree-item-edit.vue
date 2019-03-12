<template>
  <div class="tree-item-edit">
    <div style="display:flex;justify-content:flex-start;">
      <el-checkbox @change="selectChange"></el-checkbox>
      <div @click="openChild">{{model.menuName}}</div>
    </div>
    <transition name="slide">
      <div v-if="showChild">
        <tree-item-edit
          v-for="(item,index) in model.childTree"
          :model="item"
          :key="index"
          v-on:select="select"
        ></tree-item-edit>
      </div>
    </transition>
  </div>
</template>
 
<script>
export default {
  name: "tree-item-edit",
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
.tree-item-edit {
  position: relative;
  padding-left: 12px;
  cursor: pointer;
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