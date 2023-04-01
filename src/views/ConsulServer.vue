<template>
   <div>
    <h1>Usuarios</h1>
    <ul>
        <li>{{ items }}</li>
         <li v-for="(dato,key,index) in items" :key="index">
            {{ items.name }}, {{ index }}
        </li>
    </ul>
   </div>
</template>
<script>
import axios from 'axios';

export default {
    data(){
        return{
          items: []
        }
    },
    methods: {
    axiosData(){ 
        axios.get('http://localhost:3000/items').then(res =>{
         this.items = res.data;
     })}    
    },
    created(){
        this.axiosData()
    }
}
</script>