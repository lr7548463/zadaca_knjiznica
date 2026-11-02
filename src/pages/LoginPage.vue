<template>
  <q-page class="q-pa-lg">
    <h1 class="text-h4"> Prijava korisnika </h1>

    <p class="text-body1">
      Unesite korisničko ime i lozinku za prijavu u sustav knjižnice.
    </p>

    <q-form
      @submit.prevent="potvrdi"
      class="q-gutter-md"
      style="max-width: 500px"
    >
      <q-input
        v-model="korisnickoIme"
        outlined
        label="Korisničko ime"
        :rules="[val => !!val || 'Unesite korisničko ime']"
      />

      <q-input
        v-model="lozinka"
        outlined
        label="Lozinka"
        type="password"
        :rules="[val => !!val || 'Unesite lozinku']"
      />

      <q-btn type="submit" color="primary" label="Potvrdi" />

      <p v-if="poruka" class="text-positive">
        {{ poruka }}
      </p>
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const korisnickoIme = ref('')
const lozinka = ref('')
const poruka = ref('')

function potvrdi() {
  poruka.value = 'Podaci su uneseni. Ovo je testna prijava korisnika.'
}
</script>
