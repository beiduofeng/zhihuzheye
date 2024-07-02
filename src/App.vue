<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <column-list :list="list"></column-list>

  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import 'bootstrap/dist/css/bootstrap-grid.min.css';
import ColumnList, { type ColumnProps } from './components/ColumnList.vue';
import GlobalHeader, { type UserProops } from './components/GlobalHeader.vue';
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
    return {
      list: testData,
      currentUser,
    }
  }

})
</script>



<style scoped></style>
