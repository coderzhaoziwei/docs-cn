---
title: 全局图层
---

# 全局图层 {#global-layers}

> 自 v0.17 起可用

全局图层允许你拥有**持续存在**的跨幻灯片自定义组件。这对于有页脚、跨幻灯片动画、全局特效等来说可能很有用。

Slidev 为这种用法提供了两种图层，在你的项目根目录下创建 `global-top.vue` 或 `global-bottom.vue` 文件，它们会被自动识别。

图层关系：

- 全局顶层 (`global-top.vue`)
- 幻灯片
- 全局底层 (`global-bottom.vue`)

## 示例 {#example}

```html
<!-- global-top.vue -->
<template>
  <footer class="absolute bottom-0 left-0 right-0 p-2">Your Name</footer>
</template>
```

文字 `Your Name` 将出现在你所有幻灯片中。

如需有条件地启用它，你可以用 [Vue 全局上下文](/custom/vue-context)。

```html
<!-- 在第四页时隐藏页脚 -->
<template>
  <footer
    v-if="$slidev.nav.currentPage !== 4"
    class="absolute bottom-0 left-0 right-0 p-2"
  >
    Your Name
  </footer>
</template>
```

```html
<!-- "cover" 布局的情况下隐藏页脚 -->
<template>
  <footer
    v-if="$slidev.nav.currentLayout !== 'cover'"
    class="absolute bottom-0 left-0 right-0 p-2"
  >
    Your Name
  </footer>
</template>
```

```html
<!-- 一个显示页数的页脚示例 -->
<template>
  <footer
    v-if="$slidev.nav.currentLayout !== 'cover'"
    class="absolute bottom-0 left-0 right-0 p-2"
  >
    {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
  </footer>
</template>
```
