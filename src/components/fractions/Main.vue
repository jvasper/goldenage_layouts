<script setup>
import { provide, inject } from 'vue'

const pageState = inject('pageState')
const pages = inject('pagesData')
</script>

<template>
  <div class="pages_buttons">
    <div class="page_button" v-for="item in pages" @click="pageState?.setPage(item.name)" :key="item.name">
      <div class="line"></div>
      <img :src="`/src/assets/${item.ico}.svg`" :alt="item.tittle">
      <p>{{ item.tittle }}</p>
    </div>
  </div>
</template>