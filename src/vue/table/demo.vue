<template>
  <div>
    <vbTable :conf="ctable.conf" :data="ctable.data" :action="ctable.action"></vbTable>
  </div>
</template>
<script>
import vbTable from './index';
export default {
  data() {
    return {
      ctable: {
        conf: [
          { prop: 'time', label: '历元时间-BJ', formatter: (row) => { return this.toBjTime(row, 'time') } },
          { prop: 'satLon', label: '经度' },
          { prop: 'satLat', label: '纬度' },
          { prop: 'satHeight', label: '高度' },
        ],
        data: [
          {
            time: 1593327762000,
            satLon: 'dasdas',
            satLat: 'satLat',
            satHeight: 'satHeight'
          },
          {
            time: 1593327792000,
            satLon: 'dasdas',
            satLat: 'satLat',
            satHeight: 'satHeight'
          }
        ],
        action: [
          { label: '更新', action: this.testVtable1 },
          { label: 'NICIA', action: this.testVtable2 },
          { label: 'BUZHIDAO', action: this.testVtable3 },
        ]
      }
    }
  },
  components: { vbTable },
  methods: {
    testVtable1() {},
    testVtable2() {},
    testVtable3() {},
  }
}
</script>
<style lang="less">
</style>