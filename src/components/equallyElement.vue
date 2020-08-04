<template>
    <div class="hello">
        <div class="container box-1" v-if="show">
            <p>只可预览</p>
            <!-- <p class="content" data-text="预览面板" v-html="html1" ></p> -->
            <div class="content" data-text="预览面板" v-html="html1" ></div>
        </div>
        <div class="container box-2" v-else>
            <p>可编辑以下文本</p>
            <div ref="content" class="content" data-text="编辑面板" data-id="test" contenteditable="true" v-html="html2"></div>
        </div>

        <p class="btn" @click=" switchoverEv ">切换</p>
    </div>
</template>

<script>
export default {
    name: "HelloWorld",
    data() {
        return {
            show: true,
            html1: null,
            html2: null,
        }
    },
    props: {
        page: {},
    },

    methods: {

        switchoverEv(){

            this.show = !this.show

            console.log( this.html1, this.html2, this.$refs.content && this.$refs.content.innerHTML )
        },

    },

    created(){
        this.html2 = this.html1 = this.page.content
    },
};
</script>


<style scoped>
.hello{
    padding: 16px 0;
    border: 1px solid #bbb;
    margin-bottom: 2px;
}
</style>
