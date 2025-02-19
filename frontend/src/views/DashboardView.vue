<script setup>
import BarGraph from '@/components/graphs/BarGraph.vue'
import PieChart from '@/components/graphs/PieChart.vue'
import InfoCard from '@/components/InfoCard.vue'
import SelectYearDropdown from '@/components/SelectYearDropdown.vue'
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
        <InfoCard />
      </div>
      <div class="col-span-2">
        <InfoCard />
      </div>
      <div>
        <InfoCard />
      </div>
      <div>
        <InfoCard />
      </div>
      <div>
        <InfoCard />
      </div>
      <div>
        <InfoCard />
      </div>
      <div>
        <InfoCard />
      </div>
      <div class="h-100 col-span-3 bg-gray-100 rounded-lg shadow-lg p-4">
        <BarGraph />
      </div>
      <div class="h-100 col-span-2 bg-gray-100 rounded-lg shadow-md p-4">
        <PieChart />
      </div>
    </section>
    <!-- bar graph & pie chart section -->
    <section></section>
  </main>
</template>
