<template>
    <div class="h-screen flex justify-center">
        <form @submit.prevent="login" class="flex flex-col gap-1 w-max mx-auto my-auto">
            <h1 class="mb-4 text-2xl font-semibold text-center">Login</h1>
            <label for="username">Username:</label>
            <input type="text" class="defaultInput" id="username" v-model="username" required>
            <label for="password">Password:</label>
            <input type="password" class="defaultInput" id="password" v-model="password" required>
            <button type="submit" class="mt-4 button-success">Login</button>
            <p v-if="error" style="color: red;">{{ error }}</p>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import usersData from '~/static/users.json';

const username = ref('');
const password = ref('');
const error = ref('');
const router = useRouter();

const login = () => {
    const user = usersData.users.find(user => user.username === username.value && user.password === password.value);
    if (user) {
        localStorage.setItem('user', JSON.stringify({ username: user.username, role: user.role }));
        if (user.role === "Administrator") {
            router.push('/dashboard');
        } else {
            router.push('/');
        }
    } else {
        error.value = 'Invalid username or password';
    }
};
</script>
