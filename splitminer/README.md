# SplitMiner for Home Assistant

The app source repository is private. This public store is the add-on repository Home Assistant clones. The container is the public image `ghcr.io/carpathians/miner-spliter:1.4.0`.

## Install

1. In Home Assistant, open **Settings → Apps → Install app → ⋮ → Repositories**.
2. Add `https://github.com/carpathians/store`.
3. Install **SplitMiner** from the Carpathians section and start it.
4. Open the dashboard at `http://<home-assistant-ip>:3002`.
5. Point ASICs at `stratum+tcp://<home-assistant-ip>:3333`.

Config is stored in the add-on `/data` volume. The image is published for `amd64` and `aarch64` only.
