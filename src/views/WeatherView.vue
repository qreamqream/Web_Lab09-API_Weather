<template>
    <div>
ข้อมูล 5 วัน
Lat<input type="text" v-model="latt">
Long<input type="text" v-model="long">
<button></button>



<div v-for="(i,index) in items.list" :key="index">
{{ index+1 }}
dt = {{ i.dt }}
temp = {{ i.main.temp }}
"main": {{ i.weather[0].main }}
                    "description": "scattered clouds",
                    "icon": "03d"
</div>
{{ items.city }}
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const latt = ref();
const items = ref({})
const lat = ref("18.894764041581798");
const long = ref("99.0107757651001")
const apikey = ref("e7264bbff89e1c275b88eb34c3ebcc94")

const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat='+lat.value+'&lon='+long.value+'&cnt=5&appid='+apikey.value+ '&units=metric')

function fetchPosts() {
    axios
        .get(url.value)
        .then((response) => {
            items.value = response.data
            console.log(items.value);
        })
        .catch((err) => {
            console.log(err)
        });
}
onMounted(fetchPosts)
</script>

<style scoped>

</style>