# BootChain — Secure Boot Study Path (MCU → SoC)

📖 **Live docs site:** https://sprchuoi.github.io/securebootloader/

A structured, hands-on study repo covering **Secure Boot** concepts from a
simple **MCU** (Arm Cortex-M, e.g. STM32/nRF-class) up to a complex
**SoC/Application Processor** (Arm Cortex-A with TrustZone, ARM Trusted
Firmware, HLOS such as Linux/Android) — plus CA hierarchies, Secure
Enclave, Flash Secure Boot, SSL/TLS, and HSM key-signing operations.

All study content lives under [`docs/`](docs/index.md) and is published as
a browsable, searchable website (MkDocs Material, with live Mermaid
diagrams) via GitHub Pages — this is a **docs-as-code** setup: edit the
Markdown under `docs/`, push to `main`, and the site rebuilds and deploys
automatically (see `.github/workflows/deploy-docs.yml`).

## Repo layout

```
securebootloader/
├── docs/                        # All study content (published to GitHub Pages)
│   ├── index.md                 # Site home page (study roadmap)
│   ├── 00-foundations/ ... 16-standards-by-domain/
│   └── resources/                # Glossary + references
├── mkdocs.yml                    # Site config, nav, theme, Mermaid support
├── requirements.txt               # Python deps to build docs (mkdocs-material)
└── .github/workflows/deploy-docs.yml  # CI: builds & deploys to GitHub Pages
```

## Local development

```bash
python3 -m venv .venv-docs && source .venv-docs/bin/activate
pip install -r requirements.txt
mkdocs serve      # live preview at http://127.0.0.1:8000
mkdocs build      # static site output in ./site
```

## Deployment

On every push to `main`, GitHub Actions runs `mkdocs gh-deploy`, which
builds the site and publishes it to the `gh-pages` branch. Enable
**Settings → Pages → Source: Deploy from a branch → `gh-pages`** once,
after the first workflow run, if not already configured.

See [`docs/index.md`](docs/index.md) for the full study roadmap and
folder-by-folder sequence diagram.
