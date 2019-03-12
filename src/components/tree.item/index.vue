<template>
  <div class="tree">
    <tree-item v-for="(model,index) in list" :model="model" :key="index"></tree-item>
  </div>
</template>
 
<script>
import TreeItem from "./tree-item";
export default {
  name: "Tree",
  props: {
    treeList: Array
  },
  data() {
    return {
      selections: [],
      list: this.treeList
    };
  },
  components: {
    TreeItem
  },
  created() {
    console.log(this.treeList)
  },
  methods: {
    select(id) {
      const _this = this;
      if (_this.selections.indexOf(id) >= 0) {
        _this.selections.splice(_this.selections.indexOf(id), 1);
      } else {
        _this.selections.push(id);
      }
    }
  }
};
</script>
 
<style scoped>
.tree {
  font-size: 16px;
  color: #cccccc;
  height: 40px;
  line-height: 40px;
}
</style>