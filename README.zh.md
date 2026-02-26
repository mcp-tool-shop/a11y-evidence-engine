<p align="center">
  <a href="README.ja.md">日本語</a> | <a href="README.zh.md">中文</a> | <a href="README.es.md">Español</a> | <a href="README.fr.md">Français</a> | <a href="README.hi.md">हिन्दी</a> | <a href="README.it.md">Italiano</a> | <a href="README.pt-BR.md">Português (BR)</a>
</p>

<p align="center">
  
            <img src="https://raw.githubusercontent.com/mcp-tool-shop-org/brand/main/logos/a11y-evidence-engine/readme.png"
           alt="a11y-evidence-engine" width="400">
</p>

<p align="center">
  <a href="https://github.com/mcp-tool-shop-org/a11y-evidence-engine/actions/workflows/ci.yml"><img src="https://github.com/mcp-tool-shop-org/a11y-evidence-engine/actions/workflows/ci.yml/badge.svg" alt="CI"></a>
  <a href="https://www.npmjs.com/package/@mcptoolshop/a11y-evidence-engine"><img src="https://img.shields.io/npm/v/@mcptoolshop/a11y-evidence-engine" alt="npm"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow" alt="MIT License"></a>
  <a href="https://mcp-tool-shop-org.github.io/a11y-evidence-engine/"><img src="https://img.shields.io/badge/Landing_Page-live-blue" alt="Landing Page"></a>
</p>

**一个无头可访问性检测引擎，它会生成 [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) 溯源记录。**

该引擎旨在与 **a11y-assist** 配合使用：它会发现问题并捕获可验证的证据；a11y-assist 会将这些发现转化为修复方案。

---

## 特性

- **确定性输出**：相同的输入始终产生相同的发现和溯源信息。
- **与 prov-spec 兼容**：每个发现都包含密码学上可验证的证据。
- **适用于 CI 环境**：退出码设计用于自动化。
- **无需浏览器**：纯静态 HTML 分析。

---

## 安装

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## 使用方法

```bash
# Scan a file or directory
a11y-engine scan ./path/to/html --out ./results

# View help
a11y-engine --help
```

---

## 输出

```
results/
├── findings.json                    # All findings with metadata
└── provenance/
    └── finding-0001/
        ├── record.json              # engine.extract.evidence.json_pointer
        ├── digest.json              # integrity.digest.sha256
        └── envelope.json            # adapter.wrap.envelope_v0_1
```

---

## 退出码

| Code | 含义 |
| ------ | --------- |
| 0 | 没有发现任何严重程度为 `error` 的问题。 |
| 2 | 至少发现了一个严重程度为 `error` 的问题。 |
| 3 | 引擎内部错误 / 无效输入。 |

---

## 规则 (v0.1.0)

| 规则 ID | 描述 |
| --------- | ------------- |
| `html.document.missing_lang` | `<html>` 元素缺少 `lang` 属性。 |
| `html.img.missing_alt` | `<img>` 元素缺少 `alt` 属性。 |
| `html.form_control.missing_label` | 表单控件缺少关联的标签。 |
| `html.interactive.missing_name` | 交互式元素缺少可访问的名称。 |

---

## 溯源信息

每个发现都包含三个 prov-spec 记录：

1. **record.json**：使用 `engine.extract.evidence.json_pointer` 提取证据。
2. **digest.json**：使用 `integrity.digest.sha256` 计算规范证据的 SHA-256 哈希值。
3. **envelope.json**：使用 `adapter.wrap.envelope_v0_1` 包装结果。

这些记录可以在不信任引擎的情况下独立进行验证。

---

## 相关项目

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - 溯源规范
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - 用于可访问性的 MCP 工具
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - 修复建议工具
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - 包含 CI 工作流的演示站点

---

## 许可证

[MIT](LICENSE)
