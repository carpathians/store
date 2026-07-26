# Carpathians Umbrel App Store

Community App Store based on the [Umbrel template](https://github.com/getumbrel/umbrel-community-app-store).

## Add on Umbrel

**App Store → Community App Stores → Add**

```text
https://github.com/carpathians/store
```

Then open the **Carpathians** store and install **MRR AutoRent**.

If an app does not appear: remove the store, re-add it, or run on the Umbrel host:

```bash
sudo ~/umbrel/scripts/repo update
```

## Apps

| App | Folder / ID | Image |
| --- | --- | --- |
| MRR AutoRent | `carpathians-mrr-autorent` | `ghcr.io/carpathians/mrr-autorent:latest` |

App id **must** start with the store id (`carpathians-`), matching [Umbrel’s community store rules](https://github.com/getumbrel/umbrel-community-app-store).

## Layout

```text
umbrel-app-store.yml
carpathians-mrr-autorent/
  umbrel-app.yml
  docker-compose.yml
  icon.svg
```
