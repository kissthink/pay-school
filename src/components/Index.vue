<template>
  <div>
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
    <tabbar style="position:fixed">
      <tabbar-item v-for="(item,index) in tabbars" @on-item-click="item_click" :key="index" :link="{name:item.route_name,replace:true}" :selected="route_name===item.route_name?true:false">
        <span slot="icon" class="iconfont tabbar-icon" :class="item.icon"></span>
        <span slot="icon-active" class="iconfont tabbar-icon" :class="item.icon_active"></span>
        <span slot="label">{{item.name}}</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>
<script>
import { Tabbar, TabbarItem } from 'vux'
export default {
  components: {
    Tabbar,
    TabbarItem
  },
  data () {
    return {
      route_name: '',
      selected: 1,
      tabbars: [
        {
          name: '首页',
          route_name: 'home',
          icon: 'icon-home',
          icon_active: 'icon-homefill'
        },
        {
          name: '会员',
          route_name: 'vip',
          icon: 'icon-crown',
          icon_active: 'icon-crownfill'
        },
        {
          name: '我的课程',
          route_name: 'courses',
          icon: 'icon-news_hot_light',
          icon_active: 'icon-news_hot_fill_light'
        },
        /* {
          name: '圈子',
          route_name: 'circle',
          icon: 'icon-circle',
          icon_active: 'icon-circlefill'
        }, */
        {
          name: '我的',
          route_name: 'member',
          icon: 'icon-my',
          icon_active: 'icon-myfill'
        }
      ]
    }
  },
  mounted () {
    this.route_name = this.$route.name
  },
  methods: {
    item_click (index) {
      let item = this.tabbars[index]
      if (item.route_name === this.route_name) {
        console.log('123')
        document.body.scrollTop = 0
        document.documentElement.scrollTop = 0
      }
    }
  }
}
</script>

<style lang="less">
.tabbar-icon {
  font-size: 23px;
  line-height: 27px;
}
</style>