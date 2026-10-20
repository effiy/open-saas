---
title: Open SaaS Blog (Starlight Starter Kit)
tags: [astro, starlight, blog, docs, template]
category: documentation
created: 2024-01-01
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# Open SaaS Blog

---

## 💡 概述

This is the blog and documentation starter for the Open SaaS template, built with Astro and the Starlight documentation framework. Based on the Starlight Starter Kit: Basics.

```
npm create astro@latest -- --template starlight
```

[![Built with Starlight](https://astro.badg.es/v2/built-with-starlight/tiny.svg)](https://starlight.astro.build)

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/starlight/tree/main/examples/basics)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/starlight/tree/main/examples/basics)

---

## ⚡ 功能

- 📖 **Markdown/MDX documentation** -- `.md` and `.mdx` files in `src/content/docs/` exposed as routes
- 🖼️ **Image support** -- embed images from `src/assets/` with relative links
- 🎯 **Static assets** -- favicons and static files in `public/` directory

---

## 📊 指標

「待補充」

---

## 🏛️ 设计

### Project Structure

Inside of your Astro + Starlight project, you'll see the following folders and files:

```
.
├── public/
├── src/
│   ├── assets/
│   ├── content/
│   │   ├── docs/
│   │   └── config.ts
│   └── env.d.ts
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

Starlight looks for `.md` or `.mdx` files in the `src/content/docs/` directory. Each file is exposed as a route based on its file name.

Images can be added to `src/assets/` and embedded in Markdown with a relative link.

Static assets, like favicons, can be placed in the `public/` directory.

---

## 📁 目录

- `public/` -- static assets (favicons, etc.)
- `src/assets/` -- images and assets
- `src/content/docs/` -- Markdown/MDX documentation content
- `src/content/config.ts` -- Starlight content configuration
- `src/env.d.ts` -- TypeScript environment declarations
- `astro.config.mjs` -- Astro + Starlight configuration
- `package.json` -- dependencies and scripts
- `tsconfig.json` -- TypeScript configuration

---

## 🔗 资源

- [Starlight's docs](https://starlight.astro.build/)
- [Astro documentation](https://docs.astro.build)
- [Astro Discord server](https://astro.build/chat)

---

## 🚀 快速开始

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

---

## ⚙️ 技术栈

- [Astro](https://astro.build) + [Starlight](https://starlight.astro.build/) -- documentation framework
- Markdown / MDX -- content authoring
- TypeScript