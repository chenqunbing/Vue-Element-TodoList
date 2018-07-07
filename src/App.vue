<template>
  <div id="app">
    <input v-model="inputVal" />
    <button @click='addItem'>Add</button>
    <ul>
      <li v-for="(list, index) in lists" :key="index" @click="showMessage(index)">{{list}}</li>
      <el-dialog :visible.sync="visible" title="Hello world">
        <p>Try Element</p>
        <el-row>
          <el-button @click="deletItem">确认删除</el-button>
          <el-button @click="cancelDelete">取消删除</el-button>
        </el-row>
      </el-dialog>
    </ul>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  data () {
    return {
      inputVal: '',
      lists: [],
      visible: false,
      index: 0
    }
  },
  methods: {
    addItem () {
      this.lists.push(this.inputVal)
      this.inputVal = ''
    },
    showMessage (index) {
      this.visible = true
      this.index = index
    },
    cancelDelete () {
      this.visible = false
    },
    deletItem () {
      this.lists.splice(this.index, 1)
      this.visible = false
    }
  }
  // components: {
  //   HelloWorld
  // }
}
</script>

<style>

</style>
