# Carpathians App Store

Third-party app store for **ZimaOS** and **CasaOS**.

## Add the store

### ZimaOS

**Settings → App Store sources → Add**

```text
https://carpathians.github.io/store/store.json
```

### CasaOS

**App Store → Add source** (paste the ZIP URL)

```text
https://github.com/carpathians/store/archive/refs/heads/main.zip
```

Then open **Carpathians** and install an app below.

### Home Assistant

The same repository is a Home Assistant add-on store.

**Settings → Apps → Install app → ⋮ → Repositories**

```text
https://github.com/carpathians/store
```

Install **SplitMiner**, then set **Maximum virtual miners** on the add-on Configuration tab (1–16). The dashboard is `http://<home-assistant-ip>:3002`. Point ASICs at `stratum+tcp://<home-assistant-ip>:3333`.

## Apps

| App | Folder | Image | UI port |
| --- | --- | --- | --- |
| LLM Proxy | `Apps/LLM-Proxy` | `ghcr.io/carpathians/llm-proxy:0.9.30` | 8788 |
| Strata | `Apps/Strata` | `ghcr.io/niko1221/strata:0.2.9-cuda13` | 8088 |
| SplitMiner | `Apps/SplitMiner` | `ghcr.io/carpathians/miner-spliter:1.4.7` | 8755 |
| MRR AutoRent | `Apps/MRR-AutoRent` | `ghcr.io/carpathians/mrr-autorent:latest` | 8742 |

App identity is the reverse-domain `x-casaos.id` (`com.carpathians.*`). Persistent data lives under `/DATA/AppData/$AppID/data`.

## Layout

```text
repository.yaml
store-config.json
supported-languages.json
category-list.json
recommend-list.json
splitminer/
  config.yaml
Apps/LLM-Proxy/
  docker-compose.yml
  icon.svg
  icon.png
  screenshot-1.png
Apps/Strata/
  docker-compose.yml
  icon.png
  screenshot-1.png
  screenshot-2.png
Apps/SplitMiner/
  docker-compose.yml
  icon.svg
  icon.png
  screenshot-1.png
Apps/MRR-AutoRent/
  docker-compose.yml
  icon.png
  screenshot-1.png
```

ZimaOS consumes the built `dist/` on GitHub Pages. CasaOS reads the `Apps/` tree from the GitHub ZIP.

LLM Proxy follows IceWhale: pin a **version tag** that matches `x-casaos.version` (currently `:0.9.30`). Do not use `:latest`. Always ship the store bump in the same release as the llm-proxy `VERSION` / GHCR tag. Strata is the official upstream image and follows the same rule: the version tag matches `x-casaos.version` (`:0.2.9-cuda13`).

The CUDA 12 Maxwell `llama-server` tarball is a GitHub Release on this public repo (`llama-cuda12`), not a git file. The private llm-proxy repo cannot serve that download to a NAS.

## Notes

- **LLM Proxy GPU:** NVIDIA via the same ZimaOS `deploy` reservation as Ollama (Nvidia GPU) (`driver: nvidia`, `count: -1`).
- **Strata:** NVIDIA RTX 20/30/40/50, driver 580+, 12 GB+ VRAM, 32 GB+ RAM. The store entry ships `0.2.9-cuda13` and defaults to Qwen3.6-35B-A3B; set `FAMILY` / `MODEL` for Qwen3.8-Flash-Next or DeepSeek. GTX 10/Pascal, AMD, and Intel Arc need a different upstream image tag. No CPU-only path.
- **SplitMiner:** host ports 3333 and 4028–4043 must be free. Point ASICs at `stratum+tcp://YOUR_HOST_IP:3333`. Up to 16 virtual miners, one CG-API port each.
- **MRR AutoRent:** API key needs Rent = Write. The worker can spend MRR balance.
