<script setup>
import TableHead from '@/components/TableHead.vue'
// import { ref } from 'vue'

// Sample Data
// const tableData = ref([
//   {
//     id: 1,
//     image: 'https://via.placeholder.com/100',
//     species: 'Scylla Serrata',
//     edibility: 'Edible',
//     address: 'Brgy. Cagangohan',
//     dateTime: '2024-02-18 10:00 AM',
//     classified: true,
//     year: 2024,
//   },
//   {
//     id: 2,
//     image: 'https://via.placeholder.com/100',
//     species: 'Portunos Pelagicus',
//     edibility: 'Edible',
//     address: 'Brgy. Liboganon',
//     dateTime: '2024-02-17 02:30 PM',
//     classified: false,
//     year: 2024,
//   },
//   {
//     id: 3,
//     image: 'https://via.placeholder.com/100',
//     species: 'Cardisoma Carnifex',
//     edibility: 'Edible',
//     address: 'Brgy. Cagangohan',
//     dateTime: '2025-03-10 05:45 PM',
//     classified: true,
//     year: 2025,
//   },
//   {
//     id: 4,
//     image: 'https://via.placeholder.com/100',
//     species: 'Metopograpsus Spp',
//     edibility: 'Inedible',
//     address: 'Brgy. Cagangohan',
//     dateTime: '2026-01-08 08:15 AM',
//     classified: false,
//     year: 2026,
//   },
//   {
//     id: 5,
//     image: 'https://via.placeholder.com/100',
//     species: 'Venitus Latreillei',
//     edibility: 'Inedible',
//     address: 'Brgy. Ising',
//     dateTime: '2026-01-08 08:15 AM',
//     classified: false,
//     year: 2026,
//   },
// ])
</script>

<template>
  <!-- Data Table -->
  <div class="overflow-x-auto rounded-lg border border-gray-200 shadow">
    <table class="w-full">
      <thead>
        <tr class="bg-gray-50">
          <TableHead>Image</TableHead>
          <TableHead>Species</TableHead>
          <TableHead>Edibility</TableHead>
          <TableHead>Address</TableHead>
          <TableHead>Date & Time</TableHead>
          <TableHead>Action</TableHead>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>
  <!-- Pagination -->
</template>
