<template>
  <div class="card-container">
    <div class="card card2" :style="{backgroundColor: background}">
      <p class="card_name"> {{name}} </p>
      <div class="grid-container">
        <div class="grid-child-tec">
          {{empresa}}
        </div>
        <div class="grid-child-experience">
          {{edad}}
          {{nightModeComputed}}
          {{nMode}}
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
    empresa: String,
    edad: String,
    backgroundColor: String,
    nightMode: Boolean
  }, setup(props) {
    const background = toRef(props, 'backgroundColor')
    const nMode = toRef(props, 'nightMode')
    const nightModeComputed = computed(() => {
      let p = nMode.value
      if(p === true){
        return 'aaa'
      } else {
        return 'eee'
      }

    })
    return {
      background,
     nightModeComputed,
     nMode
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