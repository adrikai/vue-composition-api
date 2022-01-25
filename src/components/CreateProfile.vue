
<template>
<div id="container">
  <div id="card" style="height: 100px; width: 100px;">
    {{prueba}}----{{prueba3}}
    <radio-component @seletedOption="option" :opciones="[{prueba:1}]"></radio-component>
  </div>
  <div>
    <label>Prueba</label>
    <input v-model="prueba">
    <input v-model="prueba3">
  </div>
  </div>
</template>

<script>
import { reactive, ref, toRefs } from '@vue/reactivity'
import RadioComponent from '../commons/components/RadioComponent.vue'
export default {
  components: { RadioComponent },
  name: 'CreateProfile',
  props: {
    inputvalue: String
  },
  setup() {
    const prueba = ref('')
    const state = reactive({
      prueba3: ''
    })
    function option(event) {
console.log('asdasd', event);
    }
    return {prueba,
    ...toRefs(state), option}
  }
}
</script>

<style>

</style>