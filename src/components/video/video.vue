<template>
    <div class="video">
        <div class="desk">
            <!-- 视屏 -->
            <div class="box">
                <canvas id="video-canvas"></canvas>
            </div>
            <!-- 镜头切换 -->
            <div class="shot">
                <div class="eye iconfont icon-xiangjiqiehuan" @click.stop="change"></div>
            </div>
            <!-- 公告 -->
            <div class="notice" v-show="msgbl">
                <div class="shell">
                    <div class="iconf">
                        <span class="iconfont icon-xiaolaba"></span>
                    </div>
                    <div class="content">公告：消息内容</div>
                    <div class="iconf">
                        <span class="iconfont icon-cha2" @click.stop="hideNotice"></span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import JSMpeg from "../../assets/js/jsmpeg.min.js";

export default {
    name: "videos",
    data() {
        return {
            address: "222.64.232.244:9210", // 视频流地址
            camera_type: "main", // 视口规格
            ws_url: "",         // ws视频流地址
            poster_url: "",     // 
            player: {},         // player对象
            name: "kenan",      // 弹幕用户昵称
            msg: "",            // 弹幕消息
            playbl: true,      // 游戏中  
            msgbl: true,        // 公告显示
            getBl: false,       // 开始抓
        };
    },
    mounted() {
        this.ws_url = "ws://" + this.address + "/camera/" + this.camera_type;
        var canvas = document.getElementById("video-canvas");
        this.player = new JSMpeg.Player(this.ws_url, {
            canvas: canvas,
            audio: false,
            poster: this.poster_url,
            pauseWhenHidden: false,
            disableGl: true,
            chunkSize: 512 * 1024,
            videoBufferSize: 512 * 1024
        });
    },
    methods: {
        change() {
            // 切换视角
            if (this.camera_type == "main") {
                this.camera_type = "second";
            } else {
                this.camera_type = "main";
            }
            this.ws_url = "ws://" + this.address + "/camera/" + this.camera_type;
            this.player.stop();
            this.player.source.socket.close();
            this.player.source.url = this.ws_url;
            this.player.source.start();
            this.player.source.shouldAttemptReconnect = false;
            this.player.play();
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.video {
    overflow: hidden;
    width: 7.5rem;
    margin: 0 auto;
    .box {
        height: 9.06rem;
        width:7.5rem;
        overflow: hidden;
        #video-canvas {
            height: 9.06rem;
            width: 7.5rem;
        }
    }
    .desk {
        position: relative;
        .shot {
            height: 0.76rem;
            width: 0.89rem;
            position: absolute;
            right: 0;
            top: 3.6rem;
            background-color: rgb(249, 208, 15);
            border-radius: .38rem 0 0 .38rem;
            .eye {
                height: 0.5rem;
                width: 0.5rem;
                margin-left: 0.24rem;
                margin-top: 0.14rem;
                font-size: 0.45rem;
                color: rgb(255, 249, 239);
                line-height: .5rem;
            }
        }
        .notice {
            height: .58rem;
            width: 7.02rem;
            position: absolute;
            bottom: .12rem;
            left: 0;
            top: 8.28rem;
            background: url("../../assets/images/room/msgban.png") no-repeat;
            background-size: 100%;
            padding: 0 .24rem;
            .shell {
                height: .58rem;
                display: flex;
                justify-content: space-between;
                align-items: center;
                .iconf {
                    height: .58rem;
                    line-height: .58rem;
                    .iconfont {
                        font-size: .3rem;
                    }
                }
                .content {
                    height: .58rem;
                    line-height: .58rem;
                    margin-left: .1rem;
                    flex: 1;
                    -webkit-box-flex: 1;
                    text-align: left;
                    font-size: .26rem;
                }
            }
        }
    }
}
</style>
