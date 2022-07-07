<template>
  <div id="app">
    <ejs-chart :primaryXAxis="chartPrimaryXAxis" :title="chartTitle"
    :primaryYAxis="chartPrimaryYAxis">
    <e-annotations>
      <e-annotation :content="'sunTemplate'" coordinateUnits="Point" x="Tuesday" y="33"
      verticalAlignment="Top">
        <template v-slot:sunTemplate="{}">
           <img src="@/assets/images/sunny.png" style="width: 41px; height: 41px" />
        </template>
      </e-annotation>
    </e-annotations>
      <e-series-collection>
        <e-series type="Spline" :dataSource="chartData" xName="days" yName="temperature" 
        :marker="chartMarker"></e-series>
      </e-series-collection>   
    </ejs-chart>
  </div>
</template>

<script>
import Vue from "vue";
import { ChartPlugin, SplineSeries, Category, ChartAnnotation } from '@syncfusion/ej2-vue-charts';
Vue.use(ChartPlugin);

export default {
  provide : {chart : [SplineSeries, Category, ChartAnnotation ]},
  data() {
    return {
      chartMarker : {
        visible : true,
        height :10,
        width : 10
      },
      chartPrimaryYAxis : { title : 'Temperature Value', labelFormat : " {value}°C"},
      chartTitle : 'Weather Statistics',
      chartPrimaryXAxis : {
        valueType : 'Category',
        title : 'Days of the Week'
      },
      chartData : [
         { days : "Sunday", temperature : 15 },
         { days : "Monday" , temperature : 22 },
         { days : "Tuesday", temperature : 33 },
         { days : "Wednesday" , temperature : 31 },
         { days : "Thursday", temperature : 29 },
         { days : "Friday", temperature : 24 },
         { days : "Saturday", temperature : 18 }
      ]
    };
  }
}
</script>





