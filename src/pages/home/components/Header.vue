<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市景点游玩主题
        </div>
        <router-link to="city">
            <div class="header-right">{{city}}
                <span class="iconfont arrow-icon">&#xe64a;</span>
            </div>
        </router-link>
    </div>
</template>

<script>
export default{
  name: 'HomeHeader',
  props: {
      city:String
  }
}
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles';
    .header
        display flex
        height $headerHight
        line-height $headerHight
        background $bgColor
        color #fff
        .header-left
            width .64rem
            float left
            .back-icon
                text-align center
                font-size .4rem
        .header-input
            flex 1
            background #ffffff
            border-radius .1rem
            margin-top .12rem
            height .64rem
            line-height .64rem
            margin-left .2rem
            color #ccc
            padding-left .2rem
        .header-right
            width 1.24rem
            float right
            text-align center
            color #fff
            .arrow-icon
                margin-left -.04rem
                font-size .24rem
</style>
