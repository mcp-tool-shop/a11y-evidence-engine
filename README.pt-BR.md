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

**Motor de análise de acessibilidade sem interface que gera registros de rastreabilidade [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec).**

Projetado para funcionar em conjunto com o **a11y-assist**: este motor identifica problemas e coleta evidências verificáveis; o a11y-assist transforma essas descobertas em soluções.

---

## Características

- **Saída determinística:** a mesma entrada sempre produz os mesmos resultados e informações de rastreabilidade.
- **Compatível com prov-spec:** cada descoberta inclui evidências verificáveis criptograficamente.
- **Compatível com CI:** códigos de saída projetados para automação.
- **Não requer navegador:** análise estática de HTML.

---

## Instalação

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## Uso

```bash
# Scan a file or directory
a11y-engine scan ./path/to/html --out ./results

# View help
a11y-engine --help
```

---

## Saída

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

## Códigos de Saída

| Code | Significado |
| ------ | --------- |
| 0 | Nenhuma descoberta com severidade "erro". |
| 2 | Pelo menos uma descoberta com severidade "erro". |
| 3 | Falha interna do motor / entrada inválida. |

---

## Regras (v0.1.0)

| ID da Regra | Descrição |
| --------- | ------------- |
| `html.document.missing_lang` | Elemento `<html>` sem o atributo `lang`. |
| `html.img.missing_alt` | Elemento `<img>` sem o atributo `alt`. |
| `html.form_control.missing_label` | Elemento de controle de formulário sem o rótulo associado. |
| `html.interactive.missing_name` | Elemento interativo sem um nome acessível. |

---

## Rastreabilidade

Cada descoberta inclui três registros prov-spec:

1. **record.json**: Extração de evidências usando `engine.extract.evidence.json_pointer`.
2. **digest.json**: Hash SHA-256 das evidências canônicas usando `integrity.digest.sha256`.
3. **envelope.json**: Resultado encapsulado usando `adapter.wrap.envelope_v0_1`.

Esses registros podem ser verificados independentemente, sem a necessidade de confiar no motor.

---

## Relacionado

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - Especificação de rastreabilidade.
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - Ferramentas MCP para acessibilidade.
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - Sugestões de correção.
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - Demonstração com fluxos de trabalho de CI.

---

## Licença

[MIT](LICENSE)
