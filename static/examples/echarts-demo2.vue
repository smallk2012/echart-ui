<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo2" title="柱图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :loading="opt.loading" :chart-type="opt.chartType" :legendData="opt.legendData" :unit="opt.unit" :colors="opt.colors" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo2',
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
                loading:false,
                chartType: 'bar',
                legendData: ['客流量'],
                unit: '万元',
                colors: [[['#3FA2EA', '#73CFF6']]],
                yAxis: 'line-split-dashed',
                tooltip: '',
                series: [
                    { name: '周一', value: 100 },
                    { name: '周二', value: 200 },
                    { name: '周三', value: 300 },
                    { name: '周四', value: 400 },
                    { name: '周五', value: 500 }
                ]
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
