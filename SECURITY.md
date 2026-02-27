# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | Yes       |
| 0.3.x   | No        |

## Reporting a Vulnerability

Email: **64996768+mcp-tool-shop@users.noreply.github.com**

Include:
- Description of the vulnerability
- Steps to reproduce
- Version affected
- Potential impact

### Response timeline

| Action | Target |
|--------|--------|
| Acknowledge report | 48 hours |
| Assess severity | 7 days |
| Release fix | 30 days |

## Scope

This tool operates **locally only** — it is a headless HTML accessibility scanner.

- **Data touched:** HTML files passed as CLI arguments (read-only), findings and provenance written to `--out` directory
- **Data NOT touched:** no files outside specified arguments and output directory, no OS credentials, no browser data
- **No network egress** — all scanning is local, no cloud calls
- **No secrets handling** — does not read, store, or transmit credentials
- **No telemetry** is collected or sent
