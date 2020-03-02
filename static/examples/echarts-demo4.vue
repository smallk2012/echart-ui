<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo4" title="4柱组图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :chart-type="opt.chartType" :legendData="opt.legendData" :unit="opt.unit" :colors="opt.colors" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo4',
    data () {
        return {
            tempOpt: null,
            code: '',
            trs: [
                {
                    attr: 'chartType',
                    explain: '<span>类型:bar,line,lineArea,barStack</span>',
                    type: 'String,Array',
                    default: 'bar'
                },
                {
                    attr: 'xData',
                    explain: 'x轴数据',
                    type: 'Array',
                    default: '[]'
                },
                {
                    attr: 'yData',
                    explain: 'y轴数据',
                    type: 'Array',
                    default: '[]'
                }
            ],
            opt: {
                chartType: 'bar',
                legendData: ['0-30分钟', '30-60分钟', '60-90分钟', '>90分钟'],
                unit: '%',
                colors: [[['#FD687D', '#FFC796'], ['#55D284', '#9FE7BB'], ['#3FA2EA', '#73CFF6'], ['#E3495F', '#FD687D']]],
                yAxis: 'line-split-dashed',
                tooltip: '',
                series: {
                    y0: [
                        { name: 'B1', value: 10 },
                        { name: '1L', value: 20 },
                        { name: '2L', value: 30 },
                        { name: '3L', value: 40 },
                        { name: '4L', value: 50 },
                        { name: '5L', value: 60 },
                        { name: '6L', value: 50 }
                    ],
                    y1: [
                        { name: 'B1', value: 20 },
                        { name: '1L', value: 27 },
                        { name: '2L', value: 37 },
                        { name: '3L', value: 41 },
                        { name: '4L', value: 53 },
                        { name: '5L', value: 36 },
                        { name: '6L', value: 15 }
                    ],
                    y2: [
                        { name: 'B1', value: 33 },
                        { name: '1L', value: 55 },
                        { name: '2L', value: 22 },
                        { name: '3L', value: 44 },
                        { name: '4L', value: 55 },
                        { name: '5L', value: 90 },
                        { name: '6L', value: 44 }
                    ],
                    y3: [
                        { name: 'B1', value: 22 },
                        { name: '1L', value: 44 },
                        { name: '2L', value: 33 },
                        { name: '3L', value: 88 },
                        { name: '4L', value: 34 },
                        { name: '5L', value: 65 },
                        { name: '6L', value: 20 }
                    ]
                }
            }
        }
    },
    methods: {
        clickRunEvt () {
            var _opt = window.opt || {}
            var _tempOpt = JSON.parse(this.tempOpt)
            for (var o in _opt) {
                if (_tempOpt.hasOwnProperty(o)) {
                    _tempOpt[o] = _opt[o]
                }
            }
            this.opt = _tempOpt
        }
    },
    mounted () {
        this.tempOpt = JSON.stringify(this.opt)
        this.code = 'opt={ ' + (tool.deepJson(this.opt) || '') + '}'
    }
}

</script>

<style scoped lang="scss">
pre {
    display: none;
}
</style>
