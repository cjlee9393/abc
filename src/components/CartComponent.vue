<script setup>
import { ref } from 'vue';
import { onBeforeMount } from 'vue';

const props = defineProps({
  pokemons: Object
})
const cart = ref([]);

onBeforeMount(() => {
  for (let pokemon of props.pokemons) {
    cart.value.push({
      ...pokemon,
      quantity: 0
    })
  }
})

const onClick = (pokemon, isAdd) => {
  const val = isAdd ? 1 : -1;

  if (pokemon.quantity + val <= pokemon.stock && pokemon.quantity + val >= 0) {
    pokemon.quantity += val;
  }else if (pokemon.quantity > pokemon.stock){
    alert("재고가 초과 되었습니다.");
  }else if (pokemon.quantity < 0){
    alert("재고가 부족합니다.");
  }
}
</script>

<template>
  <div id="cart-container">
    <h2>Shopping List</h2>
    
    <q-list v-for="pokemon in cart" :key="pokemon.id">
      <q-item clickable v-ripple>
        <q-item-section>{{pokemon.name}}</q-item-section>
        <div>
          <q-btn flat color="primary" label="-" @click="onClick(pokemon, false)"/>
          {{ pokemon.quantity }}
          <q-btn flat color="primary" label="+" @click="onClick(pokemon, true)" />
        </div>
        <q-item-section thumbnail>
          <div id="img-wrap">
            <img id="img-pokemon" :src="pokemon.imgSrc">
          </div>
        </q-item-section>
      </q-item>
    </q-list>
    
    <q-btn color="black" label="주문하기" />
  </div>
</template>

<style scoped>
#img-wrap {
  width: 75px;
  height: 100px;
}

#img-pokemon {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

#cart-container {
  display:flex;
  flex-direction: column;
}
</style>