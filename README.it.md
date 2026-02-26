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

**Motore di analisi dell'accessibilità senza interfaccia utente che genera record di provenienza conformi a [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec).**

Progettato per essere utilizzato in combinazione con **a11y-assist**: questo motore individua i problemi e raccoglie prove verificabili; a11y-assist trasforma queste scoperte in soluzioni.

---

## Caratteristiche

- **Output deterministico**: lo stesso input produce sempre risultati identici e informazioni sulla provenienza.
- **Compatibile con prov-spec**: ogni risultato include prove verificabili crittograficamente.
- **Adatto per l'integrazione continua (CI)**: codici di uscita progettati per l'automazione.
- **Non richiede un browser**: analisi statica di file HTML.

---

## Installazione

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## Utilizzo

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

## Codici di uscita

| Code | Significato |
| ------ | --------- |
| 0 | Nessun risultato con gravità "errore" |
| 2 | Almeno un risultato con gravità "errore" |
| 3 | Errore interno del motore / input non valido |

---

## Regole (v0.1.0)

| ID della regola | Descrizione |
| --------- | ------------- |
| `html.document.missing_lang` | Elemento `<html>` privo dell'attributo `lang` |
| `html.img.missing_alt` | Elemento `<img>` privo dell'attributo `alt` |
| `html.form_control.missing_label` | Elemento di controllo del modulo privo dell'etichetta associata |
| `html.interactive.missing_name` | Elemento interattivo privo di un nome accessibile |

---

## Provenienza

Ogni risultato include tre record conformi a prov-spec:

1. **record.json**: Estrazione delle prove utilizzando `engine.extract.evidence.json_pointer`
2. **digest.json**: Hash SHA-256 delle prove standardizzate utilizzando `integrity.digest.sha256`
3. **envelope.json**: Risultato incapsulato utilizzando `adapter.wrap.envelope_v0_1`

Questi record possono essere verificati indipendentemente, senza dover fidarsi del motore.

---

## Correlati

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - Specifiche sulla provenienza
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - Strumenti MCP per l'accessibilità
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - Suggerimenti per la correzione
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - Dimostrazione con flussi di lavoro CI

---

## Licenza

[MIT](LICENSE)
