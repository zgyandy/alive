<template>
    <div class="toydetail">
        <mt-navbar v-model="selected" value=1>
            <mt-tab-item id="1">娃娃详情</mt-tab-item>
            <mt-tab-item id="2">抓中记录</mt-tab-item>
            <mt-tab-item id="3">抓娃娃达人</mt-tab-item>
        </mt-navbar>
        <mt-tab-container v-model="selected">
            <mt-tab-container-item id="1">
                <ul class="detail">
                    <li>
                        <img src="../../assets/images/demo1.jpg" alt="">
                    </li>
                    <li>
                        <img src="../../assets/images/demo1.jpg" alt="">
                    </li>
                </ul>
            </mt-tab-container-item>
            <mt-tab-container-item id="2">
                <ul class="record">
                    <li v-for="(val,key) in arr" :key="key">
                        <div class="head-img">
                            <img slot="icon" src="../../assets/images/free.png">
                        </div>
                        <div class="right">
                            <div>昵称</div>
                            <div>时间记录</div>
                        </div>
                    </li>
                </ul>
            </mt-tab-container-item>
            <mt-tab-container-item id="3">
                <ul class="expert">
                    <li>
                        <img src="../../assets/images/demo1.jpg" alt="">
                    </li>
                    <li>
                        <img src="../../assets/images/demo1.jpg" alt="">
                    </li>
                </ul>
            </mt-tab-container-item>
        </mt-tab-container>
    </div>
</template>

<script>
export default {
  props: {
    toy_id: {
            default: Number
        }
    },
    data(){
        return {
            num: 1,
            selected: "1",
            name: "昵称",
            arr: 30,
        }
    }

};
</script>

<style lang="scss" scoped>
.toydetail {
    width: 6.9rem;
    margin: 0 0.3rem;
    .mint-navbar .mint-tab-item {
        font-size: .3rem;
        .is-selected {
            color: #0ff;
        }
    }
    .mint-tab-container-item {
        .detail {
            img {
                width: 100%;
            }
        }
        .expert {
            li {
                img {
                    width: 100%;
                }
            }
        }
        .record {
            background-color: #fff;
            height: 7rem;
            margin-bottom: 2rem;
            overflow-y: auto;
            li {
                height: .6rem;
                width: 6.9rem;
                display: flex;
                justify-content: space-between;
                align-items: center;
                border-bottom: 1px #ccc solid;
                .head-img {
                    height: .4rem;
                    width: .4rem;
                    overflow: hidden;                
                    border-radius: .2rem;
                    margin-right: .2rem;
                    img {
                        height: .4rem;
                        width: .4rem;
                    }
                }
                .right {
                    height: .6rem;
                    width: 6.4rem;
                    line-height: .6rem;
                    display: flex;
                    justify-content: space-between;
                }
            }
        }
    }
}
</style>
