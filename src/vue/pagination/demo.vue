<template>
  <div>
    <vbPagination
      :currentPage="currentPage"
      :total="total"
      :limit="limit"
      @handleCurrentChange="currentChange"
      @handleSizeChange="sizeChange"
    ></vbPagination>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentPage: 1,
      total: 10,
      limit: 5,
    }
  },
  methods: {
    currentChange(val) {
      // console.log('main: ' + val);;
    },
    sizeChange(val) {
      // console.log('main: ' + val);;
    },
  }
}
</script>
<style lang="less">
</style>