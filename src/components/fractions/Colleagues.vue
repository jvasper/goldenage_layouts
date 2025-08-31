<script setup>
import { inject, ref } from 'vue'
let players = ref([
    {
        id: 1,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 0,
        lastEntry: "10.03.2023"
    },
    {
        id: 1,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 0,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agdasdasda ent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
    {
        id: 5,
        name: "John Doe",
        uid: "123456",
        position: "Agent",
        rank: 5,
        today: "8 ч 30 м",
        month: "120 ч",
        status: 1,
        lastEntry: "10.03.2023"
    },
])
let leader = ref({
    position: 30,
    date: "12.03.2023"
})
function dayText(days) {
    if (days % 10 == 1 && days % 100 != 11) {
        return "день"
    } else if ([2, 3, 4].includes(days % 10) && ![12, 13, 14].includes(days % 100)) {
        return "дня"
    } else {
        return "дней"
    }
}
</script>

<template>
    <p class="leader">
    <div>Лидер в должности</div>
    <div>
        <font>{{ leader.position }} {{ dayText(leader.position) }}</font>
    </div>
    <div>{{ leader.date }}</div> | <div>Коллеги онлайн</div>
    <div>
        <font>{{players.filter(player => player.status === 1).length}}</font> / {{ players.length }}
    </div>
    </p>
    <div class="search_input">
        <img src="../../assets/search.svg" alt="">
        <input type="text" name="" id="" placeholder="Введите значение для поиска">
    </div>
    <div class="colleagues_table">
        <div class="table_row tittle">
            <div class="table_column">№</div>
            <div class="table_column">Имя и фамилия</div>
            <div class="table_column">UID</div>
            <div class="table_column">Должность</div>
            <div class="table_column">Ранг</div>
            <div class="table_column">Сегодня</div>
            <div class="table_column">Месяц</div>
            <div class="table_column">Статус в сети</div>
        </div>
        <div class="table_wrapper">
            <div v-for="(player, index) in players" :key="player.id" class="table_row">
                <div class="table_column">{{ player.id }}</div>
                <div class="table_column">{{ player.name }}</div>
                <div class="table_column">{{ player.uid }}</div>
                <div class="table_column">{{ player.position }}</div>
                <div class="table_column">{{ player.rank }}</div>
                <div class="table_column">{{ player.today }}</div>
                <div class="table_column">{{ player.month }}</div>
                <div class="table_column">
                    {{ player.status === 1 ? 'Сейчас в игре' : player.lastEntry }} <div class="circle" :style="{background: player.status === 1 ? '#D9D9D9' : '#1F1F1F'}"></div>
                </div>
            </div>
        </div>
    </div>
</template>