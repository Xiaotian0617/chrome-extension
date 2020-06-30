<template>
  <div>
  <el-button type="success" @click="tableNum===1?tableNum=0:tableNum=1">切换按钮</el-button>
   <el-table
      :data="tableNum === 1 ?tableData:tableData2"
      v-loading="loading"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
        <el-table-column
      fixed="right"
      label="操作"
      width="100">
      <template slot-scope="scope">
        <el-popover
          placement="right"
          width="400"
          trigger="click">
          <el-table :data="gridData">
            <el-table-column width="150" property="date" label="日期"></el-table-column>
            <el-table-column width="100" property="name" label="姓名"></el-table-column>
            <el-table-column width="300" property="address" label="地址"></el-table-column>
          </el-table>
          <el-button slot="reference">查看</el-button>
        </el-popover>
        <!-- <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button> -->
        <el-button type="text" size="small" @click="showDiaog">编辑</el-button>
      </template>
    </el-table-column>
    </el-table>
    <el-dialog
      title="提示"
      :visible.sync="dialogVisible"
      width="30%"
      :before-close="handleClose">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>
    
  </div>
</template>

<script>
export default {
  data () {
    return {
      message: '我的热情，好像一把火',
      loading:true,
      dialogVisible:false,
      tableNum: 1,
      gridData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
      tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }],
        tableData2: [{
            date: '2016-05-02',
            name: '王虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }]
    }
  },
  created(){
    console.log('this is created')
  },
  beforeCreate(){
    console.log('this is beforeCreate')
  },
  mounted(){
    setTimeout(()=>{
      this.loading = false;
    },2000)
  },
  methods: {
    showDiaog(){
      this.dialogVisible = true
    }
  }
}
</script>

<style lang="scss" scoped>
p {
  font-size: 20px;
}
</style>
