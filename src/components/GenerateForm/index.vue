<template>
  <el-form :ref="name" :rules="rules" :model="data" label-width="100px" class="form-box">
    <item v-for="(value,key) in items"
      :rule-form="data"
      :prop="key" :options="value" :key="key">
    </item>
    <el-form-item>
      <el-button type="primary" @click="submitForm(name)">提交</el-button>
      <el-button type="primary" @click="resetForm(name)">重置</el-button>
      <el-button @click="cancel">取消</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
import Item from './form-item.vue'

export default {
  props: {
    name: String,
    items: Object,
    data: Object,
    rules: Object
  },

  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$emit('on-submit', this.data)
        } else {
          this.$emit('on-fail')
          return false
        }
      })
    },
    // 重置
    resetForm(formName) {
      this.$refs[formName].resetFields()
    },
    cancel() {
      this.$emit('on-cancel')
    }
  },

  components: {
    Item
  }
}
</script>

<style scoped>
  .form-box{
    margin-top: 20px;
    width: 60%;
  }
</style>
