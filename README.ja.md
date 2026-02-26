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

**ヘッドレスアクセシビリティ検証エンジン。 [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) に準拠したトレーサビリティ情報を出力します。**

**a11y-assist** と連携するように設計されています。このエンジンは問題点を検出し、検証可能な証拠を収集し、a11y-assist はそれらの結果を修正に変換します。

---

## 機能

- **決定論的な出力:** 同じ入力に対して常に同じ結果（問題点とトレーサビリティ情報）を出力します。
- **prov-spec 準拠:** すべての問題点には、暗号学的に検証可能な証拠が含まれています。
- **CI 環境に最適:** 自動化のために設計された終了コードを提供します。
- **ブラウザ不要:** 静的な HTML ファイルのみを解析します。

---

## インストール

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

## 出力

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

## 終了コード

| Code | 意味 |
| ------ | --------- |
| 0 | `error` 以上の重大度を持つ問題点が見つからなかった |
| 2 | 少なくとも 1 つの `error` の重大度を持つ問題点が見つかった |
| 3 | エンジンの内部エラーまたは無効な入力 |

---

## ルール (v0.1.0)

| ルール ID | 説明 |
| --------- | ------------- |
| `html.document.missing_lang` | `<html>` 要素に `lang` 属性が設定されていない |
| `html.img.missing_alt` | `<img>` 要素に `alt` 属性が設定されていない |
| `html.form_control.missing_label` | フォームコントロールに関連するラベルが設定されていない |
| `html.interactive.missing_name` | インタラクティブな要素にアクセシブルな名前が設定されていない |

---

## トレーサビリティ

各問題点には、prov-spec に準拠した 3 つのレコードが含まれています。

1. **record.json**: `engine.extract.evidence.json_pointer` を使用して証拠を抽出します。
2. **digest.json**: `integrity.digest.sha256` を使用して、正規化された証拠の SHA-256 ハッシュ値を計算します。
3. **envelope.json**: `adapter.wrap.envelope_v0_1` を使用して結果をラップします。

これらのレコードは、エンジンを信頼しなくても、個別に検証することができます。

---

## 関連

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - トレーサビリティ仕様
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - アクセシビリティのための MCP ツール
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - 修正アドバイザー
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - CI ワークフローを使用したデモ

---

## ライセンス

[MIT](LICENSE)
