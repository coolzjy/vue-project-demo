<template>
  <div class="hello">
    <div style="display: flex; width: 500px;">
      <el-input v-model="input" placeholder="记录 ID"></el-input>
      <el-button @click="handler">提交</el-button>
    </div>
    <el-table
      :data="rows"
      :row-class-name="getRowClass"
      style="width: 100%">
      <el-table-column
        prop="userId"
        label="用户ID"
        width="180">
      </el-table-column>
      <el-table-column
        prop="id"
        label="ID"
        width="180">
      </el-table-column>
      <el-table-column
        prop="title"
        label="标题">
      </el-table-column>
      <el-table-column
        prop="body"
        label="详情">
        <template slot-scope="scope">
          <el-input v-model="scope.row.body"></el-input>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      input: '',
      rows: []
    }
  },

  methods: {
    getRowClass ({ row, rowIndex }) {
      if (rowIndex === 9) {
        return 'red'
      }
    },

    handler () {
      axios.get('https://jsonplaceholder.typicode.com/posts').then(res => {
        this.rows = res.data
      })
    }
  },

  created () {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.red {
  color: red;
}
</style>
