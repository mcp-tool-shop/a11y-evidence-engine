# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] — 2026-02-27

### Added

- Structured error handling with typed codes (INPUT_MISSING, INPUT_UNKNOWN_COMMAND, SCAN_FAILED)
- Verify script: test + CLI smoke + pack in one command
- Dependency audit job in CI
- Codecov upload in CI (Node 22.x)
- Threat model paragraph in README (Security & Data Scope)
- Shipcheck compliance: SHIP_GATE.md, SCORECARD.md

### Changed

- Bumped to v1.0.0 — production-stable
- SECURITY.md updated with real data scope
- CLI errors now emit structured `[CODE] message` format with hints

## [0.3.3] — 2026-02-25

### Added

- Landing page via @mcptoolshop/site-theme
- 7 translations (ja, zh, es, fr, hi, it, pt-BR)
- Brand logo in README

## [0.3.0] — 2026-02-24

### Added

- CI pipeline with Node 20/22 matrix, syntax check, CLI verification
- npm publish workflow (release-triggered)

## [0.1.0] — 2026-02-22

### Added

- Initial release
- HTML scanning with 4 rules: missing_lang, missing_alt, missing_label, missing_name
- prov-spec provenance records (record, digest, envelope)
- Deterministic finding IDs
- CLI with scan command and exit codes (0, 2, 3)
