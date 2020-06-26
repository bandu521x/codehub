<!-->
    Coder:  bandu;
    Date:   2020-06-26 10:40:05
    Desc:   封装的 element 表单及table组件
<-->
<!-- 搜索表单 -->
<template>
  <el-form
    ref="editForm"
    :size="size"
    :inline="inline"
    :label-width="labelWidth"
    :model="data"
    :rules="rules"
  >
    <el-form-item v-for="item in conf" :label="item.label" :prop="item.prop" :key="item.label">

      <!-- 输入框 -->
      <el-input
        v-if="item.type==='input'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :style="{width:item.width}"
      ></el-input>


      <!-- 文本域 -->
      <el-input
        v-if="item.type==='textarea'"
        type="textarea"
        :disabled="item.disabled && item.disabled(data)"
        @change="item.change && item.change(data[item.prop])"
        v-model="data[item.prop]"
        :style="{width:item.width}"
      ></el-input>


      <!-- 下拉框 -->
      <el-select
        v-if="item.type==='select'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :style="{width:item.width}"
        :placeholder="item.placeholder"
      >
        <el-option v-for="op in item.options" :label="op.label" :value="op.value" :key="op.value"></el-option>
      </el-select>


      <!-- 单选 -->
      <el-radio-group
        v-if="item.type==='radio'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
      >
        <el-radio v-for="ra in item.radios" :label="ra.value" :key="ra.value">{{ra.label}}</el-radio>
      </el-radio-group>


      <!-- 单选按钮 -->
      <el-radio-group
        v-if="item.type==='radioButton'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        style="margin-right: 30px"
      >
        <el-radio-button v-for="ra in item.radios" :label="ra.value" :key="ra.value">{{ra.label}}</el-radio-button>
      </el-radio-group>



      <!-- 复选框 -->
      <el-checkbox-group
        v-if="item.type==='checkbox'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :style="{width:item.width}"
      >
        <el-checkbox v-for="ch in item.checkboxs" :label="ch.value" :key="ch.value">{{ch.label}}</el-checkbox>
      </el-checkbox-group>


      <!-- 日期 -->
      <el-date-picker
        v-if="item.type==='date'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :style="{width:item.width}"
      ></el-date-picker>


      <!-- 时间 -->
      <el-time-select
        v-if="item.type==='time'"
        v-model="data[item.prop]"
        type
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :style="{width:item.width}"
      ></el-time-select>


      <!-- 日期时间 -->
      <el-date-picker
        v-if="item.type==='dateTime'"
        type="datetime"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disable && item.disable(data[item.prop])"
        :style="{width:item.width}"
      ></el-date-picker>


      <!-- 滑块 -->
      <!-- <el-slider v-if="item.type==='Slider'" v-model="data[item.prop]"></el-slider> -->


      <!-- 开关 -->
      <el-switch
        v-if="item.type==='switch'"
        v-model="data[item.prop]"
        @change="item.change && item.change(data[item.prop])"
        :disabled="item.disabled && item.disabled(data)"
        :active-text="item.activeText"
        :inactive-text="item.inactiveText"
      ></el-switch>


      <!-- 上传 -->
      <el-upload
        v-if="item.type==='upload'"
        class="upload-demo"
        ref="upload"
        :action="item.action"
        :on-success="(response, file, fileList)=>item.success(that,response, file, fileList)"
        :auto-upload="item.autoUpload"
      >
        <el-button slot="trigger" size="small" type="primary">选取文件</el-button>
        <!-- <el-button style="margin-left: 10px;" size="small" type="success">上传到服务器</el-button> -->
        <div slot="tip" class="el-upload__tip">只能上传xlsx文件，且不超过500kb</div>
      </el-upload>



      <el-button v-if="item.type==='button'" @click="item.click" :type="btype" :size="item.size">{{item.title}}</el-button>

      <!-- 表格 -->
      <el-table v-if="item.type==='table'" index :data="data.table" style="width: 100%">
        <el-table-column type="index" label="#" align="center" width="50"></el-table-column>
        <el-table-column
          v-for="col in item.cols"
          :width="col.width"
          :key="col.prop"
          :prop="col.prop"
          :label="col.label"
          :formatter="col.formatter"
        ></el-table-column>
      </el-table>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  props: {
    that: { type: Object, default: this },
    labelWidth: {
      type: String,
      default: '100px'
    },
    inline: {
      type: Boolean,
      default: true
    },
    btype: {
      type: String,
      default: 'primary'
    },
    size: {
      type: String,
      default: 'small'
    },
    conf: {
      type: Array,
      default: () => []
    },
    data: {
      type: Object,
      default: () => { }
    },
    rules: {
      type: Object,
      default: null
    },
  },
  data() {
    return {};
  },
  methods: {
    // getThat(){
    //     this.$emit('that',this)
    // }
  }

}
</script>
<style>
</style>
