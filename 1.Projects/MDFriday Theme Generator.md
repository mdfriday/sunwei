
# MDFriday AI-Native Theme Engineering Architecture

> 基于 Gal Bakal 2026 AKU（Atomic Knowledge Unit）框架  
> 场景：AI 动态生成 Hugo-compatible Theme，并通过 Validator 驱动修复与优化

---

# 1. 背景

MDFriday 是一个：

```txt
AI-native Content Compilation Runtime
```

核心能力：

- Markdown → Static Site
    
- Hugo-compatible Theme System
    
- Local-first
    
- Deterministic Build
    
- AI-Orchestrated Workflow
    
- Validator-Governed Execution
    

---

在 Theme Engineering 场景中：

LLM 不直接生成最终 Theme。

而是：

```txt
User Intent
    ↓
LLM Semantic Reasoning
    ↓
Theme Skills
    ↓
Blueprint Generation
    ↓
Runtime Compilation
    ↓
Validators
    ↓
Repair Loop
    ↓
Final Theme
```

---

# 2. 核心理论（Gal Bakal AKU Framework）

根据论文：

```txt
LLM 不应该直接生成最终结果
而应该工作在：

Validator-Governed Procedural Systems
```

因此：

---

## LLM 负责：

### Semantic Reasoning

例如：

```txt
Stripe Docs 风格
Apple 风格
极简
开发者文档
大 Hero
```

---

## Skills 负责：

### Procedural Knowledge

例如：

- docs site 需要哪些页面
    
- blog 需要哪些组件
    
- HERO component 如何组织
    
- sidebar 如何布局
    
- course site 如何组织 premium content
    

---

## Runtime 负责：

### Deterministic Compilation

例如：

```txt
Blueprint
    ↓
layouts/
partials/
assets/
theme.yaml
```

---

## Validators 负责：

### Correctness

例如：

- Layout 正确性
    
- HTML 结构完整性
    
- CSS 风格一致性
    
- 视觉相似度
    
- 构建成功率
    

---

# 3. 系统总体架构

```txt
User Intent
    ↓
Codex / Cursor Built-in LLM
    ↓
Skill Graph Planning
    ↓
Theme Blueprint Generation
    ↓
MCP Tool Invocation
    ↓
MDFriday Runtime
    ↓
Validators
    ↓
Repair Loop
    ↓
Theme Build
```

---

# 4. User Journey（完整流程）

---

# STEP 1 — 用户输入

用户：

- 打开 Obsidian Vault
    
- 提供参考站点
    
- 描述设计风格
    

例如：

```txt
@vault
@reference-site

Create a documentation theme.

Requirements:
- style similar to Stripe Docs
- dark mode
- minimal typography
- large hero section
- responsive
- developer focused
```

---

# STEP 2 — LLM Semantic Understanding

LLM 推断：

```yaml
siteType: documentation

style:
  - stripe-like
  - minimal
  - dark

requiredFeatures:
  - sidebar
  - toc
  - hero
  - search
```

---

# STEP 3 — Skill Graph Activation

动态生成：

```txt
detect-site-type
    ↓
resolve-required-pages
    ↓
resolve-required-components
    ↓
generate-theme-blueprint
    ↓
generate-theme-files
    ↓
validate-theme
    ↓
repair-theme
```

---

# STEP 4 — Theme Blueprint Generation

生成：

```yaml
theme:
  type: docs

pages:
  - home
  - docs
  - article
  - search

components:

  hero:
    variant: large-centered

  sidebar:
    collapsible: true

  toc:
    enabled: true

style:
  typography: minimal
  spacing: spacious
  theme: dark
```

---

# STEP 5 — Runtime Theme Compilation

MDFriday Runtime：

```txt
Blueprint
    ↓
Generate:
  layouts/
  partials/
  assets/
  theme.yaml
```

---

# STEP 6 — Validators

验证：

- HTML Structure
    
- CSS Structure
    
- Visual Similarity
    
- Responsive Layout
    
- Theme Build
    

---

# STEP 7 — Repair Loop

如果失败：

```txt
validate
   ↓
feedback
   ↓
repair
   ↓
rebuild
```

---

# 5. Skill Graph Topology

---

# Topology Structure

```txt
.skills/

  topology/
    graph.yaml

  nodes/

    detect-site-type.yaml
    resolve-docs-pages.yaml
    resolve-blog-pages.yaml

    resolve-docs-components.yaml
    generate-hero-spec.yaml

    generate-theme-blueprint.yaml
    generate-theme-files.yaml

    validate-layout.yaml
    validate-visual-similarity.yaml

  workflows/

    create-docs-theme.yaml
    create-blog-theme.yaml
```

---

# 6. Skill Graph Example

---

# topology/graph.yaml

```yaml
version: 1

nodes:

  - id: detect-site-type
  - id: resolve-pages
  - id: resolve-components
  - id: generate-blueprint
  - id: generate-theme-files
  - id: validate-layout
  - id: validate-visual-similarity
  - id: build-theme

edges:

  - from: detect-site-type
    to: resolve-pages

  - from: resolve-pages
    to: resolve-components

  - from: resolve-components
    to: generate-blueprint

  - from: generate-blueprint
    to: generate-theme-files

  - from: generate-theme-files
    to: validate-layout

  - from: validate-layout
    to: validate-visual-similarity
    condition: success

  - from: validate-layout
    to: generate-theme-files
    condition: failure

  - from: validate-visual-similarity
    to: build-theme
    condition: success
```

