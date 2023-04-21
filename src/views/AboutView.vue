<script setup>
import { ref } from 'vue';
import ChildComp from '../components/ChildComp.vue';

const dynamicProps = ref('다이나믹 프로퍼티');
const myProp = ref('다이나믹 프로퍼티');

const callBackFunction = () => {
  myProp.value = "버튼이 클릭되었습니다."
}

const modelProps = ref('v-model 사용함');

</script>

<template>
  <div class="about">
    <ChildComp v-model="modelProps"/>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
