<template>
    <div class="ex-echarts-line">
        <api-panel page="echarts-line" title="线图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :chart-type="opt.chartType" :smooth="opt.smooth" :rotate="opt.rotate" :multiple="opt.multiple" :colors="opt.colors" :legend-data="opt.legendData" :unit="opt.unit" :legend="opt.legend" :x-axis="opt.xAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsLine',
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
                chartType: [['lineArea', 'line']],
                smooth: true,
                rotate: 30,
                legendData: [['客流量', '过去7天平均值']],
                unit: '人',
                //单维[]
                //单维多组[[]]
                //单维多组渐变色或多维多组[[[]]]
                colors: [['#3FA2EA', '#55D284']],
                xAxis: 'line-split-dashed',
                tooltip: '',
                series: {
                    y0: [
                        { name: '9:00', value: 677 },
                        { name: '10:00', value: 1340 },
                        { name: '11:00', value: 345 },
                        { name: '12:00', value: 690 },
                        { name: '13:00', value: 540 },
                        { name: '14:00', value: 344 },
                        { name: '15:00', value: 370 },
                        { name: '16:00', value: 890 },
                        { name: '17:00', value: 600 },
                        { name: '18:00', value: 300 },
                        { name: '19:00', value: 450 },
                        { name: '20:00', value: 666 },
                        { name: '21:00', value: 200 },
                        { name: '22:00', value: 100 }
                    ],
                    y1: [
                        { name: '9:00', value: 430 },
                        { name: '10:00', value: 334 },
                        { name: '11:00', value: 1340 },
                        { name: '12:00', value: 2230 },
                        { name: '13:00', value: 1430 },
                        { name: '14:00', value: 2000 },
                        { name: '15:00', value: 566 },
                        { name: '16:00', value: 300 },
                        { name: '17:00', value: 677 },
                        { name: '18:00', value: 299 },
                        { name: '19:00', value: 800 },
                        { name: '20:00', value: 500 },
                        { name: '21:00', value: 540 },
                        { name: '22:00', value: 345 }
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
