<template>
    <div>
        <h1>Post Page</h1>
        <input type="text" name="" id="">
        <button @click="fetchPosts()">แสดงผลข้อมูล</button>
        <div>
            <ui v-for="(post, index) in items" :key="index">
                <li>userId = {{post.userId}}</li>
                <li>id = {{post.id}}</li>
                <li>title = {{post.title}}</li>
                <!--<li>body = {{post.body}}</li>-->
                <li> 
                    <RouterLink :to="`/post/${post.id}`"> อ่านต่อ... </RouterLink> 
                </li>
            </ui>
        </div>
    </div>
</template>

<script setup>
import axios from 'axios'
import { ref } from 'vue'

const items = ref([])
const url = ref("https://jsonplaceholder.typicode.com/posts")
function fetchPosts() {
    axios
        .get(url.value)
        .then((response) => {
            items.value = response.data
        })
        .catch((err) => {
            console.log(err)
        });
}
//onMounted(fetchPosts)
</script>

<style scoped></style>