---

# 7. Atomic Skill Example

---

# generate-hero-spec.yaml

```yaml
id: generate-hero-spec

description: >
  Generate structured HERO component specification.

activationHints:
  - hero
  - landing page
  - banner
  - marketing

inputs:
  - site type
  - style intent

outputs:
  - hero blueprint

constraints:
  - semantic html
  - accessibility
  - responsive

toolBindings:
  - mdf_generate_component_spec

validators:
  - validate-hero-structure

continuations:
  success:
    - generate-theme-layouts
```

---

# 8. Component Blueprint

Blueprint 是：

```txt
LLM ↔ Runtime Contract
```

---

# HERO Example

```yaml
component:
  type: hero

html:
  semantic:
    - section
    - h1
    - p
    - cta-button

layout:
  alignment: center
  spacing: xl

style:
  background: gradient-dark
  typography: large-bold

responsive:
  mobileStack: true
```

---

# 9. Theme Blueprint（核心抽象）

Theme Blueprint：

```txt
不是最终 Theme
而是：
Procedural Intermediate Representation
```

---

# Example

```yaml
theme:
  type: documentation

pages:
  - home
  - article
  - search

components:
  hero:
    variant: large-centered

  sidebar:
    collapsible: true

layout:
  maxWidth: 1280px

style:
  typography: minimal
  spacing: spacious
  colorMode: dark
```

---

# 10. MCP Tool Design

MCP Tool：

```txt
必须 deterministic
不能依赖 AI reasoning
```

---

# Tool 1 — mdf_list_site_types

```json
{
  "name": "mdf_list_site_types"
}
```

返回：

```json
[
  "blog",
  "docs",
  "wiki",
  "course"
]
```

---

# Tool 2 — mdf_get_site_architecture

输入：

```json
{
  "siteType": "docs"
}
```

输出：

```json
{
  "requiredPages": [
    "home",
    "article",
    "search"
  ],

  "requiredComponents": [
    "sidebar",
    "toc",
    "search"
  ]
}
```

---

# Tool 3 — mdf_generate_theme_blueprint

输入：

```yaml
styleIntent:
  - stripe-like
  - minimal
  - dark
```

输出：

```yaml
themeBlueprint:
  ...
```

---

# Tool 4 — mdf_generate_theme_files

负责：

```txt
Blueprint
    ↓
layouts/
partials/
assets/
theme.yaml
```

---

# Tool 5 — mdf_build_theme

构建 Theme。

---

# Tool 6 — mdf_validate_theme

验证 Theme。

---

# Tool 7 — mdf_compare_visual_similarity

输入：

```txt
reference screenshot
generated screenshot
```

输出：

```json
{
  "layoutSimilarity": 0.88,
  "spacingSimilarity": 0.76
}
```

---

# 11. Validator Architecture

Validators：

```txt
是整个系统最关键部分
```

---

# Validator 1 — validate-layout-structure

检查：

```txt
docs site 是否包含：
- sidebar
- content area
- toc
```

---

# Validator 2 — validate-component-contract

检查：

```txt
hero component 是否包含：
- semantic section
- h1
- cta
```

---

# Validator 3 — validate-theme-build

检查：

```txt
theme 是否 build 成功
```

---

# Validator 4 — validate-visual-similarity

比较：

```txt
reference design
generated design
```

验证：

- spacing
    
- typography
    
- layout
    
- colors
    

---

# 12. Repair Loop

如果 Validator Fail：

```txt
validate
   ↓
feedback
   ↓
repair
   ↓
rebuild
```

例如：

```json
{
  "component": "hero",
  "problem": "spacing mismatch"
}
```

LLM：

```txt
Adjust hero spacing to match reference layout.
```

---

# 13. Runtime Responsibilities

MDFriday Runtime：

---

# Responsible For

- Theme Compilation
    
- HTML Generation
    
- CSS Generation
    
- Layout Assembly
    
- Hugo-Compatible Structure
    
- Static Build
    

---

# Not Responsible For

- Semantic Reasoning
    
- Intent Understanding
    
- Workflow Planning
    

这些由：

```txt
Codex / Cursor LLM
```

负责。

---

# 14. Dynamic Skill Graph vs Predefined Skill

---

# Predefined Skill

例如：

```txt
create-docs-theme
```

提供：

```txt
最佳实践 workflow
```

---

# Dynamic Skill Graph

LLM 根据：

- 用户需求
    
- 拓扑结构
    
- activationHints
    
- validator requirements
    

动态组合：

```txt
detect-site-type
    ↓
resolve-pages
    ↓
generate-sidebar
    ↓
generate-hero
    ↓
build-theme
```

---

# 15. 最终系统定义

MDFriday Theme System：

不是：

```txt
AI Theme Generator
```

而是：

```txt
AI-Native Theme Engineering Runtime
```

核心特点：

---

# 1. LLM-native

---

# 2. Skill-driven

---

# 3. Validator-governed

---

# 4. Runtime-deterministic

---

# 5. Hugo-compatible

---

# 6. Local-first

---

# 16. 最终核心思想

Gal Bakal 论文核心：

```txt
真正的瓶颈不是 Model Capability
而是：
Knowledge Architecture
```

MDFriday Theme Engineering：

通过：

```txt
Skill Graph
    +
Blueprint
    +
Validators
    +
Runtime
```

构建：

```txt
AI-Native Theme Compilation System
```