<template>
    <div class="ex-echarts">
        <api-panel page="echarts" title="基本图表" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :loading="opt.loading" :chart-type="opt.chartType" :multiple="opt.multiple" :colors="opt.colors" :legend-data="opt.legendData" :unit="opt.unit" :legend="opt.legend" :xAxis="opt.xAxis" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEcharts',
    data () {
        return {
            tempOpt: null,
            code: '',
            trs: [
                {
                    attr: 'loading',
                    explain: '加载状态',
                    type: 'Boolean',
                    default: 'false'
                },
                {
                    attr: 'chartType',
                    explain: '<span>类型:bar,line,lineArea,barStack</span>',
                    type: 'String,Array',
                    default: 'bar'
                },
                {
                    attr: 'multiple',
                    explain: '多维',
                    type: 'Boolean',
                    default: 'false'
                },
                {
                    attr: 'smooth',
                    explain: '折线是否圆滑',
                    type: 'Boolean',
                    default: 'false'
                },
                {
                    attr: 'barMaxWidth',
                    explain: '柱子宽度',
                    type: 'Number',
                    default: '20'
                },
                {
                    attr: 'legendData',
                    explain: 'legend标签',
                    type: 'Array',
                    default: '[]'
                },
                {
                    attr: 'unit',
                    explain: '轴单位',
                    type: 'String,Array',
                    default: ''
                },
                {
                    attr: 'colors',
                    explain: '颜色',
                    type: 'Array',
                    default: ''
                },
                {
                    attr: 'legend',
                    explain: 'legend标签位置top,right,bottom,left',
                    type: 'String',
                    default: 'right'
                },
                {
                    attr: 'xAxis',
                    explain: '轴不显示：none轴线-分割线-分割线类型：line-split-solid，line-split-dashed，line-split-dotted轴线不显示-分割线-分割线类型：noline-split-solid，noline-split-dashed，noline-split-dotted',
                    type: 'String',
                    default: ''
                },
                {
                    attr: 'yAxis',
                    explain: '轴不显示：none轴线-分割线-分割线类型：line-split-solid，line-split-dashed，line-split-dotted轴线不显示-分割线-分割线类型：noline-split-solid，noline-split-dashed，noline-split-dotted',
                    type: 'String,Array',
                    default: ''
                },
                {
                    attr: 'tooltip',
                    explain: '直线指示器line阴影指示器shadow无指示器none十字准星指示器cross',
                    type: 'String',
                    default: ''
                },
                {
                    attr: 'series',
                    explain: '单维单组[],多维单组{y0:[],y1:[]},多维混合{y0:{s0:[],s1:[]},y1:[]}或多维多组{y0:{s0:[],s1:[]},y1:{s0:[],s1:[]}}',
                    type: 'Array,Object',
                    default: '[]'
                },
            ],
            opt: {
                loading: false,
                chartType: ['lineArea', 'line'],
                multiple: true,
                smooth: false,
                barMaxWidth: 20,
                legendData: [['上海', '深圳'], '广州'],
                unit: ['元', '%'],
                colors: [['#8B572A', '#50E3C2'], '#7ED321'],
                legend: 'top',
                xAxis: '',
                yAxis: '',
                tooltip: '',
                series: {
                    y0: {
                        s1: [
                            { name: '周一', value: 212 },
                            { name: '周二', value: 300 },
                            { name: '周三', value: 240 },
                            { name: '周四', value: 320 },
                            { name: '周五', value: 400 },
                            { name: '周六', value: 350 },
                            { name: '周日', value: 200 }
                        ],
                        s2: [
                            { name: '周一', value: 67 },
                            { name: '周二', value: 130 },
                            { name: '周三', value: 340 },
                            { name: '周四', value: 230 },
                            { name: '周五', value: 430 },
                            { name: '周六', value: 200 },
                            { name: '周日', value: 370 }
                        ]
                    },
                    y1: [
                        { name: '周一', value: 12 },
                        { name: '周二', value: 20 },
                        { name: '周三', value: 34 },
                        { name: '周四', value: 42 },
                        { name: '周五', value: 30 },
                        { name: '周六', value: 25 },
                        { name: '周日', value: 30 }
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
