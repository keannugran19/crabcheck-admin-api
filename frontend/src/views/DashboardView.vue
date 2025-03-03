<script setup>
import BarGraph from '@/components/graphs/BarGraph.vue'
import PieChart from '@/components/graphs/PieChart.vue'
import InfoCard from '@/components/InfoCard.vue'
import SelectYearDropdown from '@/components/SelectYearDropdown.vue'
import { ref } from 'vue'

let isActive = ref('Total Crabs')

function makeActive(cardTitle) {
  isActive.value = cardTitle
  console.log('clicked')
}
</script>

<template>
  <main class="flex-1 space-y-5 p-4">
    <!-- filter by year -->
    <div>
      <SelectYearDropdown />
    </div>
    <!-- info card section -->
    <section class="grid grid-cols-5 gap-4 items-start">
      <div class="col-span-3">
        <InfoCard
          @click="makeActive('Total Crabs')"
          :class="[isActive === 'Total Crabs' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-gray-400 cursor-pointer"
          image="/assets/crabs/loginbackground.png"
          >Total Crabs</InfoCard
        >
      </div>
      <div class="col-span-2">
        <InfoCard
          class="border-t-5 border-red-400 text-white"
          image="/assets/crabs/unclassified.jpg"
          >Unclassified</InfoCard
        >
      </div>
      <div>
        <InfoCard
          @click="makeActive('Cardisoma Carnifex')"
          :class="[isActive === 'Cardisoma Carnifex' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-orange-400 cursor-pointer"
          image="/assets/crabs/cardisomaCarnifex.jpg"
          >Cardisoma Carnifex</InfoCard
        >
      </div>
      <div>
        <InfoCard
          @click="makeActive('Scylla Serrata')"
          :class="[isActive === 'Scylla Serrata' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-yellow-950 cursor-pointer"
          image="/assets/crabs/scyllaSerrata.jpg"
          >Scylla Serrata</InfoCard
        >
      </div>
      <div>
        <InfoCard
          @click="makeActive('Portunos Pelagicus')"
          :class="[isActive === 'Portunos Pelagicus' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-blue-400 cursor-pointer"
          image="/assets/crabs/portunosPelagicus.jpg"
          >Portunos Pelagicus</InfoCard
        >
      </div>
      <div>
        <InfoCard
          @click="makeActive('Venitus Latreillei')"
          :class="[isActive === 'Venitus Latreillei' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-yellow-300 cursor-pointer"
          image="/assets/crabs/venitusLatreillei.jpeg"
          >Venitus Latreillei</InfoCard
        >
      </div>
      <div>
        <InfoCard
          @click="makeActive('Metopograpsus Spp')"
          :class="[isActive === 'Metopograpsus Spp' ? 'text-orange-400' : 'text-white']"
          class="border-t-5 border-purple-600 cursor-pointer"
          image="/assets/crabs/metopograpsusSp.jpeg"
          >Metopograpsus Spp</InfoCard
        >
      </div>
      <div class="h-105 col-span-3 bg-gray-100 rounded-lg shadow-lg py-6 px-3">
        <p class="flex justify-center font-medium">Total Crabs per Month</p>
        <BarGraph />
      </div>
      <div class="h-105 col-span-2 bg-gray-100 rounded-lg shadow-md p-4">
        <p class="flex justify-center font-medium">Crab Species Distribution</p>
        <PieChart />
      </div>
    </section>
    <!-- bar graph & pie chart section -->
    <section></section>
  </main>
</template>
