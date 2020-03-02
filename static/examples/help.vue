<template>
    <div class="ex-help">
        <api-panel page="help" title="api-panel" :code="code" :trs="trs" :is-run="false" @clickRunEvt="clickRunEvt">
            <div>这里是展示组件效果的地方</div>
        </api-panel>
    </div>
</template>

<script>
import tool from '../util/tool'
export default {
    name: 'ExHelp',
    data () {
        return {
            code: '',
            trs: [
                {
                    attr: 'page',
                    explain: '页面标签',
                    type: 'String',
                    default: 'help'
                },
                {
                    attr: 'title',
                    explain: '标题',
                    type: 'String',
                    default: ''
                },
                {
                    attr: 'code',
                    explain: '示例代码',
                    type: 'Script',
                    default: ''
                },
                {
                    attr: 'trs',
                    explain: '[{attr: "title",explain: "标题",type: "String",default: ""}]',
                    type: 'Array',
                    default: '[]'
                },
                {
                    attr: 'isRun',
                    explain: '示例是否可以运行',
                    type: 'Boolean',
                    default: 'true'
                },
                {
                    attr: 'clickRunEvt',
                    explain: '运行示例按钮回调',
                    type: 'Function',
                    default: ''
                }
            ],
            opt: {
                code: '',
                trs: [
                    {
                        attr: 'page',
                        explain: '页面标签',
                        type: 'String',
                        default: 'help'
                    },
                    {
                        attr: 'title',
                        explain: '标题',
                        type: 'String',
                        default: ''
                    },
                    {
                        attr: 'code',
                        explain: '示例代码',
                        type: 'Script',
                        default: ''
                    },
                    {
                        attr: 'trs',
                        explain: '[{attr: "title",explain: "标题",type: "String",default: ""}]',
                        type: 'Array',
                        default: '[]'
                    },
                    {
                        attr: 'isRun',
                        explain: '示例是否可以运行',
                        type: 'Boolean',
                        default: 'true'
                    },
                    {
                        attr: 'clickRunEvt',
                        explain: '运行示例按钮回调',
                        type: 'Function',
                        default: ''
                    }
                ]
            }
        }
    },
    methods: {
        clickRunEvt () {
            /*
            var _opt = window.opt || {}
            for (var o in _opt) {
                if (this.opt.hasOwnProperty(o)) {
                    this.opt[o] = _opt[o]
                }
            }
            */
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
</style>
