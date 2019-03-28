<template>
  <div class="setting-container">
    设置
    <el-button @click="open('/index')" type="primary">返回</el-button>
  </div>
</template>

<script>
  export default {
    name: 'setting',
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
