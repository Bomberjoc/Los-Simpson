<script setup>
import { ref } from 'vue';

const character = ref('')
let quote = ref('')
const image = ref('')
let characterDirection = ref('')
let bgs = ['']

async function call(){
        let url = await (await fetch('https://thesimpsonsquoteapi.glitch.me/quotes')).json()
        await console.log(url[0].quote);
        await asignacion(url)
    }
call();

async function asignacion(url){
    character.value = url[0].character
    quote.value = url[0].quote
    image.value = url[0].image
    console.log(image.value)
    console.log(bgs[0])
    characterDirection.value = url[0].characterDirection
}


</script>

<template>
    <div class="shadow-lg hover:scale-110 ease-in duration-100 hover:cursor-pointer rounded-2xl p-[20px] justify-around flex items-center gap-6 w-[500px] min-h-[180px] select-none">
        <div v-if="characterDirection=='Left'" id="image2" class="w-[100px] h-[100px] overflow-hidden rounded-full min-w-[100px] min-h-[100px]">
            <img :src=image class="bg-auto ">
        </div>
        <div id="slider" class="flex flex-col gap-2">
            <div id="name">
                <p class="text-2xl">
                    {{ character }}
                </p>
            </div>
            <div id="phrase" class="flex gap-2 text-base">
                <p class="font-bold">
                    Frase:
                </p>
                <p >
                    {{quote}}
                </p>
            </div>
        </div>
        <div v-if="characterDirection=='Right'" id="image1" class="w-[100px] h-[100px] overflow-hidden rounded-full min-w-[100px] min-h-[100px]">
            <img :src=image class="bg-auto ">
        </div>
    </div>
</template>