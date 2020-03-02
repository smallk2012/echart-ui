<template>
    <div class="ex-demo">
        <api-panel page="tabs" title="tabs-navs" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-tabs :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
            <ms-tabs :size="opt.size" margin="10px 0 0 0" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
            <ms-tabs :underline="true" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
            <ms-tabs :underline="true" :size="opt.size" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExTabs',
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
                size: 'small',
                defaultIndex: 0,
                tabs: ['上海', '深圳']
            }
        }
    },
    methods: {
        clickTabEvt: function (__val, __index) {
            this.opt.defaultIndex = __val
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
