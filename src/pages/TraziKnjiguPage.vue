<template>
  <q-page class="q-pa-lg">
    <h1 class="text-h4"> Pretraživanje knjiga </h1>

    <p class="text-body1">
      Unesite naslov knjige ili ime autora kako biste pronašli željenu knjigu.
    </p>

    <q-input
      v-model="pojam"
      outlined
      label="Unesite pojam za pretraživanje"
      class="q-mb-md"
      @keyup.enter="pretrazi"
    />

    <div class="row q-gutter-md q-mb-md">
      <q-checkbox v-model="poNaslovu" label="Pretraži po naslovu" />

      <q-checkbox v-model="poAutoru" label="Pretraži po autoru" />
    </div>

    <q-btn
      color="primary"
      icon="search"
      label="Traži"
      class="q-mb-lg"
      @click="pretrazi"
    />

    <p v-if="poruka" class="text-negative">
      {{ poruka }}
    </p>

    <q-table
      title="Pronađene knjige"
      :rows="rezultati"
      :columns="columns"
      row-key="id"
      no-data-label="Nema pronađenih knjiga"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const pojam = ref('')
const poNaslovu = ref(true)
const poAutoru = ref(false)

const poruka = ref('')
const rezultati = ref([])

const columns = [
  {
    name: 'id',
    label: 'ID',
    field: 'id',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'naslov',
    label: 'Naslov',
    field: 'naslov',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'autor',
    label: 'Autor',
    field: 'autor',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'zanr',
    label: 'Žanr',
    field: 'zanr',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'godina',
    label: 'Godina izdanja',
    field: 'godina',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'dostupno',
    label: 'Dostupno',
    field: 'dostupno',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  }
]

const knjige = [
  {
    id: 1,
    naslov: 'Mali princ',
    autor: 'Antoine de Saint-Exupéry',
    zanr: 'Roman',
    godina: 1943,
    dostupno: 'Da'
  },
  {
    id: 2,
    naslov: 'Zločin i kazna',
    autor: 'Fjodor Dostojevski',
    zanr: 'Roman',
    godina: 1866,
    dostupno: 'Da'
  },
  {
    id: 3,
    naslov: 'Gospodar prstenova',
    autor: 'J. R. R. Tolkien',
    zanr: 'Fantastika',
    godina: 1954,
    dostupno: 'Ne'
  },
  {
    id: 4,
    naslov: 'Ponos i predrasude',
    autor: 'Jane Austen',
    zanr: 'Roman',
    godina: 1813,
    dostupno: 'Da'
  },
  {
    id: 5,
    naslov: '1984',
    autor: 'George Orwell',
    zanr: 'Distopija',
    godina: 1949,
    dostupno: 'Ne'
  },
  {
    id: 6,
    naslov: 'Proces',
    autor: 'Franz Kafka',
    zanr: 'Roman',
    godina: 1925,
    dostupno: 'Da'
  }
]

function pretrazi() {
  if (!poNaslovu.value && !poAutoru.value) {
    poruka.value = 'Odaberite pretraživanje po naslovu ili autoru.'
    rezultati.value = []
    return
  }

  poruka.value = ''

  const trazeniPojam = pojam.value.trim().toLocaleLowerCase('hr')

  rezultati.value = knjige.filter(knjiga => {
    const naslovOdgovara =
      poNaslovu.value &&
      knjiga.naslov.toLocaleLowerCase('hr').includes(trazeniPojam)

    const autorOdgovara =
      poAutoru.value &&
      knjiga.autor.toLocaleLowerCase('hr').includes(trazeniPojam)

    return naslovOdgovara || autorOdgovara
  })
}
</script>
