<p align="center">
  <a href="README.ja.md">日本語</a> | <a href="README.zh.md">中文</a> | <a href="README.es.md">Español</a> | <a href="README.fr.md">Français</a> | <a href="README.hi.md">हिन्दी</a> | <a href="README.it.md">Italiano</a> | <a href="README.pt-BR.md">Português (BR)</a>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/mcp-tool-shop-org/brand/main/logos/a11y-evidence-engine/readme.png" alt="a11y-evidence-engine" width="400">
</p>

<p align="center">
  <a href="https://github.com/mcp-tool-shop-org/a11y-evidence-engine/actions/workflows/ci.yml"><img src="https://github.com/mcp-tool-shop-org/a11y-evidence-engine/actions/workflows/ci.yml/badge.svg" alt="CI"></a>
  <a href="https://www.npmjs.com/package/@mcptoolshop/a11y-evidence-engine"><img src="https://img.shields.io/npm/v/@mcptoolshop/a11y-evidence-engine" alt="npm"></a>
  <a href="https://codecov.io/gh/mcp-tool-shop-org/a11y-evidence-engine"><img src="https://codecov.io/gh/mcp-tool-shop-org/a11y-evidence-engine/branch/main/graph/badge.svg" alt="Coverage"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow" alt="MIT License"></a>
  <a href="https://mcp-tool-shop-org.github.io/a11y-evidence-engine/"><img src="https://img.shields.io/badge/Landing_Page-live-blue" alt="Landing Page"></a>
</p>

**Headless accessibility evidence engine that emits [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) provenance records.**

Designed to pair with **a11y-assist**: this engine finds issues and captures verifiable evidence; a11y-assist turns those findings into fixes.

---

## Features

- **Deterministic output** -- same input always produces identical findings and provenance
- **prov-spec compatible** -- every finding includes cryptographically verifiable evidence
- **CI-friendly** -- exit codes designed for automation
- **No browser required** -- pure static HTML analysis

---

## Installation

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## Usage

```bash
# Scan a file or directory
a11y-engine scan ./path/to/html --out ./results

# View help
a11y-engine --help
```

---

## Output

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

## Exit Codes

| Code | Meaning |
|------|---------|
| 0 | No findings with severity `error` |
| 2 | At least one `error` finding |
| 3 | Internal engine failure / invalid input |

---

## Rules (v0.1.0)

| Rule ID | Description |
|---------|-------------|
| `html.document.missing_lang` | `<html>` element missing `lang` attribute |
| `html.img.missing_alt` | `<img>` element missing `alt` attribute |
| `html.form_control.missing_label` | Form control missing associated label |
| `html.interactive.missing_name` | Interactive element missing accessible name |

---

## Provenance

Each finding includes three prov-spec records:

1. **record.json**: Evidence extraction using `engine.extract.evidence.json_pointer`
2. **digest.json**: SHA-256 hash of canonical evidence using `integrity.digest.sha256`
3. **envelope.json**: Wrapped result using `adapter.wrap.envelope_v0_1`

These records are independently verifiable without trusting the engine.

---

## Related

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - Provenance specification
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - MCP tools for accessibility
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - Fix advisor
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - Demo with CI workflows

---

## Security & Data Scope

**Data touched:** HTML files passed as CLI arguments (read-only), findings and provenance written to `--out` directory. **Data NOT touched:** no files outside specified arguments and output directory, no OS credentials, no browser data. **No network egress** — all scanning is local. **No telemetry** is collected or sent.

## License

[MIT](LICENSE)

---

Built by <a href="https://mcp-tool-shop.github.io/">MCP Tool Shop</a>
