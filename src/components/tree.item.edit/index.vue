<template>
  <div class="tree-edit">
    <tree-item-edit v-for="(model,index) in list" :model="model" :key="index" v-on:select="select"></tree-item-edit>
  </div>
</template>
 
<script>
import TreeItemEdit from "./tree-item-edit";
export default {
  name: "TreeEdit",
  data() {
    return {
      selections: [],
      list: [
        {
          id: 1,
          menuName: "项目管理",
          level: 1,
          childTree: [
            {
              id: 2,
              menuName: "项目进度",
              level: 2,
              childTree: [
                {
                  id: 3,
                  menuName: "项目一",
                  level: 3,
                  childTree: [
                    {
                      id: 4,
                      menuName: "详细信息",
                      level: 4,
                      childTree: [
                        {
                          id: 5,
                          menuName: "详细信息",
                          level: 4,
                          childTree: [
                            {
                              id: 6,
                              menuName: "详细信息",
                              level: 4,
                              childTree: [
                                {
                                  id: 7,
                                  menuName: "详细信息",
                                  level: 4,
                                  childTree: [
                                    {
                                      id: 8,
                                      menuName: "详细信息",
                                      level: 4,
                                      childTree: [
                                        {
                                          id: 9,
                                          menuName: "详细信息",
                                          level: 4,
                                          childTree: []
                                        }
                                      ]
                                    }
                                  ]
                                }
                              ]
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            },
            {
              id: 10,
              menuName: "任务安排",
              level: 2,
              childTree: []
            }
          ]
        },
        {
          id: 11,
          menuName: "数据统计",
          level: 1,
          childTree: []
        },
        {
          id: 12,
          menuName: "人员管理",
          level: 1,
          childTree: []
        }
      ]
    };
  },
  components: {
    TreeItemEdit
  },
  created() {
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
.tree-edit {
  font-size: 18px;
  /* background: #409eff; */
  color: #333333;
  height: 40px;
  line-height: 40px;
}
</style>