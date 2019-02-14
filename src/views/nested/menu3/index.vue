<template>
  <div style="padding:30px;">
    <h2>角色管理</h2>
    <el-button-group style="margin-top: 20px">
      <el-button icon="el-icon-circle-plus" @click="insertDataVisiable = true" type="primary">新增</el-button>
      <el-button icon="el-icon-delete" type="danger">删除</el-button>
      <el-button icon="el-icon-edit" type="success">编辑</el-button>
    </el-button-group>

    <div style="margin-top: 30px">
      <div class="radio">
        <el-radio v-model="rolePick" label="1">超级管理员</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="2">董事长</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="3">总经理</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="4">副总经理</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="5">业务负责人</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="6">业务专员</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="7">财务负责人</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="8">财务会计</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="9">财务出纳</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="10">风控负责人</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="11">风控信审</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="12">风控法务</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="13">操作专员</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="14">印章管理员</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="15">财务章专员</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="16">第三方资金客户</el-radio>
      </div>
      <div class="radio">
        <el-radio v-model="rolePick" label="17">管理员演示用户</el-radio>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        rolePick: []
      }
    }
  }
</script>
<style>
  .radio {
    margin-top: 10px;
  }
</style>
