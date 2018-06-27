<template>
  <div id="app">
    <app-index/>




    <footer>
      <div class="content">
        <a @click="redirect(item.link)" class="link" :class="{active:index==selected}" v-for="item,index in footData">
          <i :class="item.icon"></i>
          <i v-if="index==2" class="icon-midbg"></i>
          <div class="txt">{{item.name}}</div>
        </a>
      </div>
    </footer>


  </div>
</template>

<script>
import appIndex from './components/activate/index'

export default {
  name: 'App',
  components: {
    appIndex
  },
  props: {
    selected: 0
  },
  data: function () {
    return {
      drawerData: [
        {name: "消息中心", link: "/pages/my/details.html"},
        {name: "意见反馈", link: "/pages/my/details.html"},
        {name: "设置", link: "/pages/my/setting.html"},
      ],
      footData: [
        {name: "首页", icon: "icon-home", link: "/pages/index/index.html"},
        {name: "资讯", icon: "icon-news", link: "/pages/news/index.html?channelId=0"},
        {name: "百科", icon: "icon-cyclopedia", link: "/pages/ency/index.html"},
        {name: "活动", icon: "icon-activity", link: "/pages/activity/index.html?channelId=1"},
        {name: "活化馆", icon: "icon-activate", link: "/pages/activate/index.html"}
      ]
    }
  },
  methods: {
    redirect(href){
      sessionStorage.removeItem('indexData')
      sessionStorage.removeItem('newsData')
      sessionStorage.removeItem('activityData')
      window.location.href = href
    }
  }
}
</script>

<style>

</style>
