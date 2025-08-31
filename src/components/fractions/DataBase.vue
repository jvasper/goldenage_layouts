<script setup>
import { inject, ref } from 'vue'
let page = ref('citizines')
let database = ref({
    "citizines": {
        tittle: 'Граждане',
        tableHeader: ['Имя и фамилия', 'Организация', 'Тел.номер', 'Розыск', 'Аресты', 'Статус в сети'],
        base: [
            {
                name: "Andreas Coolman",
                fraction: "LSPD",
                phone: "223333",
                search: 1,
                arests: 5,
                status: 1,
            },
            {
                name: "Andreas Coolman",
                fraction: "LSPD",
                phone: "223333",
                search: 3,
                arests: 5,
                status: 0,
            },
            {
                name: "Andreas1 Coolman",
                fraction: "LSPD",
                phone: "223333",
                search: 3,
                arests: 5,
                status: 0,
            },
        ]
    },
    "cars": {
        tittle: 'Машины',
        tableHeader: ['Марка', 'Владелец', 'Гос.Номер', 'VIN'],
        base: [
            {
                name: "Rolls Royce Cullinan",
                owner: "Andreas Coolman",
                number: '11XXX111',
                vin: '1'
            },
            {
                name: "Rolls Royce Cullinan",
                owner: "Andreas Coolman",
                number: '11XXX111',
                vin: '1'
            },
            {
                name: "Rolls Royce Cullinan",
                owner: "Andreas Coolman",
                number: '11XXX111',
                vin: '1'
            },
        ]
    }
})
let citizenes = ref([
    {
        name: "Andreas Coolman",
        fraction: "LSPD",
        phone: "223333",
        search: 3,
        arests: 5,
        status: 0,
        lastEntry: '21 '
    }
])
</script>
<template>
    <p class="subtittle">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo </p>
    <div class="tittle_buttons">
        <button v-for="(i, key) in database" @click="page = key">{{ i.tittle }}</button>
    </div>
    <div class="search_input">
        <img src="../../assets/search.svg" alt="">
        <input type="text" name="" id="" placeholder="Введите значение для поиска">
    </div>
    <div class="colleagues_table">
        <div class="table_row tittle">
            <div class="table_column" v-for="i in database[page].tableHeader">{{ i }}</div>
        </div>
        <div class="table_wrapper">
            <div v-for="(player, index) in database[page].base" :key="index" class="table_row">
                <!-- <div class="table_column" v-for="(i, key) in player" v-if="key != 'status'">{{ i }}</div> -->
                <div class="table_column" v-for="(i, key) in player">
                    <p v-if="key != 'search'">{{ key === 'status' ? (player.status === 1 ? 'Сейчас в игре' : 'Не в сети') : i }}</p>
                    <div class="star" v-if="key === 'search'"><svg v-for="i in player.search"
                            xmlns="http://www.w3.org/2000/svg" width="13" height="12" viewBox="0 0 13 12" fill="none">
                            <path
                                d="M5.54748 1.48784C5.84683 0.566529 7.15024 0.566531 7.44959 1.48784L8.07013 3.39767C8.20401 3.8097 8.58796 4.08865 9.02119 4.08865H11.0293C11.998 4.08865 12.4008 5.32827 11.6171 5.89767L9.99249 7.07801C9.642 7.33266 9.49535 7.78402 9.62922 8.19605L10.2498 10.1059C10.5491 11.0272 9.49463 11.7933 8.71092 11.2239L7.08632 10.0436C6.73583 9.78893 6.26124 9.78893 5.91075 10.0436L4.28615 11.2239C3.50244 11.7933 2.44796 11.0272 2.74731 10.1059L3.36785 8.19605C3.50173 7.78402 3.35507 7.33266 3.00458 7.07801L1.37998 5.89767C0.596266 5.32827 0.999043 4.08865 1.96777 4.08865H3.97588C4.40911 4.08865 4.79306 3.80969 4.92694 3.39767L5.54748 1.48784Z"
                                fill="#D9D9D9" fill-opacity="1" />
                        </svg><svg v-for="i in 5 - player.search" xmlns="http://www.w3.org/2000/svg" width="13"
                            height="12" viewBox="0 0 13 12" fill="none">
                            <path
                                d="M5.54748 1.48784C5.84683 0.566529 7.15024 0.566531 7.44959 1.48784L8.07013 3.39767C8.20401 3.8097 8.58796 4.08865 9.02119 4.08865H11.0293C11.998 4.08865 12.4008 5.32827 11.6171 5.89767L9.99249 7.07801C9.642 7.33266 9.49535 7.78402 9.62922 8.19605L10.2498 10.1059C10.5491 11.0272 9.49463 11.7933 8.71092 11.2239L7.08632 10.0436C6.73583 9.78893 6.26124 9.78893 5.91075 10.0436L4.28615 11.2239C3.50244 11.7933 2.44796 11.0272 2.74731 10.1059L3.36785 8.19605C3.50173 7.78402 3.35507 7.33266 3.00458 7.07801L1.37998 5.89767C0.596266 5.32827 0.999043 4.08865 1.96777 4.08865H3.97588C4.40911 4.08865 4.79306 3.80969 4.92694 3.39767L5.54748 1.48784Z"
                                fill="#D9D9D9" fill-opacity="0.15" />
                        </svg></div>
                    <div class="circle" v-if="key === 'status'"
                        :style="{ background: player.status === 1 ? '#D9D9D9' : '#1F1F1F' }">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>