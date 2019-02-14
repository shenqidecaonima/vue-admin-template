<template>
  <div class="container" style="padding:30px;">
    <h2>用户列表</h2>
    <el-input
      placeholder="用户名/手机"
      v-model="search"
      style="width: 200px;"
      clearable />

    <el-button-group class="editButton">
      <el-button icon="el-icon-circle-plus" @click="insertDataVisiable = true" type="primary">新增</el-button>
      <el-button icon="el-icon-delete" type="danger">删除</el-button>
      <el-button icon="el-icon-refresh" type="warning">刷新</el-button>
    </el-button-group>

    <el-dialog
      :visible.sync="insertDataVisiable"
      title="用户新增"
      width="80%">
      <el-form v-model="form">
        <el-form-item label="用户名称" :label-width="formLabelWidth">
          <el-input v-model= "form.name"></el-input>
        </el-form-item>
        <el-form-item label="登录名" :label-width="formLabelWidth">
          <el-input v-model= "form.userName"></el-input>
        </el-form-item>
        <el-form-item label="手机号码" :label-width="formLabelWidth">
          <el-input v-model= "form.phone"></el-input>
        </el-form-item>
        <el-form-item label="邮箱" :label-width="formLabelWidth">
          <el-input v-model= "form.email"></el-input>
        </el-form-item>
        <el-checkbox-group v-model="form.checkList">
          <el-checkbox label="超级管理员"></el-checkbox>
          <el-checkbox label="董事长"></el-checkbox>
          <el-checkbox label="总经理"></el-checkbox>
          <el-checkbox label="副总经理"></el-checkbox>
          <el-checkbox label="业务负责人"></el-checkbox>
          <el-checkbox label="业务专员"></el-checkbox>
          <el-checkbox label="财务负责人"></el-checkbox>
          <el-checkbox label="财务会计"></el-checkbox>
          <el-checkbox label="财务出纳"></el-checkbox>
          <el-checkbox label="风控负责人"></el-checkbox>
          <el-checkbox label="风控信审"></el-checkbox>
          <el-checkbox label="风控法务"></el-checkbox>
          <el-checkbox label="操作专员"></el-checkbox>
          <el-checkbox label="印章管理员"></el-checkbox>
          <el-checkbox label="财务章专员"></el-checkbox>
          <el-checkbox label="第三方资金客户"></el-checkbox>
          <el-checkbox label="管理员演示用户"></el-checkbox>
        </el-checkbox-group>
        <div>
          <el-button>保存</el-button>
        </div>
      </el-form>

      <span>Message: {{ form.name}} {{form.userName}} {{form.phone}} {{form.email}} {{form.checkList}}</span>
    </el-dialog>
<!--Checkbox for selecting roles
    <div class="checkbox">
      <el-checkbox label="name">用户名称</el-checkbox>
      <el-checkbox label="role">角色</el-checkbox>
      <el-checkbox label="userName">登录名</el-checkbox>
      <el-checkbox label="phone">电话</el-checkbox>
      <el-checkbox label="email">邮箱</el-checkbox>
      <el-checkbox label="updateTime">更新时间</el-checkbox>
    </div>
-->
    <el-table
      class="tableData"
      :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()) || data.phone.includes(search.toLowerCase()))"
      border
      fit
      highlight-current-row
      style="width: 100%;margin-top: 30px">
      <el-table-column type="selection" />
      <el-table-column
        prop="name"
        label="用户名称"
        align="center"
        width="180" />
      <el-table-column
        prop="role"
        label="角色"
        width="180"
        align="center"
        :filters="filters"
        :filter-method="filterRole" />
      <el-table-column
        prop="userName"
        align="center"
        width="150"
        label="登录名" />
      <el-table-column
        prop="phone"
        align="center"
        width="150"
        label="手机号码" />
      <el-table-column
        prop="email"
        align="center"
        min-width="150"
        label="邮箱" />
      <el-table-column
        prop="updateTime"
        align="center"
        min-width="150"
        label="更新时间" />
    </el-table>
    

  </div>
</template>


<script>
export default {
  data() {
    return {
      search:'',
      tableData: [
        {
          name: '',
          role: '',
          userName: '',
          phone: '',
          email: '',
          updateTime: ''
        }
      ],
      dataQuery: {
        name: ''
      },
      insertDataVisiable: false,
      dialogVisible: false,
      form: {
        name: '',
        userName:'',
        phone:'',
        email:'',
        role: '',
        checkList:[]
      },
      filters: null,
      formLabelWidth: '120px'
    };
  },
  created() {
    this.getTableData()
    this.filtersStart()
    console.log('started')
  },
  methods: {
    filtersStart() {
      this.filters = [
        {
          text:'董事长',
          value:'1'
        },
        {
          text: '超级管理员',
          value: '2'
        }
      ]
    },
    filterRole(value, row) {
      return row.roleid === value;
    },
    getTableData() {
      this.tableData = [
        {
          name: '1',
          roleid: '1',
          role: '董事长',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'a',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '1',
          role: '1',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: 'A',
          roleid: '2',
          role: '超级管理员',
          userName: '1',
          phone: '1',
          email: '1',
          updateTime: '1111-11-11'
        },
        {
          name: '2',
          roleid: '2',
          role: '超级管理员',
          userName: '2',
          phone: '30',
          email: '2',
          updateTime: '1111-11-11'
        }
      ]
    }
  }
}
</script>

<style>
  .checkbox {
    margin-top: 20px;
  }
  .editButton {
    margin-left: 50%;
  }
</style>
