# Rensys v1.1 — documented model

This file summarizes the model described in the live user guide at https://renwaves.com/rensys/docs/. The live guide is the source of truth for the captured v1.1 behavior.

## Inputs documented

| Input | Documented range / options | Default |
|---|---|---|
| PV nominal peak power | 1–100 kWp, 0.5 kWp steps | 10 kWp |
| Module technology | Monocrystalline silicon (PERC), polycrystalline silicon, CdTe | Monocrystalline PERC |
| Array tilt | 0–90°, 1° steps | 30° |
| Array azimuth | −90° to +90°, 5° steps | 0° |
| Inverter efficiency | 90–99%, 0.5 percentage-point steps | 97.5% |
| Annual GHI | 500–2,800 kWh/m²/year, 25-unit steps | 1,750 kWh/m²/year |
| Location | City/address search or browser geolocation | Not set |

## Outputs

- Annual energy yield (kWh/year)
- Average daily yield (kWh/day), annual yield divided by 365
- Simplified performance ratio (%)
- Monthly energy-production profile
- Basic simulation activity log

## Equations documented

Estimated optimum tilt is a latitude-based rule of thumb, capped at 60°.

```text
orientation_factor =
  max(0.70, 1 - abs(tilt - estimated_optimum_tilt) * 0.002
          - abs(azimuth) * 0.0008)

performance_ratio =
  clamp(0.80 * technology_factor * (inverter_efficiency / 0.975),
        0.65, 0.90)

specific_yield = annual_GHI * orientation_factor * performance_ratio

annual_yield_kWh = system_peak_power_kWp * specific_yield
```

Technology factors documented in the guide:

- Monocrystalline PERC: 1.03
- Polycrystalline silicon: 1.00
- CdTe thin film: 0.98

Location lookup uses Open-Meteo geocoding. Solar climatology is requested from NASA POWER for the returned coordinates. Monthly shares are based on location climatology after a successful search; otherwise, the app uses a generic default monthly distribution.

## Known limitations documented

The current model does not separately simulate shading, soiling, hourly weather, snow, degradation, temperature profiles, cable losses, mismatch, string sizing, or detailed inverter behavior. The azimuth adjustment uses the absolute azimuth magnitude and does not distinguish east from west. Treat results as early-stage screening only; do not use them alone for guarantees, financing, permits, or final system design.

## Source references

- Live calculator: https://renwaves.com/rensys/
- User guide: https://renwaves.com/rensys/docs/
