# pmm-config

Kometa (formerly Plex Meta Manager) configuration files for automated Plex library management.

## Structure
- `config-clean.yml` — Main Kometa config
- `movies-*.yml` — Movie collection configs (best-of, holidays, MCU, etc.)
- `tv*.yml` — TV show collection and metadata configs
- `networks.yml` — Network-based collections
- `video-overlays.yml` — Video overlay definitions
- `Overlays/` — Custom overlay images
- `Posters/` — Custom collection posters

## Conventions
- YAML files validated via `.yamllint`
- Collection configs are modular — one file per category
- Use PMM defaults from upstream where available
