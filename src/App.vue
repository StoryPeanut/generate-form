<template>
  <div id="app">
    <generate-form
      name="from-test"
      @on-submit="onSubmit"
      :items="formRule"
      :data="data"
      :rules="rules">
    </generate-form>
  </div>
</template>

<script>
import GenerateForm from '@/components/GenerateForm'

export default {
  name: 'App',
  data() {
    return {
      formRule: { // 生成表单的数据
        user_id: {
          type: 'input',
          label: 'ID',
          disabled: true
        },
        date: {
          type: 'date',
          label: '时间',
          placeholder: '请选择时间'
        },
        name: {
          type: 'input',
          label: '用户名',
          placeholder: '请输入用户名'
        },
        account: {
          type: 'input',
          label: '账号',
          placeholder: '请输入账号'
        },
        sex: {
          type: 'radio',
          label: '性别',
          options: [{
            label: '男',
            value: '0'
          }, {
            label: '女',
            value: '1'
          }]
        },
        role: {
          type: 'select',
          label: '角色',
          placeholder: '请选择角色',
          options: [{
            label: '管理员',
            value: 'admin'
          }, {
            label: '编辑',
            value: 'edit'
          }]
        },
        autograph: {
          type: 'textarea',
          label: '个性签名',
          placeholder: '请输入您的个性签名'
        },
        label: {
          type: 'checkbox',
          label: '标签',
          options: [{
            label: '菜鸟',
            value: '0'
          },{
            label: '大神',
            value: '1'
          },{
            label: '不是人',
            value: '2',
            disabled: true
          }]
        },
        switchState: {
          type: 'switch',
          label: '开关'
        }
      },
      data: { // model数据
        user_id: '1234',
        date: '',
        name: '',
        account: '',
        sex: '0',
        role: '',
        autograph: '',
        label: [],
        switchState: false
      },
      rules: { // 表单验证
        name: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
        ],
        date: [
          { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
        ],
        account: [
          { required: true, message: '请输入账号', trigger: 'blur' },
          { min: 6, max: 16, message: '长度在 6 到 16 个字符', trigger: 'blur' }
        ],
        role: [
          { required: true, message: '请选择性别', trigger: 'change' }
        ],
        autograph: [
          { required: true, message: '不能为空', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    onSubmit(data) {
      console.log(data)
    }
  },
  components: {
    GenerateForm
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
