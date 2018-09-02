<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page, index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
            
        </swiper>
        
    </div>
</template>

<script>
    export default {
        name : 'HomeIcons',
        props:{
            list: Array
        },
        data(){
            return {
                swiperOption: {
                    autoplay:false
                }
            }
        },
        computed: {
            pages (){
                const pages = []
                this.list.forEach((item,idnex) => {
                    const page = Math.floor(idnex/8)
                    if(!pages[page]){
                        pages[page] = []
                    }

                    pages[page].push(item)
                    
                })

                return pages
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles';
    @import '~styles/mixins';
        .icons >>> .swiper-container
            height 0
            padding-bottom 50%
    .icons
        margin-top .1rem
    .icon
        float left
        width 25%
        height 0
        padding-bottom 25%
        overflow hidden
        position relative
        .icon-img
            position absolute
            top 0px
            left 0px
            right 0px
            bottom .44rem
            box-sizing border-box
            padding .1rem
            img
                height 100%
                display block
                margin 0 auto
        .icon-desc
            position absolute
            left 0px
            bottom 0px
            right 0px
            height .44rem
            line-height .44rem
            text-align center
            color $darkTextColor
            ellipsis()
            
</style>

