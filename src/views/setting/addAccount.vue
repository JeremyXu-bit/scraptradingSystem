<template>
    <el-form ref="form" :model="form" label-width="80px">
        <el-form-item label="角色">
            <!-- <el-input v-model="form.roles"></el-input> -->
            <template>
                <el-select v-model="roles" placeholder="角色">
                    <el-option
                    v-for="item in options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value">
                    </el-option>
                </el-select>
            </template>
        </el-form-item>
        <el-form-item label="账号">
            <el-input v-model="form.account"></el-input>
        </el-form-item>
        <el-form-item label="姓名">
            <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="电话">
            <el-input v-model="form.tel"></el-input>
        </el-form-item>
        <el-form-item>
            <el-button type="primary" style="float: right;" @click="open" v-loading.fullscreen.lock="fullscreenLoading">确认</el-button>
        </el-form-item>
    </el-form>
    
</template>
<script>
  export default {
    data() {
      return {
        fullscreenLoading: false,
        roles:'',
        form:{
            account:'',
            name:'',
            tel:''
        },
        options: [{
          value: '选项1',
          label: '运营'
        }, {
          value: '选项2',
          label: '客服'
        }],
        value:''
      }
    },
    methods: {
      open() {
          this.fullscreenLoading = true;
        setTimeout(() => {
          this.fullscreenLoading = false;
          this.$message({
            message: '添加成功！',
            type: 'success'
            });
        }, 2000);
      }
    }
  }
</script>
