---
title: OpenSaas.sh Landing Page and Demo App
tags: [wasp, saas, demo, landing-page, astro]
category: project
created: 2024-01-01
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# OpenSaas.sh

---

## 💡 概述

This is the https://opensaas.sh page and demo app, built with the Open Saas template.

It consists of a Wasp app for showcasing the Open Saas template (+ landing page), while the Astro blog is blog and docs for the Open Saas template, found at https://docs.opensaas.sh.

Inception :)!

---

## ⚡ 功能

- 🌐 **Landing page** -- https://opensaas.sh marketing site
- 🧪 **Demo app** -- Wasp app showcasing the Open SaaS template, maintained via diff/patch workflow (`app_diff/`)
- 📖 **Blog and docs** -- Astro (Starlight) blog at https://docs.opensaas.sh providing documentation and blog content

---

## 📊 指標

「待補充」

---

## 🏛️ 设计

### Demo app (app_diff/)

> [!IMPORTANT]
> The in-development version of the template uses the in-development version of Wasp. We've set up the `./tools/wasp` script.
> To use it, whenever you would normally run `wasp <command>`, run `<path-to-repo>/tools/wasp <command>` instead.

Since the demo app is just the open saas template with some small tweaks, and we want to be able to easily keep it up to date as the template changes, we don't version (in git) the actual demo app code, instead we version the diffs between it and the template: `app_diff/`.

### Blog (blog/)

Blog (and docs in it) is currently tracked in whole, as it has quite some content, so updating it to the latest version of Open Saas is done manually, but it might be interesting to also move it to the `diff` approach, as we use for the demo app, if it turns out to be a good match.

For more info on authoring content for the docs and blog, including information on custom components, see the [blog/README.md](blog/README.md).

---

## 📁 目录

- `app_diff/` -- versioned diffs between the demo app and the base Open SaaS template
- `blog/` -- Astro + Starlight blog and documentation

---

## 🔗 资源

- [OpenSaaS.sh](https://opensaas.sh/)
- [Open SaaS Docs](https://docs.opensaas.sh/)

---

## 🚀 快速开始

### Workflow

- Generate `app/` from template and diffs: `./tools/patch.sh`
- Update diffs after modifying `app/`: `./tools/diff.sh`

For detailed information about the diff/patch workflow and macOS setup requirements, see [../tools/README.md](../tools/README.md).

### Deployment

App: check its README.md (after you generate it with `.tools/patch.sh`) .

Blog (docs): hosted on Netlify.

---

## ⚙️ 技术栈

- [Wasp](https://wasp.sh) -- full-stack framework for the demo app
- [Astro](https://astro.build) + [Starlight](https://starlight.astro.build) -- for blog and docs
- Diff/patch workflow via custom `tools/` scripts
- Netlify for blog/docs hosting