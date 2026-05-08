# UrbanStudio Theme 2026

Shopify 自定义主题，基于 Dawn v15.0.0，用于 UrbanStudio 品牌电商店铺。

## 项目结构

```
UrbanStudio-theme2026/
├── assets/          # JS / CSS 静态资源（组件级拆分）
├── config/          # 主题设置
│   ├── settings_schema.json   # 主题设置字段定义
│   └── settings_data.json     # 主题设置当前值
├── layout/          # 全局布局模板
│   ├── theme.liquid           # 主布局（所有页面共用）
│   ├── ecom.liquid            # EComposer 页面构建器布局
│   └── password.liquid        # 密码页布局
├── locales/         # 多语言翻译文件（含 zh-CN）
├── sections/        # 可在 Shopify 主题编辑器拖拽的区块
├── snippets/        # 可复用的 Liquid 代码片段
└── templates/       # 页面模板（JSON 格式，声明 sections 组合）
```

## 技术栈

- **模板语言**：Liquid（Shopify）
- **样式**：原生 CSS，按组件拆分（`component-*.css`）
- **脚本**：原生 JS，无框架依赖
- **页面构建器**：EComposer（`ecom.liquid` / `ecom_*.liquid` 文件）
- **主题 CLI**：Shopify CLI (`shopify` 命令)

## 常用开发命令

```bash
# 登录 Shopify（首次或 token 过期时）
shopify auth login

# 启动本地预览开发服务（热更新）
shopify theme dev --store <your-store>.myshopify.com

# 推送主题到 Shopify（不发布，保存为草稿）
shopify theme push --unpublished

# 拉取线上主题到本地
shopify theme pull
```

## 代码规范

- Liquid 模板修改后，相关 `{% schema %}` 配置必须同步更新。
- CSS 按组件命名：`component-<name>.css`，避免全局污染。
- Snippets 应保持单一职责，不在 snippet 内再 `render` 复杂嵌套。
- 多语言字符串必须通过 `t:` 翻译键引用，不硬编码文案。
- EComposer 相关文件前缀为 `ecom_`，修改需注意兼容性。

## 分支规范

- `main`：线上稳定版本
- `zachAuth`：当前开发分支（认证相关功能）

## 注意事项

- `settings_data.json` 包含线上配置数据，谨慎覆盖。
- `header-group.json` / `footer-group.json` 定义全局 header/footer，修改影响全站。
- 颜色方案通过 `color_schemes` 设置统一管理，不要在 section 内硬编码颜色值。
