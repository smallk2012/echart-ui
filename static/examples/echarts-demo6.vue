<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo6" title="柱堆叠图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :chart-type="opt.chartType" :markLine="opt.markLine" :legend="opt.legend" :legendData="opt.legendData" :unit="opt.unit" :colors="opt.colors" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo6',
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
                chartType: 'barStack',
                markLine: 'average',
                legend: 'bottom',
                legendData: ['新游客', '老游客'],
                unit: '%',
                colors: [['#3FA2EA', '#73CFF6']],
                yAxis: 'none',
                tooltip: '',
                series: {
                    y1: [
                        { name: '周一', value: 10 },
                        { name: '周二', value: 20 },
                        { name: '周三', value: 30 },
                        { name: '周四', value: 40 },
                        { name: '周五', value: 50 }
                    ],
                    y2: [
                        { name: '周一', value: 90 },
                        { name: '周二', value: 80 },
                        { name: '周三', value: 70 },
                        { name: '周四', value: 60 },
                        { name: '周五', value: 50 }
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
