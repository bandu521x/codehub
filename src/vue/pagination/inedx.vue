<!-->
    Coder:  bandu;
    Date:   2020-06-26 10:40:05
    Desc:   封装的 element 分页组件
<-->
<template>
  <div class="pagination">
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :page-sizes="pageSizes"
      layout="total, sizes, prev, pager, next, jumper"
      :current-page="currentPage"
      :page-size="limit"
      :total="total"
    >
    </el-pagination>
  </div>
</template>

<script>
  export default {
    // name: 'pagination',
    data() {
      return {
        pageSizes: [10, 20, 30, 50, 80, 100],
      }
    },
    props: {
      // 避免直接改变prop属性
      currentPage: {
        type: Number,
        default: 1
      },
      total: {
        type: Number,
        default: 0
      },
      limit: {
        type: Number,
        default: 10
      },
    },
    watch: {
      currentPage(val) {
        // 改变这个值并不会触发 handleCurrentChange
        if (typeof val === 'number') {
          console.log('prop currentPage!!!');
          this.currentPage = val;
        }
      },
    },
    methods: {
      // 翻页
      handleCurrentChange(val) {
        console.log('ininin handleCurrentChange: ' + val)
        this.$emit('handleCurrentChange', val);
      },
      // size变化
      handleSizeChange(val) {
        // this.currentPage = 1;
        console.log('ininin  handleSizeChange: ' + val)
        this.$emit('handleSizeChange', val);
      }
    }
  }
</script>

<style scoped>
  .pagination {
    margin: 10px 0;
    text-align: right; /* 分页框出现的位置 */
  }
</style>
