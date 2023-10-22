<template>
    <div class="container">
        <div class="players">Рейтинг</div>
        <div v-if="isLoad" class="loading">Загрузка...</div>
        <div v-else class="data"></div>
           <div v-for="(el, i) in playerData" :key="el.Age">
           {{ i + 1 }}. {{  el.Name }}, {{ el.Age }} y.o.
           <img src="https://www.kindpng.com/picc/m/540-5402522_delete-garbage-remove-trash-trash-can-icon-delete.png" alt="delete" style="width: 15px; height: 15px; " @click="removePlayer(el.id)">
        </div>
    </div>
</template>


<script>
    export default {
        name: 'TestApi',
        data() {
            return {
            playerData: [],
            isLoad: true
        }
    },
    methods: {
        removePlayer(id) {
            this.playerData=this.playerData.filter((el) => el.id !== id);
        }
    },
    mounted() {
        const url = 'https://ultimate-tennis1.p.rapidapi.com/live_leaderboard/50';
const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': '74cc246dd5msh37cd08b6241976bp10815ejsn6019bddf0a98',
		'X-RapidAPI-Host': 'ultimate-tennis1.p.rapidapi.com'
	}
};

    fetch(url, options)
        .then((res) => res.json())
        .then((res) => {
            this.playerData = res.data;
            if (this.playerData !== '')
                this.isLoad = false;
        })

}
}
</script>
 
<style scoped>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .players {
        font-size: 2em;
        color: rgb(13, 50, 0);
        margin: 10px;
        font-weight: bold;
    }
    .data {
        padding: 20px;
    }
    .loading {
        padding-bottom: 20px;
    }
    img {
        cursor: pointer;
        margin-left: 10px;
    }
    
</style>