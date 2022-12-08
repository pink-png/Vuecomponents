<template>
    <div class="contioner">
        <div class="box">
            <!-- 配置头部 -->
            <div class="header">
                <div class="item" v-for="(item, index) in navheader" :key="index">
                    <template v-if="(item.type == 1)">
                        <div class="title">{{ item.title }}：</div>
                        <el-input :ref="`input${index}`" v-model="vmodelnavdata[`model${index}`]"
                            @input="inputer($event, index)" :placeholder="item.placeholder"></el-input>
                    </template>
                    <template v-else-if="(item.type == 2)">
                        <div class="title">{{ item.title }}：</div>
                        <el-select @change="changeselect($event, index)" v-model="vmodelnavdata[`model${index}`]"
                            :placeholder="item.placeholder">
                            <el-option v-for="child in item.options" :key="child.value" :label="child.label"
                                :value="child.value">
                            </el-option>
                        </el-select>
                    </template>
                    <template v-else-if="(item.type == 3)">
                        <div class="title">{{ item.title }}：</div>
                        <el-date-picker v-model="vmodelnavdata[`model${index}`]" @change="datapoicker($event, index)"
                            type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期">
                        </el-date-picker>
                    </template>
                    <template v-else-if="(item.type == 4)">
                        <el-button :type="primary">{{ item.title }}</el-button>
                    </template>
                    <template v-else>
                        请输入正确的type
                    </template>
                </div>
            </div>
            <!-- 中间内容 -->
            <div class="btnpj">
            </div>
            <!-- 底部表格 -->
            <div class="btnpj">
                <el-table :data="tableData.data" style="width: 100%" max-height="350">
                    <el-table-column v-for="(childta, tbindex) in tableData.proplabelobj" :prop="(childta.prop)"
                        :label="(childta.label)" width="150">
                    </el-table-column>
                    <el-table-column fixed="right" label="操作" width="250">
                        <template slot-scope="scope">
                            <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                            <el-button size="mini" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                        </template>
                    </el-table-column>
                </el-table>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    props: {
        /**
         * 表格数据
         * data 数组数据
         * proplabelobj 配置字段和字段名回显
         * setting  iscaozuo 是否展示操作按钮
         */
        tableData: {
            type: Object,
            default: { data: [], proplabelobj: [{ prop: '', label: '' }], setting: { iscaozuo: true } }
        },
        /**
         * 头部配置
         *  type 是组件类型 title 是title 
         */
        navheader: {
            type: Array,
            default: [
                { type: 1, title: '配置1', placeholder: '请输入城市名称' },
                { type: 1, title: '配置2', placeholder: '请输入姓名' },
                { type: 3, title: '配置4', primary: 'primary' },
                {
                    type: 2,
                    title: '配置3',
                    placeholder: '请输入选择类型',
                    options: [{
                        value: '选项1',
                        label: '黄金糕'
                    }, {
                        value: '选项2',
                        label: '双皮奶'
                    }]
                },
                { type: 4, title: '配置1', placeholder: '请输入城市名称' },
            ]
        },
        /**
         * 新增按钮
         */
        addpop: {
            type: Boolean,
            default: false
        }
    },
    data() {
        const resdata = JSON.parse(JSON.stringify(this.$props)).navheader.map((item, index) => {
            return {
                "model": `model${index}`
            }
        })

        return {
            vmodelnavdata: resdata
        }
    },
    methods: {
        // 输入框
        // 根据index来判断是具体组件
        inputer(e, index) {
            // console.log('index', index)
            this.$emit('inputer', { data: e, index: index })
        },
        // 筛选框
        changeselect(e, index) {
            this.$emit('changeer', e)
        },
        // 时间选择框
        datapoicker(e, index) {
            this.$emit('datapoicker', e)
        },
        // 编辑
        handleEdit(index, row) {
            // console.log(index)
            // console.log(row)
            this.$emit('handleEdit', { index: index, data: row })
        },
        // 删除
        handleDelete(index, row) {
            // console.log(index)
            // console.log(row)
            this.$emit('handleDelete', { index: index, data: row })
        }
    }
}
</script>
<style scoped  lang="scss">
.contioner {
    .box {
        width: 100%;
        box-sizing: border-box;
        padding: 24px;

        .header {
            width: 100%;
            height: 140px;
            border: 1px solid #cccccc;
            display: flex;
            flex-wrap: wrap;

            .item {
                margin-left: 20px;
                display: flex;
                justify-content: space-between;
                align-items: center;

                .title {
                    min-width: 90px;
                }
            }
        }

        .btnpj {
            margin-top: 20px;
            width: 100%;
            border-radius: 30px;
        }

        .ertable {
            margin-top: 20px;
            width: 100%;
        }
    }
}
</style>