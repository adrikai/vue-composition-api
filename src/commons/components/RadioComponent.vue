<template>
<div v-for="(option, index) in options" v-bind:key="index">
  <input type="radio" id="option.value" v-bind:value="option.value" v-model="picked" v-on:change="radioOptionChanged">
<label for="option.value">{{option.label}}</label>
</div>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
  name: 'radioComponent',
  props: {
    options: Array,
    default: String
  },
  emits: ['optionChanged'],
  setup(props, {emit}) {
    const picked = ref(props.default)
    function radioOptionChanged(event) {
 emit('optionChanged', event.target.value)
    }
    return {picked,radioOptionChanged}
  }
}
</script>

<style>

</style>