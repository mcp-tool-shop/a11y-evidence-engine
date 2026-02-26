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

**एक "हेडलेस" एक्सेसिबिलिटी जांच इंजन जो [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) प्रमाण रिकॉर्ड उत्पन्न करता है।**

यह इंजन **a11y-assist** के साथ काम करने के लिए डिज़ाइन किया गया है: यह इंजन समस्याओं का पता लगाता है और सत्यापन योग्य प्रमाण एकत्र करता है; a11y-assist उन निष्कर्षों को समाधानों में बदल देता है।

---

## विशेषताएं

- **निश्चित आउटपुट:** समान इनपुट हमेशा समान निष्कर्ष और प्रमाण उत्पन्न करता है।
- **prov-spec के साथ संगत:** प्रत्येक निष्कर्ष में क्रिप्टोग्राफिक रूप से सत्यापन योग्य प्रमाण शामिल होता है।
- **CI-अनुकूल:** स्वचालन के लिए डिज़ाइन किए गए एग्जिट कोड।
- **ब्राउज़र की आवश्यकता नहीं:** केवल स्थिर HTML विश्लेषण।

---

## स्थापना

```bash
npm install -g @mcptoolshop/a11y-evidence-engine
```

---

## उपयोग

```bash
# Scan a file or directory
a11y-engine scan ./path/to/html --out ./results

# View help
a11y-engine --help
```

---

## आउटपुट

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

## एग्जिट कोड

| Code | अर्थ |
| ------ | --------- |
| 0 | कोई भी गंभीर त्रुटि नहीं मिली। |
| 2 | कम से कम एक गंभीर त्रुटि मिली। |
| 3 | इंजन में आंतरिक त्रुटि / अमान्य इनपुट। |

---

## नियम (v0.1.0)

| नियम आईडी | विवरण |
| --------- | ------------- |
| `html.document.missing_lang` | `<html>` तत्व में `lang` विशेषता गायब है। |
| `html.img.missing_alt` | `<img>` तत्व में `alt` विशेषता गायब है। |
| `html.form_control.missing_label` | फॉर्म नियंत्रण में संबंधित लेबल गायब है। |
| `html.interactive.missing_name` | इंटरैक्टिव तत्व में सुलभ नाम गायब है। |

---

## प्रमाण

प्रत्येक निष्कर्ष में तीन prov-spec रिकॉर्ड शामिल हैं:

1. **record.json**: `engine.extract.evidence.json_pointer` का उपयोग करके प्रमाण निष्कर्षण।
2. **digest.json**: `integrity.digest.sha256` का उपयोग करके मानक प्रमाण का SHA-256 हैश।
3. **envelope.json**: `adapter.wrap.envelope_v0_1` का उपयोग करके लिपटे हुए परिणाम।

ये रिकॉर्ड इंजन पर भरोसा किए बिना स्वतंत्र रूप से सत्यापित किए जा सकते हैं।

---

## संबंधित

- [prov-spec](https://github.com/mcp-tool-shop-org/prov-spec) - प्रमाण विनिर्देश।
- [a11y-mcp-tools](https://github.com/mcp-tool-shop-org/a11y-mcp-tools) - एक्सेसिबिलिटी के लिए MCP उपकरण।
- [a11y-assist](https://github.com/mcp-tool-shop-org/a11y-assist) - समाधान सलाहकार।
- [a11y-demo-site](https://github.com/mcp-tool-shop-org/a11y-demo-site) - CI वर्कफ़्लो के साथ डेमो।

---

## लाइसेंस

[MIT](LICENSE)
