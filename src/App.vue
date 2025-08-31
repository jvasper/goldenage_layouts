<script setup>
import { ref, provide, inject, computed } from 'vue'
import Main from './components/fractions/Main.vue'
import Colleagues from './components/fractions/Colleagues.vue'
import DataBase from './components/fractions/DataBase.vue'

const page = ref('main')
const pages = [
  {
    name: "colleagues",
    tittle: "Коллеги",
    ico: "user"
  },
  {
    name: "settings",
    tittle: "Настройки",
    ico: "settings"
  },
  {
    name: "stock",
    tittle: "Склад",
    ico: "boxes"
  },
  {
    name: "prize",
    tittle: "Премирование",
    ico: "prize"
  },
  {
    name: "blacklist",
    tittle: "Черный список",
    ico: "blacklist"
  },
  {
    name: "balance",
    tittle: "Управление балансом",
    ico: "dollar"
  },
  {
    name: "deliverycars",
    tittle: "Доставка транспорта",
    ico: "cars"
  },
  {
    name: "money",
    tittle: "Финансы",
    ico: "dollar"
  },
  {
    name: "database",
    tittle: "База данных",
    ico: "bd"
  },
  {
    name: "challanges",
    tittle: "Вызовы",
    ico: "challanges"
  },
  {
    name: "supply",
    tittle: "Поставки",
    ico: "boxes"
  },
  {
    name: "camera",
    tittle: "Система видеонаблюдения",
    ico: "camera"
  }
]
provide('pagesData', pages)
provide('pageState', {
  page,
  setPage: (newPage) => {
    page.value = newPage
  }
})
</script>

<template>
  <div class="image-container">
    <img class="tablet_image" src="./assets/tablet.svg" alt="">
    <div class="tablet_wrapper">
      <div class="tablet_content">

        <div class="top_content">
          <div>
            <p>12:22</p>
            <img src="./assets/location.svg" alt="">
          </div>
          <div>
            <img src="./assets/signal.svg" alt="">
            <img src="./assets/wifi.svg" alt="">
            <img src="./assets/power.svg" alt="">
          </div>
        </div>
        <div class="fraction_tittle">
          <div>
            <h1 v-if="page === 'main'">Federal Investigation Bureau</h1>
            <h1 v-else><button @click="page = 'main'"><img src="./assets/arrow.svg" alt=""></button>{{pages.find(p => p.name === page).tittle
              }}</h1>
            <p v-if="page === 'main'">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo </p>
          </div>
          <div class="player_info">
            <div>
              <p>Игрок</p>
              <h1>Andreas Coolman</h1>
            </div>
            <img src="./assets/avatar.svg" alt="">
          </div>
        </div>
        <Main msg="Vite + Vue" v-if="page === 'main'" />
        <Colleagues msg="Vite + Vue" v-if="page === 'colleagues'" />
        <DataBase msg="Vite + Vue" v-if="page === 'database'" />
        <div class="home_button">
          <div></div>
        </div>
      </div>
    </div>
  </div>
</template>