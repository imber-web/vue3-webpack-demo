<template>
  <div class="about">
    <div class="text">This is an about page</div>
    <!-- <div class="item" v-for="(item, index) in list" :key="index">
      <div>
        {{ item }}Lorem ipsum dolor sit amet, consectetur adipisicing elit.
        Laborum, facilis? Ipsum, dolor iure, explicabo consequatur, dolore atque
        omnis excepturi distinctio magni officia unde accusantium odit quis eius
        magnam quas saepe?
      </div>
    </div> -->
    <RecycleScroller
      class="scroller"
      :items="list"
      :item-size="32"
      key-field="id"
      v-slot="{ item }"
    >
      <div class="user">
        {{ item.name }}
      </div>
    </RecycleScroller>
  </div>
</template>
<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { RecycleScroller } from 'vue-virtual-scroller'
import 'vue-virtual-scroller/dist/vue-virtual-scroller.css'
const list = ref()
onMounted(() => {
  new Promise((resolve) => {
    setTimeout(() => {
      resolve([1, 2, 3, 4, 5, 6, 7, 8, 9])
    }, 1000)
  }).then((res) => {
    list.value = res
  })
})
</script>
<style>
.text {
  font-size: 20px;
}
.item {
  background-color: pink;
  margin: 16px;
}
.user {
  height: 100px;
  width: 100%;
  background-color: pink;
}
</style>
