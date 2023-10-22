<template>
    <h1 style="color: rgb(13, 50, 0);">Главная</h1>
        <h2>Добро пожаловать на мой сайт!
            <br>
            На сайте представлен список лучших теннисистов
        </h2>

    <div v-if="isAuth"><div>Удачи на корте, {{ username }}!</div>
        <button @click="logout">Выйти</button>
    </div>
    <div v-else>
        <label >Введите ваше имя:</label>
        <input v-model="username" @keyup.enter="login">
        <button @click="login">Войти</button>
    </div>
</template>


<script>
    export default {
        name: 'HomePage',
        data() {
            return {
                isAuth: false,
                username: ""
            }
        },
        created() {
            if(localStorage.getItem('isAuth')) {
                this.isAuth=true;
                this.username = localStorage.getItem('username');
            }
        },
        methods: {
            logout() {
            this.isAuth = false;
            this.username = ""

            localStorage.removeItem('isAuth')
            localStorage.removeItem('username')
        },
            login() {
            if (this.username !== "") {
                this.isAuth = true;
                localStorage.setItem('isAuth', true);
                localStorage.setItem('username', this.username);


                this.$router.push ({
                name: 'Chat',
                query: { username: this.username}
            })

            } else {
                alert ('Пожалуйста, введите значение')
            }
        }
        }
    }
</script>
 
<style scoped>
    div {
        padding: 30px;
        font-size: 22px;
    }
    label {
        margin: 0 15px;
    }
    button {
        margin-left: 5px;
    }
</style>
    
