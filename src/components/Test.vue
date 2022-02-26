<template>
    <div >
        <h1>{{ msg }}</h1>
    <hr>
        <!-- tipo de representacion de texto en div -->
        <div v-text="myhttp"></div>
        <div v-html="myhttp"></div>
    <hr>
        <!-- representaciond e datos y variables desde script -->
        <h1>{{ title }}</h1>
        <h2>{{ user.nombre }}</h2>
    <hr>

        <!-- estructura condocinal if -->
        <div v-if="vf">
            <p>Existen user agregados</p>
        </div>
        <div v-else>
            <p>no Existen user agregados</p>
        </div>
    <hr>
        <!-- listas con vue -->
        <ul>
            <li v-for="tare in tareas" :key="tare.id" >
                {{ tare.task +" | "+ tare.hora }}
            </li>
        </ul>
    <hr>
        <!-- botones con vue and inputs -->
        <input type="text" v-model="user.nombre">

        <button type="button" v-on:click="saludar(user.nombre)">
            click saludos
        </button>
    <hr>
        <!-- tecleo en tiempo real -->
        <h5>typiando en tiempo real </h5>
        <input class='btn' type="text" v-on:keyup.enter="typing">
        <h2></h2>
    <hr>
        <div>
            <h4>
            {{ user.nombre +"  "+ user.edad }}
            </h4>
            <h4>
            {{datosUser}}    
            </h4>
        </div>
        
    </div>
</template>

<script>


export default {
    data() {
        return {
            title: 'Ususarios registrados',
            user: {
                nombre: "Carlos",
                edad: "21",
                correo: "Laparabiri@mail.com"
            },
            myhttp: '<h4>http://localhost:8080/#/</h4>',
            vf: true,
            tareas: [
                {task: 'Comer', hora: '2:00 pm'},
                {task: 'Pintar', hora: '4:00 pm'},
                {task: 'Caagr', hora: '12:00 pm'},
                {task: 'Ayudar al vecino', hora: '3:00 pm'}
            ]
        }
    },
    methods:{
        saludar(name) {
            alert(`Hola, Buenos dias ${name}`)
        },
        typing (e) {
            console.log(e.target.value)
            
        }
    },
    computed:{
        datosUser() {
            return this.user.nombre +" | "+this.user.edad
        }
    },
    props:{
        msg:{
            type: String,
            default: "Mensage por defecto"
        }
    }
}
</script>

<style media='screem'>
    .btn{
        background-color: bisque;
        border: none;
        color: brown;
    }

</style>