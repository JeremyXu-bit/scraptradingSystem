<template>
    <div>
      <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="入库时间" style="margin-bottom: -15px;">
              <el-col :span="11">
              <el-date-picker type="date" placeholder="开始时间" v-model="form.date1" style="width: 100%;"></el-date-picker>
              </el-col>
              <el-col class="line" :span="2"> -</el-col>
              <el-col :span="11">
              <el-date-picker type="date" placeholder="结束时间" v-model="form.date2" style="width: 100%;"></el-date-picker>
              </el-col>
          </el-form-item>
          <!-- <el-form-item label="审核状态">
              <el-select v-model="form.status" placeholder="审核中">
              <el-option label="审核中" value="auditing"></el-option>
              <el-option label="成功" value="success"></el-option>
              <el-option label="失败" value="faily"></el-option>
              </el-select>
          </el-form-item> -->
          <el-form-item label="供应商类型">
              <el-select v-model="form.type" placeholder="个人">
              <el-option label="企业" value="company"></el-option>
              <el-option label="个人" value="personal"></el-option>
              </el-select>
          </el-form-item>
          <el-form-item label="供应商名称">
              <el-input v-model="form.name"></el-input>
          </el-form-item>
          <el-form-item label="入库单号">
              <el-input v-model="form.number"></el-input>
          </el-form-item>
          <el-form-item label="核心企业名称">
              <el-input v-model="form.coreName"></el-input>
          </el-form-item>
          <el-form-item label="仓库名称">
              <el-input v-model="form.entrepotName"></el-input>
          </el-form-item>
          <el-form-item>
              <el-button>搜索</el-button>
              <!-- <el-button @click="dialogFormVisible = true">确定接受</el-button> -->
          </el-form-item>
          <div style="margin-top:50px">
              <stockInData></stockInData>
          </div>
      </el-form>
      </div>
    </template>

<script>
    import stockInData from '../../views/data/stockInData.vue'

  export default {
    components: {stockInData},

    data() {
      return {
        form: {
          date1: '',
          date2: '',
          number: '',
          type: '',
          name:''
        }
      };
    },
    methods: {
      onSubmit() {
        this.$message({
            message: '提交成功',
            type: 'success'
            });
        }
    }
  }
</script>
<style scoped>
.el-form-item{
    width: 50%;
    display: inline-block;
}
</style>