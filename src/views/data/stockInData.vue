<template>
<div>
  <el-table
    border
    ref="multipleTable"
    :data="tableData"
    tooltip-effect="dark"
    style="width: 100%"
    @selection-change="handleSelectionChange">
    <el-table-column
      label="入库时间">
      <template slot-scope="scope">{{ scope.row.date }}</template>
    </el-table-column>
    <el-table-column
      prop="number"
      label="入库单号"
      width="200">
      <el-button slot-scope="scope" type="text" size="small" round @click="dialogTableVisible = true">{{ scope.row.number }}</el-button>
    </el-table-column>
    <el-table-column
      prop="providerType"
      label="供应商种类">
    </el-table-column>
    <el-table-column
      prop="coreName"
      label="核心企业名称">
    </el-table-column>
    <el-table-column
      prop="entrepotName"
      label="仓库名称">
    </el-table-column>
    <el-table-column
      prop="wasteTotals"
      label="废品总数量">
    </el-table-column>
  </el-table> 

  <template>
    <div>
      <el-pagination
        small
        layout="prev, pager, next"
        :total="50"
        style="text-align:right;padding-top:10px" /> 
      </div>
  </template>
    
    <template>
      <div>
        <el-dialog title="入库单详情" :visible.sync="dialogTableVisible">
          <el-table :data="gridData" border>
            <el-table-column property="name" label="供应商名称"></el-table-column>
            <el-table-column property="acceptName" label="核心企业名称"></el-table-column>
            <el-table-column property="date" label="入库时间"></el-table-column>
            <el-table-column property="number" label="入库单号"></el-table-column>
            <el-table-column property="entrepotName" label="仓库名称"></el-table-column>
            <el-table-column property="entrepotAdd" label="仓库地址"></el-table-column>
            <el-table-column property="name2" label="仓库联系人"></el-table-column>
            <el-table-column property="tel" label="仓库联系电话"></el-table-column>
          </el-table>
          <el-table :data="gridData2" style="margin-top:50px" border>
            <el-table-column property="number" label="废品单号"></el-table-column>
            <el-table-column property="name" label="废品名称"></el-table-column>
            <el-table-column property="totals" label="总量"></el-table-column>
          </el-table>
          <div slot="footer" class="dialog-footer">
            <el-button type="primary" @click="dialogTableVisible = false">确 定</el-button>
          </div>
        </el-dialog>
      </div>        
    </template>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tableData: [{
          date: '2016-05-03',
          number:'SF20191230123456030',
          providerType:'国企',
          providerName:'福建船厂',
          name: '中国重工',
          coreName:'中国化工',
          entrepotName:'八号仓库',
          wasteTotals:'5000KG'
        },
        {
          date: '2018-12-23',
          number:'SF2456030',
          providerType:'国企',
          providerName:'福建船厂',
          name: '中国重工',
          coreName:'中国石化',
          entrepotName:'五号仓库',
          wasteTotals:'5000KG'
        }],
        multipleSelection: [],
        dialogTableVisible: false,
        gridData: [{
          name:'中国园林',
          acceptName:'绿化企业',
          date: '2016-05-03',
          number: 'SW2345678',
          name2: '钟启超',
          tel:'18679089745',
          entrepotName:'五号仓库',
          entrepotAdd:'上海市'
        }],
        gridData2: [{
          number: 'SW2345678',
          name: '树木',
          totals: '50吨'
        }, 
        {
          number: 'SW2345678',
          name: '树木',
          totals: '50吨'
        }]
      }
    },

    methods: {
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      }
    }
  }
</script>