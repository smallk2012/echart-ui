<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo11" title="饼图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-pie :unit="opt.unit"  :radius="opt.radius" :colors="opt.colors" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-pie>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo11',
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
                unit: '%',
                radius: [65, 80],
                legend:'right',
                labelLine: 25,
                colors: [['#D0021B', '#F5A623'], ['#F8E71C', '#8B572A']],
                series: {
                    y1: [
                        { name: '新游客', value: 10 },
                        { name: '老游客', value: 20 }
                    ],
                    y2: [
                        { name: '外地', value: 40 },
                        { name: '本地', value: 30 }
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
