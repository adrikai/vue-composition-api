<template>
<div class="form-container">
  <input type="text" placeholder="name" v-model="name">
  <input type="text" placeholder="edad" v-model="edad">
  <input type="text" placeholder="pp" v-model="empresa">
</div>

</template>

<script>
import { reactive, toRefs } from '@vue/reactivity';
import { watch } from '@vue/runtime-core';
export default {
  name: 'FormComponent',
  setup(props,{emit}) {
    const state = reactive({
      name: '',
      edad: '',
      empresa: ''
    })

    watch(state, (newVal) => {
      emit('formChanged', newVal)
    })

    return {...toRefs(state)}
}
}
</script>

<style>

</style>