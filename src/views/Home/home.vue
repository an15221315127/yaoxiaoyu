<template>
    <div class="home">
       <div class="header">
           <van-image
                   round
                   class="avatar"
                   src="https://img.yzcdn.cn/vant/cat.jpeg"
           />
           <van-tabs :border="false" background="transparent" color="#FFA70D" class="tabs" v-model="active" title-active-color="#FFA70D" title-inactive-color="#999999">
               <van-tab title="关注" />
               <van-tab title="推荐" />
               <van-tab title="话题" />
           </van-tabs>
           <van-icon size="24" class="search" name="search" />
       </div>
        <van-pull-refresh class="box" v-model="refreshing" @refresh="onRefresh">
            <van-list
                    v-model="loading"
                    :finished="finished"
                    finished-text="没有更多了"
                    @load="onLoad"
            >
                <an-block :current-obj="item" :current-index="index" v-for="(item,index) in list" :key="index"/>
            </van-list>
        </van-pull-refresh>

    </div>
</template>

<script>
    import AnBlock from "@/components/block/an-block";
    export default {
        name: "home",
        components: {AnBlock},
        data(){
            return {
                active:'',
                list:[],
                loading: false,
                finished: false,
                refreshing: false,
            }
        },
        watch:{

        },
        methods:{
            onLoad() {
                setTimeout(() => {
                    if (this.refreshing) {
                        this.list = [];
                        this.refreshing = false;
                    }
                    for (let i = 0; i < 10; i++) {
                        this.list.push({
                            star_status:0,
                            star_num:3214,
                            tip_status:0,
                            tip_num:4432,
                        });
                    }
                    this.loading = false;

                    if (this.list.length >= 40) {
                        this.finished = true;
                    }
                }, 1000);
                console.log(this.list,'菏泽...')
            },
            onRefresh() {
                // 清空列表数据
                this.finished = false;

                // 重新加载数据
                // 将 loading 设置为 true，表示处于加载状态
                this.loading = true;
                this.onLoad();
            },
        }
    }
</script>

<style lang="less" scoped>
.home{
    height: 100%;
    background: url("../../assets/icon/bg.png");
    background-repeat: no-repeat;
    background-size: 100% 100%;
    padding-top: 8px;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 50px;
        overflow: hidden;
        flex-shrink: 0;
        .avatar{
            width:35px;
            height:35px;
            margin-left: 15px;
        }
        .tabs{
            width: 220px;
            margin:auto;
            /deep/ .van-tab{
                font-size: 18px;
            }
            /deep/ .van-tab--active{
                font-size: 21px;
            }
        }
        .search{
            margin-left: auto;
            margin-right: 15px;
        }
    }
    .box{
        flex:1;
        overflow-y: auto;
    }

}
</style>
