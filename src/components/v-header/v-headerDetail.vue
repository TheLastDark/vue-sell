<template>
    <div id="r4" v-show="visible">
        <div id="r4r1-content">
            <div id="r4r1r1-title">{{seller.name}}</div>
            <!--<star id="r4r1r2-star" :size="48" :score="seller.score"></star>-->
            <div id="r4r1r3-supportTitle">
                <div class="line"></div>
                <div class="words">优惠信息</div>
                <div class="line"></div>
            </div>
            <div id="r4r1r4-support" v-if="seller.supports">
                <div v-for="(item,index) in seller.supports" class="flex">
                    <!--<icon :type="item.type" style="width:24px;margin:2px 10px;"></icon>-->
                    {{item.description}}
                </div>
            </div>
            <div id="r4r1r5-bulletinTitle">
                <div class="line"></div>
                <div class="words">商家公告</div>
                <div class="line"></div>
            </div>
            <div id="r4r1r6-bulletin">{{seller.bulletin}}</div>
        </div>
        <div id="r4r2-button">
            <div class="iconfont icon-close" @click="visible=false"></div>
        </div>
    </div>
</template>

<script>/* eslint-disable */
    // import Star from '../star/star'
    // import Icon from '../icon/icon'
    export default {
        name: "headerDetail",
        props:{
            seller:Object
        },
        data(){
            return{
                visible: false,
            }
        },
        methods:{
            show(){
                this.visible=true;
            }
        },
        components:{
            // Star,
            // Icon,
        }
    }
</script>

<style scoped lang="stylus">
    @import "common/stylus/var.styl"
    .words
        font-size:$fontSize*1.2
        padding:$padding
    .line
        line-height:0px
        height:0px
        flex:1
        border-bottom:1px solid rgba(255,255,255,0.2)
    .flex
        display:flex
        align-items:center
    #r4
        z-index:100
        height: 100%
        width:100%
        top:0
        left:0

        position:fixed
        overflow:auto

        display:flex
        flex-flow:column

        box-sizing:border-box
        padding:$fontSize*4 $fontSize*1.5 0 $fontSize*1.5

        color: white
        background-color:rgba(0,0,0,0.8)
        line-height:$fontSize*1.5
    #r4r1-content
        flex:1
        #r4r1r1-title
            font-size:$fontSize*1.5
            text-align:center
        #r4r1r2-star
            padding:$padding
            text-align:center
        #r4r1r4-support
            padding-bottom:$padding*1
        #r4r1r6-bulletin
            padding-bottom:$padding*2
        #r4r1r3-supportTitle
            display:flex
            flex-flow:row
            align-items:center
        #r4r1r5-bulletinTitle
            display:flex
            flex-flow:row
            align-items:center
    #r4r2-button
        flex:0
        text-align:center
        line-height:$fontSize*4
        border-top:1px solid gray
        .icon-close
            border:1px solid gray
            border-radius:$fontSize
            display:inline-block
            line-height:$fontSize*2
            width:$fontSize*2
</style>
