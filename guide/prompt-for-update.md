---
title: 新内容刷新提示 | 指南
outline: deep
---

# 新内容刷新提示

<prompt-for-update-img />

## 插件配置

因为这是 `registerType` 插件选项的默认行为，你不需要配置它

### 清理过期缓存

<CleanupOutdatedCaches />

<GenerateSWCleanupOutdatedCaches />

### Inject Manifest Source Map <Badge type="tip" text="新选项 自 v0.18.0+" />

<InjectManifestSourceMap />

### Generate SW Source Map

<GenerateSWSourceMap />

## 导入虚拟模块

您必须在 `main.ts` 或 `main.js` 文件中包含以下代码:

```ts
import { registerSW } from 'virtual:pwa-register';

const updateSW = registerSW({
  onNeedRefresh() {},
  onOfflineReady() {},
});
```

你需要:

- 在`onNeedRefresh`方法中向用户显示带有 刷新 和 取消 按钮的提示。
- 在`onOfflineReady` 方法中展示一个准备好离线工作带有 确认 按钮提示给用户。

当 `onNeedRefresh` 被调用，用户点击刷新按钮，然后会调用 `updateSW（）` 函数;页面将重新加载，并提供最新内容。

无论如何，当用户分别在`onNeedRefresh`或`onOfflineReady`情况下单击`取消`或`确认`按钮时，关闭相应的显示提示。

### SSR/SSG

<SsrSsg />
