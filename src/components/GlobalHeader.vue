<template>
    <nav class="navbar navbar-dark bg-primary justify-content-between mb-4 px-4">
        <router-link class="navbar-brand" to="/">者也专栏</router-link>
        <ul v-if="!user.isLogin" class="list-inline mb-0">
            <li class="list-inline-item"><router-link to="/login" class="btn btn-outline-light my-2">登陆</router-link>
            </li>
            <li class="list-inline-item"><router-link to="/signup" class="btn btn-outline-light my-2">注册</router-link>
            </li>
        </ul>
        <ul v-else class="list-inline mb-0">
            <li class="list-inline-item">
                <dropdown :title="`你好 ${user.name}`"></dropdown>
            </li>
        </ul>
    </nav>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'
import Dropdown from './Dropdown.vue'
import 'bootstrap/dist/css/bootstrap.min.css'



export interface UserProops {
    column: any;
    nickName: any;
    isLogin: boolean;
    name?: string;
    id?: number;
}
export default defineComponent({
    name: 'GlobalHeader',
    components: {
        Dropdown
    },
    props: {
        user: {
            type: Object as PropType<UserProops>,
            required: true
        }
    }

})

</script>

<style></style>