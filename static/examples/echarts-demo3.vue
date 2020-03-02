<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo3" title="柱组图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :chart-type="opt.chartType" :legendData="opt.legendData" :unit="opt.unit" :colors="opt.colors" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo3',
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
                chartType: 'bar',
                legendData: ['认证', '新增', '净增'],
                unit: '人',
                colors: [[['#FD687D', '#FFC796'], ['#55D284', '#9FE7BB'], ['#3FA2EA', '#73CFF6']]],
                yAxis: 'line-split-dashed',
                tooltip: '',
                series: {
                    y0: [
                        { name: '白羊座', value: 100 },
                        { name: '金牛座', value: 200 },
                        { name: '双子座', value: 300 },
                        { name: '巨蟹座', value: 400 },
                        { name: '狮子座', value: 500 },
                        { name: '处女座', value: 600 },
                        { name: '天秤座', value: 500 },
                        { name: '天蝎座', value: 400 },
                        { name: '射手座', value: 300 },
                        { name: '摩羯座', value: 200 },
                        { name: '水瓶座', value: 100 },
                        { name: '双鱼座', value: 200 }
                    ],
                    y1: [
                        { name: '白羊座', value: 200 },
                        { name: '金牛座', value: 270 },
                        { name: '双子座', value: 370 },
                        { name: '巨蟹座', value: 410 },
                        { name: '狮子座', value: 530 },
                        { name: '处女座', value: 360 },
                        { name: '天秤座', value: 150 },
                        { name: '天蝎座', value: 340 },
                        { name: '射手座', value: 830 },
                        { name: '摩羯座', value: 620 },
                        { name: '水瓶座', value: 210 },
                        { name: '双鱼座', value: 520 }
                    ],
                    y2: [
                        { name: '白羊座', value: 333 },
                        { name: '金牛座', value: 555 },
                        { name: '双子座', value: 222 },
                        { name: '巨蟹座', value: 444 },
                        { name: '狮子座', value: 555 },
                        { name: '处女座', value: 900 },
                        { name: '天秤座', value: 444 },
                        { name: '天蝎座', value: 654 },
                        { name: '射手座', value: 324 },
                        { name: '摩羯座', value: 123 },
                        { name: '水瓶座', value: 654 },
                        { name: '双鱼座', value: 765 }
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
