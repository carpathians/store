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

## Apps

| App | Folder | Image | UI port |
| --- | --- | --- | --- |
| LLM Proxy | `Apps/LLM-Proxy` | `ghcr.io/carpathians/llm-proxy:0.9.24` | 8788 |
| SplitMiner | `Apps/SplitMiner` | `ghcr.io/carpathians/miner-spliter:latest` | 8755 |
| MRR AutoRent | `Apps/MRR-AutoRent` | `ghcr.io/carpathians/mrr-autorent:latest` | 8742 |

App identity is the reverse-domain `x-casaos.id` (`com.carpathians.*`). Persistent data lives under `/DATA/AppData/$AppID/data`.

## Layout

```text
store-config.json
supported-languages.json
category-list.json
recommend-list.json
Apps/LLM-Proxy/
  docker-compose.yml
  icon.svg
  icon.png
  screenshot-1.png
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

## Notes

- **LLM Proxy GPU:** NVIDIA via the same ZimaOS `deploy` reservation as Ollama (Nvidia GPU) (`driver: nvidia`, `count: -1`).
- **SplitMiner:** host ports 3333 and 4028–4030 must be free. Point ASICs at `stratum+tcp://YOUR_HOST_IP:3333`.
- **MRR AutoRent:** API key needs Rent = Write. The worker can spend MRR balance.
