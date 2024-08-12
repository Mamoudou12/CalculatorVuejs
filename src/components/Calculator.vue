<template>
  <form @submit.prevent="calcul">
    <div>
      <input type="radio" id="addition" value="addition" v-model="choix">
      <label for="addition">Addition</label>
    </div>
    <div>
      <input type="radio" id="division" value="division" v-model="choix">
      <label for="division">Division</label>
    </div>
    <div>
      <input type="radio" id="soustraction" value="soustraction" v-model="choix">
      <label for="soustraction">Soustraction</label>
    </div>
    <div>
      <input type="radio" id="multiplication" value="multiplication" v-model="choix">
      <label for="multiplication">Multiplication</label>
    </div>
    <div>
      <input type="number" id="valeur1" v-model.number="valeur1" placeholder="Enter first value">
      <input type="number" id="valeur2" v-model.number="valeur2" placeholder="Enter second value">
    </div>
    <button type="submit">Calculer</button>
    <div v-if="result !== null">
      <p>Resultat: {{ result }}</p>
    </div>
    <div v-if="error">
      <p style="color: red;">{{ error }}</p>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const choix = ref('');  
const valeur1 = ref(0);
const valeur2 = ref(0);
const result = ref(null);
const error = ref('');

const calcul = () => {
  error.value = '';
  result.value = null;

  switch (choix.value) {
    case 'addition':
      result.value = valeur1.value + valeur2.value;
      break;
    case 'division':
      if (valeur2.value === 0) {
        error.value = "La division par zéro n'est pas possible.";
      } else {
        result.value = valeur1.value / valeur2.value;
      }
      break;
    case 'soustraction':
      result.value = valeur1.value - valeur2.value;
      break;
    case 'multiplication':
      result.value = valeur1.value * valeur2.value;
      break;
    default:
      error.value = "Veuillez choisir une opération.";
  }
};
</script>
