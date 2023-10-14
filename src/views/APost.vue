<template>
    <div>
        <h1>A-Post Page {{ route.params.id }}</h1>
        <div>
            <ui>
                <li>userId = {{items.userId}}</li>
                <li>id = {{items.id}}</li>
                <li>title = {{items.title}}</li>
                <li>body = {{items.body}}</li>
            </ui>
        </div>
    </div>
</template>

<script setup>

import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import axios from 'axios'

const route = useRoute()
const id = parseInt(route.params.id)
console.log("ID"+id.value);

const items = ref({})
//const url = ref('https://jsonplaceholder.typicode.com/posts/1')
//const url = ref('https://jsonplaceholder.typicode.com/posts/' + route.params.id)
const url = ref('https://jsonplaceholder.typicode.com/posts/' + id.value)

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
onMounted(fetchPosts)
</script>

<style scoped></style>
