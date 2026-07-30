# Carpathians Umbrel App Store

Community App Store based on the [Umbrel template](https://github.com/getumbrel/umbrel-community-app-store).

## Add on Umbrel

**App Store → Community App Stores → Add**

```text
https://github.com/carpathians/store
```

Then open the **Carpathians** store and install an app below.

If an app does not appear: remove the store, re-add it, or run on the Umbrel host:

```bash
sudo ~/umbrel/scripts/repo update
```

## Apps

| App | Folder / ID | Image | UI port |
| --- | --- | --- | --- |
| MRR AutoRent | `carpathians-mrr-autorent` | `ghcr.io/carpathians/mrr-autorent:latest` | 8742 |
| LLM Proxy | `carpathians-llm-proxy` | `ghcr.io/carpathians/llm-proxy:0.9.20` | 8788 |
| SplitMiner | `carpathians-miner-spliter` | `ghcr.io/carpathians/miner-spliter:latest` | 8755 |

App id **must** start with the store id (`carpathians-`), matching [Umbrel’s community store rules](https://github.com/getumbrel/umbrel-community-app-store).

## Layout

```text
umbrel-app-store.yml
carpathians-mrr-autorent/
  umbrel-app.yml
  docker-compose.yml
  icon.png
  gallery-1.png
carpathians-llm-proxy/
  umbrel-app.yml
  docker-compose.yml
  icon.png
  gallery-1.png
carpathians-miner-spliter/
  umbrel-app.yml
  docker-compose.yml
  icon.png
  gallery-1.png
```
