<template>
  <div id="app">
    <Chart id="demo" :option="option"/>
  </div>
</template>

<script>
import Chart from './components/Chart'

export default {
  name: 'App',
  data() {
    return {
      option: {
        title: {
          text: "vue_echarts"
        },
        tooltip: {},
        legend: {
            data:['销量']
        },
        xAxis: {
              data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
          },
          yAxis: {},
          series: [{
              name: '销量',
              type: 'bar',
              data: [5, 20, 36, 10, 10, 20]
          }]
      },
      chartData: {
        xData: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
        sData: [5, 20, 36, 10, 10, 70]
      }
    };
  },
  components: {
    Chart
  },
  mounted() {
    this.refreshData();
  },
  methods: {
    //添加refreshData方法进行自动设置数据
    refreshData() {
      //横轴数据
      let xData = this.chartData.xData,
        //系列值
          sData = this.chartData.sData;
      for (let i = 0; i < xData.length; i++) {
        //此处使用let是关键，也可以使用闭包。原理不再赘述
           setTimeout(() => {
          this.option.xAxis.data.push(xData[i]);
          this.option.series[0].data.push(sData[i]);
        }, 1000*i)//此处要理解为什么是1000*i
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


