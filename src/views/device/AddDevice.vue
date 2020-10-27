<template>
  <a-form :form="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="handleSubmit">
    <a-form-item label="设备名称">
      <a-input
        v-decorator="['deviceName', { rules: [{ required: true, message: '请输入设备名称' }] }]"
      />
    </a-form-item>
    <a-form-item label="设备描述">
      <a-input
        v-decorator="['description', { rules: [{ required: true, message: '请输入你对设备的描述' }] }]"
      />
    </a-form-item>
    <a-form-item label="模型名称">
      <a-select :size="size" initialValue="a1" v-decorator="['deviceModelRefName', { rules: [{ required: true, message: '请输入模型名称' }] }]">
        <a-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
          {{ (i + 9).toString(36) + i }}
        </a-select-option>
      </a-select>
    </a-form-item>
    <a-form-item label="选择属性">
      <a-select mode="tags" style="width: 100%" placeholder="Tags Mode" v-decorator="['deviceProperties', { rules: [{ required: true, message: '请选择属性' }] }]">
        <a-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
          {{ (i + 9).toString(36) + i }}
        </a-select-option>
      </a-select>
    </a-form-item>
    <a-form-item :wrapper-col="{ span: 12, offset: 5 }">
      <a-button type="primary" html-type="submit">
        创建
      </a-button>
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  name: 'AddDevice',
  data () {
    return {
      formLayout: 'horizontal'
    }
  },
  beforeCreate () {
    this.form = this.$form.createForm(this, { name: 'dynamic_form_item' })
    this.form.getFieldDecorator('keys', { initialValue: [], preserve: true })
  },
  methods: {
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    }
  }
}
</script>
