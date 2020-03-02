<template>
    <div class="ex-json">
        <api-panel title="JSON格式工具" :code="code" lang="text">
            <div slot="api-panel-cont-left">
                <textarea v-model="code"></textarea>
            </div>
            <div>
                <textarea v-model="jsonCode"></textarea>
            </div>
            <div slot="api-panel-footer">
                <div class="btn-run" @click="clickRunEvt">提交</div>
                <div class="ex-tips"></div>
            </div>
        </api-panel>
    </div>
</template>

<script>
import jftm from '../util/formatJson'
export default {
    name: 'ExHelp',
    data () {
        return {
            code: '{"name":"cC","job":"coding","info":[{"address":"shanghai"},{"interest":"coding"}]}',
            jsonCode: ''
        }
    },
    methods: {
        clickRunEvt () {
            this.jsonCode = jftm.json(this.code)
        }
    },
    mounted () {
        this.jsonCode = jftm.json(this.code)
    }
}

</script>

<style scoped lang="scss">
textarea {
    display: block;
    padding: 10px;
    width: 100%;
    height: 340px;
    border-radius: 4px;
    border-color: #ccc;
    outline: none;
}
pre {
    display: none;
}
.api-panel {
    padding-bottom: 10px;
}
.btn-run {
    display: block;
    margin-left: 10px;
    width: 80px;
    height: 32px;
    line-height: 32px;
    text-align: center;
    color: #2d8cf0;
    font-size: 14px;
    border: 1px solid #2d8cf0;
    border-radius: 4px;
    cursor: pointer;
}
.ex-tips {
    font-size: 14px;
    color: #ff0000;
}
</style>
