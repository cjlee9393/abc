<script setup>
const props = defineProps({
  picked: String,
  pokemon: Object
})

const order = (pokemon) => {
  pokemon.stock--;
}

const editStock = (pokemon) => {
  const regex = new RegExp("^[0-9]*");

  if(regex.test(pokemon.stockInput)) {
    pokemon.stock = pokemon.stockInput;
  }else{
    alert("잘못된 입력값 입니다.");
  }
}
</script>

<template>
  <main>
    <div class="card">
      <div id="img-wrap">
        <img id="img-pokemon" :src=pokemon.imgSrc>
      </div>
      
      <div v-if="pokemon.stock">
        <span style="font-weight:800">재고: {{ pokemon.stock }}</span>
      </div>
      <span v-else style="color:red">재고 없음</span>

      <q-btn v-if="picked=='Customer' && pokemon.stock > 0" @click="order(pokemon)">주문</q-btn>
      <div id="stock-wrap" v-else-if="picked=='Admin'">
        <input id="stock-input"
          :value="pokemon.stockInput"
          @input="event => pokemon.stockInput = event.target.value"
          :placeholder="`현재수량 ${pokemon.stock}`">
        <q-btn id="stock-input-button" @click="editStock(pokemon)">입력</q-btn>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card {
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 50px;
  width: 200px;
  height: 350px;
}

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
  width: 200px;
}

#stock-input {
  width: 60%;
}

#stock-input-button {
  width: 70px;
}
</style>