<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo1" title="柱线图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-basic :loading="opt.loading" :chart-type="opt.chartType" :multiple="opt.multiple" :legendData="opt.legendData" :unit="opt.unit" :colors="opt.colors" :yAxis="opt.yAxis" :tooltip="opt.tooltip" :series="opt.series"></ms-echarts-basic>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo1',
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
                loading: false,
                chartType: ['bar', 'line'],
                multiple: true,
                legendData: ['客流量', '客流比'],
                unit: ['人', '%'],
                colors: [[['#3FA2EA', '#73CFF6']], '#55D284'],
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
                        { name: '白羊座', value: 10 },
                        { name: '金牛座', value: 20 },
                        { name: '双子座', value: 30 },
                        { name: '巨蟹座', value: 40 },
                        { name: '狮子座', value: 50 },
                        { name: '处女座', value: 60 },
                        { name: '天秤座', value: 50 },
                        { name: '天蝎座', value: 40 },
                        { name: '射手座', value: 30 },
                        { name: '摩羯座', value: 20 },
                        { name: '水瓶座', value: 10 },
                        { name: '双鱼座', value: 20 }
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
