<template>
  <div class="main-container">
    <el-input v-model="inputValue" class="todo-input" placeholder="搜索/创建任务" >
      <i slot="prefix" v-if="inputValue === ''" class="el-input__icon el-icon-search"></i>
      <i v-show="inputValue !== ''" slot="suffix" class="el-input__icon el-icon-plus" @click="handleAddTodo"></i>
    </el-input>
    <div class="tip-container">{{amount}}件任务</div>
    <ul class="todo-item-container">
      <li v-for="(item, index) in todoList" :key="index">
        {{item}}
        <i slot="suffix" class="el-icon-delete" @click="handleDelete(index)"></i>
      </li>
    </ul>
    <div class="footer-container">
      <el-button-group>
        <el-button @click="open('/index')" type="primary" icon="el-icon-date"></el-button>
        <el-button @click="open('/count')" type="primary" icon="el-icon-loading"></el-button>
        <el-button @click="open('/setting')" type="primary" icon="el-icon-setting"></el-button>
      </el-button-group>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'main-layout',
    data: () => {
      return {
        todoList: [
          '吃饭',
          '睡觉',
          '敲代码',
          '走路'
        ],
        inputValue: ''
      }
    },
    computed: {
      amount: function () {
        return this.todoList.length
      }
    },
    methods: {
      open (link) {
        this.$router.push(link)
      },
      handleAddTodo () {
        this.todoList.push(this.inputValue)
        this.inputValue = ''
      },
      handleDelete (index) {
        this.todoList.splice(index, 1)
      }
    }
  }
</script>

<style lang="scss" scoped>
.main-container {
  text-align: center;
  background:
    radial-gradient(
      ellipse at top left,
      rgba(255, 255, 255, 1) 40%,
      rgba(229, 229, 229, .9) 100%
    );
  height: 100vh;
  padding: 10px 15px;
  width: 100vw;
  position: relative;
}

h1 {
  color: #6a6a6a;
  margin-right: 6px;
}

li {
  list-style: none;
}

.todo-input {
  width: 100%;
}

.tip-container {
  text-align: right;
  font-size: 12px;
  color: #c0c4cc;
  margin-top: 8px;
}

.todo-item-container {
  width: 100%;
}

.todo-item-container li {
  padding: 8px;
  border-bottom: 1px solid #f0f4ff;
  &:last-child {
    border: none
  }
  &:hover { background: #ccffff }
  i { 
    font-size: 16px;
    &:hover {
      cursor: pointer;
    }
  }
}

.footer-container {
  text-align: center;
  box-sizing: border-box;
  position: absolute;
  bottom: 20px;
  left: calc(50% - 83px);
}
</style>
