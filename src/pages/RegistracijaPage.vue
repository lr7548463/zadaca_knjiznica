<template>
  <q-page class="q-pa-lg">
    <h1 class="text-h4"> Registracija korisnika </h1>

    <p class="text-body1">
      Ispunite sljedeće podatke kako biste se registrirali u sustav knjižnice.
    </p>

    <q-form
      @submit.prevent="potvrdi"
      class="q-gutter-md"
      style="max-width: 500px"
    >
      <q-input
        v-model="ime"
        outlined
        label="Ime"
        :rules="[val => !!val || 'Unesite ime']"
      />

      <q-input
        v-model="prezime"
        outlined
        label="Prezime"
        :rules="[val => !!val || 'Unesite prezime']"
      />

      <q-input
        v-model="korisnickoIme"
        outlined
        label="Korisničko ime"
        :rules="[val => !!val || 'Unesite korisničko ime']"
      />

      <q-input
        v-model="email"
        outlined
        type="email"
        label="E-mail"
        :rules="[
          val => !!val || 'Unesite e-mail',
          val => /.+@.+\..+/.test(val) || 'Neispravna e-mail adresa'
        ]"
      />

      <q-input
        v-model="lozinka"
        outlined
        type="password"
        label="Lozinka"
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

const ime = ref('')
const prezime = ref('')
const korisnickoIme = ref('')
const email = ref('')
const lozinka = ref('')
const poruka = ref('')

function potvrdi() {
  poruka.value = 'Podaci su uspješno uneseni. Ovo je testna registracija.'
}
</script>
