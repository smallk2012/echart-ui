<template>
    <div class="ex-demo">
        <api-panel page="select" title="select" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-select @changeOptionEvt="onChangeOption" :defaultIndex="opt.defaultIndex" :width="opt.width" :options="opt.options"></ms-select>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExSelect',
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
                defaultIndex: '北京',
                width: 160,
                options: [
                    {
                        name: '上海',
                        value: '0'
                    },
                    {
                        name: '北京',
                        value: '1'
                    },
                    {
                        name: '广州',
                        value: '2'
                    },
                    {
                        name: '深圳',
                        value: '3'
                    }
                ]
            }
        }
    },
    methods: {
        onChangeOption (__val, __index) {
            // this.opt.defaultIndex = __index
        },
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
