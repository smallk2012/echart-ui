<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo12" title="饼图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-pie :chart-type="opt.chartType" :unit="opt.unit" :radius="opt.radius" :colors="opt.colors" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-pie>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo12',
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
                chartType: 'piePercent',
                unit: '万',
                radius: [65, 80],
                colors: ['#D0021B', '#F5A623', '#F8E71C', '#8B572A'],
                series: [
                    { name: '新游客', value: 10 },
                    { name: '老游客', value: 20 },
                    { name: '外地', value: 40 },
                    { name: '本地', value: 30 }
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
