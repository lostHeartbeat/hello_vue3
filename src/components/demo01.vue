<template>
    <div>
        <div> {{msg}} </div>
        <div v-html="html"></div>
        <div :title="title">鼠标放在上面看看</div>
        <!-- 动态参数=动态属性 -->
        <a :[myHref]="'http://www.baidu.com'">跳转百度</a><br>
        <a :[myHref]="url">进入哔哩哔哩</a>
    </div>
</template>

<script>
    export default {
        name:"demo01",
        data() {
            return {
                msg:"绑定信息",
                html:"<p>HTML</p>",
                title:"提示信息",
                myHref:"href",
                url:"https://bilibili.com"
            }
        },
        
    }
</script>

<style lang="less" scoped>

</style>