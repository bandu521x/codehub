<template>
  <div class="tableBorder">
    <el-table stripe :data="data" style="width: 100%;border-radius: 4px;">
      <el-table-column
        v-for="col in conf"
        :key="col.prop"
        :prop="col.prop"
        :label="col.label"
        :formatter="col.formatter"
      ></el-table-column>
      <el-table-column fixed="right" label="操作" width="200" v-if="action.length !== 0">
        <template slot-scope="scope">
          <el-button v-for="(act, i) in action" :key="i" @click="act.action(scope.row, scope.$index)" type="text" size="small">{{act.label}}</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'VbTable',
  data() {
    return {}
  },
  props: {
    conf: {
      type: Array,
      default: () => []
    },
    data: {
      type: Array,
      default: () => []
    },
    action: {
      type: Array,
      default: () => []
    }
  },
  methods: {}
}
</script>

<style scoped>
.tableBorder {
  border: 1px solid #d3d3d3;
  border-radius: 4px;
}
</style>
