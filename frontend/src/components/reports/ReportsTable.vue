<template>
  <div class="p-5 max-w-7xl mx-auto bg-white rounded-lg shadow-sm">
    <h2 class="text-2xl font-semibold text-gray-800 mb-6">Crab Classification Records</h2>

    <!-- Filters -->
    <div class="flex flex-wrap gap-4 mb-6">
      <!-- Year Filter -->
      <select
        v-model="selectedYear"
        class="px-4 py-2 bg-white border border-gray-200 rounded-lg shadow-sm text-gray-700 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 focus:outline-none transition-all"
      >
        <option value="">2025</option>
        <option v-for="year in years" :key="year" :value="year">{{ year }}</option>
      </select>

      <!-- Species Filter -->
      <select
        v-model="selectedSpecies"
        class="px-4 py-2 bg-white border border-gray-200 rounded-lg shadow-sm text-gray-700 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 focus:outline-none transition-all"
      >
        <option value="">All Species</option>
        <option v-for="species in speciesList" :key="species" :value="species">
          {{ species }}
        </option>
      </select>

      <!-- Classification Filter -->
      <select
        v-model="selectedClassification"
        class="px-4 py-2 bg-white border border-gray-200 rounded-lg shadow-sm text-gray-700 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 focus:outline-none transition-all"
      >
        <option value="">All</option>
        <option value="classified">Classified</option>
        <option value="unclassified">Unclassified</option>
      </select>
    </div>

    <!-- Data Table -->
    <div class="overflow-x-auto rounded-lg border border-gray-200 shadow">
      <table class="w-full">
        <thead>
          <tr class="bg-gray-50">
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Image</th>
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Species</th>
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Edibility</th>
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Address</th>
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Date & Time</th>
            <th class="px-6 py-4 text-left text-sm font-semibold text-gray-600">Action</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-gray-200">
          <tr
            v-for="item in paginatedData"
            :key="item.id"
            class="hover:bg-gray-50 transition-colors"
          >
            <td class="px-6 py-4">
              <img
                :src="item.image"
                class="w-16 h-16 object-cover rounded-lg shadow-sm"
                alt="Crab Image"
              />
            </td>
            <td class="px-6 py-4 text-gray-800">{{ item.species }}</td>
            <td class="px-6 py-4 text-gray-800">{{ item.edibility }}</td>
            <td class="px-6 py-4 text-gray-800">{{ item.address }}</td>
            <td class="px-6 py-4 text-gray-800">{{ item.dateTime }}</td>
            <td class="px-6 py-4">
              <button
                @click="deleteRow(item.id)"
                class="inline-flex items-center px-3 py-2 border border-transparent text-sm font-medium rounded-md text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 transition-all"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Pagination -->
    <div class="flex justify-between items-center mt-6">
      <button
        @click="prevPage"
        :disabled="currentPage === 1"
        class="inline-flex items-center px-4 py-2 border border-gray-300 rounded-md text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 disabled:opacity-50 disabled:cursor-not-allowed transition-all"
      >
        Previous
      </button>
      <span class="text-sm text-gray-700">Page {{ currentPage }} of {{ totalPages }}</span>
      <button
        @click="nextPage"
        :disabled="currentPage === totalPages"
        class="inline-flex items-center px-4 py-2 border border-gray-300 rounded-md text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 disabled:opacity-50 disabled:cursor-not-allowed transition-all"
      >
        Next
      </button>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  setup() {
    // Sample Data
    const tableData = ref([
      {
        id: 1,
        image: 'https://via.placeholder.com/100',
        species: 'Scylla Serrata',
        edibility: 'Edible',
        address: 'Brgy. Cagangohan',
        dateTime: '2024-02-18 10:00 AM',
        classified: true,
        year: 2024,
      },
      {
        id: 2,
        image: 'https://via.placeholder.com/100',
        species: 'Portunos Pelagicus',
        edibility: 'Edible',
        address: 'Brgy. Liboganon',
        dateTime: '2024-02-17 02:30 PM',
        classified: false,
        year: 2024,
      },
      {
        id: 3,
        image: 'https://via.placeholder.com/100',
        species: 'Cardisoma Carnifex',
        edibility: 'Edible',
        address: 'Brgy. Cagangohan',
        dateTime: '2025-03-10 05:45 PM',
        classified: true,
        year: 2025,
      },
      {
        id: 4,
        image: 'https://via.placeholder.com/100',
        species: 'Metopograpsus Spp',
        edibility: 'Inedible',
        address: 'Brgy. Cagangohan',
        dateTime: '2026-01-08 08:15 AM',
        classified: false,
        year: 2026,
      },
      {
        id: 5,
        image: 'https://via.placeholder.com/100',
        species: 'Venitus Latreillei',
        edibility: 'Inedible',
        address: 'Brgy. Ising',
        dateTime: '2026-01-08 08:15 AM',
        classified: false,
        year: 2026,
      },
      // Add more data here...
      // Add more data here...
    ])

    // Filters
    const selectedYear = ref('')
    const selectedSpecies = ref('')
    const selectedClassification = ref('')

    // Pagination
    const currentPage = ref(1)
    const rowsPerPage = 10

    // Computed: Filtered Data
    const filteredData = computed(() => {
      return tableData.value.filter((item) => {
        return (
          (!selectedYear.value || item.year === parseInt(selectedYear.value)) &&
          (!selectedSpecies.value || item.species === selectedSpecies.value) &&
          (!selectedClassification.value ||
            (selectedClassification.value === 'classified' && item.classified) ||
            (selectedClassification.value === 'unclassified' && !item.classified))
        )
      })
    })

    // Computed: Paginated Data
    const paginatedData = computed(() => {
      const start = (currentPage.value - 1) * rowsPerPage
      const end = start + rowsPerPage
      return filteredData.value.slice(start, end)
    })

    // Total Pages
    const totalPages = computed(() => Math.ceil(filteredData.value.length / rowsPerPage))

    // Pagination Functions
    const prevPage = () => {
      if (currentPage.value > 1) currentPage.value--
    }

    const nextPage = () => {
      if (currentPage.value < totalPages.value) currentPage.value++
    }

    // Delete Function
    const deleteRow = (id) => {
      tableData.value = tableData.value.filter((item) => item.id !== id)
    }

    // Dynamic Filter Options
    const years = computed(() => [...new Set(tableData.value.map((item) => item.year))].sort())
    const speciesList = computed(() =>
      [...new Set(tableData.value.map((item) => item.species))].sort(),
    )

    return {
      tableData,
      selectedYear,
      selectedSpecies,
      selectedClassification,
      years,
      speciesList,
      filteredData,
      paginatedData,
      deleteRow,
      currentPage,
      totalPages,
      prevPage,
      nextPage,
    }
  },
}
</script>
