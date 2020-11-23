<template>
    <div id="app">
        <h1>Monty Hall</h1>
        <div class="form">

            <div v-if="!started">
                <label for="portsAmount">QUANTAS PORTAS</label>
                    <input type="text" id="portsAmount" size="3"
                            v-model.number="portAmount">
                            <!-- salvando valor numerico -->
            </div>    
            <div v-if="!started">
                             <label for="DoorSelected">QUAL PORTA</label>
                    <input type="text" id="DoorSelected" size="3"
                            v-model.number="DoorSelected">

            </div>
            <button v-if="!started" @click="started =true">Iniciar</button>
            <button v-if="started" @click="started = false">Reiniciar</button>
        </div>    

        <div class="doors" v-if="started">
            <div v-for="i in portAmount" :key="i">
                <Door :hasgift="i === DoorSelected" :number="i"/>
            </div>
        </div>

    </div>
</template>

<script>

import Door from './components/Door'

export default {
    name: 'App',
    components:{Door},
    
    data(){
        return{
             started:false,
             portAmount:3, 
             DoorSelected: null
  
         }
    }
}
</script>

<style>
*{
    box-sizing: border-box;
    font-family: 'Montserrat',sans-serif;
}

body{
    color: #f0f0f0;
    background-color: royalblue;
}

#app{
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1{
    border:  1px solid #000;
    background-color: #0004;
    padding: 20px;
    margin-bottom: 60px;


}
.form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}
.form, .form input, .form button{
    margin-bottom: 10px;
    font-size: 2rem;
}

.doors{
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}


</style>