<template>
    <div class="content">
        <div class="top">
            <van-image
                    round
                    class="avatar"
                    src="https://img.yzcdn.cn/vant/cat.jpeg"
            />
            <span class="name one-txt-cut">啊一啾啾</span>
            <img class="more" src="@/assets/icon/icon_details_more.png" alt="">
        </div>
        <p class="text txt-cut">
            729声工场， 创始于2005年7月29日，原名7
            29配音组。2016年7月29日，729配音组正式
            更名729声工场，发展成为一支 专也，729配音组正式
            更名729声工场，发展成为一支 专也
        </p>
        <div class="view">
            <div class="play">
                <img src="@/assets/icon/icon_boardcast.png" alt="">
            </div>
            <div class="bottom">
                <span class="time">01:24</span>
                <div class="valume">
                    <img src="@/assets/icon/icon_mute.png" alt="">
                </div>
            </div>
        </div>
        <div class="tags">
            #话题名称最长可有十二个字 >
        </div>
        <div class="controller">
            <div class="tab">
                <img src="@/assets/icon/icon_share.png" alt="">
                <span>4568</span>
            </div>
            <div class="tab" @click="changeTopStatus">
                <img :src="!currentObj.tip_status?require('@/assets/icon/icon_unpressed_dislike.png'):require('@/assets/icon/icon_pressed_dislike.png')" alt="">
                <span>{{currentObj.tip_num}}</span>
            </div>
            <div class="tab">
                <img src="@/assets/icon/icon_comment.png" alt="">
                <span>4568</span>
            </div>
            <div class="tab" @click="changeStarStatus">
                <img :src="!currentObj.star_status?require('@/assets/icon/icon_unpressed_thumds-up.png'):require('@/assets/icon/icon_pressed_thumds-up.png')" alt="">

                <span>{{currentObj.star_num}}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "an-block",
        props:['currentObj','currentIndex'],
        methods:{
            changeTopStatus(){
                this.currentObj.tip_status = !this.currentObj.tip_status;
                this.currentObj.tip_num += this.currentObj.tip_status ? 1 :-1;
            },
            changeStarStatus(){
                this.currentObj.star_status = !this.currentObj.star_status;
                this.currentObj.star_num += this.currentObj.star_status ? 1 :-1;
            }
        }

    }
</script>

<style lang="less" scoped>
    .content{
        width:345px;
        padding-bottom: 12px;
        background:rgba(255,255,255,1);
        box-shadow:0px 2px 5px 0px rgba(0,0,1,0.3);
        border-radius:5px;
        margin:15px;
    .top{
        display: flex;
        align-items: center;
        justify-content: flex-start;
        padding-top: 10px;
    .avatar{
        width:25px;
        height:25px;
        margin-left: 10px;
        margin-right: 11px;
    }
    .name{
        font-size:15px;
        font-family:Source Han Sans CN;
        font-weight:400;
        color:rgba(0,0,0,1);
        width: 250px
    }
    .more{
        width:15px;
        height:3px;
        margin-left: auto;
        margin-right: 15px;
    }
    }
    .text{
        width:314px;
        font-size:16px;
        font-family:Source Han Sans CN;
        font-weight:400;
        color:rgba(0,0,0,1);
        line-height:24px;
        margin:13px 16px;
        -webkit-line-clamp: 3;
    }
    .view{
        width:320px;
        border-radius:10px;
        height: 215px;
        box-sizing: border-box;
        background: url("../../assets/icon/WechatIMG2.jpeg");
        background-size: 100% 100%;
        background-repeat: no-repeat;
        margin:0 auto 12px auto;
        padding-top: 93px;
        padding-bottom: 8px;
    .play{
        width:30px;
        height:30px;
        margin:0 auto 72px auto;
    img{
        width: 100%;
        height: 100%;
    }
    }
    .bottom{
        display: flex;
        align-items: center;
        justify-content: space-between;
    .time{
        font-size: 12px;
        color: white;
        margin-left: 10px;
    }
    .valume{
        margin-right: 10px;
        width:17px;
        height:13px;
    img{
        width: 100%;
        height: 100%;
    }
    }
    }
    }
    .tags{
        background:rgba(0,0,0,1);
        opacity:0.1;
        border-radius:5px;
        display: inline-block;
        color: #999999;
        padding: 4px 8px;
        margin-left: 15px;
        margin-bottom: 13px;
    }
    .controller{
        display: flex;
        align-items: center;
        justify-content: flex-end;
        padding-right: 16px;
        box-sizing: border-box;
    .tab{
        display: flex;
        align-items: center;
        margin-left: 24px;
    img{
        width:19px;
        height:19px;
    }
    span{
        font-size: 12px;
        color: #BBBBBB;
        margin-left: 6px;
    }
    }
    }
    }
</style>
