<template>
    <h2>Здесь вы можете общаться</h2>

    <div v-if="username"> 
        <div class="chat">
            <h2>Чат</h2>

            <div class="text" v-for="message in messages" :key="message.id">
                {{ message.user }}: {{ message.text }}
            </div>

            <div v-show="emptyMsg" class="empty">Текущих сообщений нет</div>
            <input v-model="newMessage" placeholder="Введите сообщение">
            <button @click="sendMsg">Отправить</button>
            <button v-show="deleteBtn" @click="delMsg">Удалить</button>
        </div>
    </div>

    <div v-else class="alert"> Для начала вам необходим аккаунт. <br> Для авторизации перейдите по <router-link :to="{name: 'Home'}" >ссылке</router-link>
    
    </div>

</template>


<script>
    export default {
        name: 'ChatPage',
        
        data() {
            return{
                messages: [],
                newMessage: '',
                deleteBtn: false,
                emptyMsg: true,
                username: localStorage.getItem('username')
            }
        },
        computed() {
            localStorage.setItem('username', this.$route.query.username);
        },
        methods: {
            delMsg() {
            this.messages = [];
            this.emptyMsg = true;
            alert('Все сообщения удалены')
        },

            sendMsg() {
                if(!this.username ) {
                    this.username = 'Аноним'
                }
                if(this.newMessage !== '') {
                    this.emptyMsg = false;
                    this.messages.push( { id: new Date().getTime (), text: this.newMessage, user: this.username })
                    this.newMessage= '';
                    this.deleteBtn = true;
            }
        }
        }
    }
</script>
 
<style scoped>
    h2 {
        color: rgb(13, 50, 0);  
    }
    .text {
        margin-bottom: 20px;
    }
    .chat {
        width: 500px;
        height: 100%;
        border: 10px inset rgb(108, 156, 54);
        background-color: white;
        border-radius: 10px;
        color: black;
        font-size: 18;
        font-weight: bold;
        margin: 20px;
        padding: 15px;
    }
    .empty {
        margin-bottom: 25px;
        font-style: italic;
    }
    input {
        margin-right: 10px;
    }
    .alert {
        padding: 30px;
    }
    button {
        margin-left: 5px;
        margin-bottom: 25px;
    }
</style>