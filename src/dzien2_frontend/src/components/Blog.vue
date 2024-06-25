<template>
    <div>
        <button @click="pobierzWpisy">refresh</button>
        {{ wpisy }}
        <input v-model="nowyBlog" type="text"> 
        <button @click="dodajWpisy">dodaj</button>
        {{ nowyBlog }}
    </div>
</template>

<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';
    export default{
        //dane
        data(){
            return {
                wpisy: []
            }
        },
        //metody
        methods: {
            async dodajWpisy(){
                await dzien2_backend.dodaj_wpis(this.nowyBlog);
            },
            async pobierzWpisy(){
                this.wpisy = await dzien2_backend.odczytaj_wpisy();
            }
        }
    }
</script>