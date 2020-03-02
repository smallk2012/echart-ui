<template>
    <div class="ex-echarts-demo">
        <api-panel page="echarts-demo14" title="横轴柱图" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-echarts-axis :chart-type="opt.chartType" :unit="opt.unit" :legend="opt.legend" :legendData="opt.legendData" :colors="opt.colors" :series="opt.series"></ms-echarts-axis>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExEchartsDemo14',
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
                chartType: 'barStack',
                legend: 'bottom',
                legendData:['0-50次','50-100次','100-150次','150次及以上'],
                unit: '分钟',
                colors: ['#DA97A1', '#FFC796', '#55D284', '#9C87E5'],
                series: {
                    y0: [
                        {
                            name: '白羊座',
                            value: 10
                        },
                        {
                            name: '金牛座',
                            value: 10
                        },
                        {
                            name: '双子座',
                            value: 10
                        },
                        {
                            name: '巨蟹座',
                            value: 10
                        },
                        {
                            name: '狮子座',
                            value: 10
                        },
                        {
                            name: '处女座',
                            value: 10
                        },
                        {
                            name: '天秤座',
                            value: 10
                        },
                        {
                            name: '天蝎座',
                            value: 10
                        },
                        {
                            name: '射手座',
                            value: 10
                        },
                        {
                            name: '摩羯座',
                            value: 10
                        },
                        {
                            name: '水瓶座',
                            value: 10
                        },
                        {
                            name: '双鱼座',
                            value: 10
                        }
                    ],
                    y1: [
                        {
                            name: '白羊座',
                            value: 25
                        },
                        {
                            name: '金牛座',
                            value: 25
                        },
                        {
                            name: '双子座',
                            value: 25
                        },
                        {
                            name: '巨蟹座',
                            value: 25
                        },
                        {
                            name: '狮子座',
                            value: 25
                        },
                        {
                            name: '处女座',
                            value: 25
                        },
                        {
                            name: '天秤座',
                            value: 25
                        },
                        {
                            name: '天蝎座',
                            value: 25
                        },
                        {
                            name: '射手座',
                            value: 25
                        },
                        {
                            name: '摩羯座',
                            value: 25
                        },
                        {
                            name: '水瓶座',
                            value: 25
                        },
                        {
                            name: '双鱼座',
                            value: 25
                        }
                    ],
                    y2: [
                        {
                            name: '白羊座',
                            value: 40
                        },
                        {
                            name: '金牛座',
                            value: 40
                        },
                        {
                            name: '双子座',
                            value: 40
                        },
                        {
                            name: '巨蟹座',
                            value: 40
                        },
                        {
                            name: '狮子座',
                            value: 40
                        },
                        {
                            name: '处女座',
                            value: 40
                        },
                        {
                            name: '天秤座',
                            value: 40
                        },
                        {
                            name: '天蝎座',
                            value: 40
                        },
                        {
                            name: '射手座',
                            value: 40
                        },
                        {
                            name: '摩羯座',
                            value: 40
                        },
                        {
                            name: '水瓶座',
                            value: 40
                        },
                        {
                            name: '双鱼座',
                            value: 40
                        }
                    ],
                    y3: [
                        {
                            name: '白羊座',
                            value: 25
                        },
                        {
                            name: '金牛座',
                            value: 25
                        },
                        {
                            name: '双子座',
                            value: 25
                        },
                        {
                            name: '巨蟹座',
                            value: 25
                        },
                        {
                            name: '狮子座',
                            value: 25
                        },
                        {
                            name: '处女座',
                            value: 25
                        },
                        {
                            name: '天秤座',
                            value: 25
                        },
                        {
                            name: '天蝎座',
                            value: 25
                        },
                        {
                            name: '射手座',
                            value: 25
                        },
                        {
                            name: '摩羯座',
                            value: 25
                        },
                        {
                            name: '水瓶座',
                            value: 25
                        },
                        {
                            name: '双鱼座',
                            value: 25
                        }
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
