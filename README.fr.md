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

**Moteur d'analyse de l'accessibilité sans interface utilisateur, qui génère des enregistrements de traçabilité au format [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec).**

Conçu pour fonctionner en complément de **a11y-assist** : ce moteur identifie les problèmes et collecte des preuves vérifiables ; a11y-assist transforme ces résultats en corrections.

---

## Fonctionnalités

- **Résultats déterministes** : les mêmes entrées produisent toujours les mêmes résultats et la même traçabilité.
- **Compatible avec prov-spec** : chaque résultat inclut des preuves vérifiables cryptographiquement.
- **Adapté aux environnements CI** : codes de sortie conçus pour l'automatisation.
- **Aucun navigateur requis** : analyse statique pure du code HTML.

---

## Installation

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## Utilisation

```bash
# Scan a file or directory
a11y-engine scan ./path/to/html --out ./results

# View help
a11y-engine --help
```

---

## Sortie

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

## Codes de sortie

| Code | Signification |
| ------ | --------- |
| 0 | Aucune anomalie détectée avec la sévérité "erreur". |
| 2 | Au moins une anomalie détectée avec la sévérité "erreur". |
| 3 | Erreur interne du moteur / entrée invalide. |

---

## Règles (v0.1.0)

| Identifiant de la règle | Description |
| --------- | ------------- |
| `html.document.missing_lang` | L'élément `<html>` est dépourvu de l'attribut `lang`. |
| `html.img.missing_alt` | L'élément `<img>` est dépourvu de l'attribut `alt`. |
| `html.form_control.missing_label` | Un élément de formulaire est dépourvu de son étiquette associée. |
| `html.interactive.missing_name` | Un élément interactif est dépourvu de son nom accessible. |

---

## Traçabilité

Chaque anomalie inclut trois enregistrements au format prov-spec :

1. **record.json** : Extraction des preuves à l'aide de `engine.extract.evidence.json_pointer`.
2. **digest.json** : Hachage SHA-256 des preuves canoniques à l'aide de `integrity.digest.sha256`.
3. **envelope.json** : Résultat encapsulé à l'aide de `adapter.wrap.envelope_v0_1`.

Ces enregistrements peuvent être vérifiés indépendamment, sans avoir à faire confiance au moteur.

---

## Liens connexes

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - Spécification de la traçabilité.
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - Outils MCP pour l'accessibilité.
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - Assistant de correction.
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - Démonstration avec des flux de travail CI.

---

## Licence

[MIT](LICENSE)
