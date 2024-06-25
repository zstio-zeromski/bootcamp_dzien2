<template>
    <div>
        <h1>Wszystkie wpisy:</h1>
        <button @click="pobierzWpisy">wyświetl wszystkie wpisy</button>
        {{ wpisy }}
        <br>
        <h1>Podaj nowy wpis:</h1>
        <input v-model="nowyBlog" type="text"> 
        <button @click="dodajWpisy">dodaj wpis</button>
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