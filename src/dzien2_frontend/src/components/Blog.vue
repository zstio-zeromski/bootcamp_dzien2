<template>
    <div>
        <h2 class="text-blue-600">Wpisy na bloga:</h2>
        <div class="w-100 flex flex-row-reverse">
            <button class="bg-blue-600 rounded-md text-white p-4" @click="pobierzWpisy">odświerz</button>
        </div>
        <div class="grid mx-6 gap-4 my-4">
            <div v-for="wpis in wpisy" class="drop-shadow-x1 bg-stone-300 p-4"><p>{{ wpis }}</p></div>
        </div>
        <input class="border-2 border-blue-600 p-4" v-model="nowyBlog" type="text"> 
        <button class="bg-blue-600 rounded-md text-white p-4" @click="dodajWpisy">dodaj wpis</button>
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
        },
        //uruchomienie wpisow na starcie
        async mounted(){
            this.pobierzWpisy()
        }
    }
</script>