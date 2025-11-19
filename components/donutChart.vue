<template>
  <apexchart
    type="donut"
    width="100%"
    :series="series"
    :options="chartOptions"
  />
</template>

<script setup>
const props = defineProps({
  value: {
    type: Object,
    required: true,
  }
});

const series = computed(() => [props.value.charged,props.value.approaching,props.value.burnt,props.value.leave ]);

const chartOptions = computed(() => ({
  labels: ["charged",'Approaching Burnout', 'Burnouts', "on Leave"],

  legend: { show: false },

  chart: {
    toolbar: { show: false }
  },

  colors: ["#86DC3D", "#FA9C1B", '#DC143C','#DCDCDC'], 

  dataLabels: { enabled: false },

  plotOptions: {
    pie: {
      donut: {
        size: "70%",
        labels: {
          show: false,
          total: {
            show: true,
            label: false,
            fontSize: "16px",
            // formatter: () => `${props.value}%`
          }
        }
      }
    }
  },
}));
</script>