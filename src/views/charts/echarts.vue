<template>
    <section class="chart-container">
        <el-row>
             <el-col :span="12">
                <el-card>
                <div id="chartPie" style="width:100%; height:400px;"></div>
                </el-card>
            </el-col>
            <el-col :span="12">
                <el-card>
                <div id="chartColumn" style="width:100%; height:400px;"></div>
                </el-card>
            </el-col>
            <el-col :span="12">
                <el-card>
                <div id="chartLine" style="width:100%; height:400px;"></div>
                </el-card>
            </el-col>
            <el-col :span="12">
                <el-card>
                <div id="chartBar" style="width:100%; height:400px;"></div>
                </el-card>
            </el-col>
            
           
        </el-row>
    </section>
</template>

<script>
    import echarts from 'echarts'

    export default {
        data() {
            return {
                chartColumn: null,
                chartBar: null,
                chartLine: null,
                chartPie: null
            }
        },

        methods: {
            drawColumnChart() {
                this.chartColumn = echarts.init(document.getElementById('chartColumn'));
                this.chartColumn.setOption({
                  title: { text: 'Column Chart' },
                  tooltip: {},
                  xAxis: {
                      data: ["星期一", "星期二", "星期三", "星期四", "星期五", "星期六","星期日"]
                  },
                  yAxis: {},
                  series: [{
                      name: '销量',
                      type: 'bar',
                      data: [5, 20, 36, 10, 10, 20,15],
                      itemStyle: {
                      normal: {
                      color: function(params) {
                      var colorList = ['#67C23A','#E6A23C', '#F56C6C', '#409EFF', '#909399','#749f83', '#ca8622'];
                      return colorList[params.dataIndex]
                }
            }
        }
                    }]
                });
            },
            drawBarChart() {
                this.chartBar = echarts.init(document.getElementById('chartBar'));
                this.chartBar.setOption({
                    title: {
                        text: 'Bar Chart',
                        subtext: '数据来自网络'
                    },
                    tooltip: {
                        trigger: 'axis',
                        axisPointer: {
                            type: 'shadow'
                        }
                    },
                    legend: {
                        data: ['female', 'male']
                    },
                    color:['#67C23A','#E6A23C'],
                    grid: {
                        left: '3%',
                        right: '4%',
                        bottom: '3%',
                        containLabel: true
                    },
                    xAxis: {
                        type: 'value',
                        boundaryGap: [0, 0.01]
                    },
                    yAxis: {
                        type: 'category',
                        data: ['促销特价', '两件包邮', '感恩回馈', '清仓甩卖', '镇店之宝', '数量(百)']
                    },
                    series: [
                        {
                            name: 'female',
                            type: 'bar',
                            data: [18203, 23489, 29034, 104970, 131744, 630230],
                   
                        },
                        {
                            name: 'male',
                            type: 'bar',
                            data: [19325, 23438, 31000, 121594, 134141, 681807]
                        }
                    ]
                });
            },
            drawLineChart() {
                this.chartLine = echarts.init(document.getElementById('chartLine'));
                this.chartLine.setOption({
                    title: {
                        text: 'Line Chart'
                    },
                    tooltip: {
                        trigger: 'axis'
                    },
                    legend: {
                        data: ['2017年', '2018年', '2019年']
                    },
                    color:['#67C23A','#E6A23C','#749f83'],
                    grid: {
                        left: '3%',
                        right: '4%',
                        bottom: '3%',
                        containLabel: true
                    },
                    xAxis: {
                        type: 'category',
                        boundaryGap: false,
                        data: ['海尔', '美的', '日普', '海信', '松下', '先科', '西门子']
                    },
                    yAxis: {
                        type: 'value'
                    },
                    series: [
                        {
                            name: '2017年',
                            type: 'line',
                            stack: '总量',
                            data: [120, 132, 101, 134, 90, 230, 210]
                        },
                        {
                            name: '2018年',
                            type: 'line',
                            stack: '总量',
                            data: [220, 182, 191, 234, 290, 330, 310]
                        },
                        {
                            name: '2019年',
                            type: 'line',
                            stack: '总量',
                            data: [820, 932, 901, 934, 1290, 1330, 1320]
                        }
                    ]
                });
            },
            drawPieChart() {
                this.chartPie = echarts.init(document.getElementById('chartPie'));
                this.chartPie.setOption({
                    title: {
                        text: 'Pie Chart',
                        subtext: '纯属虚构',
                        x: 'center'
                    },
                    tooltip: {
                        trigger: 'item',
                        formatter: "{a} <br/>{b} : {c} ({d}%)"
                    },
                    legend: {
                        orient: 'vertical',
                        left: 'left',
                        data: ['美食特产', '服装内衣', '母婴用品', '运动户外', '鞋包首饰']
                    },
                    color:['#67C23A','#E6A23C','#749f83','#F56C6C', '#409EFF', '#909399','#F56C6C'],
                    series: [
                        {
                            name: '访问来源',
                            type: 'pie',
                            radius: '55%',
                            center: ['50%', '60%'],
                            data: [
                                { value: 335, name: '美食特产' },
                                { value: 310, name: '服装内衣' },
                                { value: 234, name: '母婴用品'},
                                { value: 135, name: '运动户外' },
                                { value: 1548, name: '鞋包首饰' }
                            ],
                            itemStyle: {
                                emphasis: {
                                    shadowBlur: 10,
                                    shadowOffsetX: 0,
                                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                                }
                            }
                        }
                    ]
                });
            },
            drawCharts() {
                this.drawColumnChart()
                this.drawBarChart()
                this.drawLineChart()
                this.drawPieChart()
            },
        },

        mounted: function () {
            this.drawCharts()
        },
        updated: function () {
            this.drawCharts()
        }
    }
</script>

<style scoped>
    .chart-container {
        width: 100%;
        float: left;
    }
    /*.chart div {
        height: 400px;
        float: left;
    }*/

    .el-col {
        padding: 30px 20px;
    }
</style>
