<template>
  <div class="container">
    <!-- <global-header :user="currentUser"></global-header> -->
    <!-- <column-list :list="list"></column-list> -->
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">邮箱地址</label>
      <input type="email" class="form-control" id="exampleInputEmail1" v-model="emailRef.val" @blur="validateEmail">
      <div id="emailHelp" class="form-text">提示信息：</div>
      <div class="form-text" v-if="emailRef.error"></div>
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">密码</label>
      <input type="password" class="form-control" id="exampleInputPassword1">
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import 'bootstrap/dist/css/bootstrap-grid.min.css';
import ColumnList, { type ColumnProps } from './components/ColumnList.vue';
import GlobalHeader, { type UserProops } from './components/GlobalHeader.vue';


//import ValidateInput, { RulesProp } from './components/ValidateInput.vue';
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
export default defineComponent({
  name: 'App',
  components: { ColumnList, GlobalHeader },
  setup() {
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
      }
    }
    //---------------------
    return {
      list: testData,
      //currentUser,
      emailRef,
      validateEmail
    }
  }

})
</script>



<style scoped></style>
