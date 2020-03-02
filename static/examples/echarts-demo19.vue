<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo19" title="云字符图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-cloud :unit="opt.unit" :colors="opt.colors" :series="opt.series"></ms-echarts-cloud>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo19',
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
                colors: ['#EAC780', '#E0B05A', '#D09D52', '#8B572A'],
                series: [
                    {
                        name: '时尚',
                        value: 100
                    },
                    {
                        name: '体育',
                        value: 96
                    },
                    {
                        name: '音乐',
                        value: 95
                    },
                    {
                        name: '娱乐',
                        value: 94
                    },
                    {
                        name: '健康养生',
                        value: 90
                    },
                    {
                        name: '财经',
                        value: 85
                    },
                    {
                        name: '游戏',
                        value: 90
                    },
                    {
                        name: '动漫',
                        value: 83
                    },
                    {
                        name: '外语',
                        value: 85
                    },
                    {
                        name: '宠物',
                        value: 85
                    },
                    {
                        name: '旅游',
                        value: 85
                    },
                    {
                        name: '科技',
                        value: 85
                    },
                    {
                        name: '军事',
                        value: 85
                    },
                    {
                        name: '新闻',
                        value: 85
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
