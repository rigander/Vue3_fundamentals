<template>
<div>
    <h1>{{ likes }}</h1>
    <button
        @click="addLike"
    >Add Like</button>
<!--        <h1>Posts Page</h1>-->
<!--        <my-input-->
<!--                v-model="searchQuery"-->
<!--                placeholder="Search..."-->
<!--                v-focus-->
<!--        />-->
<!--        <div class="app__btns">-->
<!--            <my-button-->
<!--                    @click="showDialog"-->
<!--            >Create Post-->
<!--            </my-button>-->
<!--            <my-select-->
<!--                    v-model="selectedSort"-->
<!--                    :options="sortOptions"-->
<!--            />-->
<!--        </div>-->
<!--        <my-dialog-->
<!--                v-model:show="dialogVisible"-->
<!--        >-->
<!--            <post-form-->
<!--                    @create="createPost"-->
<!--            />-->
<!--        </my-dialog>-->
<!--        <post-list-->
<!--                :posts="sortedAndSearchedPosts"-->
<!--                @remove="removePost"-->
<!--                v-if="!isPostsLoading"-->
<!--        />-->
<!--        <div-->
<!--                v-else-->
<!--        >Loading Posts...</div>-->
<!--        <div v-intersection="loadMorePosts" class="observer"-->
<!--        ></div>-->
</div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from "axios";
import MySelect from "@/components/UI/MySelect.vue";
import {ref} from "vue";
export default {
    components: {
        MySelect,
        MyButton,
        PostList, PostForm
    },
    data() {
        return {
            dialogVisible: false,
            sortOptions: [
                {value: 'title', name: 'By name'},
                {value: 'body', name: 'By description'},
                {value: 'id', name: 'By Id'},
            ]
        }
    },
    methods: {
        createPost(post){
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog(){
            this.dialogVisible = true;
        },
        changePage(pageNumber){
            this.page = pageNumber
        },
        async fetchPosts() {
            try {
                this.isPostsLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
                    params: {
                        _page: this.page,
                        _limit: this.limit
                    }
                });
                this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit);
                this.posts = response.data;
            }catch (e){
                alert('Error')
            } finally {
                this.isPostsLoading = false;
            }
        },
    },
    setup(props) {
        const likes = ref(2)
        const addLike = () => {
            likes.value += 1
        }
        return {
            likes,
            addLike
        }
    }
}
</script>

<style>

body{
    background-color: #3c3f41;
    color: aliceblue;
    font-size: 30px;
}
.app__btns{
    display: flex;
    justify-content: space-between;
}
.page__wrapper{
    display: flex;
    margin-top: 15px;
}
.page__wrapper:hover{
    cursor: pointer;
}
.page{
    border: 1px solid black;
    padding: 10px;
}
.current_page{
    border: 3px solid green;
    border-radius: 2px;
    background-color: #2b2b2c;
}
.observer{
    height: 30px;
    background: green;
}
button{
    width: 100px;
    height: 30px;
    font-size: 18px;
    font-weight: bold;
    color: chocolate;
}
</style>