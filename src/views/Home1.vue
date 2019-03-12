<template>
    <el-row class="container">
  <el-col :span="24" class="main">
    <!-- <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item index="1-3">选项3</el-menu-item>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
    </el-menu> -->

    <aside :class="collapsed?'menu-collapsed':'menu-expanded'">
                <!--导航菜单-->
                <el-menu background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" v-bind:style=" collapsed ? {} : { 'width': '230px' } " :default-active="$route.path" class="el-menu-vertical-demo" unique-opened router v-show="!collapsed">
                    <template v-for="(item,index) in menuData" v-if="item.hidden">
                        <el-submenu :index="index+''" v-if="item.children.length >0" :key="index+''">
                            <template slot="title">
                                <i :class="item.iconCls"></i>{{item.name}}
                            </template>
                            <el-menu-item v-for="child in item.children" :index="child.path" :key="child.path" v-if="child.hidden">
                                {{child.name}}
                            </el-menu-item>
                        </el-submenu>
                        <el-menu-item v-if="item.children.length>0" :index="item.children[0].path" :key="item.children[0].path">
                            <i :class="item.iconCls"></i>{{item.children[0].name}}
                        </el-menu-item>
                    </template>
                </el-menu>
                <!--导航菜单-折叠后-->
                <ul class="el-menu el-menu-vertical-demo collapsed el-menu-collapsed" v-show="collapsed" ref="menuCollapsed">
                    <li v-for="(item,index) in menuData" v-if="item.hidden" class="el-submenu item" :key="index">
                        <template v-if="item.children.length>0">
                            <div class="el-submenu__title" style="padding-left: 20px;" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)">
                                <i :class="item.iconCls"></i>
                            </div>
                            <ul class="el-menu submenu" :class="'submenu-hook-'+index" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)">
                                <li v-for="child in item.children" v-if="child.hidden" :key="child.path" class="el-menu-item" style="padding-left: 40px; color: #fff;" :class="$route.path==child.path?'is-active':''" @click="$router.push(child.path)">
                                    {{child.name}}
                                </li>
                            </ul>
                        </template>
                        <template v-else>
                            <li class="el-submenu">
                                <div class="el-submenu__title el-menu-item" style="padding-left: 20px;height: 56px;line-height: 56px;padding: 0 20px;" :class="$route.path==item.children[0].path?'is-active':''" @click="$router.push(item.children[0].path)">
                                    <i :class="item.iconCls"></i>
                                </div>
                            </li>
                        </template>
                    </li>
                </ul>
            </aside>
  </el-col>
</el-row>
</template>

<script>
let data = () => {
        return {
            sysName: '后台管理系统',
            collapsed: false,
            sysUserName: '管理员',
            menuData: [
        {
          id: 1,
          name: "项目管理",
          level: 1,
          path: '1',
          children: [
            {
              id: 2,
              name: "项目进度",
              level: 2,
              path: '2',
              children: [
                {
                  id: 3,
                  name: "项目一",
                  level: 3,
                  path: '3',
                  children: [
                    {
                      id: 4,
                      name: "详细信息",
                      level: 4,
                      path: '4',
                      children: [
                        {
                          id: 5,
                          name: "详细信息",
                          level: 4,
                          path: '5',
                          children: [
                            {
                              id: 6,
                              name: "详细信息",
                              level: 4,
                              path: '6',
                              children: [
                                {
                                  id: 7,
                                  name: "详细信息",
                                  level: 4,
                                  path: '7',
                                  children: [
                                    {
                                      id: 8,
                                      name: "详细信息",
                                      level: 4,
                                      path: '8',
                                      children: [
                                        {
                                          id: 9,
                                          name: "详细信息",
                                          level: 4,
                                          path: '9',
                                          children: []
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
              name: "任务安排",
              level: 2,
              path: '10',
              children: []
            }
          ]
        },
        {
          id: 11,
          name: "数据统计",
          level: 1,
          path: '11',
          children: []
        },
        {
          id: 12,
          name: "人员管理",
          level: 1,
          path: '12',
          children: []
        }
      ]
        }
    }

    // let initMenu = function() {
    //     for(let i in this.$router.options.routes) {
    //         let root = this.$router.options.routes[i]
    //         if(root.hidden)
    //             continue
    //         let children = []
    //         for(let j in root.children) {
    //             let item = root.children[j]
    //             if(item.hidden)
    //                 continue
    //             children.push(item)
    //         }

    //         if(children.length < 1)
    //             continue
    //         this.menuData.push(root)
    //         root.children = children
    //     }
    // }
export default {
    data: data,
    methods: {
      //折叠导航栏
            collapse: function() {
                this.collapsed = !this.collapsed;
            },
            showMenu: function(i, status) {
                this.$refs.menuCollapsed.getElementsByClassName('submenu-hook-' + i)[0].style.display = status ? 'block' : 'none';
            },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style lang="scss" scoped="scoped">
.container {
        position: absolute;
        top: 0;
        bottom: 0;
        width: 100%;
        .header {
            height: 60px;
            line-height: 60px;
            background: #545c64;
            color: #fff;
            .userinfo {
                text-align: right;
                padding-right: 35px;
                float: right;
                .userinfo-inner {
                    cursor: pointer;
                    color: #fff;
                    img {
                        width: 40px;
                        height: 40px;
                        border-radius: 20px;
                        margin: 10px 0 10px 10px;
                        float: right;
                    }
                }
            }
            .logo {
                height: 60px;
                font-size: 22px;
                padding-left: 20px;
                padding-right: 20px;
                border-color: rgba(238, 241, 146, 0.3);
                border-right-width: 1px;
                border-right-style: solid;
                img {
                    width: 40px;
                    float: left;
                    margin: 10px 10px 10px 18px;
                }
                .txt {
                    color: #fff;
                }
            }
            .logo-width {
                width: 230px;
            }
            .logo-collapse-width {
                width: 60px;
            }
            .tools {
                padding: 0 23px;
                width: 14px;
                height: 60px;
                line-height: 60px;
                cursor: pointer;
            }
        }
        .main {
            display: flex;
            position: absolute;
            top: 60px;
            bottom: 0;
            overflow: hidden;
            aside {
                flex: 0 0 230px;
                width: 230px;
                /*侧边菜单*/
                .el-menu {
                    height: 100%;
                    background-color: #545c64;
                    /*选中列*/
                    .el-menu-item {
                        background-color: #545c64;
                    }
                    .el-submenu__title {
                        i {
                            color: #fff;
                        }
                    }
                }
                .el-menu:first-child {
                    overflow-y: auto !important;
                }
                .el-menu-collapsed li:hover {
                    background-color: #434a50;
                }
                /*当前选中菜单*/
                .is-opened {
                    color: #fff;
                    background-color: #fff;
                }
                .collapsed {
                    width: 60px;
                    .item {
                        position: relative;
                    }
                    .submenu {
                        position: absolute;
                        top: 0;
                        left: 60px;
                        z-index: 99999;
                        height: auto;
                        display: none;
                    }
                }
            }
            .menu-collapsed {
                flex: 0 0 60px;
                width: 60px;
            }
            .menu-expanded {
                flex: 0 0 230px;
                width: 230px;
            }
            .content-container {
                flex: 1;
                overflow-y: scroll;
                padding: 20px;
                background-color: #d3d7d4;
                .breadcrumb-container {
                    display: none;
                    .title {
                        width: 200px;
                        float: left;
                        color: #475669;
                    }
                    .breadcrumb-inner {
                        float: right;
                    }
                }
                .content-wrapper {
                    box-sizing: border-box;
                }
            }
        }
    }
</style>
