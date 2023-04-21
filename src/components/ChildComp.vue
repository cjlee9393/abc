<script setup>
const props = defineProps({
    pokemon: Object,
    picked: String
});

const order = (pokemon) => {
  pokemon.stock--;
}

const editStock = (pokemon) => {
  pokemon.stock = +pokemon.stockInput;
}
</script>

<template>
  <div class="card">
      <div id="img-wrap">
          <img id="img-pokemon" :src=pokemon.imgSrc>
      </div>
      
      <div v-if="pokemon.stock">
          <p>재고: {{ pokemon.stock }}</p>
      </div>
      <p v-else style="color:red">재고 없음</p>

      <button v-if="picked=='Customer' && pokemon.stock > 0" @click="order(pokemon)">주문</button>
      <div v-else-if="picked=='Admin'" id="stock-wrap">
          <span>재고수정</span>
          <input id="stock-input"
          :value="pokemon.stockInput"
          @input="event => pokemon.stockInput = event.target.value"
          :placeholder="`현재수량 ${pokemon.stock}`">
          <q-btn color="secondary" text-color="black" label="입력" @click="editStock(pokemon)" />
      </div>
  </div>
</template>

<style scoped>
#img-wrap {
  width: 150px;
  height: 200px;
}

#img-pokemon {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

#stock-wrap {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  width: 150px;
}

#stock-input {
  width: 40%;
}
.card {
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 50px;
}
</style>