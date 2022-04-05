<template>
    
<div class="editor-page">
    <div class="container page">
        <div class="row">

            <div class="col-md-10 offset-md-1 col-xs-12">
                <form @submit.prevent="onSubmit">
                   
                        <fieldset class="form-group">
                            <input type="text" class="form-control form-control-lg" v-model="article.title" placeholder="Article Title">
                        </fieldset>
                        <fieldset class="form-group">
                            <input type="text" class="form-control" v-model="article.description" placeholder="What's this article about?">
                        </fieldset>
                        <fieldset class="form-group">
                            <textarea class="form-control" rows="8" v-model="article.body"
                                      placeholder="Write your article (in markdown)"></textarea>
                        </fieldset>
                        <fieldset class="form-group">
                            <input type="text" class="form-control" v-model="article.tagList" placeholder="Enter tags">
                            <div class="tag-list"></div>
                        </fieldset>
                        <button class="btn btn-lg pull-xs-right btn-primary">
                            Publish Article
                        </button>
                   
                </form>
            </div>

        </div>
    </div>
</div>


  </template>

<script>
    import {
        getArticless
    } from '@/api/article'
    export default {
        // 在路由匹配组件渲染之前会先执行中间件处理
        middleware: 'authenticated',
        name: 'EditorIndex',
        props: [''],
        data() {
            return {
                article: {
                    title: "",
                    description: "",
                    body: "",
                    tagList: ''
                }
            };
        },

        components: {},

        computed: {},

        beforeMount() {},

        mounted() {},

        methods: {
            async onSubmit() {
                console.log('dasda')
                const {
                    data
                } =
                await getArticless({
                    article: this.article
                })
                console.log('555', data)

                // 成功以后跳转到首页
                //this.$router.push('/')
            }
        },

        watch: {}

    }
</script>
<style lang='' scoped>

</style>