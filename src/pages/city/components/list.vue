<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">北京</div>
                    </div>
                    
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wrapper"
                     v-for="item of hot"
                      :key="item.id">
                        <div class="button">{{item.name}}</div>
                    </div>
                    
                    
                </div>
            </div>
            <div class="area" 
            v-for="(item, key) of cities"
            :key="key"
            :ref="key"
            >
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div class="item border-bottom" 
                    v-for="innerItem of item"
                    :key="innerItem.id"
                    >{{innerItem.name}}</div>
                </div>
            </div>
            
        </div>
        
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default{
  name: 'CityList',
  props:{
      hot: Array,
      cities: Object,
      letter: String
  },
  watch: {
    letter () {
        if (this.letter) {
            const element = this.$refs[this.letter][0]
            this.scroll.scrollToElement(element)
        }
    }  
  },
  mounted () {
      this.scroll = new Bscroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
    .border-topbottom
        &:before
            border-color #cccccc
        &:after
            border-color #cccccc
    .list
        position absolute
        top 1.58rem
        left 0px
        right 0px
        bottom 0px
        overflow hidden
        .border-bottom
            &:before
                border-color #cccccc
        .title
            line-height .54rem
            background #eee
            padding-left .2rem
            color #666666
            font-size .26rem
        .button-list
            padding .1rem .6rem .1rem .1rem
            overflow hidden
            .button-wrapper
                float left
                width 33.33%
                .button
                    margin .1rem
                    text-align center
                    border .02rem solid #ccc
                    padding .1rem 0
                    border-radius .06rem
        .item-list
            .item
                line-height .76rem
                padding-left .2rem

        
</style>
