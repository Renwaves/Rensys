# Rensys

**Current baseline: v1.1**  
Repository: [KaramiLakeh/Rensys](https://github.com/KaramiLakeh/Rensys)  
Live application: [renwaves.com/rensys/](https://renwaves.com/rensys/)  
User guide: [renwaves.com/rensys/docs/](https://renwaves.com/rensys/docs/)

Rensys is a free, browser-based photovoltaic (PV) yield estimator. This repository is being bootstrapped from the currently published WordPress implementation and its published documentation. The initial files are a snapshot of the live page content retrieved on 2026-10-19, plus standalone HTML wrappers for local inspection.

## Repository contents

- `index.html` — standalone HTML snapshot of the Rensys v1.1 page content.
- `docs/index.html` — standalone HTML snapshot of the published user guide.
- `wordpress-export/rensys-page-content.html` — original WordPress page content, including its block markers.
- `wordpress-export/rensys-docs-page-content.html` — original WordPress documentation content, including its block markers.
- `docs/technical-model.md` — summary of the model and the controls documented for v1.1.

## v1.1 scope documented on the live site

The interface supports location search, nominal PV capacity, module technology, tilt, azimuth, inverter efficiency, and annual global horizontal irradiance (GHI). It reports estimated annual yield, average daily yield, performance ratio, and a monthly production profile. Location lookup uses Open-Meteo geocoding and solar climatology from NASA POWER.

The current model is a simplified screening estimate, not a bankable or permit-ready engineering simulation. See the technical notes and user guide for documented assumptions and limitations.

## Important implementation note

The published page was authored as WordPress Custom HTML blocks and may depend on the live WordPress theme, page structure, and browser-loaded libraries. The standalone HTML files are a **source snapshot for version control and review**, not yet a validated production deployment package. Test locally and compare behavior with the live site before using this repository as a replacement for WordPress.

No changes have been made to the live Renwaves site by creating this repository baseline. This snapshot does not deploy automatically to WordPress.

## Suggested workflow

1. Preserve this v1.1 snapshot as the reference baseline.
2. Build improvements on a separate feature branch for v1.2.
3. Separate calculation logic, data access, UI, and documentation as the project is refactored.
4. Add repeatable tests for equations, parameter boundaries, location-data failures, and monthly totals.
5. Review the diff and test the result before any live-site deployment.

## License

Rensys is licensed under the [Apache License 2.0](LICENSE) (`Apache-2.0`).

Copyright 2026 renwaves.com.
