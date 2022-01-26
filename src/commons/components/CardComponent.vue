<template>
  <div class="card-container">
    <div class="card card2" :style="themeModeComputed">
      <p class="card_name">Nombre: {{name}} </p>
      <div class="grid-container">
        <div class="grid-child-age">
         Edad: {{age}}
        </div>
        <div class="grid-child-company">
         Empresa: {{company}}
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import { toRef } from '@vue/reactivity';
import { computed } from '@vue/runtime-core';
export default {
  name: 'Card',
  props: {
    name: String,
    company: String,
    age: String,
    themeMode: String
  }, setup(props) {
    const background = toRef(props, 'backgroundColor')
    const themeModeRef = toRef(props, 'themeMode')
    const themeModeComputed = computed(() => {
      return {
        backgroundColor: themeModeRef.value === 'dark' ? 'blue' : 'red',
        color: themeModeRef.value === 'dark' ? 'red' : 'blue'
      }
    })
    return {
      background,
     themeModeComputed,
     themeModeRef
    }
  }
}
</script>

<style>
.card-container {
  display:grid;
  grid-template-columns: 1fr 1fr 1fr;
  justify-content: center;
  align-items: center;
  gap: 0px 0px;
  grid-template-areas: 
  "card1 card2 card3";
}
.card {
  background-color: #222831;
  height: 15rem;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: rgba(0,0,0,0.7);
  color: white;
}

.card2 {
  grid-area: card2;
}
</style>