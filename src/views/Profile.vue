<template>
  <h1> Desarrollador Vue Card </h1>
  <div class="container">
    <div class="card-"><card-component v-model:themeMode="themeMode" v-model:name="name" v-model:age="age" v-model:company="company"/></div>
    <div class="formulario">
      <form-component @formChanged="formChanged" />
      <label>Seleccione el tema:</label>
      <radio-component :default="themeMode" @optionChanged="radioOptionChanged" :options="[{label: 'Claro', value: 'white'}, {label: 'Óscuro', value: 'dark'}]" />
    </div>
  </div>
</template>

<script setup>
import { reactive, toRefs } from '@vue/reactivity';
import CardComponent from '../commons/components/CardComponent.vue'
import FormComponent from '../commons/components/FormComponent.vue'
import RadioComponent from '../commons/components/RadioComponent.vue'
export default {
  components: { RadioComponent, CardComponent, FormComponent },
  name: 'Profile',
  setup(){
        const state = reactive({
      name: '',
      age: '',
      company: '',
      themeMode: 'white'
    })

    function radioOptionChanged(themeMode) {
      console.log(themeMode)
      state.themeMode = themeMode
    }

    function formChanged({name,age,company}) {
      state.name = name
      state.age = age,
      state.company = company
    }

    return {formChanged, radioOptionChanged, ...toRefs(state)}
  }


}
</script>

<style>
.container {
  display: grid; 
  grid-template-columns: 1fr 1fr; 
  grid-template-rows: 1fr 1fr; 
  gap: 0px 0px; 
  grid-template-areas: 
    "card- formulario"
    ". ."; 
}
.card- { grid-area: card-; }
.formulario { grid-area: formulario; }
</style>