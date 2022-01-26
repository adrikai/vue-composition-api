<template>
<div v-for="(option, index) in options" v-bind:key="index">
  <input type="radio" id="option.value" v-bind:value="option.value" v-model="picked">
<label for="option.value">{{option.label}}</label>
</div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { watch } from '@vue/runtime-core'
export default {
  name: 'radioComponent',
  props: {
    options: Array
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