<template>
  <div id="app">
    <Diytablenav :tableData="tableData" :navheader="heade" :addpop="true" @inputer="inputpa" @datapoicker="datapoicker"
      @changeselect="changepa" @handleEdit="handleEdit" @handleDelete="handleDelete">
    </Diytablenav>
  </div>
</template>

<script>
import Diytablenav from "./components/Diytablenav/index.vue"

export default {
  name: 'App',
  components: {
    Diytablenav
  },
  data() {
    return {
      tableData: {
        data: [{
          date: '2016-05-03',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-02',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-04',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-01',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-08',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-06',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-07',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }],
        proplabelobj: [{ prop: 'date', label: '日期' }, { prop: 'name', label: '姓名' },
        { prop: 'province', label: '省份' }, { prop: 'city', label: '市区' }, { prop: 'city', label: '地址' }], setting: {},
      },
      heade: [
        { type: 1, title: '配置1', placeholder: '请输入城市名称' },
        { type: 1, title: '配置2', placeholder: '请输入姓名' },
        { type: 3, title: '配置4' },
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
        {
          type: 2,
          title: '配置5',
          placeholder: '请输入城市类型',
          options: [{
            value: '选项1',
            label: '黄金糕'
          }, {
            value: '选项2',
            label: '双皮奶'
          }]
        }
      ]
    }
  },
  methods: {
    inputpa(e) {
      console.log('input', e)
    },
    changepa(e) {
      console.log('selecet', e)
    },
    datapoicker(e) {
      console.log('datapoicker', e)
    },
    handleEdit(e) {
      console.log('handleEdit', e)
    },
    handleDelete(e) {
      console.log('handleDelete', e)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
