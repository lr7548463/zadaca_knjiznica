<template>
  <q-page class="q-pa-lg">
    <h1 class="text-h4"> Popis svih knjiga </h1>

    <p class="text-body1">
      U nastavku je prikazan popis knjiga naše knjižnice.
    </p>

    <q-table
      title="Katalog knjiga"
      :rows="rows"
      :columns="columns"
      row-key="id"
      :pagination="{ rowsPerPage: 5 }"
    />
  </q-page>
</template>

<script setup>
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

const rows = [
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
</script>
