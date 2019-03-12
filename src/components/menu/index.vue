<template>
    <div class="menu">
      <tree-item :treeList="list"></tree-item>
    </div>
</template>

<script>
import TreeItem from './../tree.item'

export default {
  name: 'Menu',
  components: {TreeItem},
  data() {
    return {
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
    }
  }

}
</script>

<style lang="scss">
</style>
