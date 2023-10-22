<template>
    <div class="container" >
        <nav >
            <router-link to="/" style="text-decoration: none; color: black; border: 3px inset rgb(108, 156, 54); background-color: white; border-radius: 10px; border-width: 5px;margin-bottom: 5px;"> <h1>ГЛАВНАЯ</h1> </router-link>
            <router-link to="/chat" style="text-decoration: none; color: black; border: 3px inset rgb(108, 156, 54); background-color: white; border-radius: 10px; border-width: 5px;margin-bottom: 7px;"> <h1>ЧАТ</h1> </router-link>
            <router-link to="/testapi" style="text-decoration: none; color: black; border: 3px inset rgb(108, 156, 54); background-color: white; border-radius: 10px; border-width: 5px; margin-bottom: 5px;"> <h1>РЕЙТИНГ</h1> </router-link>
        </nav>
    </div>
</template>

<script>
    export default {
        name: 'NavComp',

    }
</script>

<style scoped>
    .container {
        background-color: #dfff4f;
        height: 70px;
        display: flex;
        justify-content: center;
    }
    nav {
        width: 800px;
        height: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>