<template>
<div v-for="(opcion, index) in opciones" v-bind:key="index">
  <input type="radio" id="opcion.value" v-bind:value="opcion.value" v-model="picked">
<label for="uno">{{opcion.label}}</label>
</div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { watch } from '@vue/runtime-core'
export default {
  name: 'radioComponent',
  props: {
    opciones: Array
  },
  emits: ['optionChanged'],
  setup(props, {emit}) {
    const picked = ref('')
    watch(picked, (newVal) => {
      emit('optionChanged', newVal)
    })
    return {picked}
  }
}
</script>

<style>

</style>