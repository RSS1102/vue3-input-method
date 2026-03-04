# vue3-input-method

> 🐛 **问题复现项目**：演示在 Vue 3 中，使用输入法（IME）输入时会意外触发父容器 `mouseleave` 事件的 Bug。

## 问题描述

在 Web 开发中，当用户在输入框内使用输入法（如中文/日文/韩文等 IME 输入法）进行输入时，浏览器会错误地触发父元素的 `mouseleave` 事件，即使鼠标并未真正离开该元素区域。

本项目提供了一个最小化的复现示例，便于分析和定位该问题。

## 技术栈

| 技术 | 版本 |
|------|------|
| Vue | ^3.5.25 |
| TypeScript | ~5.9.3 |
| Vite | ^7.3.1 |
| TDesign Vue Next | ^1.18.2 |
| @tdesign-vue-next/chat | ^0.4.6 |

## 项目结构

```
vue3-input-method/
├── src/
│   ├── App.vue        # 核心复现组件（包含 mouseleave 监听 + 输入框）
│   ├── main.ts        # 应用入口
│   └── style.css      # 全局样式
├── public/
│   └── vite.svg
├── index.html
├── vite.config.ts
└── package.json
```

## 核心复现代码

`src/App.vue` 中的关键逻辑：

```vue
<script setup lang="ts">
const onMouseLeave = (e: MouseEvent) => {
  console.log("onMouseLeave", e);
};
</script>

<template>
  <div class="card" @mouseleave="onMouseLeave">
    <input type="text" />
    输入框示例
  </div>
</template>
```

**复现步骤：**
1. 打开项目后，将鼠标移入灰色卡片区域
2. 在输入框中使用中文输入法输入内容
3. 打开浏览器控制台，观察 `onMouseLeave` 被触发

## 快速开始

### 安装依赖

```bash
pnpm install
```

### 启动开发服务器

```bash
pnpm dev
```

### 构建生产版本

```bash
pnpm build
```

### 预览构建产物

```bash
pnpm preview
```

## License

MIT
