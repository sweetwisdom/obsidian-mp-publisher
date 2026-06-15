# Repository Guidelines

## 项目结构与模块组织
本仓库是一个基于 TypeScript 的 Obsidian 插件（`mp-publisher`）。

- `src/`：插件核心源码。
- `src/publisher/`：微信公众号发布能力。
- `src/settings/`：设置页与配置持久化。
- `src/themes/`、`src/styles/`：内置主题与样式层。
- `src/utils/`：通用工具（日志、路径、HTML 清理、公式处理等）。
- `custom/`：本地自定义 CSS 主题目录。
- `.github/workflows/release.yml`：基于 Git Tag 的发布流程。

入口文件为 `src/main.ts`，构建产物为 `main.js`（发布时同时包含 `manifest.json`、`styles.css`）。

## 构建、测试与开发命令
- `npm install`：安装依赖（建议 Node 18+，与 CI 一致）。
- `npm run dev`：开发模式构建（esbuild）。
- `npm run build`：执行 TypeScript 类型检查（`tsc -noEmit`）并产出生产构建。

当前未配置独立测试脚本，提交 PR 前至少执行一次 `npm run build`。

## 代码风格与命名规范
- 语言：TypeScript（ES Module 导入）。
- 缩进：2 空格；保持现有尾随逗号风格。
- 命名规范：
- 类/视图使用 `PascalCase`（如 `ThemeManagerView`）。
- 变量/函数使用 `camelCase`。
- 文件名按功能语义命名（如 `themeManager.ts`、`wechat.ts`）。
- 注释保持简洁，仅在逻辑不直观时补充说明。

## 测试指南
仓库暂未接入单元/集成测试框架，贡献时请执行：

- 提交前运行 `npm run build`。
- 在 Obsidian 中手动验证关键流程：预览、主题切换、复制、发布。
- 若修改 CSS/主题，请在 PR 附上前后对比截图。

## 提交与 Pull Request 规范
提交历史采用 Conventional Commits 风格，常见前缀：
- `feat: ...`
- `fix: ...`
- `docs: ...`
- `chore: ...`

建议小步提交、单一主题。PR 需包含：

- 面向用户的变更说明。
- 关联 Issue（如有）。
- 本地验证记录。
- 涉及 UI/主题时附截图或 GIF。

## 安全与配置提示
禁止提交真实微信公众号凭据（`AppID`、`AppSecret`）或私有仓库内容。漏洞反馈前请先阅读 `SECURITY.md`。
