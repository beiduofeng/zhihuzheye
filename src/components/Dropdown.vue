<template>
    <div class="dropdown" ref="dropdowRef">
        <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" @click.prevent="toggleOpen">
            {{ title }}
        </a>
        <ul class="dropdown-menu" :style="{ display: 'block' }" v-if="isOpen">
            <li class="dropdown-item">
                <a href="#"></a>
            </li>
            <li class="dropdown-item">
                <a href="#"></a>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onUnmounted, watch } from 'vue'
import useClickOutside from '@/hooks/useClickOutside'
export default defineComponent({
    name: 'Dropdown',
    props: {
        title: {
            type: String,
            required: true
        }

    },
    setup() {
        const isOpen = ref(false)
        //用于挂载后获取dom节点
        const dropdownRef = ref<null | HTMLElement>(null)
        const toggleOpen = () => {
            isOpen.value = !isOpen.value
        }
        const isCLickOutside = useClickOutside(dropdownRef)

        watch(isCLickOutside, () => {
            if (isOpen.value && isCLickOutside.value) {
                isOpen.value = false
            }
        })
        return {
            isOpen,
            toggleOpen,
            dropdownRef
        }
    }

})
</script>

<style></style>