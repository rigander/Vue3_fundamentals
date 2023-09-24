<template>
    <div>
        <h1>Post Page</h1>
        <my-input
            :model-value="searchQuery"
            @update:model-value="setSearchQuery"
            placeholder="Search...."
            v-focus
        />
        <div class="app__btns">
            <my-button
                @click="showDialog"
            >
                Create Post
            </my-button>
            <my-select
                :model-value="selectedSort"
                @update:model-value="setSelectedSort"
                :options="sortOptions"
            />
        </div>
        <my-dialog v-model:show="dialogVisible">
            <post-form
                @create="createPost"
            />
        </my-dialog>
        <post-list
            :posts="sortedAndSearchedPosts"
            @remove="removePost"
            v-if="!isPostsLoading"
        />
        <div v-else>Идет загрузка...</div>
        <div v-intersection="loadMorePosts" class="observer"></div>
        <div class="page__wrapper">
            <div
                v-for="pageNumber in totalPages"
                :key="pageNumber"
                class="page"
                :class="{
              'current-page': page === pageNumber
            }"
                @click="changePage(pageNumber)"
            >
                {{ pageNumber }}
            </div>
        </div>
    </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/MyButton";
import axios from 'axios';
import MySelect from "@/components/UI/MySelect";
import MyInput from "@/components/UI/MyInput";
import {mapState, mapGetters, mapActions, mapMutations} from 'vuex'

export default {
    components: {
        MyInput,
        MySelect,
        MyButton,
        PostList, PostForm
    },
    data() {
        return {
            dialogVisible: false,
        }
    },
    methods: {
        ...mapMutations({
            setPage: 'post/setPage',
            setSearchQuery: 'post/setSearchQuery',
            setSelectedSort: 'post/setSelectedSort',
        }),
        ...mapActions({
            loadMorePosts: 'post/loadMorePosts',
            fetchPosts: 'post/fetchPosts'
        }),
        createPost(post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog() {
            this.dialogVisible = true;
        },
    },
    mounted() {
        this.fetchPosts();
    },
    computed: {
        ...mapState({
            posts: state => state.post.posts,
            isPostsLoading: state => state.post.isPostsLoading,
            selectedSort: state => state.post.selectedSort,
            searchQuery: state => state.post.searchQuery,
            page: state => state.post.page,
            limit: state => state.post.limit,
            totalPages: state => state.post.totalPages,
            sortOptions: state => state.post.sortOptions
        }),
        ...mapGetters({
            sortedPosts: 'post/sortedPosts',
            sortedAndSearchedPosts: 'post/sortedAndSearchedPosts'
        })
    },
    watch: {
        // page() {
        //   this.fetchPosts()
        // }
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
</style>