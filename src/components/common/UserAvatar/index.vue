<script setup lang='ts'>
import { computed } from 'vue'
import { NAvatar } from 'naive-ui'
import { useUserStore } from '@/store'
import defaultAvatar from '@/assets/avatar.jpg'
import { isString } from '@/utils/is'

const userStore = useUserStore()

const userInfo = computed(() => userStore.userInfo)
</script>

<template>
  <div class="flex items-center">
    <div class="overflow-hidden">
      <template v-if="isString(userInfo.avatar) && userInfo.avatar.length > 0">
        <NAvatar :size="96" :src="userInfo.avatar" :fallback-src="defaultAvatar" />
      </template>
      <template v-else>
        <NAvatar :size="96" :src="defaultAvatar" />
      </template>
    </div>

    <div class="ml-2">
      <h1 class="overflow-hidden font-bold text-md text-ellipsis whitespace-nowrap">
        {{ userInfo.name ?? '睿畜科技' }}
      </h1>
    </div>
  </div>
</template>
