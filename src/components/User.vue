<template>
    <div class="cuerpo">
        <hr>
            <h1>Usuarios agregados</h1>
            <form v-on:submit.prevent="add">
                <input type="text" v-model="newUser.name" placeholder="nombre" >
                <input type="text" v-model="newUser.email" placeholder="Mail">
                <button type="submit">enviar</button>
            </form>
            <div>
                <ul>
                    <li v-for="user in users" :key="user.id"  v-on:click="edit(user)">
                        {{ user.name +"  |  "+ user.email}} 
                        <button class="btn btn-danger" v-on:click="deleteUser(user)">X</button>
                    </li>
                </ul>
            </div>

            <hr>

            <nav>
      <ul>
        <li>
          <router-link to="/">
            User
          </router-link>
        </li>
        <li>
          <router-link to="/test">
            test
          </router-link>
        </li>
        <li>
            <a href="/test">User con etiqueta a</a>
        </li>
      </ul>
    </nav>
    <hr>
      <router-view></router-view>
            

        <hr>
    </div>
</template>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
export default {
    data () {
        return {
            users: [], 
            newUser: {},
            
        }
    },
    methods:{
        add(){
            this.users.push(this.newUser)
            this.newUser = {}
        },
        deleteUser(user){
            this.users.splice(this.users.indexOf(user), 1)
        },
        edit(user) {
            console.log('funcioas'+ user.nombre)
        }
        
    },
    created()  {
        this.$http.get('https://jsonplaceholder.typicode.com/users')
            .then(res => (this.users = (res.body)))
    }
    
}
</script>

<style>
    .cuerpo{
        background: burlywood;
        color: aliceblue;
        border-radius: 2rem;
    }
    li{
        background: aliceblue;
        color: black;
        border-radius: 12rem;
        padding: 5px;
        margin: 20px;
        list-style:none;
    }
</style>