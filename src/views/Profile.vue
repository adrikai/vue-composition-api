<template>
  <h1> Desarrollador Vue Card </h1>
  <div class="container">
    <div class="card-"><card-component v-model:nightMode="nightMode" v-model:backgroundColor="backgroundColor" v-model:name="name" v-model:edad="edad" v-model:empresa="empresa"/></div>
    <div class="formulario">
      <form-component @formChanged="formChanged" />
      <radio-component @optionChanged="radioOptionChanged" :opciones="[{label: 'Rojo', value: 'red'}, {label: 'Azul', value: 'blue'}]" />
    </div>
  </div>
</template>

<script>
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
      edad: '',
      empresa: '',
      backgroundColor: '',
      nightMode: true
    })

    function radioOptionChanged(event) {
      console.log(event)
      state.backgroundColor = event
      state.nightMode = !state.nightMode
      console.log(state.nightMode)
    }

    function formChanged({name,edad,empresa}) {
      state.name = name
      state.edad = edad,
      state.empresa = empresa
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