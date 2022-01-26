<template>
  <div class="container">
    <div class="card-">
      <card-component
        v-model:themeMode="themeMode"
        v-model:name="name"
        v-model:age="age"
        v-model:company="company"
      />
    </div>
    <div class="formulario">
      <form-component @formChanged="formChanged" />
      <label>Seleccione el tema:</label>
      <radio-component
        :default="themeMode"
        @optionChanged="radioOptionChanged"
        :options="[
          { label: 'Xbox', value: 'xbox' },
          { label: 'Playstation', value: 'ps' },
        ]"
      />
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from "@vue/reactivity";
import CardComponent from "../commons/components/CardComponent.vue";
import FormComponent from "../commons/components/FormComponent.vue";
import RadioComponent from "../commons/components/RadioComponent.vue";
export default {
  components: { RadioComponent, CardComponent, FormComponent },
  name: "Profile",
  setup() {
    const state = reactive({
      name: "",
      age: "",
      company: "",
      themeMode: "xbox",
    });

    function radioOptionChanged(themeMode) {
      state.themeMode = themeMode;
    }

    function formChanged({ name, age, company }) {
      state.name = name;
      (state.age = age), (state.company = company);
    }

    return { formChanged, radioOptionChanged, ...toRefs(state) };
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  max-width: 1200px;
  margin: 40px 0;
}
</style>
