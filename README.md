# pmm-config

[![pre-commit](https://github.com/baker-scripts/pmm-config/actions/workflows/pre-commit.yml/badge.svg)](https://github.com/baker-scripts/pmm-config/actions/workflows/pre-commit.yml)
[![Release](https://img.shields.io/github/v/release/baker-scripts/pmm-config)](https://github.com/baker-scripts/pmm-config/releases)

Kometa (formerly Plex Meta Manager) configuration files for automated Plex library management: collections, metadata, overlays, and posters.

## Quick Start

1. Copy the files you want into your Kometa config directory, or clone this repo there.
2. Reference them from `collection_files`, `metadata_files`, or `overlay_files` in your own Kometa config. `config-clean.yml` does not load the other files here; it only uses Kometa defaults.
3. Run Kometa with a dry run first.

## Files

| Path | Kometa type | Contents |
| --- | --- | --- |
| `config-clean.yml` | main config | Libraries, Kometa defaults, and service settings with `<<SECRET_*>>` placeholders |
| `movies-best.yml` | collections | Best-of movie collections |
| `movies-collections.yml` | collections | Curated movie collections |
| `movies-general.yml` | collections | General movie metadata |
| `movies-holidays.yml` | collections | Holiday-themed collections |
| `movies-mcu.yml` | collections | Marvel Cinematic Universe collections |
| `movies-special.yml` | collections | Special and themed movie collections |
| `tv.yml` | collections | TV show collections |
| `tv-networks.yml` | collections | TV network collections |
| `tv-meta.yml` | metadata | TV show metadata |
| `networks.yml` | metadata | Network posters |
| `aired-refresh.yml` | collections | Hidden collections that refresh metadata for recently aired shows |
| `unmatched-refresh.yml` | collections | Hidden collection that retries matching for unmatched items |
| `video-overlays.yml` | overlays | Video overlay definitions (4K, HDR, Dolby) |
| `Overlays/` | | Overlay images |
| `Posters/` | | Collection posters, backgrounds, and logos |

## Configuration

Edit `config-clean.yml` before use. Every `<<SECRET_*>>` value is a placeholder; replace it or supply it through your own secret handling.

| Key | Setting |
| --- | --- |
| `plex` | `url` (default `http://plex:32400`) and `token` (`<<SECRET_PLEX>>`). Required. |
| `tmdb`, `tautulli`, `notifiarr` | `apikey` placeholders; Tautulli URL is `http://tautulli:8181/tautulli` |
| `radarr` | `url` (`http://radarr:7878/radarr`), `token`, `quality_profile: HD - Web`, `root_folder_path: /mnt/data/media/movies`, `tag: pmm` |
| `radarr.sonarr` | Nested under `radarr` in the file. `url` (written as `http://sonarr:8989/# sonarr`; the `# sonarr` suffix is part of the value, so fix it), `token`, `quality_profile: HD - Low`, `root_folder_path: /mnt/data/media/tv`, `tag: pmm` |
| `trakt` | `client_id` and `client_secret` placeholders; the stored `authorization` tokens are `[REMOVED]` |
| `settings.asset_directory` | `/config/assets` |

Library schedules (weekly by weekday) and per-collection Radarr tags (`PMM,PMM-<<collection_name>>`) are set per entry under `libraries`.

## Usage

- Validate YAML with `yamllint` or `pre-commit run --all-files`; CI runs the same pre-commit checks.
- Poster URLs in `movies-best.yml` point at `Posters/` on this repo's `main` branch. `networks.yml` and `tv-networks.yml` use posters from `Drapersniper/Posters`.
- Upstream: [Kometa](https://github.com/Kometa-Team/Kometa).

## Contributing

Issues and pull requests welcome. See the [contributing guidelines](https://github.com/baker-scripts/.github/blob/main/CONTRIBUTING.md); [open an issue](https://github.com/baker-scripts/pmm-config/issues) to discuss larger changes.

## Disclaimer

These configs are provided as-is with no warranty. Test with a Kometa dry run before applying them to your library. This project is not affiliated with or endorsed by Kometa or Plex.

## License

[MIT](LICENSE)
