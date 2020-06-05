<template>
  <form @submit.prevent="submit">
    <div class="md-layout md-alignment-center-center">
      <div class="md-layout-item md-size-25">
        <md-field>
          <label>Número</label>
          <md-input
            v-model="value"
            v-model.trim="$v.value.$model"
            autofocus
            class="input"
          />
          <span class="error md-caption" v-if="!$v.value.required">
            El número es requerido.
          </span>
          <span class="error md-caption" v-if="!$v.value.integer">
            Numero no válido.
          </span>
        </md-field>
        <md-button
          class="md-raised md-accent"
          v-on:click="calcFibonacci"
          :disabled="$v.$invalid"
          >Obtener Fibonacci</md-button
        >
        <h2>Fibonacci: {{ fibonacci }}</h2>
      </div>
    </div>
  </form>
</template>
<script>
import Vue from "vue";
import VueMaterial from "vue-material";
import Vuelidate from "vuelidate";
import { required, integer } from "vuelidate/lib/validators";
import "vue-material/dist/vue-material.min.css";
Vue.use(VueMaterial);
Vue.use(Vuelidate);

export default {
  name: "Fibonacci",
  data: function() {
    return {
      value: "",
      fibonacci: null,
    };
  },
  methods: {
    calcFibonacci: function() {
      let serieFibonacci = [];
      for (let i = 0; i < this.value; i++) {
        if (i === 0) {
          serieFibonacci.push(0);
        } else if (i === 1) {
          serieFibonacci.push(1);
        } else {
          serieFibonacci.push(serieFibonacci[i - 1] + serieFibonacci[i - 2]);
        }
        if (serieFibonacci[i] <= this.value) {
          this.fibonacci = serieFibonacci[i];
        }
      }
      this.numberValid(this.value);
    },

    numberValid: function(number) {
      number = parseInt(number);
      if (number === 0 || number === 1) this.fibonacci = number;
      if (number < 0) this.fibonacci = "Error";
    },
  },
  validations: {
    value: {
      required,
      integer,
    },
  },
};
</script>
