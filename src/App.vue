<template>
    <div id="app">

        <h3>以下为组件</h3>
        <equallyElement :page="itemData_1" ></equallyElement>

        <h3>以下为组件 但 不同的元素名</h3>
        <differentElement :page="itemData_2" ></differentElement>

        <div class="no-component-container">
        
            <h3>非组件</h3>
            <div class="container box-1" v-if="show">
                <p>只可预览</p>
                <!-- <p class="content" data-text="预览面板" v-html="html1" ></p> -->
                <div class="content" data-text="预览面板" v-html="html1" ></div>
            </div>
            <div class="container box-2" v-else>
                <p>可编辑以下文本</p>
                <div ref="content" class="content" data-text="编辑面板" data-id="test" contenteditable="true" v-html="html2"></div>
            </div>

            <p class="btn" @click=" show = !show ">切换</p>
        </div>

    </div>
</template>

<script>
import equallyElement from "./components/equallyElement.vue"
import differentElement from "./components/differentElement.vue"

export default {
    name: "App",
    data() {
        return {
            itemData_1:{
                id: 1,
                content: "这是一条内容，测试v-html 在相同元素名下的区分"
            },
            itemData_2:{
                id: 1,
                content: "这是2条内容，测试v-html 在不同元素名下的区分"
            },

            show: true,
            html1: '这是第一个html字符串',
            html2: '这是第2个html字符串，加多点区分',
        };
    },
    components: {
        equallyElement,
        differentElement,
    },

    mounted() {}
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
h3{
    margin: 30px 0px;
}

.content{
    margin: 20px 0;
}
.btn{
    display: inline-block;
    width: 120px;
    background: #41b883;
    line-height: 36px;
    color: #fff;
    border-radius: 2px;
    font-size: 14px;
    user-select: none;
    cursor: pointer;
} 
</style>
