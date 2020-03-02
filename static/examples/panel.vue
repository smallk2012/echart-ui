<template>
    <div class="ex-demo">
        <api-panel page="panel" title="面板" :code="code" lang="text" :trs="trs" @clickRunEvt="clickRunEvt">
            <ms-panel :title="opt.title"></ms-panel>
            <ms-panel :title="opt.title" :tip="opt.tip">
                <div slot="header-cont">
                    <ms-select size="small" @changeOptionEvt="onChangeOption" label="选择1" :defaultIndex="selectData.defaultIndex" :options="selectData.options"></ms-select>
                    <ms-tabs size="small" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
                    <ms-select size="small" @changeOptionEvt="onChangeOption" label="选择2" :defaultIndex="selectData.defaultIndex" :options="selectData.options"></ms-select>
                </div>
            </ms-panel>
            <ms-panel :title="opt.title" :tip="opt.tip" :bodyPadding="opt.bodyPadding">
                <ms-tabs slot="header" size="small" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
                <div class="body">
                    <p>我是面板的内容，可以自由发挥</p>
                    <ms-tabs slot="header" :defaultIndex="opt.defaultIndex" :tabs="opt.tabs" @clickTabEvt="clickTabEvt"></ms-tabs>
                </div>
            </ms-panel>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExPanel',
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
                defaultIndex: '我',
                tabs: ['你', '我'],
                title: '我是一个面板',
                tip: '我是提示',
                bodyPadding: '10px'
            },
            selectData: {
                defaultIndex: 0,
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
        clickTabEvt: function (__val) {
            this.opt.defaultIndex = __val
        },
        onChangeOption (__index) {
            this.selectData.defaultIndex = __index
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
        this.code = 'opt={ ' + (tool.deepJson(this.opt) || '') + '}'
    }
}

</script>

<style scoped lang="scss">
pre {
    display: none;
}
.ms-panel /deep/ {
    .ms-tabs {
        float: left;
        margin-left: 1px;
        padding-top: 10px;
    }
    .ms-select {
        float: left;
        margin-top: 10px;
        margin-left: 15px;
    }
}
</style>
