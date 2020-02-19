<template>
  <div>
    <page-title :heading="heading" :subheading="subheading" :icon="icon"></page-title>

    <div class="content">
   
        <b-row>

          <b-col md="6">
            <b-card title="Line Graph" class="main-card mb-3">
              <chartone :values="valores"></chartone>
            </b-card>
          </b-col>

          <b-col md="6">
            <b-card title="Solid Gauge" class="main-card mb-3">
              <highcharts :options="chartOptionsOne"></highcharts>
            </b-card>
          </b-col>

        </b-row>

        <b-row>

          <b-col md="6">
            <b-card title="Column Vertical" class="main-card mb-3">
               <highcharts :options="chartOptionsThree"></highcharts>
            </b-card>
          </b-col>

          <b-col md="6">
            <b-card title="Column Horizontal" class="main-card mb-3">
              <highcharts :options="chartOptionsFour"></highcharts>
            </b-card>
          </b-col>

        </b-row>

        <b-row>

          <b-col md="6">
            <b-card title="Column Vertical" class="main-card mb-3">
               <highcharts :options="chartOptionsFive"></highcharts>
            </b-card>
          </b-col>

          <b-col md="6">
            <b-card title="Column Horizontal" class="main-card mb-3">
              <highcharts :options="chartOptionsSix"></highcharts>
            </b-card>
          </b-col>

        </b-row>

        <b-row>

          <b-col md="6">
            <b-card title="Multi Axes" class="main-card mb-3">
               <highcharts :options="chartOptionsSeven"></highcharts>
            </b-card>
          </b-col>

          <b-col md="6">
            <b-card title="Column Horizontal" class="main-card mb-3">
              <highcharts :options="chartOptionsSeven"></highcharts>
            </b-card>
          </b-col>

        </b-row>

      
    </div>
  </div>
</template>

<script>

  import PageTitle from "../../Layout/Components/PageTitle.vue";

  import chartone from "../../Components/blank.vue";

  import {Chart} from 'highcharts-vue'

  import Highcharts from  "highcharts";

  import highchartsMore from 'highcharts/highcharts-more';
  import solidGauge from 'highcharts/modules/solid-gauge';

  highchartsMore(Highcharts);
  solidGauge(Highcharts);

  export default {
    components: {
      PageTitle,
      highcharts: Chart,
      chartone
    },
    data: () => ({
      heading: 'Portfolio Charts',
      subheading: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
      icon: 'pe-7s-voicemail icon-gradient bg-arielle-smile',

      valores: [1,1,1,1,1,1,2,2,3],

      chartOptionsOne: {

        chart: {
          type: 'solidgauge'
        },
        title: null,
        pane: {
            center: ['50%', '85%'],
            size: '140%',
            startAngle: -90,
            endAngle: 90,
            background: {
                backgroundColor:
                    Highcharts.defaultOptions.legend.backgroundColor || '#EEE',
                innerRadius: '60%',
                outerRadius: '100%',
                shape: 'arc'
            }
        },

        exporting: {
            enabled: false
        },

        tooltip: {
            enabled: false
        },

        // the value axis
        yAxis: {
            stops: [
                [0.1, '#55BF3B'], // green
                [0.5, '#DDDF0D'], // yellow
                [0.9, '#DF5353'] // red
            ],
            lineWidth: 0,
            tickWidth: 0,
            minorTickInterval: null,
            tickAmount: 2,
            title: {
                y: -70
            },
            labels: {
                y: 16
            }
        },

        plotOptions: {
            solidgauge: {
                dataLabels: {
                    y: 5,
                    borderWidth: 0,
                    useHTML: true
                }
            }
        },
     
        series: [{
            name: 'Speed',
            data: [20],
            tooltip: {
                valueSuffix: ' km/h'
            }
        }]

       
      },

      chartOptionsThree: {
        chart: {
          type: 'column'
        },
        title: {
          text: 'Entire title'
        },
        series: [{
          data: [10, 0, 8, 2, 6, 4, 5, 5]
        },{
          data: [4, 3, 4, 6, 3, 8, 5, 5]
        }]
      },

       chartOptionsFour: {
        chart: {
          type: 'bar'
        },
        title: {
          text: 'Entire title'
        },
        series: [{
          data: [10, 0, 8, 2, 6, 4, 5, 5]
        }]
      },

      chartOptionsFive: {
        chart: {
          type: 'column'
        },
        title: {
          text: 'Entire title'
        },
        xAxis: {
            categories: ['Apples', 'Oranges', 'Pears', 'Grapes', 'Bananas','Melon','Oil','Drops']
        },
        yAxis: {
            min: 0,
            title: {
                text: 'Total fruit consumption'
            },
            stackLabels: {
                enabled: true,
                style: {
                    fontWeight: 'bold'
                }
            }
        },
        plotOptions: {
            column: {
                stacking: 'normal',
                dataLabels: {
                    enabled: true
                }
            }
        },
        series: [{
          data: [10, 0, 8, 2, 6, 4, 5, 5]
        },{
          data: [3, 4, 6, 8, 5, 8, 8, 3]
        }]
      },

      chartOptionsSix: {
        chart: {
            plotBackgroundColor: null,
            plotBorderWidth: null,
            plotShadow: false,
            type: 'pie'
        },
        title: {
          text: 'Entire title'
        },
        series: [{
          data: [10, 2, 8]
        }]
      },

      chartOptionsSeven: {
        chart: {
          type: 'column'
        },
        title: {
          text: 'Entire title'
        },
        plotOptions: {
            column: {
                colorByPoint: true
            }
        },
        colors: [
            '#ff0000',
            '#ff0000',
            '#ff0000',
            '#00ff00',
            '#ff0000',
            '#ff0000',
            '#ff0000'
        ],
        series: [{
          type: 'column',
          data: [10, 0, 8, 2, 6, 4, 5, 5]
        },{
          type: 'spline',
          data: [4, 3, 4, 6, 3, 8, 5, 5]
        }]
      }


    }),
    methods: {
        update: function(){
            this.valores = [1,1,2,2]
        }
    },
    mounted: function(){
      
      
     this.update()
        
    }


  }
</script>
