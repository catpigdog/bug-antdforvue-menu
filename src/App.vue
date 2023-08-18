<template>
  <div style="width: 256px">
    <Button type="primary" @click="toggleCollapsed">{{ state.collapsed ? '展开' : '收起' }}</Button>

    <Menu
      v-model:openKeys="state.openKeys"
      :selectedKeys="state.selectedKeys"
      :inline-collapsed="state.collapsed"
      :items="menus"
      mode="inline"
      theme="dark"
    ></Menu>
  </div>
</template>

<script setup>
import { reactive, computed, createVNode } from 'vue';
import { Button, Menu } from 'ant-design-vue'
import { HomeFilled, AccountBookFilled } from '@ant-design/icons-vue'

const state = reactive({
  collapsed: false,
  // collapsed: true,
  selectedKeys: ['test1'],
  openKeys: ['key1'],
  preOpenKeys: []
})

const menus = computed(() => [
  {
    name: 'key1',
    title: 'test1',
    icon: () => createVNode(HomeFilled),
    label: 'test1',
    children: [
      {
        name: 'key1-1',
        title: 'test1-1',
        label: createVNode(HomeFilled) // 用图标组件代替 实际情况是RouterLink组件
      }
    ]
  },
  {
    name: 'key2',
    title: 'test2',
    icon: () => createVNode(AccountBookFilled),
    label: 'test2',
    children: [
      {
        name: 'key2-1',
        title: 'test2-1',
        label: createVNode(AccountBookFilled)
      },
      {
        name: 'key2-2',
        title: 'test2-2',
        label: createVNode(AccountBookFilled)
      }
    ]
  }
])


const toggleCollapsed = () => {
  state.collapsed = !state.collapsed;
  if (state.collapsed) {
    state.openKeys = []
  }
}
</script>
