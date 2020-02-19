<template>
    <div>
      <highcharts :options="chartOptions"></highcharts>
    </div>
</template>

<script>

    import {Chart} from 'highcharts-vue'

    export default {
        components: {
            highcharts: Chart
        },
        props: ['labels', 'values'],
        watch: {
            values: function(){
               this.chartOptions.series[0].data = this.values
            }
        },
        data: () => ({
            chartOptions: {
                chart: {
                type: 'spline'
                },
                responsive: true,
                title: {
                text: null
                },
                series: [{
                data: [10, 0, 8, 2, 6, 4, 5, 5]
                }]
            },
        })
    }
</script>
