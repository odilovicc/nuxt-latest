<template>
    <div class="w-full py-5 px-8">
        <div class="flex justify-between items-center">
            <div class="flex flex-col gap-0.5">
                <h1 class="text-xl font-semibold">{{ user.username }}</h1>
                <h1 class="italic">{{ user.role }}</h1>
            </div>
            <!-- <button @click="logout" class="button-success">Logout</button> -->
            <Button @click="logout" success label="Logout"/>
        </div>
    </div>

    <main class="flex flex-wrap gap-5 justify-between px-8">
        <div v-for="cinema in cinemaList" class="">
            <div class="rounded-md shadow-md">
                <img :src="cinema.poster" class="w-80 rounded-t-md" alt="">
                <div class="px-4 py-2">
                    <h1 class="text-xl font-semibold">{{ cinema.name }}</h1>
                    <p class="italic">{{ cinema.author }}</p>
                    <p class="italic">Rating {{ cinema.rating }}</p>
                </div>
                <div class="flex justify-between p-4">
                    <Button label="Edit" success/>
                    <Button label="Delete" danger/>
                </div>
            </div>
        </div>
    </main>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { cinema } from '~/static/cinemalist';

const user = JSON.parse(localStorage.getItem('user'));
const router = useRouter();
const cinemaList = cinema


function logout(){
    localStorage.removeItem('user');
    router.push('/login');
};
</script>