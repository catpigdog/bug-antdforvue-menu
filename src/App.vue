<template>
  <button @click="inlineCollapsed = !inlineCollapsed">tagg</button>
  <Menu v-model:selectedKeys="current" mode="inline" :items="items" :inlineCollapsed="inlineCollapsed" style="width: 200px" />
</template>

<script lang="ts" setup>
import { h, ref, computed } from 'vue';
import { Menu } from 'ant-design-vue'
import { AppstoreOutlined, SettingOutlined } from '@ant-design/icons-vue';
const current = ref<string[]>(['mail']);
const inlineCollapsed = ref(false)
const items = computed(() => [
  {
    key: 'sub1',
    icon: () => h(SettingOutlined),
    label: 'Navigation Three - Submenu',
    title: 'Navigation Three - Submenu',
    children: [
      {
        type: 'group',
        label: 'Item 1',
        children: [
          {
            label: h(AppstoreOutlined),
            title: 'setting:1',
            key: 'setting:1',
          },
          {
            label: 'Option 2',
            key: 'setting:2',
          },
        ],
      }
    ],
  }
]);

// items.value 执行下item.value就能暂时性解决此问题
</script>
