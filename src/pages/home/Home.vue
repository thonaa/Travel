<template>
    <div>
        <home-header :city="city"></home-header>
        <home-swiper :list="swiperList"></home-swiper>
        <home-icons :list="iconList"></home-icons>
        <home-recommend :list="recommendList"></home-recommend>
        <home-weekend :list="weekendList"></home-weekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/recommend'
import HomeWeekend from './components/weekend'
import axios from 'axios'
export default{
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend,
  },
  data(){
      return{
          city:'',
          iconList:[],
          recommendList:[],
          swiperList:[],
          weekendList:[]
      }
  },
  mounted () {
      this.getHomeInfo()
  },
  methods: {
      getHomeInfo(){
          axios.get('/api/index.json')
          .then(this.getHomeInfoSucc)
      },
      getHomeInfoSucc(res){
          res = res.data
          if(res.data && res.ret){
              console.log(res)
              const data = res.data
              this.city = data.city
              this.iconList = data.iconList
              this.recommendList = data.recommendList
              this.swiperList = data.swiperList
              this.weekendList = data.weekendList
          }
      }
  }
}
</script>
