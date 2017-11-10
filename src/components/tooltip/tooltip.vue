<template>
    <div class="tooltip">
        <div class="content">
            <div class="title layout">{{title}}</div>
            <div class="msg layout">{{content}}</div>
            <div class="button">
                <div class="cancel layout">取消</div>
                <div class="sure layout">知道了</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        title:{
            default: "提示"
        },
        content:{
            default: '本次游戏将消耗9金币'
        }
    }
}
</script>

<style scoped lang="scss">
    .tooltip {
        height: 3.7rem;
        width: 5rem;
        position: fixed;
        left: 50%;
        top: 50%;
        transform: translate(-50%,-50%);
        border-radius: .2rem;
        -webkit-border-radius: .2rem;
        background-color: rgb(244,152,33);
        padding: .1rem;
        .content {
            height: 3.5rem;
            width: 5rem;
            background-color: rgb(255,231,189);
            border-radius: .2rem;
            -webkit-border-radius: .2rem;
            margin-top: .2rem;
            box-shadow: 0 -.08rem .1rem rgb(192,108,0);
            -webkit-box-shodow: 0 -.08rem .1rem rgb(192,108,0);
            overflow: hidden;
            .layout {
                text-align: center;
            }
            .title {
                height: .5rem;
                width: 5rem;
                margin-top: .5rem;
                line-height: .5rem;
                font-size: .36rem;
                font-weight: bold;
            }
            .msg {
                height: .3rem;
                width: 5rem;
                margin-top: .25rem;
                line-height: .3rem;
                font-size: .26rem;
            }
            .button {
                height: .8rem;
                width: 5rem;
                display: flex;
                justify-content: space-around;
                margin-top: .57rem;
                div{
                    height: .8rem;
                    width: 2rem;
                    border-radius: .4rem;
                    font-size: .36rem;
                    font-weight: bold;
                    line-height: .8rem;
                    color: #fff;
                    // text-shadow: 0 2px 16px #000, 0 0 1px #000, 0 0 1px #000;
                }
                .cancel {
                    background-color: rgb(186,66,12);
                }
                .sure {
                    background-color: rgb(248,201,126);
                }
            }
        }
    }
</style>
