<script>
  import { Line, Bar } from 'vue-chartjs'
  let linechart = [];
  let barchart = [];
  var i;
  for(i=0; i<31; i++) {
    barchart[i] = 5;
  }
  linechart[0] = 10;
  for(i=1; i<21; i++) {
    linechart[i] = linechart[i-1]+i/30;
  }
  for(i=21; i<31; i++) {
    linechart[i] = linechart[i-1]+i/25;
  }
    
  export default {
    extends: Line,
    data () {
      return {
        chartData: {
          labels: ["0",	"",  "", "1",  "", "", "2",  "", "", "3",  "", "", "4",	 "", "", "5",  "", "", "6", "", "", "7", "", "", "8", "", "", "9",  "", "", "10"],
          datasets: [
            {
              type: 'line',
              label: 'Yield',
              data: linechart,
              yAxisID:'yAxis1',
              fill: false,
              borderColor: '#FFFFFF',
              backgroundColor: '#2554FF',
              borderWidth: 5
            },
            {
              type: 'bar',
              label: 'Stake',
              data: barchart,
              fill: false,
              borderColor: '#6d1eda',
              backgroundColor: '#6d1eda',
              
            },
          ]
        },
        options: {
          plugins: {
             subtitle: {
                display: true,
                text: 'Custom Chart Subtitle'
            }
          },
          elements: {
            point: {
              radius: 0
            }
          },
          bezierCurve: true,
          scales: {
            yAxes: [
              {
                id: 'yAxis1',
                
                ticks: {
                  beginAtZero: true,
                  callback: (value, index, values) => {
                    return `${value}.00%`;
                  },
                  fontColor: 'white',
                },
                gridLines: {
                  display: true,
                  color: "gray",
                  width: 3
                },
                scaleLabel: {
                  display: true,
                  labelString: 'Annualised Yield'
                }
              },
              {
                id:'yAxis2',
                position: 'right',
                gridLines: {
                  drawOnChartArea: false, // only want the grid lines for one axis to show up
                },
                scaleLabel: {
                  display: true,
                  labelString: 'Stake %'
                },
                ticks:{
                  callback: (value, index, values) => {
                    return `${value*10}.00%`;
                  },
                  fontColor: 'white'
                }
              }
            ],
            xAxes: [ {
              barThickness: 6,
              gridLines: {
                display: false,    
              },
              scaleLabel: {
                display: true,
                labelString: 'Stake Maturity (Years)'
              },
              ticks:{
                fontColor: 'white'
              }
            }]
          },
          legend: {
            position: 'bottom',
            align: 'start',
            labels: {
              fontColor: 'white',
              boxWidth: 30,
              boxHeight: 2,
            }
           
          },
          responsive: true,
          maintainAspectRatio: false,
        }
      }
    },
    mounted () {
      this.renderChart(this.chartData, this.options)
    }
  }
</script>