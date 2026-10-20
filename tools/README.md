---
title: Open SaaS Tools
tags: [tools, bash, diff, patch, devops, scripting]
category: tools
created: 2024-01-01
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# Open SaaS Tools

---

## 💡 概述

Utility scripts for the Open SaaS monorepo, primarily the `dope.sh` (Diff Or Patch Executor) tool. This tool enables maintaining derived applications (like `opensaas-sh` and `template-test`) as small diffs on top of the base Open SaaS template, keeping them in the same repo without duplicating code.

Since derived apps (like `opensaas-sh` and `template-test`) are just the Open SaaS template with some small tweaks, and we want to keep them up to date as the template changes, we don't version the actual app code in git. Instead, we version the diffs between it and the template in an `opensaas-sh/app_diff/` directory.

---

## ⚡ 功能

- 📦 **Diff creation** -- generate minimal `.diff` files capturing changes between base and derived directories
- 🩹 **Patch application** -- apply `.diff` files onto a base directory to recreate a derived directory
- 📋 **File copying** -- `.copy` files for binary assets that can't be diffed
- 🍎 **macOS support** -- auto-detects macOS and uses GNU tools (`gpatch`, `grealpath`, `gdiff`)

---

## 📊 指標

「待補充」

---

## 🏛️ 设计

### dope.sh - Diff Or Patch Executor

The `dope.sh` script allows you to easily create a diff between two projects (base and derived), or to patch those diffs onto the base project to get the derived one. This is useful when a derived project has only small changes on top of the base project and you want to keep it in a directory in the same repo as the main project.

### Diff structure

The diff directory can contain `.diff` files to patch files from the base directory, and `.copy` files to copy files directly from the diff directory to the derived directory (useful for binary files).

---

## 📁 目录

「待補充」

---

## 🔗 资源

「待補充」

---

## 🚀 快速开始

### Usage

```sh
./dope.sh <BASE_DIR> <DERIVED_DIR> <ACTION>
```

- `<BASE_DIR>`: The base project directory (e.g., `base/app/` or `template/app/`)
- `<DERIVED_DIR>`: The derived project directory (e.g., `derived/app/` or `opensaas-sh/app/`)
- `<ACTION>`: Either `diff` or `patch`
  - `diff`: Creates a diff between the base and derived directories
  - `patch`: Applies existing diffs onto the base directory to recreate the derived directory

The diffs are stored in a directory named `<DERIVED_DIR>_diff/` (e.g., `derived/app_diff/` or `opensaas-sh/app_diff/`).

### Workflow

The typical workflow is:

1. Run `dope.sh` with the `patch` action to generate `derived/app/` from `base/app/` and `derived/app_diff/`:

   ```sh
   ./dope.sh base/app derived/app patch
   ```

2. If there are any conflicts (usually due to updates to the `base` app), modify `derived/app/` until you resolve them. Make any additional changes as needed.

3. Run `dope.sh` with the `diff` action to generate a new `derived/app_diff/` based on the updated `derived/app/`:

   ```sh
   ./dope.sh base/app derived/app diff
   ```

### Requirements

#### Running on macOS

If you're running the `dope.sh` script on macOS, install:

- `grealpath` (packaged within `coreutils`)
- `gpatch`
- `diffutils`

You can easily install them through `brew`:

```sh
brew install coreutils # contains grealpath
brew install gpatch
brew install diffutils
```

The script automatically detects macOS and uses `gpatch` instead of the default `patch` command.

---

## ⚙️ 技术栈

- Bash shell scripting
- GNU coreutils (`grealpath`)
- GNU patch (`gpatch`)
- GNU diffutils
- Homebrew (macOS dependency management)