<template>
  <div>
    <apexchart
      width="100%"
      type="bar"
      :options="chartOptions"
      :series="formattedSeries"
    />
  </div>
</template>

<script setup>
const props = defineProps({
  teamName: {
    type: String,
    required: true,
  },
  stats: {
    type: Object,
    required: true,
  },
});

const formattedSeries = computed(() => [
  { name: "Charged", data: [props.stats.charged] },
  { name: "On Leave", data: [props.stats.leave] },
  { name: "Approaching Burnout", data: [props.stats.approaching] },
  { name: "Burnt Out", data: [props.stats.burnt] },
]);

const chartOptions = computed(() => ({
  chart: { stacked: false, toolbar: { show: false } },
  plotOptions: { bar: { columnWidth: "40%", borderRadius: 4 } },
  dataLabels: { enabled: false },
  xaxis: { categories: [props.teamName] , },
  colors: ["#88d16f", "#c8c8c8", "#f6a538", "#d14343"],
  legend: { show: false },
}));
</script>
<style>

</style>