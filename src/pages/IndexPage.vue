<template>
  <q-page class="flex flex-center column q-pa-lg">
    <h1 class="text-h3 text-weight-bold text-center">
      Dobro došli u Knjižnicu!
    </h1>

    <p class="text-h6 text-center">
      Dobro došli na web stranicu naše knjižnice. Ovdje možete pregledavati
      dostupne knjige, pretraživati naslove i autore te saznati više informacija
      o knjižnici.
    </p>

    <q-img
      src="../assets/library.jpg"
      alt="Slika knjižnice"
      style="max-width: 700px; width: 100%"
      class="q-mt-lg rounded-borders"
    />

    <q-btn
      color="primary"
      label="Pregledaj knjige"
      to="/popis_knjiga"
      class="q-mt-lg"
    />
  </q-page>
</template>
