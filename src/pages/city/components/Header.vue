<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <div class="iconfont back-icon">&#xe624;</div>
        </router-link>
        
    </div>
</template>

<script>
export default{
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
    .header
    position relative
        height $headerHight
        line-height $headerHight
        overflow hidden
        text-align center
        color #fff
        background $bgColor
        font-size .32rem
        .back-icon{
            position absolute
            top 0px
            left 0px
            width .64rem
            text-align center
            font-size .4rem
            color #fff
        }
</style>
