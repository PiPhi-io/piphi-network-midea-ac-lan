# Piphi Network Midea Ac Lan

Generated PiPhi integration runtime.

## Run locally

```bash
pdm install -G dev
pdm run uvicorn piphi_network_midea_ac_lan.main:app --reload --port 4208
pdm run pytest
pdm run python scripts/validate.py
```

The runtime listens on port `4208` by default and exposes the common PiPhi runtime route contract:

- `GET /health`
- `GET /diagnostics`
- `POST /discover`
- `POST /config`
- `POST /config/sync`
- `POST /deconfigure`
- `POST /deconfigure/{config_id}`
- `GET /state`
- `GET /contract`
- `GET /entities`
- `GET /events`
- `POST /events/device/{config_id}/example`
- `POST /telemetry/example`
- `POST /telemetry/device/{config_id}/example`
- `POST /command`

## Capability coverage

`capability-catalog.json` inventories the reviewed climate state, optional
features, energy and diagnostic telemetry, compatible appliance profiles,
events, conditions, actions, and protocol variants. Every entry is classified
as implemented, planned, or excluded. Contract tests enforce that only
implemented entries are advertised.

Device features remain planned until LAN discovery, protocol normalization,
per-model capability negotiation, safe command dispatch, and representative
fixtures exist. Tokens, keys, arbitrary attributes, and raw protocol commands
are never exposed through the runtime contract.

## Manifest

`manifest.json` is a starter manifest. Before publishing, update:

- `image`
- `version`
- capabilities and commands
- config fields and identity fields
- entity metadata

## Docker

```bash
docker build -t docker.io/piphinetwork/piphi-network-midea-ac-lan:0.1.0 .
docker run --rm -p 4208:4208 docker.io/piphinetwork/piphi-network-midea-ac-lan:0.1.0
```
