<template>
  <div id="app">
    <h1>电商运营数据看板</h1>
    <div id="sales-chart" style="width: 600px; height: 400px;"></div>
    <div id="orders-chart" style="width: 600px; height: 400px;"></div>
    <div id="users-chart" style="width: 600px; height: 400px;"></div>
    <div id="category-sales-chart" style="width: 600px; height: 400px;"></div>
  </div>
</template>

<script>
import * as echarts from 'echarts';

export default {
  name: 'App',
  mounted() {
    // 销售额折线图
    this.initSalesChart();
    // 订单量折线图
    this.initOrdersChart();
    // 用户数量折线图
    this.initUsersChart();
    // 商品品类销售额占比饼图
    this.initCategorySalesChart();
  },
  methods: {
    initSalesChart() {
      let salesChartElement = document.getElementById('sales-chart');
      if (!salesChartElement) {
        console.error('无法获取 sales-chart 元素');
        return;
      }
      let salesChart = echarts.init(salesChartElement);

      // 模拟销售额数据
      let salesData = [
        { month: '1月', value: 5000 },
        { month: '2月', value: 6000 },
        { month: '3月', value: 8000 },
        { month: '4月', value: 7000 },
        { month: '5月', value: 9000 },
        { month: '6月', value: 10000 },
      ];

      let option = {
        title: {
          text: '销售额走势',
        },
        tooltip: {},
        xAxis: {
          data: salesData.map(item => item.month),
        },
        yAxis: {},
        series: [
          {
            name: '销售额',
            type: 'line',
            data: salesData.map(item => item.value),
          },
        ],
      };

      salesChart.setOption(option);
    },
    initOrdersChart() {
      let ordersChartElement = document.getElementById('orders-chart');
      if (!ordersChartElement) {
        console.error('无法获取 orders-chart 元素');
        return;
      }
      let ordersChart = echarts.init(ordersChartElement);

      // 模拟订单量数据
      let ordersData = [
        { month: '1月', value: 300 },
        { month: '2月', value: 400 },
        { month: '3月', value: 500 },
        { month: '4月', value: 450 },
        { month: '5月', value: 600 },
        { month: '6月', value: 700 },
      ];

      let option = {
        title: {
          text: '订单量走势',
        },
        tooltip: {},
        xAxis: {
          data: ordersData.map(item => item.month),
        },
        yAxis: {},
        series: [
          {
            name: '订单量',
            type: 'line',
            data: ordersData.map(item => item.value),
          },
        ],
      };

      ordersChart.setOption(option);
    },
    initUsersChart() {
      let usersChartElement = document.getElementById('users-chart');
      if (!usersChartElement) {
        console.error('无法获取 users-chart 元素');
        return;
      }
      let usersChart = echarts.init(usersChartElement);

      // 模拟用户数量数据
      let usersData = [
        { month: '1月', value: 1000 },
        { month: '2月', value: 1200 },
        { month: '3月', value: 1500 },
        { month: '4月', value: 1300 },
        { month: '5月', value: 1800 },
        { month: '6月', value: 2000 },
      ];

      let option = {
        title: {
          text: '用户数量走势',
        },
        tooltip: {},
        xAxis: {
          data: usersData.map(item => item.month),
        },
        yAxis: {},
        series: [
          {
            name: '用户数量',
            type: 'line',
            data: usersData.map(item => item.value),
          },
        ],
      };

      usersChart.setOption(option);
    },
    initCategorySalesChart() {
      let categorySalesChartElement = document.getElementById('category-sales-chart');
      if (!categorySalesChartElement) {
        console.error('无法获取 category-sales-chart 元素');
        return;
      }
      let categorySalesChart = echarts.init(categorySalesChartElement);

      // 模拟不同商品品类销售额占比数据
      let categorySalesData = [
        { category: '服装', value: 30 },
        { category: '数码', value: 25 },
        { category: '食品', value: 20 },
        { category: '家居', value: 15 },
        { category: '美妆', value: 10 },
      ];

      let option = {
        title: {
          text: '不同商品品类销售额占比',
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b}: {c}%',
        },
        series: [
          {
            name: '销售额占比',
            type: 'pie',
            data: categorySalesData.map(item => ({
              name: item.category,
              value: item.value,
            })),
          },
        ],
      };

      categorySalesChart.setOption(option);
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>