<template>
  <section class="sailing-section pb-20">
    <div class="w-full">
      <apexchart type="area" height="350" :options="chartOptions" :series="series"></apexchart>
      <apexchart type="radialBar" height="350" :options="chartOptions2" :series="series2"></apexchart>
    </div>
    <div class="w-full">
      <apexchart type="bar" height="350" :options="chartOptions" :series="series"></apexchart>
    </div>
  </section>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  components: {
  },
  setup() {
    let series = ref([{
      name: 'series1',
      data: [31, 40, 28, 51, 42, 109, 100]
    }, {
      name: 'series2',
      data: [11, 32, 45, 32, 34, 52, 41]
    }])

    let chartOptions = ref({
      chart: {
        height: 350,
        type: 'area'
      },
      dataLabels: {
        enabled: false
      },
      stroke: {
        curve: 'smooth'
      },
      xaxis: {
        type: 'datetime',
        categories: ["2018-09-19T00:00:00.000Z", "2018-09-19T01:30:00.000Z", "2018-09-19T02:30:00.000Z", "2018-09-19T03:30:00.000Z", "2018-09-19T04:30:00.000Z", "2018-09-19T05:30:00.000Z", "2018-09-19T06:30:00.000Z"]
      },
      tooltip: {
        x: {
          format: 'dd/MM/yy HH:mm'
        },
      },
    })




    let series2 = ref([44, 55, 67, 83])
    let chartOptions2 = ref({
      chart: {
        height: 350,
        type: 'radialBar',
      },
      plotOptions: {
        radialBar: {
          dataLabels: {
            name: {
              fontSize: '22px',
            },
            value: {
              fontSize: '16px',
            },
            total: {
              show: true,
              label: 'Total',
              formatter: function (w) {
                // By default this function returns the average of all series. The below is just an example to show the use of custom formatter function
                return 249
              }
            }
          }
        }
      },
      labels: ['Apples', 'Oranges', 'Bananas', 'Berries'],
    })

    return {
      series,
      series2,
      chartOptions,
      chartOptions2,
    };
  },
};
</script>

<style></style>
