<template>
  <div class="count-container">
    倒计时
    <el-button @click="open('/index')" type="primary">返回</el-button>
  </div>
</template>

<script>
  export default {
    name: 'count',
    data: () => {
      return {
  
      }
    },
    computed: {

    },
    methods: {
      open (link) {
        this.$router.push(link)
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
