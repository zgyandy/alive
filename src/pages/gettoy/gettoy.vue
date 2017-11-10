<template>
    <div class="gettoy">
        <nav class="navbar">
            <div class="left">
                <span class="iconfont icon-svg-" @click.stop="go"></span>
            </div>
            <div class="right">
                
            </div>
        </nav>
        <!-- 视屏 -->
        <videos></videos>
        <!-- 玩具详情 -->
        <!-- <toydetail toyid="toyid"></toydetail> -->
        <!-- 蒙层 -->
        <cover v-show="false"></cover>
        <!-- 提示框 -->
        <tooltip :content="price" v-show="false"></tooltip>
    </div>
</template>

<script>
import cover from "@/components/common/cover.vue"
import tooltip from "@/components/tooltip/tooltip.vue"
import videos from "@/components/video/video.vue"
import toydetail from "@/components/toydetail/toydetail.vue"
export default {
    data () {
        return {
            toyid: '',      // 玩具id
            price:"本次消耗9金币"
        }
    },
    methods:{
        go(){
            this.$router.go(-1)
        }
    },
    components:{
        videos,toydetail,cover,tooltip
    }

}
</script>

<style scoped lang="scss">
    .gettoy {
        .navbar {
            height: .88rem;
            padding-left: .24rem;
            background: url("../../assets/images/room/nav.png") no-repeat;
            display: flex;
            justify-content: space-between;
            align-items: center;
            .left {
                .iconfont {
                    color: #fff;
                    font-size: .3rem;
                }
            }
        }
    }
</style>
