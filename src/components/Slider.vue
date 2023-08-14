<script setup>
import { ref, onMounted, onBeforeUnmount, nextTick } from "vue";

const items = ref([
  "https://plus.unsplash.com/premium_photo-1690489323622-6033f11bb1a4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1253&q=80",
  "https://images.unsplash.com/photo-1688437309979-f6b96dfa67af?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1171&q=80",
  "https://images.unsplash.com/photo-1688437309992-06ab64e3cbf8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
  "https://images.unsplash.com/photo-1571091717414-6c87e1c21aa4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
  "https://images.unsplash.com/photo-1533089860892-a7c6f0a88666?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80"

]);
let carousel = null;

const img = ref("https://images.unsplash.com/photo-1682685796063-d2604827f7b3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80")

const addNewItem = () => {
    items.value.push(img.value);
    carousel.destroy();
    nextTick(() => {
        carousel = new Flickity("#carousel",{});
    })
}


onMounted(() => {
    carousel = new Flickity("#carousel", {});
})

onBeforeUnmount(()=>{
    carousel.destroy();
    carousel = null
})



</script>
<template>
    <div class="flex flex-center justify-center">
        <input type="text" class="border text-black" v-model="img" />
        <button @click="addNewItem()" class="ml-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
        Add New Item
        </button>
    </div>

    <div class="mx-auto items" id="carousel">
        <div :style="`background-image:url(${item})`" class="item " v-for="(item, index) in items" :key="item">{{ index+1 }}</div>
    </div>
</template>

<style scoped>
.items {
    width: 600px;
    height: 500px;
    margin-top: 100px;
}
.item{
    width: 600px;
    height: 500px;
    background-size: cover;
}
</style>