<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo20" title="雷达图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-radar :unit="opt.unit" :colors="opt.colors" :radius="opt.radius" :series="opt.series"></ms-echarts-radar>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo20',
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
                colors: ['#EAC780', '#E0B05A'],
                radius: 100,
                series: [
                    {
                        name: '时尚',
                        value: 100
                    },
                    {
                        name: '体育',
                        value: 36
                    },
                    {
                        name: '音乐',
                        value: 25
                    },
                    {
                        name: '娱乐',
                        value: 75
                    },
                    {
                        name: '健康养生',
                        value: 65
                    }
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
