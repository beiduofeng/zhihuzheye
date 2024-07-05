<template>
  <div class="container">
    <!-- <global-header :user="currentUser"></global-header> -->
    <!-- <column-list :list="list"></column-list> -->
    <!-- 组件引入式 -->
    <ValidateForm-form @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <validate-input :rules="emailRules" v-model="emailVal" type="text" placeholder="请输入邮箱地址"
          ref="inputRef"></validate-input>

      </div>
      <div>
        <label class="form-label">密码</label>
        <validate-input :rules="passwordRules" v-model="passwordVal" type="password"
          placeholder="请输入密码"></validate-input>

      </div>
      <template #submit>
        <span class="btn btn-danger">Submit</span>
      </template>


    </ValidateForm-form>
    <!-- 组件引入式 -->

    <!-- <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">密码</label>
      <input type="password" class="form-control" id="exampleInputPassword1">
    </div> -->

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue';
import 'bootstrap/dist/css/bootstrap-grid.min.css';
import ColumnList, { type ColumnProps } from './components/ColumnList.vue';
import GlobalHeader, { type UserProops } from './components/GlobalHeader.vue';


import ValidateInput, { type RulesProp } from './components/ValidateInput.vue';
import ValidateForm from './components/ValidateForm.vue';
// const currentUser: UserProops = {
//   column: 1
//   nickName: sun,
//   isLogin: true,
// }

const testData: ColumnProps[] = [
  {
    id: 1,
    title: '铺先生',
    description: '这是test1的专栏，可以更新一下哦',
    avatar: ''
  },
  {
    id: 2,
    title: 'test2的专栏',
    description: '这是test1的专栏，可以更新一下哦',
    avatar: ''
  },
  {
    id: 2,
    title: 'test3的专栏',
    description: '这是test1的专栏，可以更新一下哦'
    //avatar: ''
  },
  {
    id: 2,
    title: 'test4的专栏',
    description: '这是test1的专栏，可以更新一下哦',
    avatar: ''
  },
]
const emailReg = /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
export default defineComponent({
  name: 'App',
  components: { ColumnList, GlobalHeader, ValidateInput, ValidateForm },
  setup() {
    const inputRef = ref<any>()
    const emailVal = ref('123@test.com')
    const emailRules: RulesProp = [
      { type: 'required', message: '电子邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]
    const passwordVal = ref('123')
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' }
    ]

    //form表单
    const emailRef = reactive({
      val: '',
      error: false,
      message: ''
    })
    const validateEmail = () => {
      if (emailRef.val.trim() === '') {
        emailRef.error = true
        emailRef.message = 'can not be empty'
      } else if (!emailReg.test(emailRef.val)) {
        emailRef.error = true
        emailRef.message = 'should be valid email'
      }
    }
    //---------------------
    const onFormSubmit = (result: boolean) => {

    }
    return {
      list: testData,
      //currentUser,
      emailRef,
      validateEmail,
      emailRules,
      emailVal,
      onFormSubmit,
      inputRef,
      passwordVal,
      passwordRules
    }
  }

})
</script>



<style scoped></style>
