---
title: Open SaaS Template Testing
tags: [testing, wasp, template, ci, release]
category: testing
created: 2024-01-01
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# Template Testing

---

## 💡 概述

Tests the production version of the Open SaaS template that users get from `wasp new app -t saas`.

**Why this exists:** As a part of our release checklist, we want to test that the production version of the Open SaaS template works.

**How it works:** We create a new Wasp app from the production Open SaaS template, and then modify the app to be production-ready (e.g. replace `Dummy` email service with `SMTP`, add Dotenv Vault with real credentials, etc.).

---

## ⚡ 功能

- ✅ **Production template validation** -- ensures `wasp new app -t saas` produces a working app
- 🔧 **App patching** -- applies production-ready modifications (SMTP, Dotenv Vault credentials) via diff/patch workflow
- 🧪 **Dev and prod mode testing** -- verifies app works in both `dev` and `build` modes
- 🔄 **Wasp release testing** -- part of the release checklist for new Wasp versions

---

## 📊 指標

「待補充」

---

## 🏛️ 设计

The `template-test` directory uses the same diff/patch workflow as `opensaas-sh` -- the actual `app/` directory is not versioned in git. Instead, diffs between the base template and the test app are stored and applied via scripts.

---

## 📁 目录

- `app/` -- generated directory (not versioned), created by `./tools/patch.sh`
- `tools/patch.sh` -- generates `app/` from template and diffs
- `tools/diff.sh` -- updates diffs after modifying `app/`

---

## 🔗 资源

- [Wasp](https://wasp.sh)
- [Open SaaS](https://opensaas.sh)

---

## 🚀 快速开始

### Testing a new Wasp release

When testing a new Wasp release:

```bash
cd template-test
# Create a new Wasp app and apply our patches to it.
./tools/patch.sh

cd app

# Get the environment variables from Dotenv Vault.
npm run env:pull

# Install dependencies.
wasp install

# Run the dev database and create migrations.
wasp db start
wasp db migrate-dev --name "init"

# You can stop the dev database after you created the migration.

# Test that the app works in dev and prod modes.
# Make sure the `@wasp.sh/wasp-app-runner` is updated to the latest version.
npx @wasp.sh/wasp-app-runner dev
npx @wasp.sh/wasp-app-runner build
```

### If you want to update the template test app

- Generate `app/` from template and diffs: `./tools/patch.sh`
- Modify the app in `app/` as needed and then update diffs: `./tools/diff.sh`

For detailed information about the diff/patch workflow and MacOS setup requirements, see [../tools/README.md](../tools/README.md).

---

## ⚙️ 技术栈

- [Wasp](https://wasp.sh) -- full-stack framework
- npm / Node.js runtime
- Dotenv Vault -- environment variable management
- `@wasp.sh/wasp-app-runner` -- dev and build testing tooling
- Diff/patch workflow via `tools/patch.sh` and `tools/diff.sh`