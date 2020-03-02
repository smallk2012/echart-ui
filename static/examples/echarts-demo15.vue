<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo15" title="漏斗图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-funnel :unit="opt.unit" :colors="opt.colors" :series="opt.series"></ms-echarts-funnel>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo15',
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
                unit: '万',
                colors: [
                    '#D0021B',
                    '#F5A623',
                    '#F8E71C',
                    '#8B572A',
                    '#7ED321'
                ],
                series: [
                    { name: '周一', value: 100 },
                    { name: '周二', value: 74 },
                    { name: '周三', value: 62 },
                    { name: '周四', value: 38 },
                    { name: '周五', value: 26 }
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
