<template>
    <div class="app">
        <my-dialog show="true">
            <post-form
                @create="createPost"
            />
        </my-dialog>
        <post-list
            :posts="posts"
            @remove="removePost"
        />
    </div>
</template>

<script>
    import PostForm from "./components/PostForm";
    import PostList from "./components/PostList";
    import MyDialog from "./components/UI/MyDialog.vue";
    export default {
        components: {
            PostList, PostForm, MyDialog,
        },
        data() {
            return {
                posts: [
                    {id: 1, title: 'JavaScript', body: 'Описание поста'},
                    {id: 2, title: 'JavaScript 2', body: 'Описание поста 2'},
                    {id: 3, title: 'JavaScript 3', body: 'Описание поста 3'},
                ],
            }
        },
        methods: {
           createPost(post) {
            this.posts.push(post);
           },
           removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
           }
        }
    }
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app {
    padding: 20px;
}
</style>