<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo13" title="升降柱图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-negative :unit="opt.unit" :colors="opt.colors" :series="opt.series"></ms-echarts-negative>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo13',
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
                unit: '人',
                colors: ['#D0021B', '#F5A623', '#F8E71C', '#8B572A', '#7ED321'],
                series: [
                    { name: '周一', value: 100 },
                    { name: '周二', value: 200 },
                    { name: '周三', value: 300 },
                    { name: '周四', value: -200 },
                    { name: '周五', value: -100 }
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
