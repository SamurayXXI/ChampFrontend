<template>
  <div class="Championships">
    <h1>Чемпионаты</h1>
    <el-button plain @click="onOpenClick">Открыть</el-button>
    <el-button plain>Добавить</el-button>
    <el-button plain>Удалить</el-button>
    <el-table
      :data="champs"
      ref="champTable"
      highlight-current-row
      @current-change="handleCurrentChange"
      style="width: 100%">
      <el-table-column
        type="index"
        width="50">
      </el-table-column>
      <el-table-column
        prop="name"
        label="Имя"
        width="180">
      </el-table-column>
      <el-table-column
        prop="national"
        label="Национальный"
        width="180">
        <template slot-scope="scope">
          <i v-if="scope.row.national" class="el-icon-check"></i>
          <i v-else class="el-icon-close"></i>
        </template>
      </el-table-column>

      <el-table-column>
      </el-table-column>

    </el-table>
    <p>{{ this.currentRow }}</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Championships',
  props: {
    msg: String
  },
  data() {
    return {
      champs: null,
      currentRow: null
    };
  },
  methods: {
    setCurrent(row) {
        this.$refs.champTable.setCurrentRow(row);
      },
    handleCurrentChange(val) {
      this.currentRow = val;
    },
    onOpenClick(){
      console.log("onOpenClick")
      this.$router.push("/champs/"+this.currentRow.id+"/seasons")
    }
  },
  mounted() {
    axios
      .get('http://localhost:8000/championships/', { 'headers': {"accept": "application/json"} })
      .then(response => (this.champs = response.data));
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: white;
}
</style>
