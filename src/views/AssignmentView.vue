<script setup>
import { ref } from 'vue';
import CardComponent from '../components/CardComponent.vue';
import AuthComponent from '../components/AuthComponent.vue';
import CartComponent from '../components/CartComponent.vue';

// switch to compoisition api
const assetDir = "/src/assets/";
const picked = ref('Customer');
const pokemons = ref(
  [
    {
      id: 0,
      name: "파이리",
      imgSrc: assetDir + "pokemon1.jpg", 
      stock: 10,
      stockInput: '' 
    },
    {
      id: 1,
      name: "고라파덕",
      imgSrc: assetDir + "pokemon2.jpg",
      stock: 10,
      stockInput: ''
    },
    {
      id: 0,
      name: "파이리",
      imgSrc: assetDir + "pokemon1.jpg", 
      stock: 10,
      stockInput: '' 
    },
    {
      id: 0,
      name: "파이리",
      imgSrc: assetDir + "pokemon1.jpg", 
      stock: 10,
      stockInput: '' 
    },
  ]
);
// for문을 component 안으로 넣어서 구현 가능.
// 정규식 포함하여 구현할 수 있음.
</script>

<template>
  <q-layout view="lHh lpr lFf" container style="height: 800px; width:900px;" class="shadow-2 rounded-borders">
    <q-header elevated>
      <q-toolbar id="q-toolbar">
        <div id="auth-container">
          <AuthComponent v-model="picked" />
        </div>

        <div class="cursor-pointer">
          <span>Cart</span>
          <q-popup-edit>    
              <CartComponent :pokemons="pokemons" />
          </q-popup-edit>
        </div>
      </q-toolbar>
    </q-header>
    <div id="card-container">
      <div v-for="pokemon in pokemons">
        <q-card class="my-card">
          <CardComponent :pokemon="pokemon" :picked="picked" :key="pokemon.id"/> 
        </q-card>
      </div>
    </div>
  </q-layout>
</template>

<style>
#q-toolbar {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

#popup {
  position: relative;
  top: 50%;
  left: 50%;
}

#auth-container  {
  margin-right:50px;
}

#card-container {
  padding-top: 50px;
  width: 800px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.my-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 10px;
}
</style>