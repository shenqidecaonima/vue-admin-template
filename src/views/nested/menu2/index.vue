<template>
  <div class="container" style="padding:30px;">
    <h2>菜单列表</h2>
    <el-input
      placeholder="菜单名称"
      style="width: 200px;"
      v-model="search"
      clearable />
    <el-button-group class="editButton">
      <el-button icon="el-icon-circle-plus" @click="insertDataVisiable = true">新增</el-button>
      <el-button icon="el-icon-refresh">刷新</el-button>
    </el-button-group>

    <el-dialog
      :visible.sync="insertDataVisiable"
      title="菜单新增"
      width="50%">
      <el-form v-model="form">
        <el-form-item label="菜单名称" :label-width="formLabelWidth">
          <el-input v-model= "form.name"></el-input>
        </el-form-item>
        <el-form-item label="菜单链接" :label-width="formLabelWidth">
          <el-input v-model= "form.link"></el-input>
        </el-form-item>
        <el-form-item label="上级菜单" :label-width="formLabelWidth">
          <el-select v-model="form.prevMenu" placeholder="请选择上级菜单">
            <el-option label="顶级菜单" value="1"></el-option>
            <el-option label="客户管理" value="2"></el-option>
          </el-select>
        </el-form-item>
      </el-form>
      <span>Message: {{ form.name}} {{form.link}} {{form.prevMenu }}</span>
    </el-dialog>

    <el-checkbox class="checked" v-model = "checked">菜单名称</el-checkbox>

    <el-table
      class="tableData"
      :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()))"
      border
      fit
      highlight-current-row
      style="width: 80%; margin-top: 20px">
      <el-table-column
        prop="name"
        label="菜单名称"
        header-align="center"
        width="180" />
      <el-table-column
        prop="link"
        label="链接"
        header-align="center" />
      <el-table-column
        prop="updateTime"
        header-align="center"
        width="300"
        label="更新时间" />
    </el-table>
    <el-pagination
      :page-size="5"
      :total="20"
      layout="prev, pager, next, jumper, total" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      search:'',
      checked: false,
      tableData: null,
      dataQuery: {
        name: ''
      },
      insertDataVisiable: false,
      dialogVisible: false,
      form: {
        name: '',
        link:'',
        updateTime:'',
        prevMenu:''
      },
      formLabelWidth: '120px'
    };
  },
  created() {
    this.getTableData()
    console.log('started')
  },
  methods: {
    getTableData() {
      this.tableData = [
        {
          name: '1',
          link: '1',
          updateTime: '0000-00-00'
        },
        {
          name: '2',
          link: '2',
          updateTime: '0000-00-00'
        },
        {
          name: '3',
          link: '3',
          updateTime: '0000-00-00'
        },
        {
          name: '4',
          link: '4',
          updateTime: '0000-00-00'
        }
      ]
    },
    cellClickEvent() {
      console.log("cell clicked")
    }
  }
}
</script>

<style>
  .editButton {
    margin-left: 50%;
  }
</style>
