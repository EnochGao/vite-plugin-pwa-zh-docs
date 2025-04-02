---
title: 开始 | PWA Assets 生成器
prev: 常见问题解答 | 指南
outline: deep
---

# 开始

通过使用[sharp](https://github.com/lovell/sharp/) 和 [sharp-ico](https://github.com/ssnangua/sharp-ico)包，[@vite-pwa/assets-generator](https://github.com/vite-pwa/assets-generator)将会为您的 PWA 应用程序生成所有必需的图标。

该软件包是在[Elk PWA Icon Generator Script](https://github.com/elk-zone/elk/blob/main/scripts/generate-pwa-icons.ts)的基础上开发的

使用一个源图像，您可以通过 `@vite-pwa/assets-generator` [CLI](/assets-generator/cli) 或 [API](/assets-generator/api) 为 PWA 应用生成所需的所有图标

## 源图像

我们强烈建议使用 SVG 图像作为源图像，因为它们可以在不损失质量的情况下缩放到所需的大小，并且应该可以与任何图像类型一起使用。

SVG 源文件还可以用于在 HTML 头部链接中设置网站的图标

## PWA 最小图标要求

正如 [PWA 最低要求](/guide/pwa-minimal-requirements) 指出, 你需要:

- 一个 192x192 像素的图标（PWA Manifest 图标）
- 一个 512x512 像素的图标（PWA Manifest 图标）
- 一个适用于 iOS/MacOS 的 180x180 图标（HTML 头部链接： `<link rel="apple-touch-icon" href="/apple-touch-icon.png">` ）

我们还建议您添加以下内容:

- 一个适用于 Windows（Edge）的 64x64 图标（PWA Manifest 图标）
- 一个适用于Android带有`purpose: 'any'` 512x512 的图标(PWA Manifest 图标)
- 避免使用`purpose: 'any maskable'`图标，因为并非所有浏览器都支持
- 一个`favicon.ico`和`favicon.svg`， 有关更多详细信息查看[最小预设2023](#preset-minimal-2023) 

### Preset Minimal 2023 <Badge type="tip" text="新 从 v0.1.0" />

更多详细信息参考[Definitive edition of "How to Favicon" in 2023](https://dev.to/masakudamatsu/favicon-nightmare-how-to-maintain-sanity-3al7).

我们的最低建议是:

- 透明的 48x48 图标: 在html head中注册它: `<link rel="icon" href="/favicon.ico" sizes="48x48">`
- 使用SVG图像作为源图像: 在html head中注册它: `<link rel="icon" href="/favicon.svg" sizes="any" type="image/svg+xml">`
- 透明的 64x64 图标 (PWA Manifest icon)
- 透明的 192x192 图标 (PWA Manifest icon)
- 透明的 512x512 带有 `purpose: 'any'`图标 (PWA Manifest icon)
- 带有 `purpose: 'maskable'`的白色 512x512 图标  (PWA Manifest icon): 背景颜色可以根据需要进行自定义
- 用于iOS/MacOS白色 180x180 图标 (html head link: `<link rel="apple-touch-icon" href="/apple-touch-icon.png">`): 背景颜色可以根据需要进行自定义

### Preset Minimal <Badge type="danger" text="已弃用 从 v0.1.0" />

我们的最低建议是:

- 透明的 64x64 图标: 在html head中注册它: `<link rel="icon" href="/favicon.ico" sizes="any">`
- 使用SVG图像作为源图像: 在html head中注册它: `<link rel="icon" href="/favicon.svg" type="image/svg+xml">`
- 透明的 64x64 图标 (PWA Manifest icon)
- 透明的 192x192 图标 (PWA Manifest icon)
- 透明的 512x512 图标 带有 `purpose: 'any'` (PWA Manifest icon)
- 带有 `purpose: 'maskable'`白色 512x512 图标 (PWA Manifest icon): 背景颜色可以根据需要进行自定义
- 用于iOS/MacOS白色 180x180 图标 (html head link: `<link rel="apple-touch-icon" href="/apple-touch-icon.png">`): 背景颜色可以根据需要进行自定义

## 最小化预设使用案例

通过一个源图像，您可以使用包含在[@vite-pwa/assets-generator](https://github.com/vite-pwa/assets-generator)包中的`minimal-2023`预设生成图标，请查看[CLI](/assets-generator/cli)和[API](/assets-generator/api)文档以获取更多详细信息。

更新您的PWA清单图标条目:

```ts
icons: [
  {
    src: 'pwa-64x64.png',
    sizes: '64x64',
    type: 'image/png',
  },
  {
    src: 'pwa-192x192.png',
    sizes: '192x192',
    type: 'image/png',
  },
  {
    src: 'pwa-512x512.png',
    sizes: '512x512',
    type: 'image/png',
    purpose: 'any',
  },
  {
    src: 'maskable-icon-512x512.png',
    sizes: '512x512',
    type: 'image/png',
    purpose: 'maskable',
  },
];
```

并在入口点HTML head中使用以下条目:

### 使用 Preset Minimal 2023 <Badge type="tip" text="新 从 v0.1.0" />

```html
<head>
  <link rel="icon" href="/favicon.ico" sizes="48x48" />
  <link rel="icon" href="/favicon.svg" sizes="any" type="image/svg+xml" />
  <link rel="apple-touch-icon" href="/apple-touch-icon-180x180.png" />
</head>
```

### 使用 Preset Minimal <Badge type="danger" text="已弃用 从 v0.1.0" />

```html
<head>
  <link rel="icon" href="/favicon.ico" sizes="any" />
  <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
  <link rel="apple-touch-icon" href="/apple-touch-icon-180x180.png" />
</head>
```
