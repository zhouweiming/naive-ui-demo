<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { NAutoComplete, NButton, NGradientText, NInput, useDialog, useMessage } from 'naive-ui'
import { computed, h, ref, type VNodeChild } from 'vue';


const prompt = ref<string>('')
const searchOptions = computed(() => [
  { value: '111111', label: '1' },
  { value: '222222', label: '2' }
])
const renderOption = (obj: { option: { label: string; value: string } }): VNodeChild => {
  return obj
    ? h('div',
      {
        class: 'wrapper',
      },
      [
        h('h4', { class: 'label' }, obj.option.label),
        h('p', { class: 'desc' }, obj.option.value),
      ])
    : undefined
}
</script>

<template>
  <header>
      <NAutoComplete
        v-model:value="prompt"
        :options="searchOptions"
        :render-option="renderOption"
      >
        <template #default="{ handleInput, handleBlur, handleFocus }">
          <NInput
            ref="inputRef"
            v-model:value="prompt"
            type="textarea"
            @input="handleInput"
            @focus="handleFocus"
            @blur="handleBlur"
          />
        </template>
      </NAutoComplete>
  </header>
</template>

<style scoped>
.wrapper {
  background-color: red;
}
:deep(.wrapper) {
  background-color: red;
}
</style>
